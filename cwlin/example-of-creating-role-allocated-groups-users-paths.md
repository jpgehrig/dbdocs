## Example of Creating Role-allocated Groups, Users, and Paths

Understand this example of how to create role-allocated groups and users that is compliant with an Optimal Flexible Architecture (OFA) deployment.

###

This example illustrates the following scenario:

- An Oracle Grid Infrastructure installation

- Two separate Oracle Database installations planned for the cluster, `DB1` and `DB2`

- Separate installation owners for Oracle Grid Infrastructure, and for each Oracle Database

- Full role allocation of system privileges for Oracle ASM, and for each Oracle Database

- Oracle Database owner `oracle1` granted the right to start up and shut down the Oracle ASM instance

Create groups and users for a role-allocated configuration for this scenario using the following commands:

    # groupadd -g 54321 oinstall
    # groupadd -g 54322 dba1
    # groupadd -g 54332 dba2
    # groupadd -g 54323 oper1
    # groupadd -g 54333 oper2
    # groupadd -g 54324 backupdba1
    # groupadd -g 54334 backupdba2
    # groupadd -g 54325 dgdba1
    # groupadd -g 54335 dgdba2
    # groupadd -g 54326 kmdba1
    # groupadd -g 54336 kmdba2
    # groupadd -g 54327 asmdba
    # groupadd -g 54328 asmoper
    # groupadd -g 54329 asmadmin
    # groupadd -g 54330 racdba1
    # groupadd -g 54340 racdba2
    # useradd -u 54322 -g oinstall -G asmadmin,asmdba,racdba1,racdba2 grid
    # useradd -u 54321 -g oinstall -G dba1,backupdba1,dgdba1,kmdba1,asmdba,racdba1,asmoper oracle1
    # useradd -u 54323 -g oinstall -G dba2,backupdba2,dgdba2,kmdba2,asmdba,racdba2 oracle2
    # mkdir -p /u01/app/19.0.0/grid
    # mkdir -p /u01/app/grid
    # mkdir -p /u01/app/oracle1
    # mkdir -p /u01/app/oracle2
    # chown -R grid:oinstall /u01
    # chmod -R 775 /u01/
    # chown oracle1:oinstall /u01/app/oracle1
    # chown oracle2:oinstall /u01/app/oracle2

After running these commands, you have a set of administrative privileges groups and users for Oracle Grid Infrastructure, and for two separate Oracle databases (`DB1` and `DB2`):

Example 6-1 Oracle Grid Infrastructure Groups and Users Example

The command creates the following Oracle Grid Infrastructure groups and users:

- An Oracle central inventory group, or `oraInventory` group (`oinstall`), whose members that have this group as their primary group. Members of this group are granted the OINSTALL system privileges, which grants permissions to write to the `oraInventory` directory, and other associated install binary privileges.

- An OSASM group (`asmadmin`), associated with Oracle Grid Infrastructure during installation, whose members are granted the SYSASM privileges to administer Oracle ASM.

- An OSDBA for ASM group (`asmdba`), associated with Oracle Grid Infrastructure storage during installation. Its members include grid and any database installation owners, such as `oracle1` and `oracle2`, who are granted access to Oracle ASM. Any additional installation owners that use Oracle ASM for storage must also be made members of this group.

- An OSOPER for ASM group for Oracle ASM (`asmoper`), associated with Oracle Grid Infrastructure during installation. Members of `asmoper` group are granted limited Oracle ASM administrator privileges, including the permissions to start and stop the Oracle ASM instance.

- An Oracle Grid Infrastructure installation owner (`grid`), with the oraInventory group (`oinstall`) as its primary group, and with the OSASM (`asmadmin`) group and the OSDBA for ASM (`asmdba`) group as secondary groups.

- `/u01/app/oraInventory`. The central inventory of Oracle installations on the cluster. This path remains owned by `grid:oinstall`, to enable other Oracle software owners to write to the central inventory.

- An OFA-compliant mount point `/u01` owned by `grid:oinstall` before installation, so that Oracle Universal Installer can write to that path.

- An Oracle base for the grid installation owner `/u01/app/grid` owned by `grid:oinstall` with 775 permissions, and changed during the installation process to 755 permissions.

- A Grid home `/u01/app/19.0.0/grid` owned by `grid:oinstall` with 775 (drwxdrwxr-x) permissions. These permissions are required for installation, and are changed during the installation process to `root:oinstall` with 755 permissions (`drwxr-xr-x`).

Example 6-2 Oracle Database DB1 Groups and Users Example

The command creates the following Oracle Database (`DB1`) groups and users:

- An Oracle Database software owner (`oracle1`), which owns the Oracle Database binaries for `DB1`. The `oracle1` user has the oraInventory group as its primary group, and the OSDBA group for its database (`dba1`) and the OSDBA for ASM group for Oracle Grid Infrastructure (`asmdba`) as secondary groups. In addition, the `oracle1` user is a member of `asmoper`, granting that user privileges to start up and shut down Oracle ASM.

- An OSDBA group (`dba1`). During installation, you identify the group `dba1` as the OSDBA group for the database installed by the user `oracle1`. Members of `dba1` are granted the SYSDBA privileges for the Oracle Database `DB1`. Users who connect as SYSDBA are identified as user SYS on `DB1`.

- An OSBACKUPDBA group (`backupdba1`). During installation, you identify the group `backupdba1` as the OSDBA group for the database installed by the user `oracle1`. Members of `backupdba1` are granted the SYSBACKUP privileges for the database installed by the user `oracle1` to back up the database.

- An OSDGDBA group (`dgdba1`). During installation, you identify the group `dgdba1` as the OSDGDBA group for the database installed by the user `oracle1`. Members of `dgdba1` are granted the SYSDG privileges to administer Oracle Data Guard for the database installed by the user `oracle1`.

- An OSKMDBA group (`kmdba1`). During installation, you identify the group `kmdba1` as the OSKMDBA group for the database installed by the user `oracle1`. Members of `kmdba1` are granted the SYSKM privileges to administer encryption keys for the database installed by the user `oracle1`.

- An OSOPER group (`oper1`). During installation, you identify the group `oper1` as the OSOPER group for the database installed by the user `oracle1`. Members of `oper1` are granted the SYSOPER privileges (a limited set of the SYSDBA privileges), including the right to start up and shut down the `DB1` database. Users who connect as OSOPER privileges are identified as user PUBLIC on `DB1`.

- An Oracle base `/u01/app/oracle1` owned by `oracle1:oinstall` with 775 permissions. The user `oracle1` has permissions to install software in this directory, but in no other directory in the `/u01/app` path.

Example 6-3 Oracle Database DB2 Groups and Users Example

The command creates the following Oracle Database (DB2) groups and users:

- An Oracle Database software owner (`oracle2`), which owns the Oracle Database binaries for DB2. The `oracle2` user has the oraInventory group as its primary group, and the OSDBA group for its database (`dba2`) and the OSDBA for ASM group for Oracle Grid Infrastructure (`asmdba`) as secondary groups. However, the `oracle2` user is not a member of the `asmoper` group, so `oracle2` cannot shut down or start up Oracle ASM.

- An OSDBA group (`dba2`). During installation, you identify the group `dba2` as the OSDBA group for the database installed by the user `oracle2`. Members of `dba2` are granted the SYSDBA privileges for the Oracle Database DB2. Users who connect as SYSDBA are identified as user SYS on DB2.

- An OSBACKUPDBA group (`backupdba2`). During installation, you identify the group `backupdba2` as the OSDBA group for the database installed by the user `oracle2`. Members of `backupdba2` are granted the SYSBACKUP privileges for the database installed by the user `oracle2` to back up the database.

- An OSDGDBA group (`dgdba2`). During installation, you identify the group `dgdba2` as the OSDGDBA group for the database installed by the user `oracle2`. Members of `dgdba2` are granted the SYSDG privileges to administer Oracle Data Guard for the database installed by the user `oracle2`.

- An OSKMDBA group (`kmdba2`). During installation, you identify the group `kmdba2` as the OSKMDBA group for the database installed by the user `oracle2`. Members of `kmdba2` are granted the SYSKM privileges to administer encryption keys for the database installed by the user `oracle2`.

- An OSOPER group (`oper2`). During installation, you identify the group `oper2` as the OSOPER group for the database installed by the user `oracle2`. Members of `oper2` are granted the SYSOPER privileges (a limited set of the SYSDBA privileges), including the right to start up and shut down the DB2 database. Users who connect as OSOPER privileges are identified as user PUBLIC on DB2.

- An Oracle base `/u01/app/oracle2` owned by `oracle2:oinstall` with 775 permissions. The user `oracle2` has permissions to install software in this directory, but in no other directory in the `/u01/app` path.

**Parent topic:** [Creating Operating System Oracle Installation User Accounts](creating-operating-system-oracle-installation-user-accounts.md)
