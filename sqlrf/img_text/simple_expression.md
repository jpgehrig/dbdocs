# Description of the illustration simple_expression.eps

    { [ query_name.
      | [schema.] { table. | view. | materialized view. }
      | t_alias.
      ] { column | ROWID }
    | ROWNUM
    | string
    | number
    | sequence. { CURRVAL | NEXTVAL }
    | NULL
    }
