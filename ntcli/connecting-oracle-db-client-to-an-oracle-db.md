## Connecting Oracle Database Client to an Oracle Database

After you run Oracle Universal Installer to install Oracle Database Client, you must use Oracle Net Configuration Assistant (NETCA) to configure Oracle Database Client to connect to an Oracle database.

At the end of the installation, Oracle Universal Installer prompts you to configure the database connection. If you bypassed that option, or if you need to change the database connection later on, use the following procedure if you installed the Administrator, Runtime, or Custom installation types.

To connect Oracle Database Client to an Oracle Database:

1.  From the Start menu, choose Oracle - HOME_NAME, then Configuration and Migration Tools, then Oracle Net Configuration Assistant.
2.  In the Welcome window, select Local Net Service Name configuration and click Next.
3.  In the Net Service Name Configuration window, select Add and click Next.
4.  In the Service Name window, enter the name of the Oracle database to which you want to connect and click Next.
5.  In the Select Protocols window, select the protocol you want and click Next.
6.  In the Protocol window, depending on the protocol you selected, enter the appropriate information and click Next.
7.  In the Net Test window, select whether you want to test the connection, and click Next.
8.  In the Net Service Name window, enter a name for the net service and click Next.
9.  Answer the remaining prompts, which allow you to configure another net service name, and then click Finish to complete the configuration.
    Oracle Net Configuration Assistant creates the `tnsnames.ora` file in the following location:

    `ORACLE_HOME``\network\admin\tnsnames.ora`

**Parent topic:** [Recommended Postinstallation Tasks](recommended-postinstallation-tasks.md)
