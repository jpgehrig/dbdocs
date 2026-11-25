## 1.338 SHARED_SERVER_SESSIONS

`SHARED_SERVER_SESSIONS` specifies the total number of shared server sessions to allow.

| Property            | Description                                                                                                                                                                                                          |
|:--------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Parameter type      | Integer                                                                                                                                                                                                              |
| Default value       | There is no default value.                                                                                                                                                                                           |
| Modifiable          | `ALTER SYSTEM`                                                                                                                                                                                                       |
| Modifiable in a PDB | No                                                                                                                                                                                                                   |
| Range of values     | If `SHARED_SERVER_SESSIONS` is specified, then it should be less than `SESSIONS`. If `SHARED_SERVER_SESSIONS` is not specified, then a shared server session may be created as long as there is a free session slot. |
| Basic               | No                                                                                                                                                                                                                   |

Setting this parameter enables you to reserve user sessions for dedicated servers.

**See Also:**

[Oracle Database Concepts](../cncpt/process-architecture.md) for more information on sessions
