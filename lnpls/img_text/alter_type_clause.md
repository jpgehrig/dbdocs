# Description of the illustration alter_type_clause.eps

    { type_compile_clause
    | type_replace_clause
    | RESET
    | [ NOT ] { INSTANTIABLE | FINAL }
    | { alter_method_spec
      | alter_attribute_definition
      | alter_collection_clauses
      } [ dependent_handling_clause ]
    } ;
