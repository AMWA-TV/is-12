# Protocol messaging

All protocol messages must have have the following 2 properties:

* protocolVersion - describes the version of this protocol (e.g. 1.0)
* messageType - describes the message type (e.g. Command)

`Note`: When sending messages each message must contain a `handle` numeric identifier. This is then used when responses are received from the device for matching the responses to the messages sent by the controller. The `Heartbeat` message type does not contain any messages so does not require a `handle`. The `handle` has no programmatic significance for the device.

`Note`: All message results will return a response which inherits from the base `ncaMethodResult` as specified in NC-Framework. This contains at the very least a status of type `ncaMethodStatus` and an optional errorMessage of type `ncaString`.

Data types:

| Property                   | JSON representation                                                                                                                   |
| -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| protocolVersion            | String value of the protocol version                                                                                                  |
| messageType                | String enum with values: CreateSession, CreateSessionResponse, Command, CommandResponse, Notification, Heartbeat, HeartbeatResponse   |
| handle                     | Integer value of the message handle                                                                                                   |

## Session creation

When first connecting to a device, a controller MUST first ask for the creation of a session. This is achieved by sending a `CreateSession` message with a desired `heartBeatTime`. This value represents how often the controller MUST send messages back to the device to maintain the connection and session. If no control messages are sent in the interval the controller MUST send heartbeat messages as described in the `Heartbeats` subsection.

The device MUST respond with an `ncaMethodResultSessionID` result. If the creation of the session is successful the result will contain a session id value.  Alternatively if the creation failed it must signal the error status code and return an error message as specified by `ncaMethodResultSessionID`.

The controller MUST use the `session ID` for subsequent transactions with the device.

The `session ID` value type as specified in NC-Framework is `ncaSessionID`.

`Note`: All `CreateSession` message responses will return a `ncaMethodResultSessionID` result which inherits from the base `ncaMethodResult` as specified in NC-Framework.

## Command message type

Commands are clearly distinguished using the `Command` messageType.
Multiple messages MAY be sent in a `Command`.
Each message must have the following:

* handle - numeric message identification used for pairing the response
* oid - unique object id targeted by this message
* methodID - unique method ID specified as the level and index of the method inside the class.
* arguments - dictionary of arguments where the keys are the argument names and the values are their desired values (only needed if the method requires arguments)

Commands MUST be responded to by devices using the `CommandResponse` messageType and the matching `handle` for each message.

`Note`: All command results inherit from the base `ncaMethodResult` as specified in NC-Framework. This means all results MUST have a `status` property and MAY have an `errorMessage`.

`ToBeDetermined`: Mechanism to signal optional arguments/parameters in methods both in the framework classes and in the Class discovery mechanism.

## Notification message type

Notifications are clearly distinguished using the `Notification` messageType and are always send from the device to the controllers subscribed to a particular event.
Multiple messages MAY be sent in a `Notification`.
Each message must have the following:

* type - only value permitted currently is `Event`,
* oid - unique object id of the emitter
* eventID - unique event ID specified as a level and index.
* eventData - This must include the propertyID (`ncaPropertyID` in NC-Framework) of the property included in the event, the changeType (`ncaPropertyChangeType` in NC-Framework) and the return value.

## Heartbeats

Controllers MUST send heartbeats for their sessions at the intervals specified when creating the session if no other control messages are sent in that interval.

Devices MUST acknowledge each heartbeat with a response. If a heartbeat falls out of the interval they MUST signal the error.
