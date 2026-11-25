## 1.39 CLIENT_RESULT_CACHE_SIZE

`CLIENT_RESULT_CACHE_SIZE` specifies the maximum size of the client per-process result set cache (in bytes).

| Property            | Description                                          |
|:--------------------|:-----------------------------------------------------|
| Parameter type      | Big integer                                          |
| Syntax              | `CLIENT_RESULT_CACHE_SIZE = ``integer`` [K | M | G]` |
| Default value       | `0`                                                  |
| Modifiable          | No                                                   |
| Modifiable in a PDB | Yes                                                  |
| Range of values     | `0` to operating system-dependent                    |
| Basic               | No                                                   |

All OCI client processes inherit this maximum size. Setting a nonzero value enables the client query cache feature. This can be overridden by the client configuration parameter `OCI_RESULT_CACHE_MAX_SIZE`.

**See Also:**

[Oracle Call Interface Programmer's Guide](../lnoci/performance-topics.md) for more information about the client query cache feature
