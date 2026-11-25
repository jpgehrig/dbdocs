## 1.208 MEMORY_MAX_TARGET

`MEMORY_MAX_TARGET` specifies the maximum value to which a DBA can set the `MEMORY_TARGET` initialization parameter.

| Property            | Description                                                      |
|:--------------------|:-----------------------------------------------------------------|
| Parameter type      | Big integer                                                      |
| Syntax              | `MEMORY_MAX_TARGET = ``integer`` [K | M | G]`                    |
| Default value       | `0`                                                              |
| Modifiable          | No                                                               |
| Modifiable in a PDB | No                                                               |
| Range of values     | `0` to the physical memory size available to the Oracle Database |
| Basic               | No                                                               |

**Note:**

On Linux platforms only, Oracle recommends against explicitly setting values for `MEMORY_TARGET` and `MEMORY_MAX_TARGET` in the initialization parameter file at the time of instance startup. Doing so may result in suboptimal small page allocation in the SGA. Furthermore, if the `USE_LARGE_PAGES` parameter is set to `ONLY` and you attempt to set values for `MEMORY_TARGET` and `MEMORY_MAX_TARGET`, the instance will fail to start.

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/managing-memory.md) for more information about managing memory

- "[MEMORY_TARGET](MEMORY_TARGET.md)"

- "[USE_LARGE_PAGES](USE_LARGE_PAGES.md)"
