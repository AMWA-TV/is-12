# Data type marshalling

| Type                   | JSON representation                       |
| ---------------------- | ----------------------------------------- |
| enum                   | Numeric associated value as a number      |
| ncaString              | string                                    |
| ncaBoolean             | boolean                                   |
| ncaInt8                | number                                    |
| ncaInt16               | number                                    |
| ncaInt32               | number                                    |
| ncaInt64               | number                                    |
| ncaUint16              | number (must be unsigned)                 |
| ncaUint32              | number (must be unsigned)                 |
| ncaUint64              | number (must be unsigned)                 |
| ncaFloat32             | number (must be floating point)           |
| ncaFloat64             | number (must be floating point)           |

`Note`: NC-Framework will contain typedef definitions. These contain datatypes which forward to other defined datatypes.

`ToBeDetermined`: Treatments for large number types. It seems Javascript may have some problems with precision over 53 bits and one solution might be to serialize large numeric types as both the number and the string representation of the number.

More rules and mappings to be added.
