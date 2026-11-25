On occasion (for example, when reinstalling Oracle Database), you must stop Oracle Database services.

You can stop Oracle Database services from three different locations:

- Using the Control Panel

- Using the Command Prompt

### Using the Control Panel

To stop Oracle Database services from the Control Panel:

1.  Access your Windows Services dialog box.

    **See Also:**

    Your operating system documentation for instructions

2.  Select `Oracle``HOMENAME``TNSListener` and click Stop.

    `Oracle``HOMENAME``TNSListener` is stopped.

3.  Select `OracleService``SID` and click Stop.

4.  Click OK.

    `OracleService``SID` is stopped.

### Using the Command Prompt

To stop Oracle Database services from the command prompt, enter:

    C:\> net STOP service

The variable `service` is a specific service name, such as `OracleServiceORCL`.

**Related Topics**

- [Starting and Shutting Down a Database Using Services](starting-and-shutting-down-a-database-using-services.md)

**Parent topic:** [About Ways to Manage Oracle Database Services](about-ways-to-manage-oracle-database-services.md)
