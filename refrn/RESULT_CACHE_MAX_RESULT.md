## 1.314 RESULT_CACHE_MAX_RESULT

`RESULT_CACHE_MAX_RESULT` specifies the percentage of `RESULT_CACHE_MAX_SIZE` that any single result can use.

| Property            | Description                                   |
|:--------------------|:----------------------------------------------|
| Parameter type      | Integer                                       |
| Default value       | `5` percent                                   |
| Modifiable          | `ALTER SYSTEM`                                |
| Modifiable in a PDB | Yes                                           |
| Range of values     | `0` to `100`                                  |
| Basic               | No                                            |
| Oracle RAC          | Multiple instances can have different values. |
