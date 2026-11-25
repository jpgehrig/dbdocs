Run the DUPLICATE command on the destination server.

For example:

    DUPLICATE DATABASE TO dupdb
    FOR STANDBY
    FROM ACTIVE DATABASE
    PASSWORD FILE
    SPFILE PARAMETER_VALUE_CONVERT='/app/dbhome1','/app/db_home2'
    SET db_file_name_convert='/app/dbhome1/dbs','/app/db_home2/database/dbs'
    SET log_file_name_convert='/app/dbhome1/log','/app/db_home2/logfiles'
    NOFILENAMECHECK;

**Parent topic:** [Duplicating the Primary Oracle Database](duplicating-the-oracle-database.md)
