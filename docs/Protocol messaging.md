# Protocol messaging

All protocol messages must have have the following 2 properties:

* protocolVersion - describes the version of this protocol (e.g. 1.0.0)
* messageType - describes the message type (e.g. Command)

`Note`: When sending messages, each message must contain a `handle` numeric identifier. This is then used when responses are received from the device for matching the responses to the messages sent by the controller. The `handle` has no programmatic significance for the device.

`Note`: All message results will return a response which inherits from the base `NcMethodResult` as specified in [MS-05-02](https://specs.amwa.tv/ms-05-02). This contains at the very least a status of type `NcMethodStatus` and an optional errorMessage of type `NcString`.

Data types:

| Property                   | JSON representation                       |
| -------------------------- | ----------------------------------------- |
| protocolVersion            | String value of the protocol version      |
| messageType                | Integer enum value as described below     |
| handle                     | Integer value of the message handle       |

```typescript
enum MessageType {
  Command = 0,
  CommandResponse = 1,
  Notification = 2,
}
```

## Control session

The control session context is delegated to the underlying WebSocket transport and its built in mechanisms for detecting communication failure.
When a communication failure occurs, then both the controller and the device MUST dispose of the current WebSocket connection. Controllers can open a new WebSocket connection, but any previous control context is lost and must be recreated (e.g. subscriptions have to be reissued and initial states have to be reacquired).

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
