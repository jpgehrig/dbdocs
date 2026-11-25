Learn how to start an instance without mounting a database.

Start an instance without mounting a database.

    SQL> STARTUP NOMOUNT

You must not specify the `PFILE` clause in this example, because the initialization parameter file is stored in the default location. At this point, there is no database. Only the System Global Area (SGA) is created and the background processes are started in preparation for the creation of a new database.

**Parent topic:** [Overview of Database Creation Tasks on Windows Using Command-Line Tools](overview-of-database-creation-tasks-on-windows-using-command-line-tools.md)
