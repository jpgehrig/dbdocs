# Description of the illustration impnetopts.eps

    impnetopts ::=

    [ ESTIMATE = {BLOCKS | STATISTICS}
    | { FLASHBACK_SCN = scn_number | FLASHBACK_TIME = timestamp }
    | { TRANSPORTABLE = {ALWAYS | NEVER} | TRANSPORT_TABLESPACES = tablespace_name [,...] }
       TRANSPORT_DATAFILES=datafile_name
    | [TRANSPORT_FULL_CHECK = {YES | NO}]
    ]
