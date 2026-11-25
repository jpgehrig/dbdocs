## 1.337 SHARED_POOL_SIZE

`SHARED_POOL_SIZE` specifies (in bytes) the size of the shared pool.

**Note:**

Oracle recommends against setting this parameter in a PDB. The only shared memory sizing parameter that should be set in a PDB is `SGA_TARGET`, which specifies the maximum SGA that the PDB can use at any time.

| Property            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:--------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Parameter type      | Big integer                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Syntax              | `SHARED_POOL_SIZE = ``integer`` [K | M | G]`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| Default value       | If `SGA_TARGET` is set: If the parameter is not specified, then the default is `0` (internally determined by the Oracle Database). If the parameter is specified, then the user-specified value indicates a minimum value for the memory pool.<br>If `SGA_TARGET` is not set (32-bit platforms): `64` MB, rounded up to the nearest granule size.<br>If `SGA_TARGET` is not set (64-bit platforms): `128` MB, rounded up to the nearest granule size.<br>For considerations when dealing with database instances using Oracle ASM, see "SHARED_POOL_SIZE and Automatic Storage Management". |
| Modifiable          | `ALTER SYSTEM`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| Modifiable in a PDB | Yes                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| Range of values     | Minimum: the granule size<br>Maximum: operating system-dependent                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Basic               | No                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |

The shared pool contains shared cursors, stored procedures, control structures, and other structures. If `SGA_TARGET` is not set, then Oracle also allocates parallel execution message buffers from the shared pool. Larger values improve performance in multiuser systems. Smaller values use less memory.

You can monitor utilization of the shared pool by querying the view `V$SGASTAT`.

**See Also:**

- "[SGA_TARGET](SGA_TARGET.md)"

- "[V\$SGASTAT](V-SGASTAT.md)"

- [Oracle Multitenant Administrator's Guide](../multi/using-oracle-resource-manager-for-pdbs-with-sql-plus.md) for more information about the initialization parameters that control the memory usage of PDBs

- [Oracle Database Performance Tuning Guide](../tgdba/tuning-system-global-area.md) for more information on setting this parameter

### SHARED_POOL_SIZE and Automatic Storage Management

On a database instance using Oracle Automatic Storage Management (Oracle ASM), additional memory is required to store extent maps. As a general guideline, you can aggregate the values from the following queries to obtain current database storage size that is either already on Oracle ASM or will be stored in Oracle ASM. Then determine the redundancy type that is used (or will be used), and calculate the value for `SHARED_POOL_SIZE`, using the aggregated value as input.

    SELECT SUM(BYTES)/(1024*1024*1024) FROM V$DATAFILE;
    SELECT SUM(BYTES)/(1024*1024*1024) FROM V$LOGFILE a, V$LOG b
    WHERE a.group#=b.group#;
    SELECT SUM(BYTES)/(1024*1024*1024) FROM V$TEMPFILE WHERE
    status='ONLINE';

Additionally, keep the following guidelines in mind:

- For disk groups using external redundancy:

  (Every 100G of space needs 1M of extra shared pool) + 2M

- For disk groups using normal redundancy:

  (Every 50G of space needs 1M of extra shared pool) + 4M

- For disk groups using high redundancy:

  (Every 33G of space needs 1M of extra shared pool) + 6M
