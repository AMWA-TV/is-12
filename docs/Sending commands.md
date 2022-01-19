# Sending commands

Example command for calling setUserLabel (1m10) on any ncaObject (requires arguments but does not return a value)

```json
{
  "protocolVersion": "1.0",
  "sessionId": 101,
  "messageType": "Command",
  "messages": [
    {
      "handle": 2,
      "oid": 7777,
      "methodID": {
        "level": 1,
        "index": 10
      },
      "arguments": {
        "label": "My new label"
      }
    }
  ]
}
```

Example response for calling setUserLabel (1m10) on any ncaObject.

```json
{
  "protocolVersion": "1.0",
  "sessionId": 101,
  "messageType": "CommandResponse",
  "messages": [
    {
      "handle": 2,
      "result": {
        "status": 0
      }
    }
  ]
}
```

Example command for calling getClassIdentity (1m1) on any ncaObject (has no arguments but has a return value of `ncaMethodResultClassIdentity` as specified in NC-Framework)

```json
{
  "protocolVersion": "1.0",
  "sessionId": 101,
  "messageType": "Command",
  "messages": [
    {
      "handle": 2,
      "oid": 7777,
      "methodID": {
        "level": 1,
        "index": 1
      }
    }
  ]
}
```

Example response for calling getClassIdentity (1m1) on any ncaObject.

```json
{
  "protocolVersion": "1.0",
  "sessionId": 101,
  "messageType": "CommandResponse",
  "messages": [
    {
      "handle": 2,
      "result": {
        "status": 0,
        "identity": {
          "id": [1, 7, 1],
          "version": 1
        }
      }
    }
  ]
}
```
