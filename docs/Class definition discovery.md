# Class definition discovery

[MS-05-02](https://specs.amwa.tv/ms-05-02) defines a class discovery mechanism in [NcClassManager](https://specs.amwa.tv/ms-05-02/branches/v1.0-dev/docs/Managers.html#class-manager) which can be used for discovering details of class definitions. Descriptors of all the classes can be retrieved by getting the value of property `controlClasses (3p1)`. Alternatively the `GetControlClass (3m1)` method can be used to return a single class descriptor. This requires the following arguments:

* identity - of type [NcClassId](https://specs.amwa.tv/ms-05-02/branches/v1.0-dev/docs/Framework.html#ncclassid)
* includeInherited - of type [NcBoolean](https://specs.amwa.tv/ms-05-02/branches/v1.0-dev/docs/Framework.html#primitives) (if set the descriptor would contain all inherited elements)

Example for calling GetControlClass (3m1) on the ClassManager (using the oid retrieved from the root block - e.g. ClassManager oid = 3) when wanting to retrieve the class definition for [NcReceiverMonitor (1,2,3)](https://specs.amwa.tv/nmos-control-feature-sets/branches/main/monitoring/#ncreceivermonitor)

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
        "identity": [1, 2, 3],
        "includeInherited": true
      }
    }
  ]
}
```

Example response from calling GetControlClass (3m1) on the ClassManager for class [NcReceiverMonitor (1,2,3)](https://specs.amwa.tv/nmos-control-feature-sets/branches/main/monitoring/#ncreceivermonitor)

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
          "identity": [
              1,
              2,
              3
            ],
          "name": "NcReceiverMonitor",
          "fixedRole": null,
          "properties": [
            {
              "description": "Connection status property",
              "id": {
                "level": 3,
                "index": 1
              },
              "name": "connectionStatus",
              "typeName": "NcConnectionStatus",
              "isReadOnly": true,
              "isPersistent": false,
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
              "isReadOnly": true,
              "isPersistent": false,
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
              "isReadOnly": true,
              "isPersistent": false,
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
              "isReadOnly": true,
              "isPersistent": false,
              "isNullable": true,
              "isSequence": false,
              "constraints": null
            },
            {
              "description": "TRUE iff worker is enabled",
              "id": {
                "level": 2,
                "index": 1
              },
              "name": "enabled",
              "typeName": "NcBoolean",
              "isReadOnly": false,
              "isPersistent": true,
              "isNullable": false,
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
              "isReadOnly": true,
              "isPersistent": true,
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
              "isReadOnly": true,
              "isPersistent": true,
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
              "isReadOnly": true,
              "isPersistent": true,
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
              "isReadOnly": true,
              "isPersistent": true,
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
              "isReadOnly": true,
              "isPersistent": true,
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
              "isReadOnly": false,
              "isPersistent": true,
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
              "isReadOnly": true,
              "isPersistent": true,
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
                  "isSequence": false,
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
                  "isSequence": false,
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
                  "isSequence": false,
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
