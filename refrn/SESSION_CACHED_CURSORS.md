## 1.327 SESSION_CACHED_CURSORS

`SESSION_CACHED_CURSORS` specifies the number of session cursors to cache.

| Property            | Description                                   |
|:--------------------|:----------------------------------------------|
| Parameter type      | Integer                                       |
| Default value       | `50`                                          |
| Modifiable          | `ALTER SESSION, ALTER SYSTEM ... DEFERRED`    |
| Modifiable in a PDB | Yes                                           |
| Range of values     | 0 to operating system-dependent               |
| Basic               | No                                            |
| Oracle RAC          | Multiple instances can have different values. |

Repeated parse calls of the same SQL (including recursive SQL) or PL/SQL statement cause the session cursor for that statement to be moved into the session cursor cache. Oracle uses a least recently used algorithm to remove entries in the session cursor cache to make room for new entries when needed.

**See Also:**

[Oracle Database Performance Tuning Guide](../tgdba/tuning-shared-pool-and-large-pool.md) for information about enabling the session cursor cache
