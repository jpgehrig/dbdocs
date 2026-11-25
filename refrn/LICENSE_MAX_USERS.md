## 1.172 LICENSE_MAX_USERS

`LICENSE_MAX_USERS` specifies the maximum number of users you can create in the database.

| Property            | Description                                                    |
|:--------------------|:---------------------------------------------------------------|
| Parameter type      | Integer                                                        |
| Default value       | `0`                                                            |
| Modifiable          | `ALTER SYSTEM`                                                 |
| Modifiable in a PDB | No                                                             |
| Range of values     | 0 to number of user licenses                                   |
| Basic               | No                                                             |
| Oracle RAC          | Oracle recommends that multiple instances have the same value. |

When you reach the limit specified by `LICENSE_MAX_USERS`, you cannot create more users. You can, however, increase the limit.

**Note:**

Oracle no longer offers licensing by the number of concurrent sessions. Therefore the `LICENSE_MAX_SESSIONS` and `LICENSE_SESSIONS_WARNING` initialization parameters have been deprecated.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/creating-and-configuring-an-oracle-database.md) for more information about this parameter
