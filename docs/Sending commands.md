# Sending commands

Example for settings the user label (1p7) on any ncObject using the generic set method (1m2) (requires arguments but does not return a value)

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
        "index": 2
      },
      "arguments": {
        "id": {
          "level": 1,
          "index": 7
        },
        "value": "My new label"
      }
    }
  ]
}
```

Example response for setting the user label (1p7) on any ncObject using the generic set method (1m2).

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

Example command for retrieving the classId (1p1) on any ncObject using the generic get method (1m1) (has no arguments but has a return value of `ncMethodResultPropertyValue` as specified in NC-Framework)

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
      },
      "arguments": {
        "id": {
          "level": 1,
          "index": 1
        }
      }
    }
  ]
}
```

Example response for retrieving the classId (1p1) on any ncObject using the generic get method (1m1).

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
        "value": [1, 7, 1]
      }
    }
  ]
}
```
