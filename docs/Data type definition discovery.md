# Data type definition discovery

`NcClassManager` can also be used to get the descriptors of all data types used be the device by getting the value of property `datatypes (3p2)`. Alternatively the `GetDataType (3m2)` method can be used to return a single datatype descriptor. This requires the following arguments:

* name - name of the data type of type `NcName`
* includeInherited - of type `NcBoolean` (if set the descriptor would contain all inherited elements)

Example for calling GetDataType (3m2) on the ClassManager (using the oid retrieved from the root block - e.g. ClassManager oid - 3) when wanting to retrieve the data type definition for `NcConnectionStatus`

```json
{
  "protocolVersion": "1.0.0",
  "messageType": 0,
  "commands": [
    {
      "handle": 7,
      "oid": 3,
      "methodId": {
        "level": 3,
        "index": 2
      },
      "arguments": {
        "name": "NcConnectionStatus",
        "includeInherited": false
      }
    }
  ]
}
```

Example response from calling GetDataType (3m2) on the ClassManager for data type `NcConnectionStatus`

```json
{
  "protocolVersion": "1.0.0",
  "messageType": 1,
  "responses": [
    {
      "handle": 7,
      "result": {
        "status": 200,
        "value": {
          "description": "Connection status enum data type",
          "name": "NcConnectionStatus",
          "type": 3,
          "constraints": null,
          "items": [
            {
              "description": "This is the value when there is no receiver",
              "name": "Undefined",
              "value": 0
            },
            {
              "description": "Connected to a stream",
              "name": "Connected",
              "value": 1
            },
            {
              "description": "Not connected to a stream",
              "name": "Disconnected",
              "value": 2
            },
            {
              "description": "A connection error was encountered",
              "name": "ConnectionError",
              "value": 3
            }
          ]
        }
      }
    }
  ]
}
```
