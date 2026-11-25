Oracle Database services must be started for you to use Oracle Database and its products.

You can start Oracle Database services by:

- Using the Control Panel

- Using the Command Prompt

### Using the Control Panel

To start Oracle Database services from the Control Panel:

1.  Access your Windows Services dialog box.

    **See Also:**

    Your operating system documentation for instructions

2.  Find the service to start in the list, select it, and click Start.

    If you cannot find `OracleService``SID` in the list, then use ORADIM to create it.

3.  Click Close to exit the Services dialog box.

### Using the Command Prompt

To start Oracle Database services from the command prompt, enter:

    C:\> NET START service

The variable `service` is a specific service name, such as `OracleServiceORCL.`

**Related Topics**

- [Starting and Shutting Down a Database Using Services](starting-and-shutting-down-a-database-using-services.md)

**Parent topic:** [About Ways to Manage Oracle Database Services](about-ways-to-manage-oracle-database-services.md)
