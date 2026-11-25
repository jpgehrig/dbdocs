## 1.150 INMEMORY_FORCE

`INMEMORY_FORCE` allows you to specify whether tables and materialized views that are specified as `INMEMORY` are populated into the In-Memory Column Store (IM column store) or not.

| Property            | Description                                                                                                                                                                                                                                                                                                                                                                              |
|:--------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Parameter type      | String                                                                                                                                                                                                                                                                                                                                                                                   |
| Syntax              | `INMEMORY_FORCE = { DEFAULT | OFF | BASE_LEVEL | CELLMEMORY_LEVEL }`                                                                                                                                                                                                                                                                                                                     |
| Default value       | `DEFAULT`                                                                                                                                                                                                                                                                                                                                                                                |
| Modifiable          | You can use `ALTER` `SYSTEM` to dynamically modify this parameter setting as follows:<br>• From `DEFAULT` to `OFF`<br>• From `OFF` to `DEFAULT`<br>• From `BASE_LEVEL` to `DEFAULT`<br>• From `CELLMEMORY_LEVEL` to `DEFAULT`<br>• From `CELLMEMORY_LEVEL` to `OFF`<br>All other modifications of this parameter require you to update the initialization file and restart the instance. |
| Modifiable in a PDB | Yes                                                                                                                                                                                                                                                                                                                                                                                      |
| Basic               | No                                                                                                                                                                                                                                                                                                                                                                                       |
| Oracle RAC          | All instances should use the same value.                                                                                                                                                                                                                                                                                                                                                 |

The following values can be set:

- `DEFAULT`

  The IM column store is populated with objects that are specified as `INMEMORY`.

- `OFF`

  Even if the IM column store is configured on this instance, no objects are populated in memory.

- `BASE_LEVEL`

  Enables Database In-Memory Base Level. The Base Level lets you to experiment with Oracle Database In-Memory features without purchasing the Oracle Database In-Memory option. This setting is available starting with Oracle Database 19c, Release Update 19.8.

  When the Base Level is enabled, the value of the `INMEMORY_SIZE` initialization parameter is limited to 16 GB for a CDB. In an Oracle RAC environment, the value of `INMEMORY_SIZE` is limited to 16 GB for each instance. The compression level for all objects and columns is automatically and transparently set to `QUERY` `LOW`. Automatic In-Memory is disabled, and In-Memory Column Store feature tracking is tracked for "In-Memory Base Level" rather than "In-Memory Column Store." The CellMemory feature is disabled for Oracle Exadata.

- `CELLMEMORY_LEVEL`

  CellMemory is an Exadata feature that allows you to use Exadata Smart Flash Cache to populate data in in-memory columnar format. In older releases of Oracle Database, in order to use the CellMemory feature, you were required to enable the IM column store (by setting `INMEMORY_SIZE` to a value greater than `0`), even if you had no intention of using the IM column store. This incurred the overhead of enabling the IM column store without any benefit. Starting with Oracle Database 19c, Release Update 19.8, you can use the CellMemory feature without enabling the IM column store by setting `INMEMORY_FORCE=CELLMEMORY_LEVEL` and `INMEMORY_SIZE=0`. With these settings, the IM column store is not enabled and queries can use CellMemory to scan objects.

  Note that if the value of `INMEMORY_SIZE` is greater than `0`, then setting `INMEMORY_FORCE=CELLMEMORY_LEVEL` is equivalent to setting `INMEMORY_FORCE=DEFAULT`. The IM column store is enabled, even if you only use CellMemory.

**See Also:**

- "[INMEMORY_CLAUSE_DEFAULT](INMEMORY_CLAUSE_DEFAULT.md)"

- "[INMEMORY_MAX_POPULATE_SERVERS](INMEMORY_MAX_POPULATE_SERVERS.md)"

- "[INMEMORY_QUERY](INMEMORY_QUERY.md)"

- "[INMEMORY_SIZE](INMEMORY_SIZE.md)"

- [Oracle Database In-Memory Guide](../inmem/intro-to-in-memory-column-store.md) for an introduction to the IM column store

- [Oracle Database In-Memory Guide](../inmem/in-memory-column-store-architecture.md) for more information about the IM column store

- [Oracle Database Licensing Information User Manual](../dblic/Licensing-Information.md) to learn which database offerings support the Database In-Memory Base Level feature
