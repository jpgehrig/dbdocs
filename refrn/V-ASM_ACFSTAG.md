## 7.55 V\$ASM_ACFSTAG

`V$ASM_ACFSTAG` displays every file or directory that has a tag and its tag name for every mounted Oracle ACFS.

| Column      | Datatype         | Description                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:------------|:-----------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `TAG_NAME`  | `VARCHAR2(32)`   | Tag name on file or directory                                                                                                                                                                                                                                                                                                                                                                                               |
| `FS_NAME`   | `VARCHAR2(1024)` | File system mount point                                                                                                                                                                                                                                                                                                                                                                                                     |
| `PATH_NAME` | `VARCHAR2(4096)` | Complete file path name                                                                                                                                                                                                                                                                                                                                                                                                     |
| `CON_ID`    | `NUMBER`         | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data<br>For this view, the value is always `0`. |

**See Also:**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/intro-acfs-advm.md) for more information about Oracle Automatic Storage Management Cluster File System (Oracle ACFS)

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/views-acfs-advm-info.md) for additional information about using views to display Oracle Automatic Storage Management Cluster File System (Oracle ACFS) and Oracle ASM Dynamic Volume Manager (Oracle ADVM) information

**Note:**

To display information about Oracle ACFS file systems or volumes that are located on nodes in an Oracle Flex ASM configuration, you must connect to the Oracle ASM proxy instance instead of the local Oracle ASM instance. For information about Oracle Flex ASM, refer to [Oracle Automatic Storage Management Administrator's Guide](../ostmg/manage-flex-asm.md).
