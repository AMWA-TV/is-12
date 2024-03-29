# Class definition discovery

[MS-05-02](https://specs.amwa.tv/ms-05-02) defines a class discovery mechanism in [NcClassManager](https://specs.amwa.tv/ms-05-02/branches/v1.0.x/docs/Managers.html#class-manager) which can be used for discovering details of class definitions. Descriptors of all the classes can be retrieved by getting the value of property `controlClasses (3p1)`. Alternatively the `GetControlClass (3m1)` method can be used to return a single class descriptor. This requires the following arguments:

* classId - of type [NcClassId](https://specs.amwa.tv/ms-05-02/branches/v1.0.x/docs/Framework.html#ncclassid)
* includeInherited - of type [NcBoolean](https://specs.amwa.tv/ms-05-02/branches/v1.0.x/docs/Framework.html#primitives) (if set the descriptor would contain all inherited elements)

Example for calling GetControlClass (3m1) on the ClassManager (using the oid retrieved from the root block - e.g. ClassManager oid = 3) when wanting to retrieve the class definition for [NcReceiverMonitor (1,2,3)](https://specs.amwa.tv/nmos-control-feature-sets/branches/main/monitoring/#ncreceivermonitor)

```json
{
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
        "classId": [1, 2, 3],
        "includeInherited": true
      }
    }
  ]
}
```

Example response from calling GetControlClass (3m1) on the ClassManager for class [NcReceiverMonitor (1,2,3)](https://specs.amwa.tv/nmos-control-feature-sets/branches/main/monitoring/#ncreceivermonitor)

```json
{
  "messageType": 1,
  "responses": [
    {
      "handle": 6,
      "result": {
        "status": 200,
        "value": {
          "description": "NcReceiverMonitor class descriptor",
          "classId": [
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
              "isNullable": false,
              "isSequence": false,
              "constraints": null
            },
            {
              "description": "Static value. All instances of the same class will have the same identity value",
              "id": {
                "level": 1,
                "index": 1
              },
              "name": "classId",
              "typeName": "NcClassId",
              "isReadOnly": true,
              "isNullable": false,
              "isSequence": false,
              "isDeprecated": false,
              "constraints": null
            },
            {
              "description": "Object identifier",
              "id": {
                "level": 1,
                "index": 2
              },
              "name": "oid",
              "typeName": "NcOid",
              "isReadOnly": true,
              "isNullable": false,
              "isSequence": false,
              "isDeprecated": false,
              "constraints": null
            },
            {
              "description": "TRUE iff OID is hardwired into device",
              "id": {
                "level": 1,
                "index": 3
              },
              "name": "constantOid",
              "typeName": "NcBoolean",
              "isReadOnly": true,
              "isNullable": false,
              "isSequence": false,
              "isDeprecated": false,
              "constraints": null
            },
            {
              "description": "OID of containing block. Can only ever be null for the root block",
              "id": {
                "level": 1,
                "index": 4
              },
              "name": "owner",
              "typeName": "NcOid",
              "isReadOnly": true,
              "isNullable": true,
              "isSequence": false,
              "isDeprecated": false,
              "constraints": null
            },
            {
              "description": "Role of object in the containing block",
              "id": {
                "level": 1,
                "index": 5
              },
              "name": "role",
              "typeName": "NcString",
              "isReadOnly": true,
              "isNullable": false,
              "isSequence": false,
              "isDeprecated": false,
              "constraints": null
            },
            {
              "description": "Scribble strip",
              "id": {
                "level": 1,
                "index": 6
              },
              "name": "userLabel",
              "typeName": "NcString",
              "isReadOnly": false,
              "isNullable": true,
              "isSequence": false,
              "isDeprecated": false,
              "constraints": null
            },
            {
              "description": "Touchpoints to other contexts",
              "id": {
                "level": 1,
                "index": 7
              },
              "name": "touchpoints",
              "typeName": "NcTouchpoint",
              "isReadOnly": true,
              "isNullable": true,
              "isSequence": true,
              "isDeprecated": false,
              "constraints": null
            },
            {
              "description": "Runtime property constraints",
              "id": {
                "level": 1,
                "index": 8
              },
              "name": "runtimePropertyConstraints",
              "typeName": "NcPropertyConstraints",
              "isReadOnly": true,
              "isNullable": true,
              "isSequence": true,
              "isDeprecated": false,
              "constraints": null
            }
          ],
          "methods": [
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
              ],
              "isDeprecated": false
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
              ],
              "isDeprecated": false
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
                  "typeName": "NcId",
                  "isNullable": false,
                  "isSequence": false,
                  "constraints": null
                }
              ],
              "isDeprecated": false
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
                  "typeName": "NcId",
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
              ],
              "isDeprecated": false
            },
            {
              "description": "Add item to sequence",
              "id": {
                "level": 1,
                "index": 5
              },
              "name": "AddSequenceItem",
              "resultDatatype": "NcMethodResultId",
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
              ],
              "isDeprecated": false
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
                  "typeName": "NcId",
                  "isNullable": false,
                  "isSequence": false,
                  "constraints": null
                }
              ],
              "isDeprecated": false
            },
            {
              "description": "Get sequence length",
              "id": {
                "level": 1,
                "index": 7
              },
              "name": "GetSequenceLength",
              "resultDatatype": "NcMethodResultLength",
              "parameters": [
                {
                  "description": "Property id",
                  "name": "id",
                  "typeName": "NcPropertyId",
                  "isNullable": false,
                  "isSequence": false,
                  "constraints": null
                }
              ],
              "isDeprecated": false
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
              "eventDatatype": "NcPropertyChangedEventData",
              "isDeprecated": false
            }
          ]
        }
      }
    }
  ]
}
```
