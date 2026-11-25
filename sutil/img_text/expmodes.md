#

    expmodes ::=

    [ FULL = {YES | NO}
    | SCHEMAS = schema_name [, schema_name] ...
    | TABLES = [schema_name.] table_name [:partition_name] [, ...]
    | TABLESPACES = tablespace_name [, tablespace_name] ...
    | TRANSPORT_TABLESPACES = tablespace_name [, tablespace_name] ...
      [TRANSPORT_FULL_CHECK = {YES| NO}]
    ]
