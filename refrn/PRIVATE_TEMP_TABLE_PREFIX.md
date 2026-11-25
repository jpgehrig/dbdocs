## 1.293 PRIVATE_TEMP_TABLE_PREFIX

`PRIVATE_TEMP_TABLE_PREFIX` specifies the prefix that the database uses for private temporary tables.

| Property            | Description                                        |
|:--------------------|:---------------------------------------------------|
| Parameter type      | String                                             |
| Syntax              | `PRIVATE_TEMP_TABLE_PREFIX =` `string`             |
| Default value       | `ORA$PTT_`                                         |
| Modifiable          | `ALTER SYSTEM ... DEFERRED`                        |
| Modifiable in a PDB | Yes                                                |
| Basic               | No                                                 |
| Oracle RAC          | The same value must be specified on each instance. |

The default value used for the `PRIVATE_TEMP_TABLE_PREFIX` parameter is `ORA$PTT_`.

If you choose to specify a different prefix value, it must begin with the string `ORA$` and must be unique across the database. Use the following SQL query to determine if the prefix value is unique (in the query, replace prefix-value with your actual prefix value):

    select count(*) from obj$ where name like '<prefix-value>%';

If the above query returns 0, then the prefix you specified is an appropriate value to set.

**Note:**

After setting the prefix, regular table, view, and object names cannot use the same prefix.

**See Also:**

- "[DBA_PRIVATE_TEMP_TABLES](DBA_PRIVATE_TEMP_TABLES.md)"

- "[USER_PRIVATE_TEMP_TABLES](USER_PRIVATE_TEMP_TABLES.md)"

- [Oracle Database Administrator’s Guide](../admin/managing-tables.md) for an introduction to private temporary tables
