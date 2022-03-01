# Data type marshalling

| Type                   | JSON representation                      |
| ---------------------- | ---------------------------------------- |
| enum                   | Numeric associated value as a number     |
| ncString              | string                                    |
| ncBoolean             | boolean                                   |
| ncInt8                | number                                    |
| ncInt16               | number                                    |
| ncInt32               | number                                    |
| ncInt64               | number                                    |
| ncUint16              | number (must be unsigned)                 |
| ncUint32              | number (must be unsigned)                 |
| ncUint64              | number (must be unsigned)                 |
| ncFloat32             | number (must be floating point)           |
| ncFloat64             | number (must be floating point)           |

`Note`: NC-Framework will contain typedef definitions. These contain datatypes which forward to other defined datatypes.

`ToBeDetermined`: Treatments for large number types. It seems Javascript may have some problems with precision over 53 bits and one solution might be to serialize large numeric types as both the number and the string representation of the number.

More rules and mappings to be added.
