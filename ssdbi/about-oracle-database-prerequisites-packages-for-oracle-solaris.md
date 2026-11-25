Installing the Oracle Database prerequisites group package simplifies operating system configuration and ensures that you have the required packages.

Use the Oracle Database prerequisites group package `group/prerequisite/oracle/oracle-database-preinstall-19c` to ensure that all the necessary packages required for an Oracle Database and Oracle Grid Infrastructure installation are present on the system.

The `oracle-database-preinstall-19c` package also creates the `oracle` user with a home directory of `/export/home/oracle`, and creates the oraInventory (`oinstall`) and OSDBA (`dba`) groups for that user.

The `oracle-database-preinstall-19c` package consists of two packages—one that installs extra packages needed on the operating system and one that creates users and groups. The users and groups are created by the package `oracle-database-os-configuration`. If you have the `oracle` user and other user groups already defined, then you can chose not to change them.

You can install `oracle-database-preinstall-19c` even if you installed Oracle Solaris using any of the server package groups, such as `solaris-minimal-server`, `solaris-small-server`, `solaris-large-server`, or `solaris-desktop`. Oracle recommends that you install the `solaris-minimal-server` group package and then install `oracle-database-preinstall-19c`.

Configuring a server using Oracle Solaris and the Oracle Database prerequisites group package consists of the following steps:

1.  Install the recommended Oracle Solaris version for Oracle Database.

2.  Install the Oracle Database prerequisites group package `oracle-database-preinstall-19c`.

3.  If you do not want the Oracle Database prerequisites group package to create the default users and groups for you, then manually create the role-allocated groups and users.

4.  Complete network interface configuration for each cluster node candidate.

5.  Complete system configuration for shared storage access as required for each standard or core node cluster candidate.

After these steps are complete, you can proceed to install Oracle Database, Oracle Grid Infrastructure, or Oracle RAC.

**Related Topics**

- [Oracle Solaris 11.3 Package Group Lists](https://docs.oracle.com/cd/E53394_01/html/E54814/index.html)

**Parent topic:** [Automatically Configuring Oracle Solaris with Oracle Database Prerequisites Packages](automatically-configuring-oracle-solaris-with-oracle-database-prerequisites-packages.md)
