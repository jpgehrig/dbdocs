## Zero-Downtime Oracle Grid Infrastructure Patching

Use Fleet Patching and Provisioning to patch Oracle Grid Infrastructure without bringing down Oracle RAC database instances.

Current methods of patching the Oracle Grid Infrastructure require that you bring down all Oracle RAC database instances on the node where you are patching the Oracle Grid Infrastructure home. This issue is addressed in the Grid Infrastructure layer where by the database instances can continue to run during the grid infrastructure patching.

**Note:**

You can use zero-downtime patching only for out-of-place patching of Oracle Grid Infrastructure 19c Release Update (RU) 19.8 or later releases with Oracle RAC or Oracle RAC One Node databases of 19c or later releases. If your Oracle RAC or Oracle RAC One Node database release is older than 19c, then the database instances stop during zero-downtime patching.

To enable zero-downtime Oracle Grid Infrastructure patching, use the `rhpctl move gihome` command in a manner similar to the following:

    rhpctl move gihome -tgip -sourcewc source_workingcopy_name -destwc destination_workingcopy_name

### Patching System Software Binaries

When using Zero Downtime Patching, only the binaries in the Oracle Grid Infrastructure user space are patched. Additional Oracle Grid Infrastructure OS system software, kernel modules and system commands including `ACFS`, `AFD`, `OLFS`, and `OKA`, are not updated. These commands continue to run the version previous to the patch version. After patching, the OPatch inventory displays the new patch number in the inventory; however, the running OS system software does not contain these changes. Only the OS system software that is available in the Grid Infrastructure home has been patched.

To determine the OS system software that is available in the Grid Infrastructure home, you can run the `crsctl` `query` `driver` `activeversion` `-all` command. To determine what OS system software is running on the system, use `crsctl` `query` `driver` `softwareversion` `-all`.

To update the Grid Infrastructure OS system software on a single node, you must completely stop the Grid Infrastructure software. To stop the Grid Infrastructure software, you must stop the Oracle RAC databases on the single node. After stopping the Oracle RAC databases, run `root.sh` `-updateosfiles` to update all the Grid Infrastructure OS system software on the single node.

**See Also:**

- [Oracle Automatic Storage Management Administrator's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/fppad&id=OSTMG-GUID-E8C5D948-849B-4A7D-B5D7-29F9D792BDE0) for information about Oracle Patching and Oracle ACFS

**Parent topic:** [Patching Oracle Grid Infrastructure](patching-oracle-grid-infrastructure.md)
