Consider the issues of Diagnostics and Maintenance.

### 6.1 Diagnostics for Oracle Database Provider for DRDA

Diagnostics for Oracle Database Provider for DRDA consist of the trace facility, which is configurable through the trace level before the application runs, and may be adjusted by the command-line tool. Oracle Database Provider for DRDA uses the Automatic Diagnostic Repository (ADR) to hold all logs, traces and dump records. See section "Automatic Diagnostic Repository (ADR)" in [Oracle® Database Administrator’s Guide](../admin/diagnosing-and-resolving-problems.md).

The trace logs DRDA protocol errors before, during, and after each client session. There are specific DRDA architecture error alerts that are intended to diagnose a protocol violation. Additional errors from the OCI session may also be logged there.

Diagnostics may be summarized as the ability to trace, or collect diagnostic information, usually in a file.

The trace directory may be specified by the user. By default, Oracle Database Provider for DRDA creates a trace directory in` ORACLE_BASE/diag`or `ORACLE_HOME/log/diag`. Within this root directory, Oracle Database Provider for DRDA stores trace files in `dps/``drdaas``/instance/trace`, where `instance` is the instance name used in the `drdaas.ora` file. The `adrci` utility enables viewing and manipulation of trace files.

Depending on the application, different levels of diagnostic detail might become necessary. By default, diagnostic depth is set to off, for performance reasons. However, incidents are logged in the repository if the AS fails.

**Related Topics**

- [Command-line Utility](command-line-utility.md)

### 6.2 Maintaining Oracle Database Provider for DRDA

To communicate with the Application Server, Oracle provides an external command interface. The command interface supports the following interactions:

- Starting the server

- Stopping the server

- Determining server status

- Displaying connected client sessions

- Displaying details of client sessions, which includes:

  - Session state (command being executed, such as preparing, executing, fetching, idle, and so on)

  - Last SQL statement prepared

  - Client IP address and port number

  - Oracle SQL Session Id

- Pausing a SQL session

- Terminating a SQL session

- Reloading server configuration

See “Command-line Utility for Oracle Database Provider for DRDA” for details of these operations.

**Related Topics**

- [Command-line Utility for Oracle Database Provider for DRDA](command-line-utility.md)
