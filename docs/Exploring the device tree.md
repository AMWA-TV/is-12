# Exploring the device tree

All blocks (NcBlock) contain a members property which holds descriptions of all members (workers, blocks, agents, managers etc.) contained.
The members for any block can be obtained by invoking the generic Get method (1m1) for the property id (2p10).

The device `root block` MUST always have the static `oid` of `1`. No other object or member must use the `oid` of `1` besides the root block.

Example for calling the generic getter (1m1) on the root block to retrieve the members property (2p10)

```json
{
  "protocolVersion": "1.0.0",
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
          "index": 10
        }
      }
    }
  ]
}
```

Example response from calling the generic getter (1m1) on the root block to retrieve the members property (2p10)

```json
{
  "protocolVersion": "1.0.0",
  "messageType": 1,
  "responses": [
    {
      "handle": 3,
      "result": {
        "status": 200,
        "value": [
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
            "description": "The class manager offers access to control class and data type descriptors",
            "constraints": null
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
            "description": "Receiver monitor worker",
            "constraints": null
          }
          ...
        ]
      }
    }
  ]
}
```

`Note`: Members must never change their roles. Object ids might change during the operation of the device but roles must always remain fixed for the same member. The `constantOid` signals whether an object ID will be constant or not.

Controllers MAY persist the role paths of different block members and may need to inquire about the latest object ids in certain important lifecycle moments (e.g. device rebooting, firmware update finishing, new module installation etc.). A role path can be queried using the `FindMembersByPath` method defined in any block. The relative path to search for (path does not include the role of the block targeted by oid)

Example for calling FindMembersByPath (2m2) on the root block

```json
{
  "protocolVersion": "1.0.0",
  "messageType": 0,
  "commands": [
    {
      "handle": 4,
      "oid": 1,
      "methodId": {
        "level": 2,
        "index": 2
      },
      "arguments":
      {
        "path": [
          "stereo-gain",
          "channel-gain",
          "left-gain"
        ]
      }
    }
  ]
}
```

Example response from calling FindMembersByPath (2m2) on the root block

```json
{
  "protocolVersion": "1.0.0",
  "messageType": 1,
  "responses": [
    {
      "handle": 4,
      "result": {
        "status": 200,
        "value": [
          {
            "role": "left-gain",
            "oid": 22,
            "constantOid": true,
            "classId": [
              1,
              2,
              1,
              1,
              1
            ],
            "userLabel": "Left gain",
            "owner": 21,
            "description": "Left channel gain",
            "constraints": null
          }
        ]
      }
    }
  ]
}
```
