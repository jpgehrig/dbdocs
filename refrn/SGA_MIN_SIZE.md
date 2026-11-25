## 1.332 SGA_MIN_SIZE

`SGA_MIN_SIZE` indicates a possible minimum value for SGA usage of a pluggable database (PDB).

| Property            | Description                                    |
|:--------------------|:-----------------------------------------------|
| Parameter type      | Big integer                                    |
| Syntax              | `SGA_MIN_SIZE = ``integer`` [K | M | G]`       |
| Default value       | `0`                                            |
| Modifiable          | `ALTER SYSTEM`                                 |
| Modifiable in a PDB | Yes                                            |
| Range of values     | 0 to 50% of `SGA_TARGET`                       |
| Basic               | No                                             |
| Oracle RAC          | The same value must be used for all instances. |

Setting this parameter at the CDB level has no effect.

**Note:**

To be able to use Resource Manager in a CDB to control the amount of memory each PDB can use:

- The `NONCDB_COMPATIBLE` initialization parameter must be set to `FALSE` at the CDB level (in the root of the CDB).

- The `MEMORY_TARGET` initialization parameter must not be set at the CDB level.

- A value for `SGA_TARGET` must be set at the CDB level.

  If `SGA_TARGET` is not set at the CDB level, then setting `SGA_MIN_SIZE` in a PDB has no effect. You will not receive an error message, and the PDB’s `SGA_MIN_SIZE` value will not be enforced.

- You must set the `SGA_MIN_SIZE` value to a value that meets these requirements:

  - In a PDB, to a value that is less than or equal to 50% of the value of `SGA_TARGET` in the PDB

  - In a PDB, to a value that is less than or equal to 50% of the value of `SGA_TARGET` at the CDB level

  - In a PDB, to a value that is less than the value of `SGA_MAX_SIZE` at the CDB level

  - Across all the open PDBs in a CDB, the sum of `SGA_MIN_SIZE` values must be less than or equal to 50% of the managed SGA total at the CDB level. Managed SGA is `DB_CACHE_SIZE` plus `SHARED_POOL_SIZE`.

  When you set `SGA_MIN_SIZE` in a PDB to a value that does not meet these requirements, you receive an error.

**See Also:**

[Oracle Multitenant Administrator's Guide](../multi/using-oracle-resource-manager-for-pdbs-with-sql-plus.md) for more information about the initialization parameters that control the memory usage of PDBs
