# Class definition discovery

[MS-05-02](https://specs.amwa.tv/ms-05-02) defines a class discovery mechanism which can be used for discovering details of class definitions. This is offered through a set of methods which exist in the `NcClassManager`. The `NcClassManager` can be found in the members of the root block as shown in the earlier examples.

The `GetControlClass (3m1)` returns a sequence of class descriptors and requires the following arguments:

* identity - of type `NcClassIdentity`
* allElements - boolean flag which if set will include inherited class elements in the descriptors

Example for calling GetControlClass (3m1) on the ClassManager (using the oid retrieved from the root block - e.g. ClassManager oid = 3) when wanting to retrieve the class definition for NcReceiverMonitor (1,2,1)

```json
{
  "protocolVersion": "1.0.0",
  "sessionId": 101,
  "messageType": 2,
  "messages": [
    {
      "handle": 6,
      "oid": 3,
      "methodId": {
        "level": 3,
        "index": 1
      },
      "arguments":
      {
        "identity": {
          "id": [1, 2, 2],
          "version": "1.0.0"
        },
        "allElements": true
      }
    }
  ]
}
```

Example response from calling GetControlClass (3m1) on the ClassManager for class NcReceiverMonitor (1,2,2)

```json
{
  "protocolVersion": "1.0.0",
  "messageType": 3,
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
                "description": "TRUE iff worker is enabled",
                "id": {
                  "level": 2,
                  "index": 1
                },
                "name": "enabled",
                "typeName": "NcBoolean",
                "readOnly": false,
                "persistent": true,
                "isNullable": false,
                "isSequence": false,
                "constraints": null
              },
              {
                "description": "Connection status property",
                "id": {
                  "level": 3,
                  "index": 1
                },
                "name": "connectionStatus",
                "typeName": "NcConnectionStatus",
                "readOnly": true,
                "persistent": false,
                "isNullable": false,
                "isSequence": false,
                "constraints": null
              },
              {
                "description": "Connection status message property",
                "id": {
                  "level": 3,
                  "index": 2
                },
                "name": "connectionStatusMessage",
                "typeName": "NcString",
                "readOnly": true,
                "persistent": false,
                "isNullable": true,
                "isSequence": false,
                "constraints": null
              },
              {
                "description": "Payload status property",
                "id": {
                  "level": 3,
                  "index": 3
                },
                "name": "payloadStatus",
                "typeName": "NcPayloadStatus",
                "readOnly": true,
                "persistent": false,
                "isNullable": false,
                "isSequence": false,
                "constraints": null
              },
              {
                "description": "Payload status message property",
                "id": {
                  "level": 3,
                  "index": 4
                },
                "name": "payloadStatusMessage",
                "typeName": "NcString",
                "readOnly": true,
                "persistent": false,
                "isNullable": true,
                "isSequence": false,
                "constraints": null
              },
              {
                "description": "Class identity",
                "id": {
                  "level": 1,
                  "index": 1
                },
                "name": "classId",
                "typeName": "NcClassId",
                "readOnly": true,
                "persistent": true,
                "isNullable": false,
                "isSequence": false,
                "constraints": null
              },
              {
                "description": "Class version",
                "id": {
                  "level": 1,
                  "index": 2
                },
                "name": "classVersion",
                "typeName": "NcVersionCode",
                "readOnly": true,
                "persistent": true,
                "isNullable": false,
                "isSequence": false,
                "constraints": null
              },
              {
                "description": "Object identifier",
                "id": {
                  "level": 1,
                  "index": 3
                },
                "name": "oid",
                "typeName": "NcOid",
                "readOnly": true,
                "persistent": true,
                "isNullable": false,
                "isSequence": false,
                "constraints": null
              },
              {
                "description": "TRUE iff OID is hardwired into device",
                "id": {
                  "level": 1,
                  "index": 4
                },
                "name": "constantOid",
                "typeName": "NcBoolean",
                "readOnly": true,
                "persistent": true,
                "isNullable": false,
                "isSequence": false,
                "constraints": null
              },
              {
                "description": "OID of containing block. Can only ever be null for the root block",
                "id": {
                  "level": 1,
                  "index": 5
                },
                "name": "owner",
                "typeName": "NcOid",
                "readOnly": true,
                "persistent": true,
                "isNullable": true,
                "isSequence": false,
                "constraints": null
              },
              {
                "description": "role of obj in containing block",
                "id": {
                  "level": 1,
                  "index": 6
                },
                "name": "role",
                "typeName": "NcName",
                "readOnly": true,
                "persistent": true,
                "isNullable": false,
                "isSequence": false,
                "constraints": null
              },
              {
                "description": "Scribble strip",
                "id": {
                  "level": 1,
                  "index": 7
                },
                "name": "userLabel",
                "typeName": "NcString",
                "readOnly": false,
                "persistent": true,
                "isNullable": false,
                "isSequence": false,
                "constraints": null
              },
              {
                "description": "Flag signalling if the object can be locked",
                "id": {
                  "level": 1,
                  "index": 8
                },
                "name": "lockable",
                "typeName": "NcBoolean",
                "readOnly": true,
                "persistent": true,
                "isNullable": false,
                "isSequence": false,
                "constraints": null
              },
              {
                "description": "Enum property exposing the lock state",
                "id": {
                  "level": 1,
                  "index": 9
                },
                "name": "lockState",
                "typeName": "NcLockState",
                "readOnly": false,
                "persistent": false,
                "isNullable": false,
                "isSequence": false,
                "constraints": null
              },
              {
                "description": "Touchpoints to other contexts",
                "id": {
                  "level": 1,
                  "index": 10
                },
                "name": "touchpoints",
                "typeName": "NcTouchpoint",
                "readOnly": true,
                "persistent": true,
                "isNullable": true,
                "isSequence": true,
                "constraints": null
              }
            ],
            "methods": [
              {
                "description": "Method to retrieve both connection status and payload status in one call",
                "id": {
                  "level": 3,
                  "index": 1
                },
                "name": "GetStatus",
                "resultDatatype": "NcMethodResultReceiverStatus",
                "parameters": []
              },
              {
                "description": "Get property value",
                "id": {
                  "level": 1,
                  "index": 1
                },
                "name": "Get",
                "resultDatatype": "NcMethodResultPropertyValue",
                "parameters": [
                  {
                    "description": "Property id",
                    "name": "id",
                    "typeName": "NcPropertyId",
                    "isNullable": false,
                    "isSequence": false,
                    "constraints": null
                  }
                ]
              },
              {
                "description": "Set property value",
                "id": {
                  "level": 1,
                  "index": 2
                },
                "name": "Set",
                "resultDatatype": "NcMethodResult",
                "parameters": [
                  {
                    "description": "Property id",
                    "name": "id",
                    "typeName": "NcPropertyId",
                    "isNullable": false,
                    "isSequence": false,
                    "constraints": null
                  },
                  {
                    "description": "Property value",
                    "name": "value",
                    "typeName": null,
                    "isNullable": true,
                    "isSequence": null,
                    "constraints": null
                  }
                ]
              },
              {
                "description": "Sets property to initial value",
                "id": {
                  "level": 1,
                  "index": 3
                },
                "name": "Clear",
                "resultDatatype": "NcMethodResult",
                "parameters": [
                  {
                    "description": "Property id",
                    "name": "id",
                    "typeName": "NcPropertyId",
                    "isNullable": false,
                    "isSequence": false,
                    "constraints": null
                  }
                ]
              },
              {
                "description": "Get sequence item",
                "id": {
                  "level": 1,
                  "index": 4
                },
                "name": "GetSequenceItem",
                "resultDatatype": "NcMethodResultPropertyValue",
                "parameters": [
                  {
                    "description": "Property id",
                    "name": "id",
                    "typeName": "NcPropertyId",
                    "isNullable": false,
                    "isSequence": false,
                    "constraints": null
                  },
                  {
                    "description": "Index of item in the sequence",
                    "name": "index",
                    "typeName": "NcId32",
                    "isNullable": false,
                    "isSequence": false,
                    "constraints": null
                  }
                ]
              },
              {
                "description": "Set sequence item value",
                "id": {
                  "level": 1,
                  "index": 5
                },
                "name": "SetSequenceItem",
                "resultDatatype": "NcMethodResult",
                "parameters": [
                  {
                    "description": "Property id",
                    "name": "id",
                    "typeName": "NcPropertyId",
                    "isNullable": false,
                    "isSequence": false,
                    "constraints": null
                  },
                  {
                    "description": "Index of item in the sequence",
                    "name": "index",
                    "typeName": "NcId32",
                    "isNullable": false,
                    "isSequence": false,
                    "constraints": null
                  },
                  {
                    "description": "Value",
                    "name": "value",
                    "typeName": null,
                    "isNullable": true,
                    "isSequence": null,
                    "constraints": null
                  }
                ]
              },
              {
                "description": "Add item to sequence",
                "id": {
                  "level": 1,
                  "index": 6
                },
                "name": "AddSequenceItem",
                "resultDatatype": "NcMethodResultId32",
                "parameters": [
                  {
                    "description": "Property id",
                    "name": "id",
                    "typeName": "NcPropertyId",
                    "isNullable": false,
                    "isSequence": false,
                    "constraints": null
                  },
                  {
                    "description": "Value",
                    "name": "value",
                    "typeName": null,
                    "isNullable": true,
                    "isSequence": null,
                    "constraints": null
                  }
                ]
              },
              {
                "description": "Delete sequence item",
                "id": {
                  "level": 1,
                  "index": 7
                },
                "name": "RemoveSequenceItem",
                "resultDatatype": "NcMethodResult",
                "parameters": [
                  {
                    "description": "Property id",
                    "name": "id",
                    "typeName": "NcPropertyId",
                    "isNullable": false,
                    "isSequence": false,
                    "constraints": null
                  },
                  {
                    "description": "Index of item in the sequence",
                    "name": "index",
                    "typeName": "NcId32",
                    "isNullable": false,
                    "isSequence": false,
                    "constraints": null
                  }
                ]
              },
              {
                "description": "Lock method",
                "id": {
                  "level": 1,
                  "index": 8
                },
                "name": "LockWait",
                "resultDatatype": "NcMethodResult",
                "parameters": [
                  {
                    "description": "Type of lock requested, or unlock",
                    "name": "requestedLockStatus",
                    "typeName": "NcLockState",
                    "isNullable": false,
                    "isSequence": false,
                    "constraints": null
                  },
                  {
                    "description": "Method fails if wait exceeds this.  0=forever",
                    "name": "timeout",
                    "typeName": "NcTimeInterval",
                    "isNullable": false,
                    "isSequence": false,
                    "constraints": null
                  }
                ]
              },
              {
                "description": "Abort all this session's lock waits on this object",
                "id": {
                  "level": 1,
                  "index": 9
                },
                "name": "AbortLockWaits",
                "resultDatatype": "NcMethodResult",
                "parameters": []
              }
            ],
            "events": [
              {
                "description": "Property changed event",
                "id": {
                  "level": 1,
                  "index": 1
                },
                "name": "PropertyChanged",
                "eventDatatype": "NcPropertyChangedEventData"
              }
            ]
          }
        ]
      }
    }
  ]
}
```
