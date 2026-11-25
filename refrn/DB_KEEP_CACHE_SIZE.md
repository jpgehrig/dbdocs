## 1.89 DB_KEEP_CACHE_SIZE

`DB_KEEP_CACHE_SIZE` specifies the size of the `KEEP` buffer pool.

| Property            | Description                                                                                                                                                                                                            |
|:--------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Parameter type      | Big integer                                                                                                                                                                                                            |
| Syntax              | `DB_KEEP_CACHE_SIZE = ``integer`` [K | M | G]`                                                                                                                                                                         |
| Default value       | `0` (`DB_KEEP_CACHE_SIZE` is not configured by default)                                                                                                                                                                |
| Modifiable          | `ALTER SYSTEM`                                                                                                                                                                                                         |
| Modifiable in a PDB | No                                                                                                                                                                                                                     |
| Range of values     | Minimum: `0` (values greater than zero are automatically modified to be either the granule size \* number of processor groups, or 4 MB \* number of CPUs, whichever is greater)<br>Maximum: operating system-dependent |
| Basic               | No                                                                                                                                                                                                                     |

The size of the buffers in the `KEEP` buffer pool is the primary block size (the block size defined by the `DB_BLOCK_SIZE` initialization parameter).

**See Also:**

- "[DB_RECYCLE_CACHE_SIZE](DB_RECYCLE_CACHE_SIZE.md)"

- [Oracle Database Performance Tuning Guide](../tgdba/tuning-system-global-area.md) for information on setting these parameters and on using multiple buffer pools
