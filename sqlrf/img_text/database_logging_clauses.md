# Description of the illustration database_logging_clauses.eps

    { LOGFILE
        [ GROUP integer ] file_specification
          [, [ GROUP integer ] file_specification ]...
    | MAXLOGFILES integer
    | MAXLOGMEMBERS integer
    | MAXLOGHISTORY integer
    | { ARCHIVELOG | NOARCHIVELOG }
    | FORCE LOGGING
    | SET STANDBY NOLOGGING FOR {DATA AVAILABILITY | LOAD PERFORMANCE}
