## 1.195 MAX_AUTH_SERVERS

`MAX_AUTH_SERVERS` specifies the maximum number of authentication servers in the authentication pool. This pool authenticates user connections when client applications connect to Database Resident Connection Pooling (DRCP).

| Property            | Description                                                                                               |
|:--------------------|:----------------------------------------------------------------------------------------------------------|
| Parameter type      | Integer                                                                                                   |
| Default value       | `25`                                                                                                      |
| Modifiable          | `ALTER SYSTEM`                                                                                            |
| Modifiable in a PDB | No                                                                                                        |
| Range of values     | Minimum: `MIN_AUTH_SERVERS` or `1`, whichever is the greater value<br>Maximum: operating system-dependent |
| Basic               | No                                                                                                        |
| Oracle RAC          | Different instances can use different values.                                                             |

The value of this parameter must be greater than or equal to the value of the `MIN_AUTH_SERVERS` initialization parameter, which specifies the minimum number of authentication servers in the authentication pool. The exception is when `MIN_AUTH_SERVERS = 0`. In this case, the value of `MAX_AUTH_SERVERS` must be greater than or equal to `1`.

**Note:**

This parameter is available starting with Oracle Database 19c, Release Update 19.10.

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/managing-processes.md) for more information about setting this parameter

- "[MIN_AUTH_SERVERS](MIN_AUTH_SERVERS.md)"
