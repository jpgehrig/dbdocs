#

    expopts ::=

    [
    | CONTENT = {ALL | DATA_ONLY | METADATA_ONLY}
    | ExpCompression
    | DATA_OPTIONS = GROUP_PARTITION_TABLE_DATA | VERIFY_STREAM_FORMAT
    | ESTIMATE = {BLOCKS | STATISTICS}
    | ESTIMATE_ONLY = {YES | NO}
    | ExpEncrypt
    | ExpFilter
    | FLASHBACK_SCN = scn_value
    | FLASHBACK_TIME = timestamp
    | JOB_NAME = jobname_string
