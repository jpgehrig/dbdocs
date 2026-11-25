The directory that you designate as the Oracle Inventory directory (oraInventory) stores an inventory of all software installed on the system.

All Oracle software installation owners on a server are granted the OINSTALL privileges to read and write to this directory. If you have previous Oracle software installations on a server, then additional Oracle software installations detect this directory from the `/var/opt/oracle/oraInst.loc` file, and continue to use that Oracle Inventory. Ensure that the group designated as the OINSTALL group is available as a primary group for all planned Oracle software installation owners.

If you are installing Oracle software for the first time, then OUI creates an Oracle base and central inventory, and creates an Oracle inventory using information in the following priority:

- In the path indicated in the ORACLE_BASE environment variable set for the installation owner user account

- In an Optimal Flexible Architecture (OFA) path (u\[01–99\]`/app/`owner where owner is the name of the user account running the installation), and that user account has permissions to write to that path

- In the user home directory, in the path `/app/`owner, where owner is the name of the user account running the installation

For example:

If you are performing an Oracle Database installation, and you set ORACLE_BASE for user `oracle` to the path` /u01/app/oracle` before installation, and grant 755 permissions to `oracle` for that path, then Oracle Universal Installer creates the Oracle Inventory directory one level above the ORACLE_BASE in the path `ORACLE_BASE/../oraInventory`, so the Oracle Inventory path is `/u01/app/oraInventory`. Oracle Universal Installer installs the software in the ORACLE_BASE path. If you are performing an Oracle Grid Infrastructure for a Cluster installation, then the Grid installation path is changed to `root` ownership after installation, and the Grid home software location should be in a different path from the Grid user Oracle base.

If you create the OFA path `/u01`, and grant `oracle` 755 permissions to write to that path, then the Oracle Inventory directory is created in the path` /u01/app/oraInventory`, and Oracle Universal Installer creates the path` /u01/app/oracle`, and configures the ORACLE_BASE environment variable for the Oracle user to that path. If you are performing an Oracle Database installation, then the Oracle home is installed under the Oracle base. However, if you are installing Oracle Grid Infrastructure for a cluster, then be aware that ownership of the path for the Grid home is changed to `root` after installation and the Grid base and Grid home should be in different locations, such as` /u01/app/19.0.0/grid` for the Grid home path, and `/u01/app/grid` for the Grid base. For example:

`/u01/app/oraInventory`, owned by `grid:oinstall`
`/u01/app/oracle`, owned by `oracle:oinstall`
`/u01/app/oracle/product/19.0.0/dbhome_1/`, owned by `o``racle:oinistall`
`/u01/app/grid`, owned by `grid:oinstall`
`/u01/app/19.0.0/grid`, owned by `root`

If you have neither set ORACLE_BASE, nor created an OFA-compliant path, then the Oracle Inventory directory is placed in the home directory of the user that is performing the installation, and the Oracle software is installed in the path `/app/`owner, where owner is the Oracle software installation owner. For example:

    /home/oracle/oraInventory
    /home/oracle/app/oracle/product/19.0.0/dbhome_1

**Parent topic:** [Optimal Flexible Architecture](optimal-flexible-architecture.md)
