## 1.234 OBJECT_CACHE_MAX_SIZE_PERCENT

The object cache is a memory block on the client that allows applications to store entire objects and to navigate among them without round trips to the server. `OBJECT_CACHE_MAX_SIZE_PERCENT` specifies the percentage of the optimal cache size that the session object cache can grow past the optimal size.

| Property            | Description                                  |
|:--------------------|:---------------------------------------------|
| Parameter type      | Integer                                      |
| Default value       | `10`                                         |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM ... DEFERRED` |
| Modifiable in a PDB | Yes                                          |
| Range of values     | 0 to operating system-dependent maximum      |
| Basic               | No                                           |

The maximum size is equal to the optimal size plus the product of this percentage and the optimal size. When the cache size exceeds this maximum size, the system will attempt to shrink the cache to the optimal size.

**See Also:**

- "[OBJECT_CACHE_OPTIMAL_SIZE](OBJECT_CACHE_OPTIMAL_SIZE.md)" for a description of the object cache

- [Pro\*C/C++ Programmer's Guide](../lnpcc/about-Objects.md) and [Oracle Call Interface Programmer's Guide](../lnoci/object-advanced-topics-in-oci.md) for information on precompiler use of the object cache
