## Starting and Stopping the Database from the Microsoft Windows Services Utility

You can use SQL or `srvctl` utility to start or stop the database instance. SRVCTL starts the service automatically.

To use SQL to start the database instance, start the Windows services:

1.  From the Start menu, select All Programs, then Administrative Tools, and then Services.
2.  In the Services dialog box, locate the name of the database you want to start or stop.
3.  Right-click the name of the database, and from the menu, select either Start, Stop, or Pause.
    To set its startup properties, right-click Properties, and in the dialog box, select either Automatic, Manual, or Disabled from the Startup type list.

**Parent topic:** [Starting and Stopping an Oracle Database](starting-and-stopping-oracle-db.md)
