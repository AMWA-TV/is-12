# Sending commands

Example for setting the user label (1p7) on any NcObject using the generic set method (1m2) (requires arguments but does not return a value)

```json
{
  "protocolVersion": "1.0.0",
  "messageType": 2,
  "messages": [
    {
      "handle": 2,
      "oid": 7777,
      "methodId": {
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

Example response for setting the user label (1p7) on any NcObject using the generic set method (1m2).

```json
{
  "protocolVersion": "1.0.0",
  "messageType": 3,
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

Example command for retrieving the classId (1p1) on any NcObject using the generic get method (1m1) (has no arguments but has a return value of `NcMethodResultPropertyValue` as specified in [MS-05-02](https://specs.amwa.tv/ms-05-02))

```json
{
  "protocolVersion": "1.0.0",
  "messageType": 2,
  "messages": [
    {
      "handle": 2,
      "oid": 7777,
      "methodId": {
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

Example response for retrieving the classId (1p1) on any NcObject using the generic get method (1m1).

```json
{
  "protocolVersion": "1.0.0",
  "messageType": 3,
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
