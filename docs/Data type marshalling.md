# Data type marshalling

| Type                         | JSON representation                      |
| ---------------------------- | ---------------------------------------- |
| enums                        | Integer associated enum value            |
| NcString                     | string                                   |
| NcBoolean                    | boolean                                  |
| NcInt8                       | number                                   |
| NcInt16                      | number                                   |
| NcInt32                      | number                                   |
| NcInt64                      | number                                   |
| NcUint16                     | number (must be unsigned)                |
| NcUint32                     | number (must be unsigned)                |
| NcUint64                     | number (must be unsigned)                |
| NcFloat32                    | number (must be floating point)          |
| NcFloat64                    | number (must be floating point)          |
| struct types                 | object                                   |
| sequences of primitive types | array of primitive types                 |
| sequences of struct types    | array of objects                         |

`Note`: NC-Framework will contain typedef definitions. These contain datatypes which forward to other defined datatypes.
