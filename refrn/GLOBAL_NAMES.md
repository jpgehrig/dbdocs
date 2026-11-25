## 1.136 GLOBAL_NAMES

`GLOBAL_NAMES` specifies whether a database link is required to have the same name as the database to which it connects.

| Property            | Description                     |
|:--------------------|:--------------------------------|
| Parameter type      | Boolean                         |
| Default value       | `false`                         |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM` |
| Modifiable in a PDB | Yes                             |
| Range of values     | `true | false`                  |
| Basic               | No                              |

If the value of `GLOBAL_NAMES` is `false`, then no check is performed. If you use or plan to use distributed processing, then Oracle recommends that you set this parameter to `true` to ensure the use of consistent naming conventions for databases and links in a networked environment.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/distributed-database-concepts.md) for more information on setting this parameter
