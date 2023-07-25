# Exploring the device model

All blocks ([NcBlock](https://specs.amwa.tv/ms-05-02/branches/v1.0-dev/docs/Blocks.html)) contain a members property which holds descriptions of all members (workers, blocks, managers etc.) contained.
The members for any block can be obtained by invoking the generic Get method (1m1) for the property id (2p2).

Example for calling the generic getter (1m1) on the root block to retrieve the members property (2p2)

```json
{
  "messageType": 0,
  "commands": [
    {
      "handle": 3,
      "oid": 1,
      "methodId": {
        "level": 1,
        "index": 1
      },
      "arguments": {
        "id": {
          "level": 2,
          "index": 2
        }
      }
    }
  ]
}
```

Example response from calling the generic getter (1m1) on the root block to retrieve the members property (2p2)

```json
{
  "messageType": 1,
  "responses": [
    {
      "handle": 3,
      "result": {
        "status": 200,
        "value": [
          {
            "role": "DeviceManager",
            "oid": 2,
            "constantOid": true,
            "classId": [
              1,
              3,
              1
            ],
            "userLabel": "Device manager",
            "owner": 1,
            "description": "The device manager offers information about the product this device is representing"
          },
          {
            "role": "ClassManager",
            "oid": 3,
            "constantOid": true,
            "classId": [
              1,
              3,
              2
            ],
            "userLabel": "Class manager",
            "owner": 1,
            "description": "The class manager offers access to control class and data type descriptors"
          },
          {
            "role": "ReceiverMonitor_01",
            "oid": 11,
            "constantOid": true,
            "classId": [
              1,
              2,
              3
            ],
            "userLabel": "Receiver monitor 01",
            "owner": 1,
            "description": "Receiver monitor worker"
          },
          ...
        ]
      }
    }
  ]
}
```

`Note`: Members never change their roles. On reboot object ids can change but roles remain fixed for the same member. The `constantOid` signals whether an object ID will be constant or not.

Controllers MAY persist the role paths of different block members and may need to inquire about the latest object ids in certain important lifecycle moments (e.g. device rebooting, firmware update finishing, new module installation etc.). A role path can be queried using the `FindMembersByPath` method defined in any block. The relative path to search for (path does not include the role of the block targeted by oid)

Example for calling FindMembersByPath (2m2) on the root block

```json
{
  "messageType": 0,
  "commands": [
    {
      "handle": 4,
      "oid": 1,
      "methodId": {
        "level": 2,
        "index": 2
      },
      "arguments": {
        "path": [
          "receivers",
          "monitor-01"
        ]
      }
    }
  ]
}
```

Example response from calling FindMembersByPath (2m2) on the root block

```json
{
  "messageType": 1,
  "responses": [
    {
      "handle": 4,
      "result": {
        "status": 200,
        "value": [
          {
            "role": "monitor-01",
            "oid": 11,
            "constantOid": true,
            "classId": [
              1,
              2,
              3
            ],
            "userLabel": "Receiver monitor 01",
            "owner": 10,
            "description": "Receiver monitor worker"
          }
        ]
      }
    }
  ]
}
```
