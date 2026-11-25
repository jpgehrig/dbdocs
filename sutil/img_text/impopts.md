# Description of the illustration impopts.eps

    impopts ::=

    [
    | ImpContent
    | DATA_OPTIONS = {DISABLE_APPEND_HINT | SKIP_CONSTRAINT_ERRORS | REJECT_ROWS_WITH_REPL_CHAR |
    | TRUST_EXISTING_TABLE_PARTITIONS | VALIDATE_TABLE_DATA | ENABLE_NETWORK_COMPRESSION |
    | CONTINUE_LOAD_ON_FORMAT_ERROR}
    | ImpEncrypt
    | ImpFilter
    | JOB_NAME = jobname_string
    | LOGTIME = {NONE | STATUS | LOGFILE | ALL}
    | PARALLEL = integer
    | ImpPartitioning
    | ImpRacOpt
    | ImpRemap
    | REUSE_DATAFILES  = {YES | NO}
    ]
