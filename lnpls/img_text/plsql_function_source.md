# Description of the illustration plsql_function_source

    [ schema. ] function_name
      [ ( parameter_declaration [, parameter_declaration]... ) ] RETURN datatype
    [ sharing_clause ]
      [ { invoker_rights_clause
        | accessible_by_clause
        | default_collation_clause
        | deterministic_clause
        | parallel_enable_clause
        | result_cache_clause
        | aggregate_clause
        | pipelined_clause
        | sql_macro_clause
           }...
      ]
    { IS | AS } { [ declare_section ] body
                  | call_spec
                }
      ;
