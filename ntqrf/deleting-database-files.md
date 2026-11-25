Deleting database files is required only when you copy an existing database to a new database to replace the old database.

In the following example, you delete the database files of the starter database `orcl`.

To delete database files:

1.  Shut down starter database `orcl` at the command prompt:
        C:\> oradim -SHUTDOWN -SID orcl -SHUTTYPE inst -SHUTMODE immediate
2.  Delete the following files from the directory `C:\app`\\username\\`oradata\orcl`:
        control01.ctl
        control02.ctl
        control03.ctl
        index01.dbf
        drsys01.dbf
        cwmlite01.dbf
        example01.dbf
        system01.dbf
        temp01.dbf
        tools01.dbf
        undotbs01.dbf
        user01.dbf
        xdb01.dbf
        redo01.log
        redo02.log
        redo03.log

**Parent topic:** [Overview of Database Creation Tasks on Windows Using Command-Line Tools](overview-of-database-creation-tasks-on-windows-using-command-line-tools.md)
