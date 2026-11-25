## 1.317 RESULT_CACHE_REMOTE_EXPIRATION

`RESULT_CACHE_REMOTE_EXPIRATION` specifies the number of minutes that a result using a remote object is allowed to remain valid.

| Property            | Description                       |
|:--------------------|:----------------------------------|
| Parameter type      | Integer                           |
| Default value       | `0`                               |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`   |
| Modifiable in a PDB | Yes                               |
| Range of values     | `0` to operating system-dependent |
| Basic               | No                                |

Setting this parameter to `0` implies that results using remote objects should not be cached. Setting this parameter to a nonzero value can produce stale answers (for example, if the remote table used by a result is modified at the remote database).

**See Also:**

[Oracle Database Performance Tuning Guide](../tgdba/tuning-result-cache.md) for information about tuning the result cache
