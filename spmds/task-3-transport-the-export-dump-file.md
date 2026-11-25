Transport the dump file to the directory pointed to by the `DATA_PUMP_DIR` directory object, or to any other directory of your choosing. The new location must be accessible to the target database.

At the target database, run the following query to determine the location of `DATA_PUMP_DIR`:

    SELECT * FROM DBA_DIRECTORIES WHERE DIRECTORY_NAME = 'DATA_PUMP_DIR';

    OWNER      DIRECTORY_NAME   DIRECTORY_PATH
    ---------- ---------------- -----------------------------------
    SYS        DATA_PUMP_DIR    C:\app\orauser\admin\orawin\dpdump\

**Parent topic:** [Migrating Oracle Database](migrating-oracle-database.md)
