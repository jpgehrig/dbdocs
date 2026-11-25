## 7.51 V\$ASM_ACFSAUTORESIZE

`V$ASM_ACFSAUTORESIZE` displays the auto-resize settings for each mounted Oracle ACFS file system.

| Column             | Datatype         | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:-------------------|:-----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `FS_NAME`          | `VARCHAR2(1024)` | Full path name of the Oracle ACFS file system mount point                                                                                                                                                                                                                                                                                                                        |
| `RESIZE_INCREMENT` | `NUMBER`         | Auto-resize increment (in megabytes)                                                                                                                                                                                                                                                                                                                                             |
| `RESIZE_MAXIMUM`   | `NUMBER`         | Auto-resize maximum (in megabytes)                                                                                                                                                                                                                                                                                                                                               |
| `CON_ID`           | `NUMBER`         | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**Note:**

This view is available starting with Oracle Database 19c.

**See Also:**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/intro-acfs-advm.md) for more information about Oracle Automatic Storage Management Cluster File System (Oracle ACFS)

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/views-acfs-advm-info.md) for additional information about using views to display Oracle Automatic Storage Management Cluster File System (Oracle ACFS) and Oracle ASM Dynamic Volume Manager (Oracle ADVM) information

**Note:**

To display information about Oracle ACFS file systems or volumes that are located on nodes in an Oracle Flex ASM configuration, you must connect to the Oracle ASM proxy instance instead of the local Oracle ASM instance. For information about Oracle Flex ASM, refer to [Oracle Automatic Storage Management Administrator's Guide](../ostmg/manage-flex-asm.md).
