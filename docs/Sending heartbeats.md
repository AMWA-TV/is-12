# Sending heartbeats

```json
{
  "protocolVersion": "1.0",
  "sessionId": 101,
  "messageType": "Heartbeat"
}
```

Example heartbeat response when OK

```json
{
  "protocolVersion": "1.0",
  "sessionId": 101,
  "messageType": "HeartbeatResponse",
  "messages": [
    {
      "response": {
        "status": 0,
        "errorMessage": "Could not perform the action succesfully due to an internal error."
      }
    }
  ]
}
```

Example heartbeat response when an error has occurred

```json
{
  "protocolVersion": "1.0",
  "sessionId": 101,
  "messageType": "HeartbeatResponse",
  "messages": [
    {
      "response": {
        "status": 10,
        "errorMessage": "Heartbeat outside the required interval."
      }
    }
  ]
}
```
