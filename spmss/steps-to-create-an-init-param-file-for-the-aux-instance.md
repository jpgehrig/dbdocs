The initialization parameter file for the auxiliary instance must contain at least the `DB_NAME` and `DB_DOMAIN` initialization parameters. Additional parameters may be specified, if required. Ensure that the initialization parameter file is on the same host as the RMAN client that performs the duplication.

To create the initialization parameter file for the auxiliary instance:

1.  Do one of the following:
    - Copy the initialization parameter file from the source host to the destination host, placing it in the operating system-specific default location, and then modify the `DB_NAME` and `DB_DOMAIN` initialization parameters.

      If you are duplicating a CDB, ensure that the `ENABLE_PLUGGABLE_DATABASE` parameter is present and set to `TRUE`.

      See [Copying the Server Parameter File from the Source Database](copying-the-server-param-file-from-the-source-db.md).

    - Complete these steps:

      1.  Using a text editor, create an empty file for use as a text-based initialization parameter file, and save it in the operating system-specific default location.

      2.  In the parameter file, set the `DB_NAME` and `DB_DOMAIN` initialization parameters. These are the only required parameters.

          Setting the `DB_DOMAIN` parameter enables you to connect to the default database service when you connect with a net service name.

      3.  If the auxiliary instance is to be a CDB, then set the following parameter:
              ENABLE_PLUGGABLE_DATABASE=TRUE

2.  Set the various location parameters such as `CONTROL_FILES` and `DB_RECOVERY_FILE_DEST`.

3.  If necessary, set other initialization parameters like those needed for Oracle Real Application Clusters.

4.  Set the required environment variables, such as `ORACLE_HOME` and `ORACLE_SID`.

5.  (Optional) Set initialization parameters that specify the location of the duplicate database files if one of the following conditions is satisfied:

    - The source host and the destination host are the same (duplication to the local host).

    - The duplicate database uses a directory structure that is different from that of the source host to store database files.

    Depending on the technique used to specify alternate names for duplicate database files, include one or more of the following parameters in the initialization parameter file: `CONTROL_FILES`, `DB_FILE_NAME_CONVERT`, `LOG_FILE_NAME_CONVERT`, `DB_CREATE_FILE_DEST`, `DB_CREATE_ONLINE_FILE_DEST`\_`n`, and `RECOVERY_FILE_DEST`.

    **Note:**

    It is recommended that you verify that all paths specified are accessible to the destination host and to the server session of the auxiliary instance.

    See “Methods of Generating Database File Names for the Duplicate Database” in Oracle Database Backup and Recovery User’s Guide.

6.  Start SQL\*Plus and connect to the auxiliary instance as a user with `SYSDBA` or `SYSBACKUP` privileges. Start the auxiliary instance in `NOMOUNT` mode. If the file is in the default location, no `PFILE` parameter is required on the `STARTUP` command.
        SQL> STARTUP NOMOUNT;

Example 3-1 Sample Initialization Parameter File for the Auxiliary Instance

    DB_NAME=dupdb
    CONTROL_FILES=(/dup/oracle/oradata/prod/control01.ctl,
                    dup/oracle/oradata/prod/control02.ctl)
    DB_FILE_NAME_CONVERT=(/oracle/oradata/prod/,/dup/oracle/oradata/prod/)
    LOG_FILE_NAME_CONVERT=(/oracle/oradata/prod/redo,/dup/oracle/oradata/prod/redo)

**Parent topic:** [Preparing the Auxiliary Instance on the Destination Host](preparing-the-auxiliary-instance-destination-host.md)
