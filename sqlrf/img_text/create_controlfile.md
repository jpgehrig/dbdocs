# Description of the illustration create_controlfile.eps

    CREATE CONTROLFILE
      [ REUSE ] [ SET ] DATABASE database
      [ logfile_clause ]
      { RESETLOGS | NORESETLOGS }
      [ DATAFILE file_specification
                 [, file_specification ]... ]
      [ MAXLOGFILES integer
      | MAXLOGMEMBERS integer
      | MAXLOGHISTORY integer
      | MAXDATAFILES integer
      | MAXINSTANCES integer
      | { ARCHIVELOG | NOARCHIVELOG }
      | FORCE LOGGING
      | SET STANDBY NOLOGGING FOR {DATA AVAILABILITY | LOAD PERFORMANCE}
     ]...
      [ character_set_clause ] ;
