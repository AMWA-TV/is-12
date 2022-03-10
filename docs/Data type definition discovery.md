# Data type definition discovery

The `ncClassManager` can also be used to discover data types using the `GetDataType` method.

The `GetDataType (3m2)` returns the definition of a data type and requires the type name as an argument.

Example for calling GetDataType (3m2) on the Class Manager (using the oid retrieved from the root block - e.g. 201) when wanting to retrieve the data type definition for `ncConnectionStatus`

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
      "arguments": {
        "name": "ncConnectionStatus"
      }
    }
  ]
}
```

Example response from calling GetDataType (3m2) on the Class Manager for data type `ncConnectionStatus`

```json
{
  "protocolVersion": "1.0",
  "messageType": "Command",
  "sessionId": 101,
  "messages": [
    {
      "handle": 7,
      "result": {
        "status": 0,
        "value": [
          {
            "name": "ncConnectionStatus",
            "type": 3,
            "content": [
              {
                "name": "Undefined",
                "index": 0
              },
              {
                "name": "Connected",
                "index": 1
              },
              {
                "name": "Disconnected",
                "index": 2
              },
              {
                "name": "ConnectionError",
                "index": 3
              }
            ]
          }
        ]
      }
    }
  ]
}
```

`ToBeDetermined`: If further type name uniqueness rules are required.
