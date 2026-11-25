# Description of the illustration archive_log_clause.eps

    ARCHIVE LOG
       [  INSTANCE 'instance_name' ]
       { { SEQUENCE integer
         | CHANGE integer
         | CURRENT [ NOSWITCH ]
         | GROUP integer
         | LOGFILE 'filename'
              [ USING BACKUP CONTROLFILE ]
         | NEXT
         | ALL
         }
         [ TO 'location' ]
       }
