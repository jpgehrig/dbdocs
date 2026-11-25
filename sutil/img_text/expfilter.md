#

    expfilter ::=

    [
    | EXCLUDE = object_type[:name_clause] [,...]
    | INCLUDE = object_type[:name_clause] [,...]
    | QUERY = [[schema_name.]table_name:] query_clause [,...]
    | SAMPLE = [[schema_name.]table_name:] sample_percent [,...]
    ]
