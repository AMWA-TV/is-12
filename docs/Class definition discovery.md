# Class definition discovery

NC-Framework defines a class discovery mechanism which can be used for discovering details of class definitions. This is offered through a set of methods which exist in the `ncClassManager`. The `ncClassManager` can be discovered using the `GetMemberDescriptors` method shown in the earlier examples.

`Note`: Definitions are not provided for the base class and only contain properties, methods and events defined in the actual class. The controller SHOULD inquire further if the base class is not known. The identity information will contain a class ID which always contains the chain of inheritance (e.g. `"classID": [1,7,14]` shows that this class inherits from the class with `"classID": [1,7]`).

The `GetControlClass (3m1)` returns the definition of a class and requires an identity argument which consists of:

* ID - class ID numeric array
* version - the version of the class

Example for calling GetControlClass (3m1) on the Class Manager (using the oid retrieved from the root block - e.g. 201) when wanting to retrieve the class definition for ncReceiverMonitor (1,4,2)

```json
{
  "protocolVersion": "1.0",
  "sessionId": 101,
  "messageType": "Command",
  "messages": [
    {
      "handle": 6,
      "oid": 201,
      "methodID": {
        "level": 3,
        "index": 1
      },
      "arguments":
      {
        "identity": {
          "id": [1, 4, 2],
          "version": 1,
        }
      }
    }
  ]
}
```

Example response from calling GetControlClass (3m1) on the Class Manager for class ncReceiverMonitor (1,4,1)

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
          "identity": {
            "id": [1, 4, 2],
            "version": 1,
          },
          "name": "ncReceiverMonitor",
          "comments": "",
          "properties": [
            {
              "id": {
                "level": 3,
                "index": 1
              },
              "name": "connectionStatus",
              "typeName": "ncConnectionStatus"
            }
            ...
          ],
          "methods": [
            {
              "id": {
                "level": 3,
                "index": 1
              },
              "name": "GetStatus",
              "parameters": [
                {
                  "name": "label",
                  "typeName": "ncString"
                }
              ],
              "resultTypeName": "ncMethodResult"
            }
            ...
          ],
          "events": [
            {
              "ID": {
                "level": 50,
                "index": 100
              },
              "name": "exampleEvent",
              "eventDataTypeName": "exampleEventDataType"
            }
          ]
        }
      }
    }
  ]
}
```
