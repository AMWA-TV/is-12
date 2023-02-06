# Class definition discovery

[MS-05-02](https://specs.amwa.tv/ms-05-02) defines a class discovery mechanism which can be used for discovering details of class definitions. This is offered through a set of methods which exist in the `NcClassManager`. The `NcClassManager` can be found in the members of the root block as shown in the earlier examples.

The `GetControlClass (3m1)` returns a single class descriptor (the descriptor includes all inherited properties and methods) and requires the following arguments:

* identity - of type `NcClassIdentity`

Example for calling GetControlClass (3m1) on the ClassManager (using the oid retrieved from the root block - e.g. ClassManager oid = 3) when wanting to retrieve the class definition for NcReceiverMonitor (1,2,3)

```json
{
  "protocolVersion": "1.0.0",
  "messageType": 0,
  "commands": [
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
          "id": [1, 2, 3],
          "version": "1.0.0"
        }
      }
    }
  ]
}
```

Example response from calling GetControlClass (3m1) on the ClassManager for class NcReceiverMonitor (1,2,3)

```json
{
  "protocolVersion": "1.0.0",
  "messageType": 1,
  "responses": [
    {
      "handle": 6,
      "result": {
        "status": 200,
        "value": {
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
              "typeName": "NcString",
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
              "isNullable": true,
              "isSequence": false,
              "constraints": null
            },
            {
              "description": "Touchpoints to other contexts",
              "id": {
                "level": 1,
                "index": 8
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
              "parameters": [

              ]
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
              "description": "Get sequence item",
              "id": {
                "level": 1,
                "index": 3
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
                "index": 4
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
                "index": 5
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
                "index": 6
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
      }
    }
  ]
}
```
