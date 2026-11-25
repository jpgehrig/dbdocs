Unified auditing enables you to capture audit records from a variety of sources.

The unified audit trail, which resides in a read-only table in the `AUDSYS` schema in the `SYSAUX` tablespace, makes this information available in an uniform format in the `UNIFIED_AUDIT_TRAIL` data dictionary view.

When the database is writable, audit records are written to the unified audit trail. If the database is not writable, then audit records are written to new format operating system files in the POSIX file system in the `$ORACLE_BASE/audit/$ORACLE_SID` directory.

This chapter contains the following topics:

- Enabling Unified Auditing

- Disabling Unified Auditing

**See Also:**

[Oracle Database Security Guide](../dbseg/introduction-to-auditing.md) for more details

### 9.1 Enabling Unified Auditing

The Unified Auditing option is not enabled after you install Oracle Database. You can find if your database has been migrated to unified auditing by querying the `V$OPTION` dynamic view. Query the `VALUE` column of the `V$OPTION` dynamic view as follows with SQL\*Plus:

`SQL> SELECT VALUE FROM V$OPTION WHERE PARAMETER = 'Unified Auditing';`

If the output for the `VALUE` column is `TRUE`, then pure unified auditing is already enabled in your database. If unified auditing has not been enabled, then the output is `FALSE`.

To enable the Unified Auditing option, relink the `ORAKNL` binary in the `ORALOAD` library `$ORACINST.ORALOAD.LIB`. Relinking is done by calling a BS2000 command procedure.

After shutting down all databases and stopping all listeners, log in to the installation user ID `$ORACINST`. Enter the following BS2000 command to enable Unified Auditing:

`/CALL-PROCEDURE INSTALL.P.UNIAUD-ON`

Restart the databases and listeners in your DBA user IDs. After restarting, all the databases run with Unified Auditing.

### 9.2 Disabling Unified Auditing

To disable the Unified Auditing option, relink the `ORAKNL` binary in the `ORALOAD` library `$ORACINST.ORALOAD.LIB`. Relinking is done by calling a BS2000 command procedure.

After shutting down all databases and stopping all listeners, log in to the installation user ID `$ORACINST`. Enter the following BS2000 command to disable Unified Auditing:

`/CALL-PROCEDURE INSTALL.P.UNIAUD-OFF`

Restart the databases and listeners in your DBA user IDs. After restarting, all databases run without the Unified Auditing option.
