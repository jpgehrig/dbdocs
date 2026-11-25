## Moving Data Files to OMS

Use this procedure if you want to move selected data files to Oracle Memory Speed (OMS) storage.

**Note:**

If you are connected to a CDB, ensure that you switch to the PDB before you move the data file that belongs to the PDB.

1.  Choose the data file that needs to be moved to OMS by querying `v$datafile`.
2.  Select `name`, `file#` from `v$datafile`.
3.  To move `file#=3` to OMS:
        SQL> alter database move datafile 3 to ‘OMS_FILE_NAME’;
4.  If you have already set db_create_file_dest to point to the OMS mount directory, then move the data file.
        SQL> alter database move datafile 3;

    The online data file move command copies the data file contents from the original location and updates the control file with the new OMS file name location.
5.  Use `v$datafile` to verify if the move has completed.
        SQL> select file#, name from v$datafile where file#=3;

**Parent topic:** [Migrating Oracle Database to Oracle Memory Speed](migrating-db-to-oms.md)
