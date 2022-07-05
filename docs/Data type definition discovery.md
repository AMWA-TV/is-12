# Data type definition discovery

The `NcClassManager` can also be used to discover data types using the `GetDataType` method.

The `GetDataType (3m2)` returns a sequence of data type descriptors and requires the following arguments:

* name - name of the data type
* allDefs - boolean flag which if set will include descriptors of component datatypes

Example for calling GetDataType (3m2) on the ClassManager (using the oid retrieved from the root block - e.g. ClassManager oid - 3) when wanting to retrieve the data type definition for `NcConnectionStatus`

```json
{
  "protocolVersion": "1.0.0",
  "sessionId": 101,
  "messageType": 2,
  "messages": [
    {
      "handle": 7,
      "oid": 3,
      "methodId": {
        "level": 3,
        "index": 2
      },
      "arguments": {
        "name": "NcConnectionStatus"
      }
    }
  ]
}
```

Example response from calling GetDataType (3m2) on the ClassManager for data type `NcConnectionStatus`

```json
{
  "protocolVersion": "1.0.0",
  "messageType": 3,
  "sessionId": 101,
  "messages": [
    {
      "handle": 7,
      "result": {
        "status": 0,
        "value": [
          {
            "description": "Connection status enum data type",
            "name": "NcConnectionStatus",
            "type": 3,
            "constraints": null,
            "content": [
              {
                "description": "This is the value when there is no receiver",
                "name": "Undefined",
                "index": 0
              },
              {
                "description": "Connected to a stream",
                "name": "Connected",
                "index": 1
              },
              {
                "description": "Not connected to a stream",
                "name": "Disconnected",
                "index": 2
              },
              {
                "description": "A connection error was encountered",
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
