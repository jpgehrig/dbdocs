This topic describes problems that you may encounter when using Oracle Database 19c on BS2000, and provides you with information about how to diagnose and overcome such problems.

To solve a problem, identify the type of the problem and locate the relevant information in this topic. Examine each of the listed points to find the cause of the problem. Carry out the suggested solution, and try again. The event log file described in this document may help you to diagnose the problem.

This appendix contains the following topics:

- Problems Creating an Oracle Database

- Problems Starting an Oracle Database Instance

- Problems When Starting the Background Tasks

- Problems Accessing Database and Log Files

- Oracle Database Trace Files

**See Also:**

[Oracle Error Messages for BS2000](oracle-error-messages-for-bs2000-osd.md) in this guide and [Oracle Database Error Messages Reference](../errmg/using-messages.md) for information about specific messages

### D.1 Problems Creating an Oracle Database

You should always use the BS2000 procedure `INSTALL.P.SUPER` to create a new database, because this is the easiest way to get a correct instance. If you encounter problems during this process, then study the diagnostic output, correct, and run the respective part manually, or remove the partially created database, and rerun the whole process.

Also, check the following:

- If the BS2000 user ID has sufficient `PUBLIC-SPACE-LIMIT` for the corresponding pubset.

- If enough disk space is available on the pubset that is used to create the databases.

- If the disk space fragmentation is too high.

### D.2 Problems Starting an Oracle Database Instance

This topic contains information related to problems that you may encounter when starting an Oracle Database instance.

- If you get an `ORA-05032` error with no extra information, then check the following:

  If you attempt to start an instance and the startup fails, you might get an `ORA-05032` message and not much information. This indicates that a problem occurred in a very early stage of the startup, when Oracle Database error stack and backtracking mechanism were not yet active. If this is the case, then you should check the following:

  - If you called the `ORAENV` procedure prior to calling SQL\*Plus.

  - If you specified a correct and unique `ORASID` value in the `ORAENV` file

  - If there potential address range conflicts:

    The address ranges assigned to the kernel memory pool, the SGA, and the PGA, in each task, could be partially occupied by shared BS2000 subsystems also used in the instance. Contact the System Administrator to find out how the subsystems are arranged. Then change the corresponding `xxx_BASE` environment variables in the `ORAENV` file to relocate the Oracle Database areas to suitable address ranges.

  - If the user address space is large enough:

    A small address space limit may not leave enough space for Oracle Database requirements.

  - If a previous startup attempt failed, leaving invalid background, server, or user tasks:

    If the Oracle Database has not been shut down properly, then the old background tasks or server tasks may hang and may still be connected to the SGA of the old instance. This inhibits the creation of a new SGA. You may get a message indicating `shutdown in progress`.

    Cancel the remaining background, server, and user tasks. Exit SQL\*Plus, which is required to release shared memory pools of the old instance and retry.

### D.3 Problems When Starting the Background Tasks

If you get a timeout message when starting the background tasks, then check the following points:

- If the background tasks are blocked in the BS2000 job queue. This may occur due to a system overload or an insufficient task priority.

  The background tasks must always be started with the `IMMEDIATE` option and preferably in a reserved BS2000 jobclass. Check the `BGJPAR` environment variable and the user attributes of the BS2000 user ID. Cancel any background tasks that have already started.

- If no background task can be found using the `/SHOW-USER-STATUS` command, then the jobs have probably been aborted. Check the job outputs.

### D.4 Problems Accessing Database and Log Files

If you have problems opening, closing, reading, or writing a database or log file, then check the following points:

- If the file exists.

- If the file is accessible to the program that is trying to open it.

- If there is a hardware problem.

- If you specified the correct block size.

If you specified the `ORAENV` environment variable, `SF_PBLKSIZE`, at database creation, then you must continue to use the same specification whenever you run an `ALTER DATABASE` statement.

### D.5 Oracle Database Trace Files

Whenever an Oracle database encounters an exception, it writes a trace or a dump file. Verify this trace file for more detailed information about the issue. You may need to send the trace file to the Oracle Support Services Representative, if you cannot resolve the issue.
