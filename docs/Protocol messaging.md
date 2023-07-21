# Protocol messaging

All protocol messages MUST have the messageType property to indicate the type of the message (e.g. Command).

* messageType - describes the message type (e.g. Command)

`Note`: When sending messages, each message MUST contain a `handle` numeric identifier. This is then used when responses are received from the device for matching the responses to the messages sent by the controller. The `handle` has no programmatic significance for the device.

`Note`: All message results MUST return a response which inherits from the base [NcMethodResult](https://specs.amwa.tv/ms-05-02/branches/v1.0-dev/docs/Framework.html#ncmethodresult) that contains a status of type [NcMethodStatus](https://specs.amwa.tv/ms-05-02/branches/v1.0-dev/docs/Framework.html#ncmethodstatus). If the method call encountered an error then the response result returned MUST inherit from [NcMethodResultError](https://specs.amwa.tv/ms-05-02/branches/v1.0-dev/docs/Framework.html#ncmethodresulterror) and include an errorMessage of type [NcString](https://specs.amwa.tv/ms-05-02/branches/v1.0-dev/docs/Framework.html#primitives).

Data types:

| Property                   | JSON representation                       |
| -------------------------- | ----------------------------------------- |
| messageType                | Integer enum value as described below     |
| handle                     | Integer value of the message handle       |

```typescript
enum MessageType {
  Command = 0,
  CommandResponse = 1,
  Notification = 2,
  Subscription = 3,
  SubscriptionResponse = 4,
  Error = 5
}
```

## Control session

The control session context is delegated to the underlying WebSocket transport and its built in mechanisms for detecting communication failure.
When a communication failure occurs, then both the controller and the device MUST dispose of the current WebSocket connection. Controllers can open a new WebSocket connection, but any previous control context is lost and has to be be recreated (e.g. subscriptions have to be reissued and initial states have to be reacquired).  
Under normal operating circumstances devices MUST keep the WebSocket connection open until the controller closes the connection.

Concurrency control is left to specific device implementations, however devices MUST always return relevant error messages and statuses when there are conflicts, errors or other noteworthy states (see [NcMethodResultError](https://specs.amwa.tv/ms-05-02/branches/v1.0-dev/docs/Framework.html#ncmethodresulterror) and [Error messages](#error-messages)).

## Command message type

Commands are clearly distinguished using the `Command` messageType.
Multiple messages MAY be sent in a `Command`.
Each message MUST have the following:

* handle - numeric message identification used for pairing the response
* oid - unique object id targeted by this message
* methodId - unique method ID specified as the level and index of the method inside the class.
* arguments - dictionary of arguments where the keys are the argument names and the values are their desired values (only needed if the method requires arguments)

Commands MUST be responded to by devices using the [CommandResponse](#command-response-message-type) messageType and the matching `handle` for each message.

## Command response message type

Command responses are clearly distinguished using the `CommandResponse` messageType.
Multiple messages MAY be sent in a `CommandResponse`.
Each message MUST have the following:

* handle - numeric message identification used for pairing the response with the associated command
* result - result returned by the command which inherits from the base [NcMethodResult](https://specs.amwa.tv/ms-05-02/branches/v1.0-dev/docs/Framework.html#ncmethodresult). This means all results MUST have a `status` property.

When a method call encounters an error the return MUST be [NcMethodResultError](https://specs.amwa.tv/ms-05-02/branches/v1.0-dev/docs/Framework.html#ncmethodresulterror) or a derived datatype.

## Notification message type

Notifications are clearly distinguished using the `Notification` messageType and are always sent from the device to the controllers subscribed to a particular event.
Multiple messages MAY be sent in a `Notification`.
Each message MUST have the following:

* oid - unique object id of the emitter
* eventId - unique event Id specified as a level and index.
* eventData - eventData ([NcPropertyChangedEventData](https://specs.amwa.tv/ms-05-02/branches/v1.0-dev/docs/Framework.html#ncpropertychangedeventdata) for property changed events).

## Subscription message type

Subscription messages are clearly distinguished using the `Subscription` messageType.
Each message MUST have the following:

* messageType - describes the message type
* subscriptions - Array of OIDs desired for subscription

Subscription messages MUST be responded to by devices using the `SubscriptionResponse` messageType.

## Subscription response message type

Subscription response messages are clearly distinguished using the `SubscriptionResponse` messageType.
Each message MUST have the following:

* messageType - describes the message type
* subscriptions - Array of OIDs which have successfully been added to the subscription list

Devices MUST return a response where all the original OIDs requested for subscribing which are valid are in the subscriptions array. Devices are responsible for filtering out invalid OIDs which cannot be subscribed to.

Here is one example.

```json
{
  "messageType": 4,
  "subscriptions": [
    1,
    100,
    111,
    10001
  ]
}
```

This allows controllers to know which items they have successfully subscribed to.

## Error messages

Error messages are clearly distinguished using the `Error` messageType.
Each message MUST have the following:

* messageType - describes the message type
* status - status of the message response. Must include the numeric values for NcMethodStatus or other types which inherit from it.
* errorMessage - error details associated with the failure

Error messages MUST be used by devices to return general error messages when more specific responses cannot be returned using the `CommandResponse` message (for example when incoming messages do not have messageType, handles or contain invalid JSON).
