If your database release is earlier than Oracle Database 11g, then you must migrate the database that is being upgraded from using rollback segments (manual undo management) to automatic undo management.

Automatic undo management is the default undo space management mode. The `UNDO_MANAGEMENT` initialization parameter specifies which undo space management mode the system should use:

- If UNDO_MANAGEMENT is set to `AUTO` (or if UNDO_MANAGEMENT is not set), then the database instance starts in automatic undo management mode.

  A null UNDO_MANAGEMENT initialization parameter defaults to automatic undo management mode in Oracle Database 11g Release 1 (11.1) and later. In earlier releases it defaults to manual undo management mode. Use caution when upgrading earlier releases.

- If UNDO_MANAGEMENT is set to `MANUAL`, then undo space is allocated externally as rollback segments.

1.  Set the UNDO_MANAGEMENT parameter to `UNDO_MANAGEMENT=MANUAL`.
2.  Start the instance again and run through a standard business cycle to obtain a representative workload. Assess the workload, and compute the size of the undo tablespace that you require for automatic undo management.
3.  After the standard business cycle completes, run the following function to collect the undo tablespace size, and to help with the sizing of the undo tablespace. You require SYSDBA privileges to run this function.
        DECLARE
           utbsiz_in_MB NUMBER;
        BEGIN
           utbsiz_in_MB := DBMS_UNDO_ADV.RBU_MIGRATION;
        end;
        /

    This function runs a PL/SQL procedure that provides information on how to size your new undo tablespace based on the configuration and usage of the rollback segments in your system. The function returns the sizing information directly.
4.  Create an undo tablespace of the required size and turn on the automatic undo management by setting `UNDO_MANAGEMENT=AUTO` or by removing the parameter.
5.  For Oracle RAC configurations, repeat these steps on all instances.

**Parent topic:** [Recommended and Best Practices to Complete After Upgrading Oracle Database](recommended-and-best-practices-complete-upgrading-oracle-database.md)
