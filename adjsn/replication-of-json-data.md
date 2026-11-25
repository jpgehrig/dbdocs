You can use Oracle GoldenGate to replicate tables that have columns containing JSON data.

Be aware that Oracle GoldenGate requires tables that are to be replicated to have a nonvirtual primary key column; the primary key column cannot be virtual.

All indexes on the JSON data will be replicated also. However, you must execute, on the replica database, any Oracle Text operations that you use to maintain a JSON search index. Here are examples of such procedures:

- `CTX_DDL.sync_index`

- `CTX_DDL.optimize_index`

**See Also:**

- [Oracle GoldenGate](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/adjsn&id=ogg) for information about Oracle GoldenGate

- [Oracle Text Reference](../ccref/CTX_DDL-package.md) for information about `CTX_DDL.sync_index`

- [Oracle Text Reference](../ccref/CTX_DDL-package.md) for information about `CTX_DDL.optimize_index`

**Parent topic:** [Store and Manage JSON Data](store-and-manage-json-data.md)
