Oracle Text provides indexing, word and theme searching, and viewing capabilities for text in query applications and document classification applications.

This chapter describes how to install and run Oracle Text and the restrictions of this option on BS2000. It includes the following topics:

- Installing Oracle Text

- Restrictions of Oracle Text on BS2000

### 11.1 Installing Oracle Text

Oracle Text is not installed when you create a database. To install Oracle Text, you must complete the following steps:

1.  Start SQL\*Plus. To avoid being prompted for many overflow acknowledgements on the screen, set `OVERFLOW-CONTROL=*NO-CONTROL`:
        /MODIFY-TERMINAL-OPTIONS OVERFLOW-CONTROL=*NO-CONTROL
        /START-EXECUTABLE (*LINK(ORALOAD),SQLPLUS)
        * /nolog
        connect / as sysdba
        spool catctx.log
        @$ORACLE_HOME/ctx/admin/catctx.sql CTXSYS SYSAUX TEMP NOLOCK;

    where `CTXSYS` is the password for `ctxsys`, `SYSAUX` is the default tablespace for `ctxsys`, `TEMP` is the temporary tablespace for `ctxsys`, and `LOCK|NOLOCK` specifies whether the `ctxsys` user account is locked or not.
2.  If you are working with US english texts, then install the appropriate language-specific default preferences:
        connect CTXSYS/CTXSYS
        @$ORACLE_HOME/ctx/admin/defaults/drdefus.sql;

    If you are not working with US english texts, then open the `drdef*.sql` script in the `$ORACLE_HOME/ctx/admin/defaults` directory according to the preferred language, set the attributes, and run the script.

    Before you set the attributes, refer to "Restrictions of Oracle Text on BS2000."
3.  Type `exit` when finished.

### 11.2 Restrictions of Oracle Text on BS2000

The following restrictions apply for Oracle Text on Fujitsu BS2000:

- Index themes are not supported.

- INSO filters, which are licensed on special platforms only, are not supported.

- `ctxkbtc`, which is a knowledge base utility is not supported.

- `URL_DATASTORE` objects are not supported.

**Note:**

`FILE_DATASTORE` objects may reside on native BS2000 DMS as PAM files or on the POSIX file system.
