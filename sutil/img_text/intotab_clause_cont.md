#

    intotab_clause ::=

    [REENABLE] [DISABLED_CONSTRAINTS] ]
    [EXCEPTIONS table]
     [WHEN field_condition]
    [ OID_spec| SID_spec  | XMLTYPE_spec]
    [FIELDS [CSV [WITH EMBEDDED | WITHOUT EMBEDDED]][delim_spec]] [TRAILING [NULCOLS]]
    [[DATE | TIMESTAMP] FORMAT "mask"]
    [NULLIF {= | != } {"char_string" | x'hex_string' | BLANKS} ]
    [TREAT AS typename]
    [SKIP n] field_list
