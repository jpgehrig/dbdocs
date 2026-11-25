This chapter describes how to configure Oracle Database for Oracle products. It contains the following sections:

- Using Configuration Assistants

- Relinking Executables

### 3.1 Using Configuration Assistants

Oracle Database software is supplied with configuration assistants that you can use to perform various database administration operations.

This section contains the following topics:

- Using Oracle Net Configuration Assistant

- Using Oracle Database Upgrade Assistant

- Using Oracle Database Configuration Assistant

#### 3.1.1 Using Oracle Net Configuration Assistant

Oracle Net Configuration Assistant enables you to configure basic network components during installation, including listener names and protocol addresses, naming methods, net service names in `tnsnames.ora` file, and directory server usage.

After installation is complete, you can use Oracle Net Configuration Assistant to create a more detailed configuration by entering the following command:

    $ $ORACLE_HOME/bin/netca

**Note:**

When you use DBCA to create a database, it automatically updates the network configuration files to include information for the new database.

#### 3.1.2 Using Oracle Database Upgrade Assistant

Oracle Database Upgrade Assistant (DBUA) interactively guides you through a database upgrade and configures the database for the new release. DBUA automates the upgrade by performing all tasks normally performed manually. DBUA makes recommendations for configuration options such as tablespaces and the online redo log.

To start DBUA, run the following command:

    $ $ORACLE_HOME/bin/dbua

For information about the command-line options available with DBUA, use the `-help` or `-h` command-line arguments. For example:

    $ $ORACLE_HOME/bin/dbua -help

**Related Topics**

- [Oracle Database Upgrade Guide](../upgrd/intro-to-upgrading-oracle-database.md)

#### 3.1.3 Using Oracle Database Configuration Assistant

Oracle Database Configuration Assistant (DBCA) is a graphical user interface that assists you in creating and configuring a default or customized database. It also enables you to configure an existing database to add Oracle Database features, and create Oracle Automatic Storage Management disk groups. DBCA also generates a set of shell and SQL scripts that you can inspect, modify, and run at a later time to create a database.

To start DBCA, run the following command:

    $ $ORACLE_HOME/bin/dbca

For information about the command-line options available with DBCA, use the `-help` or `-h` command-line arguments. For example:

    $ $ORACLE_HOME/bin/dbca -help

### 3.2 Relinking Executables

You can relink the product executables manually by using the `relink` shell script located in the `$ORACLE_HOME/bin` directory. You must relink the product executables every time you apply an operating system patch or after an operating system upgrade.

**Note:**

Before relinking executables, you must shut down all the relinking executables which run in the Oracle home directory. In addition, shut down applications linked with Oracle shared libraries. The `relink` script takes `all` and `as_installed` as arguments. If you do not specify any argument, then the `all` argument is considered.

Depending on the products that have been installed in the Oracle home directory, the `relink` script relinks all Oracle product executables.

**See Also:**

[Oracle Database Installation Guide for Linux](../ladbi/modifying-oracle-grid-infrastructure-for-a-standalone-server-binaries-after-installation.md) for more information about how to use the relink script with Automatic Storage Manager

To relink the product executables, run the following command:

    $ relink
