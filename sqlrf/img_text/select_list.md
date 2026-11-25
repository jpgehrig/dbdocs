# Description of the illustration select_list.eps

    { *
    | { query_name.*
      | [ schema. ] { table | view | materialized view } .*
      | t_alias.*
      | expr [ [ AS ] c_alias ]
      }
        [, { query_name.*
           | [ schema. ] { table | view | materialized view } .*
           | t_alias.*
           | expr [ [ AS ] c_alias ]
           }
        ]...
    }
