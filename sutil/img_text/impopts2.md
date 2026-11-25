# Description of the illustration impopts2.eps

    impopts2 ::=

    [
    | SKIP_UNUSABLE_INDEXES  = {YES | NO}
    | STATUS = [integer]
    | STREAMS_CONFIGURATION  = {YES | NO}
    | TABLE_EXISTS_ACTION = {SKIP | APPEND | TRUNCATE | REPLACE}
    | TARGET_EDITION = target_edition_name
    | ImpTransforms
    | ImpVersion
    | VIEWS_AS_TABLES = {[schema_object.]view_name[:table_name] [,...] | [schema_object.]view_name [,...]}
    | ImpDiagnostics
    ]
