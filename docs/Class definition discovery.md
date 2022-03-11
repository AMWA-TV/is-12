# Class definition discovery

NC-Framework defines a class discovery mechanism which can be used for discovering details of class definitions. This is offered through a set of methods which exist in the `ncClassManager`. The `ncClassManager` can be discovered using the `GetMemberDescriptors` method shown in the earlier examples.

`Note`: Definitions are not provided for the base class and only contain properties, methods and events defined in the actual class. The controller SHOULD inquire further if the base class is not known. The identity information will contain a class ID which always contains the chain of inheritance (e.g. `"classID": [1,7,3]` shows that this class inherits from the class with `"classID": [1,7]`).

The `GetControlClass (3m1)` returns the definition of a class and requires an identity argument which consists of:

* ID - class ID numeric array
* version - the version of the class

Example for calling GetControlClass (3m1) on the Class Manager (using the oid retrieved from the root block - e.g. 201) when wanting to retrieve the class definition for ncReceiverMonitor (1,4,1)

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
          "classID": [1, 4, 1],
          "version": "1.0.0"
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
  "messageType": "CommandResponse",
  "sessionId": 101,
  "messages": [
    {
      "handle": 6,
      "result": {
        "status": 0,
        "value": [
          {
            "description": "NcReceiverMonitor class descriptor",
            "properties": [
              {
                "id": {
                  "level": 3,
                  "index": 1
                },
                "name": "connectionStatus",
                "typeName": "ncConnectionStatus",
                "readOnly": true,
                "persistent": false,
                "required": true
              },
              {
                "id": {
                  "level": 3,
                  "index": 2
                },
                "name": "connectionStatusMessage",
                "typeName": "ncString",
                "readOnly": true,
                "persistent": false,
                "required": true
              },
              {
                "id": {
                  "level": 3,
                  "index": 3
                },
                "name": "payloadStatus",
                "typeName": "ncPayloadStatus",
                "readOnly": true,
                "persistent": false,
                "required": true
              },
              {
                "id": {
                  "level": 3,
                  "index": 4
                },
                "name": "payloadStatusMessage",
                "typeName": "ncString",
                "readOnly": true,
                "persistent": false,
                "required": true
              },
              {
                "id": {
                  "level": 1,
                  "index": 1
                },
                "name": "classId",
                "typeName": "ncClassID",
                "readOnly": true,
                "persistent": true,
                "required": true
              },
              {
                "id": {
                  "level": 1,
                  "index": 2
                },
                "name": "classVersion",
                "typeName": "ncVersionCode",
                "readOnly": true,
                "persistent": true,
                "required": true
              },
              {
                "id": {
                  "level": 1,
                  "index": 3
                },
                "name": "oid",
                "typeName": "ncOid",
                "readOnly": true,
                "persistent": true,
                "required": true
              },
              {
                "id": {
                  "level": 1,
                  "index": 4
                },
                "name": "constantOid",
                "typeName": "ncBoolean",
                "readOnly": true,
                "persistent": true,
                "required": true
              },
              {
                "id": {
                  "level": 1,
                  "index": 5
                },
                "name": "owner",
                "typeName": "ncOid",
                "readOnly": true,
                "persistent": true,
                "required": true
              },
              {
                "id": {
                  "level": 1,
                  "index": 6
                },
                "name": "role",
                "typeName": "ncOid",
                "readOnly": true,
                "persistent": true,
                "required": true
              },
              {
                "id": {
                  "level": 1,
                  "index": 7
                },
                "name": "userLabel",
                "typeName": "ncOid",
                "readOnly": false,
                "persistent": true,
                "required": true
              },
              {
                "id": {
                  "level": 1,
                  "index": 8
                },
                "name": "lockable",
                "typeName": "ncOid",
                "readOnly": true,
                "persistent": true,
                "required": true
              },
              {
                "id": {
                  "level": 1,
                  "index": 9
                },
                "name": "lockState",
                "typeName": "ncOid",
                "readOnly": false,
                "persistent": false,
                "required": true
              },
              {
                "id": {
                  "level": 1,
                  "index": 10
                },
                "name": "touchpoints",
                "typeName": "ncTouchpoint",
                "readOnly": true,
                "persistent": true,
                "required": true
              }
            ],
            "methods": [
              {
                "id": {
                  "level": 3,
                  "index": 1
                },
                "name": "getStatus",
                "resultDatatype": "ncMethodResultReceiverStatus",
                "parameters": []
              },
              {
                "id": {
                  "level": 1,
                  "index": 1
                },
                "name": "get",
                "resultDatatype": "ncMethodResultPropertyValue",
                "parameters": [
                  {
                    "name": "id",
                    "typeName": "ncPropertyId",
                    "required": true
                  }
                ]
              },
              {
                "id": {
                  "level": 1,
                  "index": 2
                },
                "name": "set",
                "resultDatatype": "ncMethodResult",
                "parameters": [
                  {
                    "name": "id",
                    "typeName": "ncPropertyId",
                    "required": true
                  },
                  {
                    "name": "value",
                    "typeName": "",
                    "required": true
                  }
                ]
              },
              {
                "id": {
                  "level": 1,
                  "index": 3
                },
                "name": "clear",
                "resultDatatype": "ncMethodResult",
                "parameters": [
                  {
                    "name": "id",
                    "typeName": "ncPropertyId",
                    "required": true
                  }
                ]
              },
              {
                "id": {
                  "level": 1,
                  "index": 4
                },
                "name": "getCollectionItem",
                "resultDatatype": "ncMethodResultPropertyValue",
                "parameters": [
                  {
                    "name": "id",
                    "typeName": "ncPropertyId",
                    "required": true
                  },
                  {
                    "name": "index",
                    "typeName": "ncId32",
                    "required": true
                  }
                ]
              },
              {
                "id": {
                  "level": 1,
                  "index": 5
                },
                "name": "setCollectionItem",
                "resultDatatype": "ncMethodResult",
                "parameters": [
                  {
                    "name": "id",
                    "typeName": "ncPropertyId",
                    "required": true
                  },
                  {
                    "name": "index",
                    "typeName": "ncId32",
                    "required": true
                  },
                  {
                    "name": "value",
                    "typeName": "",
                    "required": true
                  }
                ]
              },
              {
                "id": {
                  "level": 1,
                  "index": 6
                },
                "name": "addCollectionItem",
                "resultDatatype": "ncMethodResultId32",
                "parameters": [
                  {
                    "name": "id",
                    "typeName": "ncPropertyId",
                    "required": true
                  },
                  {
                    "name": "value",
                    "typeName": "",
                    "required": true
                  }
                ]
              },
              {
                "id": {
                  "level": 1,
                  "index": 7
                },
                "name": "removeCollectionItem",
                "resultDatatype": "ncMethodResult",
                "parameters": [
                  {
                    "name": "id",
                    "typeName": "ncPropertyId",
                    "required": true
                  },
                  {
                    "name": "index",
                    "typeName": "ncId32",
                    "required": true
                  }
                ]
              },
              {
                "id": {
                  "level": 1,
                  "index": 8
                },
                "name": "lockWait",
                "resultDatatype": "ncMethodResult",
                "parameters": [
                  {
                    "name": "target",
                    "typeName": "ncOid",
                    "required": true
                  },
                  {
                    "name": "requestedLockStatus",
                    "typeName": "ncLockStatus",
                    "required": true
                  },
                  {
                    "name": "timeout",
                    "typeName": "ncTimeInterval",
                    "required": true
                  }
                ]
              },
              {
                "id": {
                  "level": 1,
                  "index": 9
                },
                "name": "abortWaits",
                "resultDatatype": "ncMethodResult",
                "parameters": [
                  {
                    "name": "target",
                    "typeName": "ncOid",
                    "required": true
                  }
                ]
              }
            ],
            "events": [
              {
                "id": {
                  "level": 1,
                  "index": 1
                },
                "name": "PropertyChanged",
                "eventDatatype": "ncPropertyChangedEventData"
              }
            ]
          }
        ]
      }
    }
  ]
}
```
