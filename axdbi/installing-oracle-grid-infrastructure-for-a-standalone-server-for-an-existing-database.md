Follow the high-level instructions in this section to install Oracle Grid Infrastructure for a standalone server and configure it for an existing Oracle Database.

Oracle Restart can manage resources from the same release and releases up to one version lower than Oracle Restart. For instance, you can install Oracle Grid Infrastructure for a standalone server 19c (Oracle Restart) to provide services for Oracle Database 19c and Oracle Database 18c. Earlier Oracle Database releases can coexist on the same server without being managed by Oracle Restart.

To install Oracle Grid Infrastructure for a standalone server for a database that is already installed:

1.  Log in as the Oracle Database software owner user.

2.  Set the ORACLE_HOME and ORACLE_SID environment variables.

    Bourne, Bash or Korn shell:

        $ ORACLE_SID=orcl
        $ export ORACLE_SID
        $ ORACLE_HOME=/u01/app/oracle/product/19.0.0/dbhome_1
        $ export ORACLE_HOME

    C shell:

        % setenv ORACLE_SID orcl
        % setenv ORACLE_HOME /u01/app/oracle/product/19.0.0/dbhome_1

3.  Go to the Oracle home and stop any existing database listeners.

        $ $ORACLE_HOME/lsnrctl stop listener_name

    **Note:**

    If this command throws an error, reload the listener using `lsnrctl reload LISTENER`

4.  On the same host computer as the database, install Oracle Grid Infrastructure for a standalone server, and select Configure Oracle Grid Infrastructure for a Standalone Server (Oracle Restart) as the installation option. See, “Installing Oracle Grid Infrastructure for a Standalone Server with a New Database Installation” in Oracle Database Installation Guide.

    The Oracle Grid Infrastructure for a standalone server components are installed in an Oracle Grid Infrastructure Oracle home (Grid home), which is in a different location from existing Oracle Database homes.

5.  If you have an existing Oracle Database, then register it for High Availability with Oracle Restart using the `srvctl` command:

        $ cd $ORACLE_HOME/bin
        $ srvctl add database -db dbname -o oracle_home_path

**Related Topics**

- [Installing Oracle Grid Infrastructure for a Standalone Server with a New Database Installation](installing-oracle-grid-infrastructure-for-a-standalone-server-with-a-new-database-installation.md)
- [Oracle Database Administrator’s Guide](../admin/configuring-automatic-restart-of-an-oracle-database.md)

**Parent topic:** [Installing and Configuring Oracle Grid Infrastructure for a Standalone Server](installing-and-configuring-oracle-grid-infrastructure-for-a-standalone-server.md)
