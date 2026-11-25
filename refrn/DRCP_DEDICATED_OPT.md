## 1.114 DRCP_DEDICATED_OPT

Use `DRCP_DEDICATED_OPT` to enable or disable the use of dedicated optimization with Database Resident Connection Pooling (DRCP).

Dedicated optimization makes DRCP behave like a dedicated server when the number of connections to the DRCP broker is less than the DRCP maximum size.

| Property            | Description                                   |
|:--------------------|:----------------------------------------------|
| Parameter type      | String                                        |
| Syntax              | `DRCP_DEDICATED_OPT = { YES | NO }`           |
| Default value       | `YES`                                         |
| Modifiable          | `ALTER SYSTEM`                                |
| Modifiable in a PDB | No                                            |
| Basic               | No                                            |
| Oracle RAC          | Different instances can use different values. |

When the value of this parameter is set to `YES`, the use of dedicated optimization with DRCP is enabled. When it is set to `NO`, the use of dedicated optimization with DRCP is disabled.

**Note:**

This parameter is available starting with Oracle Database 19c, Release Update 19.11.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/managing-processes.md) for more information about setting this parameter
