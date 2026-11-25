# Description of the illustration impremap.eps

    impremap ::=

    [
    REMAP_DATA = [[schema.]table.column : [schema.]pkg.function] [,...]
    | REMAP_DATAFILE = source_datafile:target_datafile [,...]
    | REMAP_DIRECTORY = source_directory_string:target_directory_string [,...]|
    | REMAP_SCHEMA = source_schema:target_schema [,...]
    | REMAP_TABLE = [schema_name.]old_table_name[:partition]:new_table_name [,...]
    | REMAP_TABLESPACE = source_tablespace:target_tablespace [,...]
    ]
