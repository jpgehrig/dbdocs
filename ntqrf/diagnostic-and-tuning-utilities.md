On UNIX, utilities such as `sar` and `vmstat` are used to monitor Oracle Database background and shadow processes.

These utilities are not integrated with Oracle Database.

Performance utilities available on Windows include Task Manager, Control Panel, Event Viewer, and Microsoft Management Console.

Oracle Database is integrated with several of these tools. For example:

- Event Viewer displays system alert messages, including Oracle Database startup/shutdown messages and audit trail.

- Task Manager on Windows displays currently running processes and their resource usage, similar to the UNIX `ps -ef `command or HP OpenVMS` SHOW SYSTEM`. But Task Manager is easier to interpret and the columns can be customized.

  **See Also:**

  - [Database Tools on Windows](database-tools-on-windows.md)

  - [Monitoring a Database on Windows](monitoring-a-database-on-windows.md)

**Parent topic:** [Oracle Database Differences on Windows and UNIX](oracle-database-differences-on-windows-and-unix.md)
