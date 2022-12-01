# Subscribing to events

A controller can subscribe to all events of an emitter object by using the `SubscriptionManager` found in the root block.

Example for calling AddSubscription (3m1) on the SubscriptionManager (using the oid retrieved from the root block - e.g. SubscriptionManager oid = 5) for a particular emitter object.

```json
{
  "protocolVersion": "1.0.0",
  "messageType": 2,
  "messages": [
    {
      "handle": 5,
      "oid": 5,
      "methodId": {
        "level": 3,
        "index": 1
      },
      "arguments": {
        "event": {
          "emitterOid": 98119,
          "eventId": {
            "level": 1,
            "index": 1
          }
        }
      }
    }
  ]
}
```

Example response from calling AddSubscription (3m1) on the SubscriptionManager (using the oid retrieved from the root block - SubscriptionManager oid = 5) for a particular emitter object.

```json
{
  "protocolVersion": "1.0.0",
  "messageType": 3,
  "messages": [
    {
      "handle": 5,
      "result": {
        "status": 0
      }
    }
  ]
}
```

Example notification for the PropertyChanged event (1e1) when the `userLabel` property (1p7) changes.

```json
{
  "protocolVersion": "1.0.0",
  "messageType": 6,
  "messages": [
    {
      "type": 0,
      "oid": 98119,
      "eventId": {
        "level": 1,
        "index": 1
      },
      "eventData": {
        "propertyId": {
          "level": 1,
          "index": 7
        },
        "changeType": 0,
        "propertyValue": "Input 1"
      }
    }
  ]
}
```
