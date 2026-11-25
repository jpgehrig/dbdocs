## 1.345 SPATIAL_VECTOR_ACCELERATION

`SPATIAL_VECTOR_ACCELERATION` enables or disables the spatial vector acceleration.

| Property            | Description                                  |
|:--------------------|:---------------------------------------------|
| Parameter type      | Boolean                                      |
| Default value       | `false`                                      |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`              |
| Modifiable in a PDB | Yes                                          |
| Range of values     | `true | false`                               |
| Basic               | No                                           |
| Oracle RAC          | Multiple instances should use the same value |

Setting this parameter to `true` improves spatial vector query performance.

**See Also:**

[Oracle Spatial and Graph Developer's Guide](../spatl/spatial-concepts.md) for more information about this parameter
