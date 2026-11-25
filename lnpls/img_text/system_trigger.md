# Description of the illustration system_trigger

    { BEFORE | AFTER | INSTEAD OF }
    { ddl_event [OR ddl_event]... | database_event [OR database_event ]... }
    ON { [schema.] SCHEMA | [ PLUGGABLE ] DATABASE }
    [ trigger_ordering_clause ] [ ENABLE | DISABLE ] trigger_body
