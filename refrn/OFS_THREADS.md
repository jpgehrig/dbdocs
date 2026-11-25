## 1.236 OFS_THREADS

`OFS_THREADS` sets the maximum number of Oracle file system (OFS) threads that can be started to service Oracle file system requests.

| Property            | Description                                          |
|:--------------------|:-----------------------------------------------------|
| Parameter type      | Integer                                              |
| Default value       | `4`                                                  |
| Modifiable          | `ALTER SYSTEM`                                       |
| Modifiable in a PDB | No                                                   |
| Range of values     | `2` to `128`                                         |
| Basic               | No                                                   |
| Oracle RAC          | The same value should be specified on all instances. |

**Note:**

This initialization parameter is supported only on the Linux operating system.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/creating-and-configuring-an-oracle-database.md) for more information about the Oracle Database NFS server feature
