Verify if the database is restored and recovered on the destination server.

For example:

`V$DATABASE` displays information about the database from the control file.

    [oracle @ oraDB-dup admin] $ sqlplus

    SQL> select name, open_mode, dbid, created from v$database;

`V$INSTANCE` displays the state of the current instance.

    SQL> select instance_name, host_name from v$instance;

`V$DATAFILE` displays information about the datafiles from the control file.

`V$CONTROLFILE` displays the names of the control files.

`V$LOGFILE` contains information about redo log files.

`V$TEMPFILE` displays temp file information.

    SQL> select name from v$datafile
    union
    select name from v$controlfile
    union
    select member from v$logfile
    union
    select name from v$tempfile;

`V$VERSION` displays the version number of Oracle Database.

    SQL> select banner from v$version;

**Parent topic:** [Duplicating the Primary Oracle Database](duplicating-the-oracle-database.md)
