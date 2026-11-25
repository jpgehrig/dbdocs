Alert logs contain important information about error messages and exceptions that occur during database operations.

Each Oracle Database for Windows instance has one alert log; information is appended to the file each time you start the instance. All threads can write to the alert log.

For example, when automatic archiving of redo logs is halted because no disk space is available, a message is placed in the alert log. The alert log is the first place to check if something goes wrong with the database and the cause is not immediately obvious.

The alert log is named `alert_``SID``.log` and is found in the ADR directory specified by the parameter `DIAGNOSTIC_DEST` in the initialization parameter file. Alert logs must be deleted or archived periodically.

**Related Topics**

- [Modifying the Initialization Parameter File](modifying-the-initialization-parameter-file.md)

**See Also:**

[Oracle Database Installation Guide for Microsoft Windows](../ntdbi/index.md) in the "ADMIN Directory" section.

**Parent topic:** [Monitoring a Database on Windows](monitoring-a-database-on-windows.md)
