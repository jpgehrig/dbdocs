## Example of Creating Minimal Groups, Users, and Paths

You can create a minimal operating system authentication configuration as described in this example.

This configuration example shows the following:

- Creation of the Oracle Inventory group (`oinstall`)

- Creation of a single group (`dba`) as the only system privileges group to assign for all Oracle Grid Infrastructure, Oracle ASM, and Oracle Database system privileges

- Creation of the Oracle Grid Infrastructure software owner (`grid`), and one Oracle Database owner (`oracle`) with correct group memberships

- Creation and configuration of an Oracle base path compliant with OFA structure with correct permissions

Enter the following commands to create a minimal operating system authentication configuration:

    # groupadd -g 54421 oinstall
    # groupadd -g 54422 dba
    # useradd -u 54321 -g oinstall -G dba oracle
    # useradd -u 54322 -g oinstall -G dba grid
    # mkdir -p  /u01/app/19.0.0/grid
    # mkdir -p /u01/app/grid
    # mkdir -p /u01/app/oracle
    # chown -R grid:oinstall /u01
    # chown oracle:oinstall /u01/app/oracle
    # chmod -R 775 /u01/

After running these commands, you have the following groups and users:

- An Oracle central inventory group, or oraInventory group (`oinstall`). Members who have the central inventory group as their primary group, are granted the OINSTALL permission to write to the oraInventory directory.

- One system privileges group, `dba`, for Oracle Grid Infrastructure, Oracle ASM and Oracle Database system privileges. Members who have the `dba` group as their primary or secondary group are granted operating system authentication for OSASM/SYSASM, OSDBA/SYSDBA, OSOPER/SYSOPER, OSBACKUPDBA/SYSBACKUP, OSDGDBA/SYSDG, OSKMDBA/SYSKM, OSDBA for ASM/SYSDBA for ASM, and OSOPER for ASM/SYSOPER for Oracle ASM to administer Oracle Clusterware, Oracle ASM, and Oracle Database, and are granted SYSASM and OSOPER for Oracle ASM access to the Oracle ASM storage.

- An Oracle Grid Infrastructure for a cluster owner, or Grid user (`grid`), with the oraInventory group (`oinstall`) as its primary group, and with the OSASM group (`dba`) as the secondary group, with its Oracle base directory `/u01/app/grid`.

- An Oracle Database owner (`oracle`) with the oraInventory group (`oinstall`) as its primary group, and the OSDBA group (`dba`) as its secondary group, with its Oracle base directory `/u01/app/oracle`.

- `/u01/app` owned by `grid:oinstall` with 775 permissions before installation, and by root after the `root.sh` script is run during installation. This ownership and permissions enables OUI to create the Oracle Inventory directory, in the path `/u01/app/oraInventory`.

- `/u01` owned by `grid:oinstall` before installation, and by root after the `root.sh` script is run during installation.

- `/u01/app/19.0.0/grid` owned by `grid:oinstall` with 775 permissions. These permissions are required for installation, and are changed during the installation process.

- `/u01/app/grid` owned by `grid:oinstall` with 775 permissions. These permissions are required for installation, and are changed during the installation process.

- `/u01/app/oracle` owned by `oracle:oinstall` with 775 permissions.

**Note:**

You can use one installation owner for both Oracle Grid Infrastructure and any other Oracle installations. However, Oracle recommends that you use separate installation owner accounts for each Oracle software installation.

**Parent topic:** [Creating Operating System Oracle Installation User Accounts](creating-operating-system-oracle-installation-user-accounts.md)
