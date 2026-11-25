## Configuring Software Binaries for Oracle Grid Infrastructure for a Standalone Server

Use these steps to configure and activate a software-only Oracle Grid Infrastructure for a standalone server installation for Oracle Restart.

### Configuring With Oracle Automatic Storage Management

1.  Install the software binaries. See, “Installing Software Binaries for Oracle Grid Infrastructure for a Standalone Server” in Oracle Database Installation Guide.

2.  Run `gridSetup.sh` to start the Oracle Grid Infrastructure setup wizard.

    See, “Installing Oracle Grid Infrastructure for a Standalone Server with a New Database Installation” in Oracle Database Installation Guide.

### Configuring Without Oracle Automatic Storage Management

1.  Log in as `root` and run the `roothas.sh` script located in the Grid_home path, using the following syntax:

        # cd Grid_home/crs/install
        # ./roothas.sh

    Where, Grid_home is the Oracle Grid Infrastructure home directory.

    For example:

        # cd /u01/app/oracle/product/19.0.0/grid/crs/install
        # ./roothas.sh

2.  Change directory to the path Grid_home/`oui/bin`.

3.  Log in as the Oracle Restart software owner user and use the following command syntax, where Grid_home is the path of the Oracle Grid Infrastructure for a standalone server home.

        $ ./runInstaller -updateNodeList ORACLE_HOME=Grid_home -defaultHomeName CLUSTER_NODES= CRS=TRUE

    For example:

        $ ./runInstaller -updateNodeList ORACLE_HOME=/u01/app/oracle/product/19.0.0/grid
        -defaultHomeName CLUSTER_NODES= CRS=TRUE

4.  Use the `SRVCTL` utility along with Oracle Network Configuration Assistant to add the listener to the Oracle Restart configuration.

**Note:**

This procedure does not work for Oracle Restart upgrades from previous releases.

**Related Topics**

- [Installing Software Binaries for Oracle Grid Infrastructure for a Standalone Server](installing-software-binaries-for-oracle-grid-infrastructure-for-a-standalone-server.md)
- [Installing Oracle Grid Infrastructure for a Standalone Server with a New Database Installation](installing-oracle-grid-infrastructure-for-a-standalone-server-with-a-new-database-installation.md)

**Parent topic:** [Installing Oracle Grid Infrastructure for a Standalone Server Using a Software-Only Installation](installing-oracle-grid-infrastructure-for-a-standalone-server-using-a-software-only-installation.md)
