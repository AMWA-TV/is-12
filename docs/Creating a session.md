# Creating a session

Example session creation

```json
{
  "protocolVersion": "1.0.0",
  "messageType": 0,
  "messages": [
    {
      "handle": 1,
      "arguments": {
        "heartBeatTime": 5000
      }
    }
  ]
}
```

Example session creation response when OK

```json
{
  "protocolVersion": "1.0.0",
  "messageType": 1,
  "messages": [
    {
      "handle": 1,
      "result": {
        "status": 0,
        "value": 101
      }
    }
  ]
}
```

Example session creation response when an error has occurred

```json
{
  "protocolVersion": "1.0",
  "messageType":1,
  "messages": [
    {
      "handle": 1,
      "result": {
        "status": 2,
        "errorMessage": "Maximum number of sessions reached"
      }
    }
  ]
}
```
