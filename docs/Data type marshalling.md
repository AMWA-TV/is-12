# Data type marshalling

| Type                         | JSON representation                      |
| ---------------------------- | ---------------------------------------- |
| enums                        | Integer associated enum value            |
| NcString                     | string                                   |
| NcBoolean                    | boolean                                  |
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

For specific datatype definitions consult the [NMOS Control Framework](https://specs.amwa.tv/ms-05-02/branches/v1.0-dev/docs/Framework.html#datatypes).
