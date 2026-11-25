## Using Oracle ASMCA to Configure an ACFS Mount Point

Oracle Automatic Storage Management Configuration Assistant (Oracle ASMCA) enables you to create an Oracle Automatic Storage Management Cluster File System (Oracle ACFS) mount point which is used in the "common file location" step of Oracle Database Configuration Assistant (DBCA).

When creating Oracle ACFS file systems on Windows, run ASMCA as a Windows domain user who is also an administrator of the computer.

1.  From the `Grid_home``/bin` directory, run `asmca.exe` to start the ASMCA.
2.  Select the Disk Groups tab.
3.  Right-click Disk Group Name and select Create ACFS for Database use.
4.  In the Create ACFS for Database window specify the mount point location, volume name, and size, then click OK.
    For example, you can specify the following:

    - Mount Point:` C:\oradatamnt`

    - Volume Name: `dbnfs`

    - Size (GB): `70`
5.  Click OK in the informational pop-up window that appears.
    This window summarizes the actions performed by ASMCA.
6.  Select the ASM Cluster File Systems tab.
    The mount point you just created is displayed on this page.

**Related Topics**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/manage-acfs-advm-asmca.md)

**Parent topic:** [Creating an Oracle RAC Database on Direct NFS](creating-an-oracle-rac-database-on-direct-nfs.md)
