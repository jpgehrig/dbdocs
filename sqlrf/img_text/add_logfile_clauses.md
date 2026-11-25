# Description of the illustration add_logfile_clauses.eps

    ADD [ STANDBY ] LOGFILE
       {
         { [ INSTANCE 'instance_name' ] | [ THREAD 'integer' ] }
         [ GROUP integer ] redo_log_file_spec
           [, [ GROUP integer ] redo_log_file_spec ]...
       | MEMBER 'filename' [ REUSE ] [, 'filename' [ REUSE ] ]...
            TO logfile_descriptor [, logfile_descriptor ]...
       }
