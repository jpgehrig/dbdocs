## 3  SQL Expressions

This chapter presents the syntax for combining values, operators, and functions into expressions.

This chapter includes the following section:

- Syntax for SQL Expression Types

### Syntax for SQL Expression Types

An expression is a combination of one or more values, operators, and SQL functions that evaluate to a value. An expression generally assumes the data type of its components.

Expressions have several forms. The sections that follow show the syntax for each form of expression. Refer to [Subclauses](Subclauses.md) for the syntax of the subclauses.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/Expressions.md) for detailed information about SQL expressions

#### [Calculated Measure Expressions](../sqlrf/index.md)

    {    av_meas_expression
       | av_simple_expression
       | single_row_function_expression
       | case_expression
       | compound_expression
       | datetime_expression
       | interval_expression
    }

#### [CASE expressions](../sqlrf/CASE-Expressions.md)

    CASE { simple_case_expression
         | searched_case_expression
         }
         [ else_clause ]
         END

#### [Column expressions](../sqlrf/Column-Expressions.md)

A column expression can be a simple expression, compound expression, function expression, or expression list, containing only columns of the subject table, constants, and deterministic functions.

#### [Compound expressions](../sqlrf/Compound-Expressions.md)

    { (expr)
    | { + | - | PRIOR } expr
    | expr { * | / | + | - | || } expr
    | expr COLLATE collation_name
    }

    Note: The double vertical bars are part of the syntax
          (indicating concatenation) rather than BNF notation.

#### [CURSOR expressions](../sqlrf/CURSOR-Expressions.md)

    CURSOR (subquery)

#### [Datetime expressions](../sqlrf/Datetime-Expressions.md)

    expr AT
       { LOCAL
       | TIME ZONE { ' [ + | - ] hh:mi'
                   | DBTIMEZONE
                   | 'time_zone_name'
                   | expr
                   }
       }

#### [Function expressions](../sqlrf/Function-Expressions.md)

You can use any built-in SQL function or user-defined function as an expression.

#### [Interval expressions](../sqlrf/Interval-Expressions.md)

    ( expr1 - expr2 )
       { DAY [ (leading_field_precision) ] TO
         SECOND [ (fractional_second_precision) ]
       | YEAR [ (leading_field_precision) ] TO
         MONTH
       }

#### [JSON object access expressions](../sqlrf/JSON-Object-Access-Expressions.md)

    table_alias.JSON_column [.JSON_object_key [ array_step ]... ]...

#### [Model expressions](../sqlrf/Model-Expressions.md)

    { measure_column [ { condition | expr } [, { condition | expr } ]... ]
    | aggregate_function
         { [ { condition | expr } [, { condition | expr } ]... ]
         | [ single_column_for_loop [, single_column_for_loop ]... ]
         | [ multi_column_for_loop ]
         }
    | analytic_function
    }

    Note: The outside square brackets shown in boldface type are part of
          the syntax. In this case, they do not represent optionality.

#### [Object access expressions](../sqlrf/Object-Access-Expressions.md)

    { table_alias.column.
    | object_table_alias.
    | (expr).
    }
    { attribute [.attribute ]...
      [.method ([ argument [, argument ]... ]) ]
    | method ([ argument [, argument ]... ])
    }

#### [Placeholder expressions](../sqlrf/Placeholder-Expressions.md)

    :host_variable
       [ [ INDICATOR ]
         :indicator_variable
       ]

#### [Scalar subquery expressions](../sqlrf/Scalar-Subquery-Expressions.md)

A scalar subquery expression is a subquery that returns exactly one column value from one row.

#### [Simple expressions](../sqlrf/Simple-Expressions.md)

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

#### [Type constructor expressions](../sqlrf/Type-Constructor-Expressions.md)

    [ NEW ] [ schema. ]type_name
       ([ expr [, expr ]... ])
