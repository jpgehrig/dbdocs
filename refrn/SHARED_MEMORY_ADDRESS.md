## 1.335 SHARED_MEMORY_ADDRESS

`SHARED_MEMORY_ADDRESS` and `HI_SHARED_MEMORY_ADDRESS` specify the starting address at run time of the system global area (SGA). This parameter is ignored on the many platforms that specify the SGA's starting address at linktime.

| Property            | Description |
|:--------------------|:------------|
| Parameter type      | Integer     |
| Default value       | `0`         |
| Modifiable          | No          |
| Modifiable in a PDB | No          |
| Basic               | No          |

Use this parameter to specify the entire address on 32-bit platforms and to specify the low-order 32 bits of a 64-bit address on 64-bit platforms. Use `HI_SHARED_MEMORY_ADDRESS` to specify the high-order 32 bits of a 64-bit address on 64-bit platforms. If both parameters are 0 or unspecified, the SGA address defaults to a platform-specific location.

**See Also:**

"[HI_SHARED_MEMORY_ADDRESS](HI_SHARED_MEMORY_ADDRESS.md)"
