## 1.88 DB_INDEX_COMPRESSION_INHERITANCE

`DB_INDEX_COMPRESSION_INHERITANCE` dictates how index creation inherits compression attributes.

| Property            | Description                                                                                      |
|:--------------------|:-------------------------------------------------------------------------------------------------|
| Parameter type      | String                                                                                           |
| Syntax              | `DB_INDEX_COMPRESSION_INHERITANCE = { TABLESPACE | TABLE | ALL | NONE }`                         |
| Default value       | `NONE`                                                                                           |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`                                                                  |
| Modifiable in a PDB | Yes                                                                                              |
| Basic               | No                                                                                               |
| Oracle RAC          | You must set this parameter for every instance, and multiple instances must have the same value. |

Values:

- `TABLESPACE`

  Index inheritance is based on tablespace attributes.

- `TABLE`

  Index inheritance is based on table attributes.

- `ALL`

  Index inheritance is based on table settings. However, if the table does not have default compression attributes, then index inheritance is based on tablespace attributes.

- `NONE`

  There is no index inheritance from the table or tablespace.

If the `CREATE INDEX` statement specifies compression attributes, then the value of `DB_INDEX_COMPRESSION_INHERITANCE` is ignored, and there is no inheritance from the table or tablespace. When there is table inheritance or tablespace inheritance (and the tablespace does not have an explicit index compression clause), then the following matrix is used:

| Table/Tablespace Level Compression | Inherited Compression for Index |
|:-----------------------------------|:--------------------------------|
| `OLTP`                             | `ADVANCED` `LOW`                |
| `QUERY` `LOW`, `QUERY` `HIGH`      | `ADVANCED` `HIGH`               |
| `ARCHIVE` `LOW`, `ARCHIVE` `HIGH`  | `ADVANCED` `HIGH`               |

**Note:**

The value of `DB_INDEX_COMPRESSION_INHERITANCE` is ignored when creating an index owned by `SYS`. Such indexes do not inherit index compression attributes from tables or tablespaces. If you want to compress an index owned by `SYS`, you must explicitly specify the index compression attributes in the `CREATE` `INDEX` or `ALTER` `INDEX` statement.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/managing-indexes.md) for more information about index compression
