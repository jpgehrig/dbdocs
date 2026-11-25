## 1.156 INMEMORY_VIRTUAL_COLUMNS

`INMEMORY_VIRTUAL_COLUMNS` controls which user-defined virtual columns are stored as In-Memory virtual columns (IM columns).

| Property            | Description                                                |
|:--------------------|:-----------------------------------------------------------|
| Parameter type      | String                                                     |
| Syntax              | `INMEMORY_VIRTUAL_COLUMNS = { ENABLE | MANUAL | DISABLE }` |
| Default value       | `MANUAL`                                                   |
| Modifiable          | `ALTER SYSTEM`                                             |
| Modifiable in a PDB | Yes                                                        |
| Basic               | No                                                         |
| Oracle RAC          | The same value must be used on all instances.              |

IM virtual columns improve query performance by avoiding the necessity of repeated calculations. Also, the database can scan and filter IM virtual columns using techniques such as SIMD vector processing.

These values can be set for the parameter:

- `ENABLE`: For a table or partition that has been enabled for in-memory storage, all virtual columns will be stored in-memory at the default table or partition memcompress level unless:

  - They have been explicitly excluded using the no inmemory syntax.

  - They have been altered to have a different memcompress level than the base table or partition, in which case they will be stored at the specified memcompress level.

- `MANUAL`: This is the default value for the parameter. For a table or partition that has been enabled for in-memory storage, no virtual columns will be stored in-memory unless:

  - They have been explicitly marked for inmemory, in which case they will be stored in-memory at the table or partition memcompress level.

  - They have been marked for inmemory with a different memcompress level than the base table or partition, in which case they will be stored at the specified memcompress level.

- `DISABLE`: For a table or partition that has been enabled for in-memory storage, no virtual columns will ever be stored in-memory. Any changes to the inmemory_column_clause for a virtual column including changes in memcompress level will be recorded, but not acted upon with regards to population of virtual columns.

**See Also:**

- "[INMEMORY_EXPRESSIONS_USAGE](INMEMORY_EXPRESSIONS_USAGE.md)"

- [Oracle Database In-Memory Guide](../inmem/populating-objects-in-memory.md) for more information about IM virtual columns
