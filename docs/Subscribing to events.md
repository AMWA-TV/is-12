# Subscribing to events

A controller can subscribe to all events of an emitter object by using the `SubscriptionManager` found in the root block.

Example for calling AddSubscription (3m1) on the SubscriptionManager (using the oid retrieved from the root block - e.g. 150) for a particular emitter object.

```json
{
  "protocolVersion": "1.0",
  "sessionId": 101,
  "messageType": "Command",
  "messages": [
    {
      "handle": 5,
      "oid": 150,
      "methodID": {
        "level": 3,
        "index": 1
      },
      "arguments": {
        "event": {
          "emitterOid": 98119,
          "eventId": {
            "level": 1,
            "index": 2
          }
        }
      }
    }
  ]
}
```

Example response from calling AddSubscription (3m1) on the SubscriptionManager (using the oid retrieved from the root block - e.g. 150) for a particular emitter object.

```json
{
  "protocolVersion": "1.0",
  "sessionId": 101,
  "messageType": "CommandResponse",
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

Example notification for the PropertyChanged event (1e1) when the `role` property (1p6) changes.

```json
{
  "protocolVersion": "1.0",
  "sessionId": 101,
  "messageType": "Notification",
  "messages": [
    {
      "type": "Event",
      "oid": 7777,
      "eventID": {
        "level": 1,
        "index": 1
      },
      "eventData": {
        "propertyID": {
          "level": 1,
          "index": 6
        },
        "changeType": 0,
        "propertyValue": "input_1"
      }
    }
  ]
}
```
