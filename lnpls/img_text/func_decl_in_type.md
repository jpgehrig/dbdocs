# Description of the illustration func_decl_in_type

    FUNCTION name [ ( parameter_declaration [, parameter_declaration ]... ) ]
       RETURN datatype
      [ { invoker_rights_clause
        | accessible_by_clause
        | DETERMINISTIC
        | parallel_enable_clause
        | result_cache_clause
        }... [ PIPELINED ]
       { IS | AS } { [ declare_section ] body | call_spec }
