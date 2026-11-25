# Description of the illustration datafile_tempfile_clauses.eps

    { ADD { DATAFILE | TEMPFILE }
       [ file_specification [, file_specification ]... ]
    | DROP {DATAFILE | TEMPFILE } { 'filename' | file_number }
    | SHRINK TEMPFILE { 'filename' | file_number } [KEEP size_clause]
    | RENAME DATAFILE 'filename' [, 'filename' ]...
        TO 'filename' [, 'filename' ]...
    | { DATAFILE | TEMPFILE } { ONLINE | OFFLINE }
    }
