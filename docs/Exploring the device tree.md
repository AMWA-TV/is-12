# Exploring the device tree

The `GetMemberDescriptors (2m9)` method from NC-Framework can be used to return the descriptions of all members (workers, blocks, agents, managers etc.) of a block.
Requesting member descriptors for anything other than a block is not allowed and will return an error status code.

The device `root block` MUST always have the static `oid` of `1`. No other object or member must use the `oid` of `1` besides the root block.

Example for calling GetMemberDescriptors (2m9) on the root block

```json
{
  "protocolVersion": "1.0",
  "sessionId": 101,
  "messageType": "Command",
  "messages": [
    {
      "handle": 3,
      "oid": 1,
      "methodID": {
        "level": 2,
        "index": 9
      }
    }
  ]
}
```

Example response from calling GetMemberDescriptors (2m9) on the root block

```json
{
  "protocolVersion": "1.0",
  "sessionId": 101,
  "messageType": "CommandResponse",
  "messages": [
    {
      "handle": 3,
      "result": {
        "status": 0,
        "value": [
          {
            "role": "SubscriptionManager",
            "oid": 150,
            "constantOid": true,
            "identity": {
              "id": [1, 7, 4],
              "version": 1
            },
            "userLabel": "Subscription Manager",
            "owner": 1
          },
          {
            "role": "ClassManager",
            "oid": 201,
            "constantOid": true,
            "identity": {
              "id": [1, 7, 14],
              "version": 1
            },
            "userLabel": "Class Manager",
            "owner": 1
          },
          {
            "role": "ReceiverMonitor_1",
            "oid": 5000,
            "constantOid": true,
            "identity": {
              "id": [1, 4, 1],
              "version": 1,
            },
            "userLabel": "Receiver monitor for receiver 1",
            "owner": 1
          }
          ...
        ]
      }
    }
  ]
}
```

`Note`: Members must never change their roles. Object ids might change during the operation of the device but roles must always remain static for the same member. The `constantOid` signals whether an object ID will be constant or not.

Controllers MAY persist the role paths of different block members and may need to inquire about the latest object ids in certain important lifecycle moments (e.g. device rebooting, firmware update finishing, new module installation etc.). A role path can be queried using the `FindMembersByPath` method defined in any block.

Example for calling FindMembersByPath (2m23) on the root block

```json
{
  "protocolVersion": "1.0",
  "sessionId": 101,
  "messageType": "Command",
  "messages": [
    {
      "handle": 4,
      "oid": 1,
      "methodID": {
        "level": 2,
        "index": 23
      },
      "arguments": 
      {
        "path": [
          "block_1",
          "processor_x",
          "input"
        ]
      }
    }
  ]
}
```

Example response from calling FindMembersByPath (2m23) on the root block

```json
{
  "protocolVersion": "1.0",
  "sessionId": 101,
  "messageType": "CommandResponse",
  "messages": [
    {
      "handle": 4,
      "result": {
        "status": 0,
        "value": {
          "role": "input",
          "oid": 264,
          "constantOid": false,
          "identity": {
            "id": [1, 1],
            "version": 1
          },
          "userLabel": "Input group",
          "owner": 131
        }
      }
    }
  ]
}
```
