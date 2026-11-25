Use this procedure to install the Oracle Database prerequisites group package for your Oracle software.

The `group/prerequisite/oracle/oracle-database-preinstall-19c` group package installs all the packages required for an Oracle Database and Oracle Grid Infrastructure installation. It also creates the `oracle` user and the `oinstall` and `dba` groups for that user.

**Caution:**

If you have the `oracle` user and other user groups already defined, and do not want to change them, then ensure that you run the following command before you install the Oracle Database prerequisites group package:

    # pkg avoid oracle-database-os-configuration

To install the `oracle-database-preinstall-19c` group packages, log in as `root`, and run the following command on Oracle Solaris 11.3 and later systems:

    # pkg install oracle-database-preinstall-19c

Note the following guidelines about the preceding command:

- For more information about the history of the preceding command, use the `pkg history` command. See `pkg (1)`.
- You do not have to specify the entire package name, only the trailing portion of the name that is unique. See `pkg(5)`.
- Oracle recommends that you install the `solaris-minimal-server` group package and then install `oracle-database-preinstall-19c`.

**Related Topics**

- [Oracle Solaris Documentation](http://docs.oracle.com/en/operating-systems/solaris.html)

**Parent topic:** [Automatically Configuring Oracle Solaris with Oracle Database Prerequisites Packages](automatically-configuring-oracle-solaris-with-oracle-database-prerequisites-packages.md)
