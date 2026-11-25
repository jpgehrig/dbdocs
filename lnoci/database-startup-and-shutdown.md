This chapter describes topics about OCI database startup and shutdown.

This section describes the following topics:

- About OCI Database Startup and Shutdown

- Examples of Startup and Shutdown in OCI

### 16.1 About OCI Database Startup and Shutdown

The OCI functions `OCIDBStartup()` and `OCIDBShutdown()` provide the minimal interface needed to start and shut down an Oracle database.

Before calling `OCIDBStartup()`, the C program must connect to the server and start a `SYSDBA` or `SYSOPER` session in the preliminary authentication mode. This mode is the only one permitted when the instance is not up, and it is used only to start the instance. A call to `OCIDBStartup()` starts one server instance without mounting or opening the database. To mount and open the database, end the preliminary authentication session and start a regular `SYSDBA` or `SYSOPER` session to execute the appropriate `ALTER` `DATABASE` statements.

An active `SYSDBA` or `SYSOPER` session is needed to shut down the database. For all modes other than `OCI_DBSHUTDOWN_ABORT`, make two calls to `OCIDBShutdown()`: one to initiate shutdown by prohibiting further connections to the database, followed by the appropriate `ALTER` `DATABASE` commands to dismount and close it; and the other call to finish shutdown by bringing the instance down. In special circumstances, to shut down the database as fast as possible, call `OCIDBShutdown()` in the `OCI_DBSHUTDOWN_ABORT` mode, which is equivalent to `SHUTDOWN ``ABORT` in SQL\*Plus.

Both of these functions require a dedicated connection to the server. `ORA-106` is signaled if an attempt is made to start or shut down the database when it is connected to a shared server through a dispatcher.

The `OCIAdmin` administration handle C data type is used to make the interface extensible. `OCIAdmin` is associated with the handle type `OCI_HTYPE_ADMIN`. Passing a value for the `OCIAdmin` parameter, `admhp`, is optional for `OCIDBStartup()` and is not needed by `OCIDBShutdown()`.

**See Also:**

- [OCIDBStartup()](connect-authorize-and-initialize-functions.md)

- [OCIDBShutdown()](connect-authorize-and-initialize-functions.md)

- [Administration Handle Attributes](handle-and-descriptor-attributes.md)

- [Oracle Database Administrator’s Guide](../admin/starting-up-and-shutting-down.md)

### 16.2 Examples of Startup and Shutdown in OCI

To perform a startup, you must be connected to the database as `SYSOPER` or `SYSDBA` in `OCI_PRELIM_AUTH` mode. You cannot be connected to a shared server through a dispatcher.

To use a client-side parameter file (`pfile`), the attribute `OCI_ATTR_ADMIN_PFILE` must be set in the administration handle using `OCIAttrSet()`; otherwise, a server-side parameter file (`spfile`) is used. In the latter case, pass `(OCIAdmin *)0`. A call to `OCIDBStartup()` starts one instance on the server.

Example 16-1 shows sample code that uses a client-side parameter file (`pfile`) that is set in the administration handle and performs a database startup operation.

To perform a shutdown, you must be connected to the database as `SYSOPER` or `SYSDBA`. You cannot be connected to a shared server through a dispatcher. When shutting down in any mode other than `OCI_DBSHUTDOWN_ABORT`, use the following procedure:

1.  Call `OCIDBShutdown()` in `OCI_DEFAULT`, `OCI_DBSHUTDOWN_TRANSACTIONAL`, `OCI_DBSHUTDOWN_TRANSACTIONAL_LOCAL`, or `OCI_DBSHUTDOWN_IMMEDIATE` mode to prohibit further connections.
2.  Use the necessary `ALTER` `DATABASE` commands to close and dismount the database.
3.  Call `OCIDBShutdown()` in `OCI_DBSHUTDOWN_FINAL` mode to shut down the instance.

Example 16-1 Calling OCIDBStartup() to Perform a Database Startup Operation

    ...

    /*  Example 0 - Startup:  */
    OCIAdmin *admhp;
    text *mount_stmt = (text *)"ALTER DATABASE MOUNT";
    text *open_stmt = (text *)"ALTER DATABASE OPEN";
    text *pfile = (text *)"/ade/viewname/oracle/work/t_init1.ora";

    /* Start the authentication session */
    checkerr(errhp, OCISessionBegin (svchp, errhp, usrhp,
             OCI_CRED_RDBMS, OCI_SYSDBA|OCI_PRELIM_AUTH));

    /* Allocate admin handle for OCIDBStartup */
    checkerr(errhp, OCIHandleAlloc((void *) envhp, (void **) &admhp,
             (ub4) OCI_HTYPE_ADMIN, (size_t) 0, (void **) 0));

    /* Set attribute pfile in the admin handle
    (do not do this if you want to use the spfile) */
    checkerr (errhp, OCIAttrSet( (void *) admhp, (ub4) OCI_HTYPE_ADMIN,
              (void *) pfile, (ub4) strlen(pfile),
              (ub4) OCI_ATTR_ADMIN_PFILE, (OCIError *) errhp));

    /* Start up in NOMOUNT mode */
      checkerr(errhp, OCIDBStartup(svchp, errhp, admhp, OCI_DEFAULT, 0));
       checkerr(errhp, OCIHandleFree((void *) admhp, (ub4) OCI_HTYPE_ADMIN));

    /* End the authentication session */
    OCISessionEnd(svchp, errhp, usrhp, (ub4)OCI_DEFAULT);

    /* Start the sysdba session */
    checkerr(errhp, OCISessionBegin (svchp, errhp, usrhp, OCI_CRED_RDBMS,
             OCI_SYSDBA));

    /* Mount the database */
    checkerr(errhp, OCIStmtPrepare2(svchp, &stmthp, errhp, mount_stmt, (ub4)
             strlen((char*) mount_stmt),
             (CONST OraText *) 0, (ub4) 0, (ub4) OCI_NTV_SYNTAX, (ub4)
             OCI_DEFAULT));
    checkerr(errhp, OCIStmtExecute(svchp, stmthp, errhp, (ub4) 1, (ub4)0,
             (OCISnapshot *) NULL, (OCISnapshot *) NULL, OCI_DEFAULT));
    checkerr(errhp, OCIStmtRelease(stmthp, errhp, (OraText *)0, 0, OCI_DEFAULT));

    /* Open the database */
    checkerr(errhp, OCIStmtPrepare2(svchp, &stmthp, errhp, open_stmt, (ub4)
             strlen((char*) open_stmt),
             (CONST OraText *)0, (ub4)0, (ub4) OCI_NTV_SYNTAX, (ub4) OCI_DEFAULT));
    checkerr(errhp, OCIStmtExecute(svchp, stmthp, errhp, (ub4) 1, (ub4)0,
             (OCISnapshot *) NULL, (OCISnapshot *) NULL, OCI_DEFAULT));
    checkerr(errhp, OCIStmtRelease(stmthp, errhp, (OraText *)0, 0, OCI_DEFAULT));

    /* End the sysdba session */
    OCISessionEnd(svchp, errhp, usrhp, (ub4)OCI_DEFAULT);
    ...

Example 16-2 Calling OCIDBShutdown() in OCI_DBSHUTDOWN_FINAL Mode

    /*  Example 1 - Orderly shutdown:  */
    ...
    text *close_stmt = (text *)"ALTER DATABASE CLOSE NORMAL";
    text *dismount_stmt = (text *)"ALTER DATABASE DISMOUNT";

    /* Start the sysdba session */
    checkerr(errhp, OCISessionBegin (svchp, errhp, usrhp, OCI_CRED_RDBMS,
             OCI_SYSDBA));

    /* Shutdown in the default mode (transactional, transactional-local,
      immediate would be fine too) */
    checkerr(errhp, OCIDBShutdown(svchp, errhp, (OCIAdmin *)0, OCI_DEFAULT));

    /* Close the database */
    checkerr(errhp, OCIStmtPrepare2(svchp, &stmthp, errhp, close_stmt, (ub4)
             strlen((char*) close_stmt),
             (CONST OraText *)0, (ub4)0, (ub4) OCI_NTV_SYNTAX,
             (ub4) OCI_DEFAULT));
    checkerr(errhp, OCIStmtExecute(svchp, stmthp, errhp, (ub4) 1, (ub4)0,
            (OCISnapshot *) NULL,
            (OCISnapshot *) NULL, OCI_DEFAULT));
    checkerr(errhp, OCIStmtRelease(stmthp, errhp, (OraText *)0, 0, OCI_DEFAULT));

    /* Dismount the database */
    checkerr(errhp, OCIStmtPrepare2(svchp, &stmthp, errhp, dismount_stmt,
             (ub4) strlen((char*) dismount_stmt), (CONST OraText *)0, (ub4)0,
             (ub4) OCI_NTV_SYNTAX, (ub4) OCI_DEFAULT));
    checkerr(errhp, OCIStmtExecute(svchp, stmthp, errhp, (ub4) 1, (ub4)0,
             (OCISnapshot *) NULL,
             (OCISnapshot *) NULL, OCI_DEFAULT));
    checkerr(errhp, OCIStmtRelease(stmthp, errhp, (OraText *)0, 0, OCI_DEFAULT));

    /* Final shutdown */
    checkerr(errhp, OCIDBShutdown(svchp, errhp, (OCIAdmin *)0,
             OCI_DBSHUTDOWN_FINAL));

    /* End the sysdba session */
    checkerr(errhp, OCISessionEnd(svchp, errhp, usrhp, (ub4)OCI_DEFAULT));
    ...

Example 16-3 Calling OCIDBShutdown() in OCI_DBSHUTDOWN_ABORT Mode

    /*  Example 2 - Shutdown using abort:  */
    ...
    /* Start the sysdba session */
    ...
    checkerr(errhp, OCISessionBegin (svchp, errhp, usrhp, OCI_CRED_RDBMS,
             OCI_SYSDBA));

    /* Shutdown in the abort mode */
    checkerr(errhp, OCIDBShutdown(svchp, errhp, (OCIAdmin *)0,
             OCI_DBSHUTDOWN_ABORT));

    /* End the sysdba session */
    checkerr(errhp, OCISessionEnd(svchp, errhp, usrhp, (ub4)OCI_DEFAULT));
    ...

Example 16-2 shows sample code that uses a client-side parameter file (`pfile`) that is set in the administration handle that performs an orderly database shutdown operation.

Example 16-3 shows a shutdown example that uses `OCI_DBSHUTDOWN_ABORT` mode.

**See Also:**

- [OCIAttrSet()](handle-and-descriptor-functions.md)

- [OCIDBStartup()](connect-authorize-and-initialize-functions.md)

- [OCIDBShutdown()](connect-authorize-and-initialize-functions.md)
