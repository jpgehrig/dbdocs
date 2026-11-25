## 1.41 CLONEDB

`CLONEDB` should be set on Direct NFS Client CloneDB databases. When this parameter is set, the CloneDB database uses the database backup as the backing store for the datafiles.

| Property            | Description                                     |
|:--------------------|:------------------------------------------------|
| Parameter type      | Boolean                                         |
| Default value       | `false`                                         |
| Modifiable          | No                                              |
| Modifiable in a PDB | No                                              |
| Range of values     | `true | false`                                  |
| Basic               | No                                              |
| Oracle RAC          | The same value should be set for all instances. |

**See Also:**

- See [Oracle Database Administrator’s Guide](../admin/creating-and-configuring-an-oracle-database.md) for more information about cloning databases on network attached storage (NAS).

- "[CLONEDB_DIR](CLONEDB_DIR.md)"
