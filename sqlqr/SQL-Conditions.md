## 4  SQL Conditions

This chapter presents the syntax for combining one or more expressions and logical (Boolean) operators to specify a condition.

This chapter includes the following section:

- Syntax for SQL Condition Types

### Syntax for SQL Condition Types

A condition specifies a combination of one or more expressions and logical (Boolean) operators and returns a value of `TRUE`, `FALSE`, or unknown.

Conditions have several forms. The sections that follow show the syntax for each form of condition. Refer to [Subclauses](Subclauses.md) for the syntax of the subclauses.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/Conditions.md) for detailed information about SQL conditions

#### [BETWEEN condition](../sqlrf/BETWEEN-Condition.md)

    expr1 [ NOT ] BETWEEN expr2 AND expr3

#### [Compound conditions](../sqlrf/Compound-Conditions.md)

    { (condition)
    | NOT condition
    | condition { AND | OR } condition
    }

#### [EQUALS_PATH condition](../sqlrf/XML-Conditions.md)

    EQUALS_PATH
        (column, path_string [, correlation_integer ])

#### [EXISTS condition](../sqlrf/EXISTS-Condition.md)

    EXISTS (subquery)

#### [Floating-point conditions](../sqlrf/Floating-Point-Conditions.md)

    expr IS [ NOT ] { NAN | INFINITE }

#### [Group comparison conditions](../sqlrf/Comparison-Conditions.md)

    { expr
         { = | != | ^= | <> | > | < | >= | <= }
         { ANY | SOME | ALL }
         ({ expression_list | subquery })
    | ( expr [, expr ]... )
      { = | != | ^= | <> }
      { ANY | SOME | ALL }
      ({ expression_list
         [, expression_list ]...
       | subquery
       }
      )
    }

where `!=`, ` ^=`, and `<>` test for inequality

#### [IN condition](../sqlrf/IN-Condition.md)

    { expr [ NOT ] IN ({ expression_list | subquery })
    | ( expr [, expr ]... )
        [ NOT ] IN ({ expression_list [, expression_list ]...
                    | subquery
                    }
                   )
    }

#### [IS A SET condition](../sqlrf/Multiset-Conditions.md)

    nested_table IS [ NOT ] A SET

#### [IS ANY condition](../sqlrf/Model-Conditions.md)

    [ dimension_column IS ] ANY

#### [IS EMPTY condition](../sqlrf/Multiset-Conditions.md)

    nested_table IS [ NOT ] EMPTY

#### [IS JSON condition](../sqlrf/SQL-JSON-Conditions.md)

    expr IS [ NOT ] JSON [ FORMAT JSON ] [ STRICT | LAX ]
    [ { WITH | WITHOUT } UNIQUE KEYS ]

#### [IS OF type condition](../sqlrf/IS-OF-type-Condition.md)

    expr IS [ NOT ] OF [ TYPE ]
       ([ ONLY ] [ schema. ] type
          [, [ ONLY ] [ schema. ] type ]...
       )

#### [IS PRESENT condition](../sqlrf/Model-Conditions.md)

    cell_reference IS PRESENT

#### [JSON_EQUAL condition](../sqlrf/index.md)

    JSON_EQUAL ( (expr), (expr) )

#### [JSON_EXISTS condition](../sqlrf/SQL-JSON-Conditions.md)

    JSON_EXISTS( expr [ FORMAT JSON ], JSON_basic_path_expression
      [ JSON_passing_clause ] [ JSON_exists_on_error_clause ] [ JSON_exists_on_empty_clause ] )

#### [JSON_TEXTCONTAINS condition](../sqlrf/SQL-JSON-Conditions.md)

    JSON_TEXTCONTAINS( column, JSON_basic_path_expression, string )

#### [LIKE condition](../sqlrf/Pattern-matching-Conditions.md)

    char1 [ NOT ] { LIKE | LIKEC | LIKE2 | LIKE4 }
      char2 [ ESCAPE esc_char ]

#### [Logical conditions](../sqlrf/Logical-Conditions.md)

    { NOT | AND | OR }

#### [MEMBER condition](../sqlrf/Multiset-Conditions.md)

    expr [ NOT ] MEMBER [ OF ] nested_table

#### [Null conditions](../sqlrf/Null-Conditions.md)

    expr IS [ NOT ] NULL

#### [REGEXP_LIKE condition](../sqlrf/Pattern-matching-Conditions.md)

    REGEXP_LIKE(source_char, pattern
                [, match_param ]
               )

#### [Simple comparison conditions](../sqlrf/Comparison-Conditions.md)

    { expr
      { = | != | ^= | <> | > | < | >= | <= }
      expr
    | (expr [, expr ]...)
      { = | != | ^= | <> }
      ( expression_list | subquery )
    }

where `!=`, ` ^=`, and `<>` test for inequality

#### [SUBMULTISET condition](../sqlrf/Multiset-Conditions.md)

    nested_table1
    [ NOT ] SUBMULTISET [ OF ]
    nested_table2

#### [UNDER_PATH condition](../sqlrf/XML-Conditions.md)

    UNDER_PATH (column [, levels ], path_string
                 [, correlation_integer ]
               )
