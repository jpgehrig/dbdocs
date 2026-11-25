# Description of the illustration create_database.eps

    CREATE DATABASE [ database ]
      { USER SYS IDENTIFIED BY password
      | USER SYSTEM IDENTIFIED BY password
      | CONTROLFILE REUSE
      | MAXDATAFILES integer
      | MAXINSTANCES integer
      | CHARACTER SET charset
      | NATIONAL CHARACTER SET charset
      | SET DEFAULT
          { BIGFILE | SMALLFILE } TABLESPACE
      | database_logging_clauses
      | tablespace_clauses
      | set_time_zone_clause
      | [ BIGFILE | SMALLFILE ] USER_DATA TABLESPACE tablespace_name
          DATAFILE datafile_tempfile_spec [, datafile_tempfile_spec ]...
      | enable_pluggable_database
      }... ;
