# Protocol messaging

All protocol messages must have have the following 2 properties:

* protocolVersion - describes the version of this protocol (e.g. 1.0.0)
* messageType - describes the message type (e.g. Command)

`Note`: When sending messages, each message must contain a `handle` numeric identifier. This is then used when responses are received from the device for matching the responses to the messages sent by the controller. The `Heartbeat` message type does not contain any messages so does not require a `handle`. The `handle` has no programmatic significance for the device.

`Note`: All message results will return a response which inherits from the base `NcMethodResult` as specified in [MS-05-02](https://specs.amwa.tv/ms-05-02). This contains at the very least a status of type `NcMethodStatus` and an optional errorMessage of type `NcString`.

Data types:

| Property                   | JSON representation                       |
| -------------------------- | ----------------------------------------- |
| protocolVersion            | String value of the protocol version      |
| messageType                | Integer enum value as described below     |
| handle                     | Integer value of the message handle       |

```typescript
enum MessageType {
  CreateSession = 0,
  CreateSessionResponse = 1,
  Command = 2,
  CommandResponse = 3,
  Heartbeat = 4,
  HeartbeatResponse = 5
  Notification = 6,
}
```

## Session creation

When first connecting to a device, a controller MUST first ask for the creation of a session. This is achieved by sending a `CreateSession` message with a desired `heartBeatTime`. This value represents how often the controller MUST send messages back to the device to maintain the connection and session. If no control messages are sent in the interval the controller MUST send heartbeat messages as described in the `Heartbeats` subsection.

The device MUST respond with an `NcMethodResultSessionID` result. If the creation of the session is successful the result will contain a session id value. Alternatively if the creation failed it must signal the error status code and return an error message as specified by the base `NcMethodResult`.

The controller MUST use the `session ID` for subsequent transactions with the device.

The `session ID` value type is of type `NcSessionId` as specified in [MS-05-02](https://specs.amwa.tv/ms-05-02).

`Note`: All `CreateSession` message responses will return a `NcMethodResultSessionID` result which inherits from the base `NcMethodResult` as specified in [MS-05-02](https://specs.amwa.tv/ms-05-02).

## Command message type

Commands are clearly distinguished using the `Command` messageType.
Multiple messages MAY be sent in a `Command`.
Each message must have the following:

* handle - numeric message identification used for pairing the response
* oid - unique object id targeted by this message
* methodId - unique method ID specified as the level and index of the method inside the class.
* arguments - dictionary of arguments where the keys are the argument names and the values are their desired values (only needed if the method requires arguments)

Commands MUST be responded to by devices using the `CommandResponse` messageType and the matching `handle` for each message.

`Note`: All command results inherit from the base `NcMethodResult` as specified in [MS-05-02](https://specs.amwa.tv/ms-05-02). This means all results MUST have a `status` property and MAY have an `errorMessage`.

## Notification message type

Notifications are clearly distinguished using the `Notification` messageType and are always sent from the device to the controllers subscribed to a particular event.
Multiple messages MAY be sent in a `Notification`.
Each message must have the following:

* type - integer enum value for the `NcNotificationType` specified in [MS-05-02](https://specs.amwa.tv/ms-05-02). The options are: `Event` which are regular event notifications or `SubscriptionEnd` which is signaled when a subscription ends for any reason.
* oid - unique object id of the emitter
* eventId - unique event Id specified as a level and index.
* eventData - For notifications of type `Event` eventData is of type `NcPropertyChangedEventData` whereas for notifications of type `SubscriptionEnd` eventData is of type `NcSubscriptionEndEventData` (see [MS-05-02](https://specs.amwa.tv/ms-05-02) for type definitions).

## Heartbeats

Controllers MUST send heartbeats for their sessions at the intervals specified when creating the session if no other control messages are sent in that interval.

Devices MUST acknowledge each heartbeat with a response. If a heartbeat falls out of the interval they MUST signal the error.
