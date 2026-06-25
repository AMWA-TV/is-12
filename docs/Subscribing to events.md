# Subscribing to events

A controller can subscribe to all OIDs it is interested in receiving notifications from by using the [Subscription](https://specs.amwa.tv/is-12/branches/v1.0.x/docs/Protocol_messaging.html#subscription-message-type) message.
Controllers always send the complete list of OIDs they want to hold active subscriptions for. Omitting a previously subscribed OID from the message's `subscriptions` array signals that the controller wishes to unsubscribe from it.

Example message for subscribing to multiple OIDs.

```json
{
  "messageType": 3,
  "subscriptions": [
    1,
    100,
    111,
    98119
  ]
}
```

Example [SubscriptionResponse](https://specs.amwa.tv/is-12/branches/v1.0.x/docs/Protocol_messaging.html#subscription-response-message-type) message received

```json
{
  "messageType": 4,
  "subscriptions": [
    1,
    100,
    98119
  ]
}
```

`Note` in this example, 111 was removed from the response subscriptions array because it was not a valid OID for subscribing.



Example message to unsubscribe all OIDs.

```json
{
  "messageType": 3,
  "subscriptions": []
}
```

Example message to unsubscribe a single previously subscribed OID.

```json
{
  "messageType": 3,
  "subscriptions": [
    100,
    111,
    98119
  ]
}
```

`Note` in this example, 1 was removed from the requests subscriptions array because the controller no longer wanted to subscribe to it.


Example notification for the PropertyChanged event (1e1) when the `userLabel` property (1p6) changes on object with OID 98119

```json
{
  "messageType": 2,
  "notifications": [
    {
      "oid": 98119,
      "eventId": {
        "level": 1,
        "index": 1
      },
      "eventData": {
        "propertyId": {
          "level": 1,
          "index": 6
        },
        "changeType": 0,
        "value": "Input 1",
        "sequenceItemIndex": null
      }
    }
  ]
}
```
