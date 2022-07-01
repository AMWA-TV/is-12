# Sending heartbeats

Example heartbeat message

```json
{
  "protocolVersion": "1.0.0",
  "sessionId": 101,
  "messageType": 4
}
```

Example heartbeat response when OK

```json
{
  "protocolVersion": "1.0.0",
  "messageType": 5,
  "sessionId": 101,
  "messages": [
    {
      "result": {
        "status": 0
      }
    }
  ]
}
```

Example heartbeat response when an error has occurred

```json
{
  "protocolVersion": "1.0.0",
  "messageType": 5,
  "sessionId": 101,
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
