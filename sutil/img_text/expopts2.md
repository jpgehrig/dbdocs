#

    expopts2 ::=

    [
     LOGTIME = {NONE | STATUS | LOGFILE | ALL}
    | NETWORK_LINK = database_link
    | PARALLEL = integer
    | ExpRacOpt
    | ExpRemap
    | SOURCE_EDITION = source_edition_name
    | STATUS = integer
    | TRANSPORTABLE = {ALWAYS | NEVER}
    | ExpVersion
    | VIEWS_AS_TABLES = [schema_object.]view_name[:table_name] [,...]
    | ExpDiagnostics
