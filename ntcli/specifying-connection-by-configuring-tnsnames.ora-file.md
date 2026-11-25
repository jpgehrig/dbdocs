## Specifying a Connection by Configuring a tnsnames.ora File

By default, when you install an Instant Client, Oracle Universal Installer does not include a sample tnsnames.ora file nor the Oracle Net Configuration Assistant utility normally used to create it.

However, if you want to shield users from having to specify actual host names and port numbers, you may want to consider using a tnsnames.ora file to set the Instant Client-to-Oracle Database connection.

You can create the tnsnames.ora file manually by copying and modifying a version of this file from another Oracle installation, or you can use Oracle Net Configuration Assistant to create and manage it for you.

To install Oracle Net Configuration Assistant:

1.  Run Oracle Universal Installer.
2.  Select the Custom installation type.
3.  In the Available Product Components list, select Oracle Network Utilities and click Next.
4.  In the Summary window, click Install, then click Exit and Yes to exit Oracle Universal Installer.
    Then, on each client computer, configure either of the following settings:

    - Set the `TNS_ADMIN` environment variable to specify the location of the `tnsnames.ora` file and specify a service name from that file.

    - Place the `tnsnames.ora` file in the `ORACLE_HOME``\network\admin` directory, and ensure that the `ORACLE_HOME` environment has been set to this Oracle home.

**Related Topics**

- [Connecting Oracle Database Client to an Oracle Database](connecting-oracle-db-client-to-an-oracle-db.md)

**Parent topic:** [Connecting Instant Client or Instant Client Light to an Oracle Database](connecting-instant-client-to-an-oracle-db.md)
