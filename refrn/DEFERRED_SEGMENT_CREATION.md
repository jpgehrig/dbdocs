## 1.105 DEFERRED_SEGMENT_CREATION

`DEFERRED_SEGMENT_CREATION` specifies the semantics of deferred segment creation.

| Property            | Description                     |
|:--------------------|:--------------------------------|
| Parameter type      | Boolean                         |
| Default value       | `true`                          |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM` |
| Modifiable in a PDB | Yes                             |
| Range of values     | `true | false`                  |
| Basic               | No                              |

If set to `true`, then segments for tables and their dependent objects (LOBs, indexes) will not be created until the first row is inserted into the table.

Before creating a set of tables, if it is known that a significant number of them will not be populated, then consider setting this parameter to `true`. This saves disk space and minimizes install time.
