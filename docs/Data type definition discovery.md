# Data type definition discovery

The `ncaClassManager` can also be used to discover data types using the `GetDataType` method.

The `GetDataType (3m2)` returns the definition of a data type and requires the type name as an argument.

Example for calling GetDataType (3m2) on the Class Manager (using the oid retrieved from the root block - e.g. 201) when wanting to retrieve the data type definition for `ncaConnectionStatus`

```json
{
  "protocolVersion": "1.0",
  "sessionId": 101,
  "messageType": "Command",
  "messages": [
    {
      "handle": 7,
      "oid": 201,
      "methodID": {
        "level": 3,
        "index": 2
      },
      "arguments":
      {
        "identity": {
          "name": "ncaConnectionStatus"
        }
      }
    }
  ]
}
```

Example response from calling GetDataType (3m2) on the Class Manager for data type `ncaConnectionStatus`

```json
{
  "protocolVersion": "1.0",
  "sessionId": 101,
  "messageType": "CommandResponse",
  "messages": [
    {
      "handle": 6,
      "result": {
        "status": 0,
        "value": {
          "name": "ncaConnectionStatus",
          "kind": 3,
          "info": [
            "Undefined",
            "Disconnected",
            "Connecting",
            "Connected",
            "ConnectionError"
          ]
        }
      }
    }
  ]
}
```

`ToBeDetermined`: If further type name uniqueness rules are required.
