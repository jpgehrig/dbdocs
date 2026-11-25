#

    dgen_fld ::=

      { RECNUM
      | SYSDATE
      | CONSTANT val
      | SEQUENCE [( { COUNT | MAX | integer } [, incr] )]
      | { REF_spec init_spec | SID_spec init_spec | BFILE_spec init_spec }
      | EXPRESSION "sql_string" }
