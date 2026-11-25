## Creating the Scheduler Agent

The Oracle Scheduler Execution Agent permits Oracle Database clients to run Scheduler jobs at the request of an Oracle instance which can be located on a remote host.

This allows for centralized control over several hosts using Oracle Scheduler and can perform jobs at the operating system level and jobs that run on another Oracle Database.

The Oracle Scheduler Execution Agent is installed with the Oracle Database Client software.

The Oracle Scheduler Execution Agent permits Oracle Database clients to run Scheduler jobs at the request of an Oracle instance which can be located on a remote host. This allows for centralized control over several hosts using Oracle Scheduler and can perform jobs at the operating system level and jobs that run on another Oracle Database.

To create the Scheduler Agent service after performing a software-only installation for Oracle Database Client, perform the following steps:

1.  Open a command window.
2.  Change directories to `ORACLE_HOME``\bin`.
3.  Run the executable utility, schagent to create the Scheduler Agent service:
    `C:\``ORACLE_HOME``\bin> schagent.exe -new`

**Parent topic:** [Recommended Postinstallation Tasks](recommended-postinstallation-tasks.md)
