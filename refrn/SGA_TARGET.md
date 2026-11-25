## 1.333 SGA_TARGET

`SGA_TARGET` specifies the total size of all SGA components.

| Property            | Description                                                                                                                                             |
|:--------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------|
| Parameter type      | Big integer                                                                                                                                             |
| Syntax              | `SGA_TARGET = ``integer`` [K | M | G]`                                                                                                                  |
| Default value       | `0` (SGA autotuning is disabled for `DEFERRED` mode autotuning requests, but allowed for `IMMEDIATE` mode autotuning requests)                          |
| Modifiable          | `ALTER SYSTEM`                                                                                                                                          |
| Modifiable in a PDB | Yes                                                                                                                                                     |
| Range of values     | 64 MB to `SGA_MAX_SIZE`<br>Note that if `MEMORY_MAX_TARGET` \> `0`, then the value of `SGA_TARGET` also cannot exceed the value of `MEMORY_MAX_TARGET`. |
| Basic               | Yes                                                                                                                                                     |

If `SGA_TARGET` is specified, then the following memory pools are automatically sized:

- Buffer cache (`DB_CACHE_SIZE`)

- Shared pool (`SHARED_POOL_SIZE`)

- Large pool (`LARGE_POOL_SIZE`)

- Java pool (`JAVA_POOL_SIZE`)

- Streams pool (`STREAMS_POOL_SIZE`)

- Data transfer cache (`DATA_TRANSFER_CACHE_SIZE`)

If these automatically tuned memory pools are set to nonzero values, then those values are used as minimum levels by Automatic Shared Memory Management. You would set minimum values if an application component needs a minimum amount of memory to function properly.

The following pools are manually sized components and are not affected by Automatic Shared Memory Management:

- Log buffer

- Other buffer caches, such as `KEEP`, `RECYCLE`, and other block sizes

- Fixed SGA and other internal allocations

The memory allocated to these pools is deducted from the total available for `SGA_TARGET` when Automatic Shared Memory Management computes the values of the automatically tuned memory pools.

In the Default value field, `IMMEDIATE` mode autotuning requests are necessary to avoid `ORA-04031` errors. The `DEFERRED` and `IMMEDIATE` modes are reflected in the `OPER_MODE` column of the `V$MEMORY_RESIZE_OPS` view.

If Automatic Memory Management is enabled (`MEMORY_TARGET` is set to a positive value) and `SGA_TARGET` is also set to a positive value, the `SGA_TARGET` value acts as the minimum value for the size of the SGA.

**Note:**

This parameter is optional for pluggable databases (PDBs). When this parameter is set for a PDB, it specifies the maximum SGA that the PDB can use at any time. When this parameter is not set at the PDB level, the PDB has no limit for the amount of SGA it can use, other than the CDB's SGA size.

To be able to use Resource Manager in a CDB to control the amount of memory each PDB can use:

- The `NONCDB_COMPATIBLE` initialization parameter must be set to `FALSE` at the CDB level (in the root of the CDB).

- The `MEMORY_TARGET` initialization parameter must not be set at the CDB level.

- You must set the `SGA_TARGET` initialization parameter at the CDB level.

- You must set `SGA_TARGET` in a PDB.

  If you set a PDB’s `SGA_TARGET` value and `SGA_TARGET` is not set at the CDB level, you will not receive an error message and the PDB’s `SGA_TARGET` value will not be enforced.

- When setting `SGA_TARGET` in a PDB, the following requirements must be met:

  - The value of `SGA_TARGET` in the PDB must be less than or equal to the `SGA_TARGET` value at the CDB level.

  - The value of `SGA_TARGET` in the PDB must be less than or equal to the `SGA_MAX_SIZE` value at the CDB level.

  - The value of `SGA_TARGET` in the PDB must be twice the PDB’s `DB_CACHE_SIZE` value, if the PDB’s `DB_CACHE_SIZE` value is set.

  - The value of `SGA_TARGET` in the PDB must be twice the PDB’s `SHARED_POOL_SIZE` value, if the PDB’s `SHARED_POOL_SIZE` value is set.

  - The value of `SGA_TARGET` in the PDB must be twice the PDB’s `SGA_MIN_SIZE` value, if the PDB’s `SGA_MIN_SIZE` value is set.

  When you set `SGA_TARGET` in a PDB to a value that does not meet these requirements, you receive an error.

**See Also:**

- "[DB_CACHE_SIZE](DB_CACHE_SIZE.md)"

- "[SHARED_POOL_SIZE](SHARED_POOL_SIZE.md)"

- "[LARGE_POOL_SIZE](LARGE_POOL_SIZE.md)"

- "[JAVA_POOL_SIZE](JAVA_POOL_SIZE.md)"

- "[STREAMS_POOL_SIZE](STREAMS_POOL_SIZE.md)"

- "[V\$MEMORY_RESIZE_OPS](V-MEMORY_RESIZE_OPS.md)"

- "[MEMORY_TARGET](MEMORY_TARGET.md)"

- "[PGA_AGGREGATE_TARGET](PGA_AGGREGATE_TARGET.md)"

- [Oracle Multitenant Administrator's Guide](../multi/using-oracle-resource-manager-for-pdbs-with-sql-plus.md) for more information about the initialization parameters that control the memory usage of PDBs

- [Oracle Database Administrator’s Guide](../admin/managing-memory.md) for information on automatic memory management

- [Oracle Database Administrator’s Guide](../admin/managing-memory.md) for information on managing the SGA manually
