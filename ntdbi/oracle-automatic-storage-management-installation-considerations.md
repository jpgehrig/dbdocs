## Oracle Automatic Storage Management Installation Considerations

In previous releases, Oracle Automatic Storage Management (Oracle ASM) was installed as part of the Oracle Database installation. Starting with Oracle Database 11g Release 2 (11.2), Oracle Automatic Storage Management is part of an Oracle Grid Infrastructure installation, either for a cluster, or for a standalone server.

If you want to upgrade an existing Oracle Automatic Storage Management installation, then you must upgrade Oracle Automatic Storage Management by running an Oracle Grid Infrastructure upgrade (upgrades of existing Oracle Automatic Storage Management installations). If you do not have Oracle Automatic Storage Management installed and you want to use Oracle Automatic Storage Management as your storage option, then you must complete an Oracle Restart installation before you start your Oracle Database installation.

You must run Oracle Automatic Storage Management Configuration Assistant for installing and configuring Oracle ASM instances, disk groups, volumes, and Oracle Automatic Storage Management Cluster File System (Oracle ACFS). In addition, you can use the ASMCA command-line interface.

Apply the following guidelines when you install Oracle Automatic Storage Management:

- You must complete the steps listed under the Configuring Storage for Oracle Automatic Storage Management section to prepare a disk partition to use for the Oracle Automatic Storage Management disk groups.

- Ensure that at least one disk is configured appropriately in an Oracle ASM disk group before beginning the installation.

- When you install Oracle Automatic Storage Management, Oracle Automatic Storage Management Configuration Assistant creates a separate server parameter file (`SPFILE`) and password file for the Oracle Automatic Storage Management instance. As soon as Oracle Automatic Storage Management is installed, `ASMSNMP` schema and user are created.

- The Oracle Automatic Storage Management instance that manages the existing disk group runs in the Oracle Grid Infrastructure home directory.

[Performance and Scalability Considerations for Disk Groups](../ostmg/considerations-asm-storage.md)

[Password File Authentication for Oracle ASM](../ostmg/authenticate-access-asm-instance.md)

**Parent topic:** [Oracle Automatic Storage Management Storage Configuration](oracle-automatic-storage-management-storage-configuration.md)
