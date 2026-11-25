These steps describe how to perform a switchover to a physical standby database.

**Note:**

If there is a far sync instance (or a combination of preferred and alternate far sync instances) connecting the primary and standby databases, then the procedure to switchover to the standby is the same as described in this topic. Whether the far sync instances are available or unavailable does not affect switchover. During switchover, the primary and standby must be able to communicate directly with each other and perform the switchover role transition steps oblivious of the far sync instances. See “Using Far Sync Instances” in Oracle Data Guard Concepts and Administration for examples of how to set up such configurations correctly so that the far sync instances can service the new roles of the two databases after switchover.

1.  Verify that the target standby database is ready for switchover.
    The new switchover statement has a `VERIFY` option that results in checks being performed of many conditions required for switchover. Some of the items checked are: whether Redo Apply is running on the switchover target; whether the release version of the switchover target is 12.1 or later; whether the switchover target is synchronized; and whether it has MRP running.

    Suppose the primary database has a `DB_UNIQUE_NAME` of `BOSTON` and the switchover target standby database has a `DB_UNIQUE_NAME` of `CHICAGO`. On the primary database `BOSTON`, issue the following SQL statement to verify that the switchover target, `CHICAGO`, is ready for switchover:

        SQL> ALTER DATABASE SWITCHOVER TO CHICAGO VERIFY;
        ERROR at line 1:
        ORA-16470: Redo Apply is not running on switchover target

    If this operation had been successful, a `Database Altered` message would have been returned but in this example an `ORA-16470` error was returned. This error means that the switchover target `CHICAGO` is not ready for switchover. Redo Apply must be started before the switchover operation.

    After Redo Apply is started, issue the following statement again:

        SQL> ALTER DATABASE SWITCHOVER TO CHICAGO VERIFY;
        ERROR at line 1:
        ORA-16475: succeeded with warnings, check alert log for more details

    The switchover target, `CHICAGO`, is ready for switchover. However, the warnings indicated by the `ORA-16475` error may affect switchover performance. The alert log contains messages similar to the following:

        SWITCHOVER VERIFY WARNING: switchover target has dirty online redo logfiles that require clearing. It takes time to clear online redo logfiles. This may slow down switchover process.

    You can fix the problems or if switchover performance is not important, those warnings can be ignored. After making any fixes you determine are necessary, issue the following SQL statement again:

        SQL> ALTER DATABASE SWITCHOVER TO CHICAGO VERIFY;
        Database altered.

    The switchover target, `CHICAGO`, is now ready for switchover.
2.  Initiate the switchover on the primary database, `BOSTON`, by issuing the following SQL statement:
        SQL> ALTER DATABASE SWITCHOVER TO CHICAGO;
        Database altered.

    If this statement completes without any errors, proceed to Step 3.

    If an error occurs, mount the old primary database (`BOSTON`) and the old standby database (`CHICAGO`). On both databases, query `DATABASE_ROLE` from `V$DATABASE`. There are three possible combinations of database roles for `BOSTON` and `CHICAGO`. The following table describes these combinations and provides the likely cause and a high level remedial action for each situation. For details on specific error situations, see “Troubleshooting Oracle Data Guard” in Oracle Data Guard Concepts and Administration.

    | Value of DATABASE_ROLE column in V\$DATABASE                | Cause and Remedial Action                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    |:------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `BOSTON` database is primary, `CHICAGO` database is standby | Cause: The `BOSTON` database failed to convert to a standby database role.<br>Action: See the alert log for details on the error that prevented `BOSTON` from switching to a standby role, take the necessary actions to fix the error, reopen one of the nodes of `BOSTON` if necessary, and repeat the switchover process from Step 1.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `BOSTON` database is standby, `CHICAGO` database is standby | Cause: The `CHICAGO` database failed to convert to a primary database role.<br>Action: Issue the following SQL statement to convert either `BOSTON` or `CHICAGO` to a primary database:<br>`SQL> ALTER DATABASE SWITCHOVER TO target_db_name`<br>`FORCE;`<br>For example:<br>• On the `CHICAGO` database, issue the following SQL statement to convert it to a primary database:<br>`ALTER DATABASE SWITCHOVER TO CHICAGO FORCE;`<br>• On the `BOSTON` database, issue the following SQL statement to convert it to a primary database:<br>`ALTER DATABASE SWITCHOVER TO BOSTON FORCE;`<br>If the SQL statement fails with an `ORA-16473` error, then you must start Redo Apply before reissuing the command.<br>Restart Redo Apply as follows:<br>`SQL> ALTER DATABASE RECOVER MANAGED STANDBY DATABASE DISCONNECT;`<br>Reissue the switchover command as follows:<br>`SQL> ALTER DATABASE SWTICHOVER TO BOSTON FORCE;`<br>`Database altered.` |
    | `BOSTON` database is standby, `CHICAGO` database is primary | Cause: The `BOSTON` and `CHICAGO` databases have successfully switched to their new roles, but there was an error communicating the final success status back to `BOSTON`.<br>Action: Continue to Step 3 to finish the switchover operation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
3.  Issue the following SQL statement on the new primary database, `CHICAGO`, to open it.
        SQL> ALTER DATABASE OPEN;
4.  Issue the following SQL statement to mount the new physical standby database, `BOSTON`:
        SQL> STARTUP MOUNT;

    Or, if `BOSTON` is an Oracle Active Data Guard physical standby database, then issue the following SQL statement to open it read only:

        SQL> STARTUP;
5.  Start Redo Apply on the new physical standby database. For example:
        SQL> ALTER DATABASE RECOVER MANAGED STANDBY DATABASE DISCONNECT FROM SESSION;

**Parent topic:** [Refresh and Switchover to the Physical Standby Oracle Database](refresh-and-switchover-to-the-phyical-standby-db.md)
