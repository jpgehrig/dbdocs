## 7.42 V\$ASM_ACFS_SEC_CMDRULE

`V$ASM_ACFS_SEC_CMDRULE` contains one row for every Oracle ACFS security command rule for each Oracle ACFS file system. This view also supports GV\$ global views.

| Column          | Datatype         | Description                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:----------------|:-----------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `CMD_RULE_NAME` | `VARCHAR2(32)`   | Name of the command rule                                                                                                                                                                                                                                                                                                                                                                                                    |
| `FS_NAME`       | `VARCHAR2(1024)` | Mount path name to identify the file system                                                                                                                                                                                                                                                                                                                                                                                 |
| `VOL_DEVICE`    | `VARCHAR2(256)`  | ADVM volume name                                                                                                                                                                                                                                                                                                                                                                                                            |
| `CON_ID`        | `NUMBER`         | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data<br>For this view, the value is always `0`. |

**See Also:**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/intro-acfs-advm.md) for more information about Oracle Automatic Storage Management Cluster File System (Oracle ACFS)

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/views-acfs-advm-info.md) for additional information about using views to display Oracle Automatic Storage Management Cluster File System (Oracle ACFS) and Oracle ASM Dynamic Volume Manager (Oracle ADVM) information

**Note:**

To display information about Oracle ACFS file systems or volumes that are located on nodes in an Oracle Flex ASM configuration, you must connect to the Oracle ASM proxy instance instead of the local Oracle ASM instance. For information about Oracle Flex ASM, refer to [Oracle Automatic Storage Management Administrator's Guide](../ostmg/manage-flex-asm.md).
