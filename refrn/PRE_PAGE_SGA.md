## 1.292 PRE_PAGE_SGA

`PRE_PAGE_SGA` determines whether Oracle accesses the entire SGA at instance startup.

Operating system page table entries are then prebuilt for each page of the SGA.

| Property            | Description    |
|:--------------------|:---------------|
| Parameter type      | Boolean        |
| Default value       | `true`         |
| Modifiable          | No             |
| Modifiable in a PDB | No             |
| Range of values     | `true | false` |
| Basic               | No             |

When this parameter is set to `true`, the database server touches the entire SGA after the instance startup. These accesses are done by a background process and are initiated after the instance startup. The accesses cause the OS to allocate memory to the SGA and populate the page tables, making the SGA memory resident and increasing database performance.

**Note:**

This setting does not prevent your operating system from paging or swapping the SGA after it is initially read into memory.

**Note:**

Starting with Oracle Database 19c, Release Update 19.22, the `PRE_PAGE_SGA` parameter is deprecated because it is obsolete. Setting this parameter typically provides little or no potential performance benefits, and can create problems.

The Oracle Database design for SGA packaging has evolved over time, so that process start-up effects on the SGA are initiated after instance startup, and there is little to no benefit in changing the value for `PRE_PAGE_SGA`. The only use case for this parameter is on Oracle Exadata systems, which should have `PRE_PAGE_SGA` set to `TRUE`. Therefore, starting with Oracle Database 19c, Release Update 19.22, the value of this parameter is always set to `TRUE` on Exadata systems. Any attempt to set this parameter to `FALSE` on an Exadata system will not take effect.
