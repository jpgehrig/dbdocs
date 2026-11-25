## Removing an RPM-based Oracle Database Installation

Use this procedure to remove and deinstall a database installed using the `yum` command.

1.  Log in as `root`.
2.  Run the following command to remove the RPM-based database installation:
        # yum -y remove oracle-database-ee-19c

The `yum` command detects the default configured components in the Oracle home such as the database (ORCLCDB) and the listener (LISTENER) and removes these components for you.

Apart from the default database (ORCLCDB) and the listener (LISTENER), if the `yum` command detects other configured components in the Oracle home such as additional databases or listeners, then it stops the deinstallation process. A message is displayed that instructs you to remove these configured components manually. To remove these configured components:

1.  Login as the Oracle Database installation owner user (`oracle`).

2.  To remove any database associated with your installation, use Oracle Database Configuration Assistant (Oracle DBCA).

        $ cd $ORACLE_HOME/bin
        $ ./dbca

3.  To remove any listeners associated with your installation, run Oracle Net Configuration Assistant (Oracle NETCA).

        $ cd $ORACLE_HOME/bin
        $ ./netca

4.  Log in as `root` and run the `yum` command again to remove the rpm-based database installation.

        # yum -y remove oracle-database-ee-19c

**Related Topics**

- [Deleting a Database Using Oracle DBCA](../admqs/installing-oracle-database-creating-database.md)
- [Using Oracle Net Configuration Assistant](../netag/managing-oracle-net-services.md)

**Parent topic:** [Removing Oracle Database Software](removing-oracle-database-software.md)
