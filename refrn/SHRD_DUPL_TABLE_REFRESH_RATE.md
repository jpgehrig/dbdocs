## 1.340 SHRD_DUPL_TABLE_REFRESH_RATE

`SHRD_DUPL_TABLE_REFRESH_RATE` displays the duplicated table refresh rate (in seconds).

| Property            | Description                                 |
|:--------------------|:--------------------------------------------|
| Parameter type      | Integer                                     |
| Default value       | `60`                                        |
| Modifiable          | `ALTER SYSTEM`                              |
| Modifiable in a PDB | Yes                                         |
| Range of values     | 20 to 2<sup>31</sup> - 1                    |
| Basic               | No                                          |
| Oracle RAC          | All instances should use the same instance. |

You can change the value of this parameter to change the duplicated table refresh rate.

A duplicated table is a table that has the same contents on all shards in a sharded database. Duplicated tables are implemented using materialized views that are refreshed at a certain rate.

**See Also:**

- [Using Oracle Sharding](../shard/sharding-overview.md) for an introduction to sharding

- [Using Oracle Sharding](../shard/architecture-and-concepts1.md) for more information about duplicated tables
