## 1.153 INMEMORY_QUERY

`INMEMORY_QUERY` is used to enable or disable in-memory queries for the entire database at the session or system level.

| Property            | Description                              |
|:--------------------|:-----------------------------------------|
| Parameter type      | String                                   |
| Syntax              | `INMEMORY_QUERY = { ENABLE | DISABLE }`  |
| Default value       | `ENABLE`                                 |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`          |
| Modifiable in a PDB | Yes                                      |
| Basic               | No                                       |
| Oracle RAC          | All instances should use the same value. |

This parameter is helpful when you want to test workloads with and without the use of the In-Memory Column Store (IM column store).

This parameter enables in-memory queries for the entire database by default when the `INMEMORY_SIZE` parameter is specified.

Set this parameter to `DISABLE` if you want to disable in-memory queries.

**See Also:**

- "[INMEMORY_CLAUSE_DEFAULT](INMEMORY_CLAUSE_DEFAULT.md)"

- "[INMEMORY_FORCE](INMEMORY_FORCE.md)"

- "[INMEMORY_MAX_POPULATE_SERVERS](INMEMORY_MAX_POPULATE_SERVERS.md)"

- "[INMEMORY_SIZE](INMEMORY_SIZE.md)"

- [Oracle Database In-Memory Guide](../inmem/intro-to-in-memory-column-store.md) for an introduction to the IM column store

- [Oracle Database In-Memory Guide](../inmem/in-memory-column-store-architecture.md) for more information about the IM column store
