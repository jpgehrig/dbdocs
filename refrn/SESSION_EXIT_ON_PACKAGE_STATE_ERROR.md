## 1.328 SESSION_EXIT_ON_PACKAGE_STATE_ERROR

Use `SESSION_EXIT_ON_PACKAGE_STATE_ERROR` to force a hard session exit when a session's state has been invalidated.

Exiting sessions after state invalidation avoids errors that can occur when applications mishandle an invalid state.

| Property            | Description                                   |
|:--------------------|:----------------------------------------------|
| Parameter type      | Boolean                                       |
| Default value       | `FALSE`                                       |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`               |
| Modifiable in a PDB | Yes                                           |
| Range of values     | `TRUE | FALSE`                                |
| Basic               | No                                            |
| Oracle RAC          | Different instances can use different values. |

When a stateful PL/SQL package undergoes modification, the sessions that have an active instantiation of the package receive an `ORA-4068` error when they attempt to run the package. When `SESSION_EXIT_ON_PACKAGE_STATE_ERROR` is set to `TRUE`, the session immediately exits instead of raising `ORA-04068`. This can be advantageous because many applications are better equipped to handle a session being discarded, and failing to catch errors related to session state, such as `ORA-04068`, can lead to silent data corruption.

**Note:**

This parameter is available starting with Oracle Database 19c, Release Update 19.23.
