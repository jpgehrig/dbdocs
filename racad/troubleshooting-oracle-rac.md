This appendix explains how diagnose problems for Oracle Real Application Clusters (Oracle RAC) components using trace and log files. This section includes the following topics:

- Where to Find Files for Analyzing Errors

- Managing Diagnostic Data in Oracle RAC

- Using Instance-Specific Alert Files in Oracle RAC

- Enabling Tracing for Java-Based Tools and Utilities in Oracle RAC

- Resolving Pending Shutdown Issues

- How to Determine If Oracle RAC Instances Are Using the Private Network

**Note:**

Trace and log files, similar to those generated for Oracle Database with Oracle RAC, are also available for the Oracle Clusterware components. For Oracle Clusterware, Oracle Database stores these under a unified directory log structure.

See the [Oracle Clusterware Administration and Deployment Guide](../cwadd/troubleshooting-oracle-clusterware.md) for more information about troubleshooting Oracle Clusterware.

### Where to Find Files for Analyzing Errors

Oracle Database records information about important events that occur in your Oracle RAC environment in trace files.

The trace files for Oracle RAC are the same as those in noncluster Oracle databases. As a best practice, monitor and back up trace files regularly for all instances to preserve their content for future troubleshooting.

Information about `ORA-600` errors appear in the `alert_``SID``.log` file for each instance where `SID` is the instance identifier.

The alert log and all trace files for background and server processes are written to the Automatic Diagnostic Repository, the location of which you can specify with the `DIAGNOSTIC_DEST` initialization parameter. For example:

    $ORACLE_BASE/diag/rdbms/$DBNAME/$SID_NAME/trace

Oracle Database creates a different trace file for each background thread. Oracle RAC background threads use trace files to record database operations and database errors. These trace logs help troubleshoot and also enable Oracle Support to more efficiently debug cluster database configuration problems. The names of trace files are operating system specific, but each file usually includes the name of the process writing the file (such as LGWR and RECO). For Linux, UNIX, and Windows systems, trace files for the background processes are named `SID_``process_name``_``process_identifier``.trc`.

Trace files are also created for user processes if you set the `DIAGNOSTIC_DEST` initialization parameter. User process trace file names have the format `SID``_ora_``process_identifier``/``thread_identifier``.trc`, where `process_identifier` is a 5-digit number indicating the process identifier (PID) on Linux and UNIX systems, and `thread_identifier` is the thread identifier on Windows systems.

**Related Topics**

- [Troubleshooting Oracle Clusterware](../cwadd/troubleshooting-oracle-clusterware.md)
- [Monitoring the Database](../admin/monitoring-the-database.md)

### Managing Diagnostic Data in Oracle RAC

Problems that span Oracle RAC instances can be the most difficult types of problems to diagnose.

For example, you may need to correlate the trace files from across multiple instances, and merge the trace files. Oracle Database 12c release 2 (12.2) includes an advanced fault diagnosability infrastructure for collecting and managing diagnostic data, and uses the Automatic Diagnostic Repository (ADR) file-based repository for storing the database diagnostic data. When you create the ADR base on a shared disk, you can place ADR homes for all instances of the same Oracle RAC database under the same ADR Base. With shared storage:

- You can use the ADRCI command-line tool to correlate diagnostics across all instances.

  ADRCI is a command-line tool that enables you to view diagnostic data in the ADR and package incident and problem information into a zip file for transmission to Oracle Support. The diagnostic data includes incident and problem descriptions, trace files, dumps, health monitor reports, alert log entries, and so on.

- You can use the Data Recovery Advisor to help diagnose and repair corrupted data blocks, corrupted or missing files, and other data failures.

  The Data Recovery Advisor is an Oracle Database infrastructure that automatically diagnoses persistent data failures, presents repair options, and repairs problems at your request.

**Related Topics**

- [ADRCI: ADR Command Interpreter](../sutil/oracle-adr-command-interpreter-adrci.md)
- [Diagnosing and Resolving Problems](../admin/diagnosing-and-resolving-problems.md)

### Using Instance-Specific Alert Files in Oracle RAC

Each instance in an Oracle RAC database has one alert file.

The alert file for each instance, `alert_``SID``.log`, contains important information about error messages and exceptions that occur during database operations. Information is appended to the alert file each time you start the instance. All process threads can write to the alert file for the instance.

The `alert_``SID``.log` file is in the directory specified by the `DIAGNOSTIC_DEST` initialization parameter.

### Enabling Tracing for Java-Based Tools and Utilities in Oracle RAC

All Java-based tools and utilities that are available in Oracle RAC are called by processing scripts of the same name as the tool or utility.

This includes the Cluster Verification Utility (CVU), Oracle Database Configuration Assistant (Oracle DBCA), the Net Configuration Assistant (NETCA), and the Server Control Utility (SRVCTL). For example, to run Oracle DBCA, enter the command `dbca`.

By default, Oracle Database enables traces for Oracle DBCA and the Database Upgrade Assistant (DBUA). For the CVU, and SRVCTL, you can set the `SRVM_TRACE` environment variable to `TRUE` to make Oracle Database generate traces. Oracle Database writes traces to log files. For example, Oracle Database writes traces to log files in `Oracle_base``/cfgtoollogs/dbca` and `Oracle_base``/cfgtoollogs/dbua` for Oracle DBCA and Oracle DBUA, respectively.

### Resolving Pending Shutdown Issues

In some situations a `SHUTDOWN IMMEDIATE` may be pending and Oracle Database will not quickly respond to repeated shutdown requests.

This is because Oracle Clusterware may be processing a current shutdown request. In such cases, issue a `SHUTDOWN ABORT` using SQL\*Plus for subsequent shutdown requests.

### How to Determine If Oracle RAC Instances Are Using the Private Network

This topic describes how to manually determine if Oracle RAC instances are using the private network.

However, the best practice for this task is to use the Oracle Enterprise Manager Cloud Control graphical user interface (GUI) to check the interconnect.

With most network protocols, you can issue the `oradebug ipc` command to see the interconnects that the database is using. For example:

    oradebug setmypid
    oradebug ipc

These commands dump a trace file to the location specified by the `DIAGNOSTIC_DEST` initialization parameter. The output may look similar to the following:

    SSKGXPT 0x1a2932c flags SSKGXPT_READPENDING     info for network 0
            socket no 10    IP 172.16.193.1         UDP 43749
            sflags SSKGXPT_WRITESSKGXPT_UP  info for network 1
            socket no 0     IP 0.0.0.0      UDP 0...

In the example, you can see the database is using IP 172.16.193.1 with a User Datagram Protocol (UDP) protocol. Also, you can issue the `oradebug tracefile_name` command to print the trace location where the output is written.

Additionally, you can query the `V$CLUSTER_INTERCONNECTS` view to see information about the private interconnect. For example:

    SQL> SELECT * FROM V$CLUSTER_INTERCONNECTS;

    NAME  IP_ADDRESS          IS_  SOURCE
    ----- -------------------------- ---  -------------------------------
    eth0  138.2.236.114         NO  Oracle Cluster Repository
