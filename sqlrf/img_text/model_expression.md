# Description of the illustration model_expression.eps

    { measure_column [ { condition | expr } [, { condition | expr } ]... ]
    | aggregate_function
            { [ { condition | expr } [, { condition | expr } ]... ]
            | [ single_column_for_loop [, single_column_for_loop ]... ]
            | [ multi_column_for_loop ]
            }
    | analytic_function
    }

    Note: The outside square brackets shown in boldface type are part of the syntax.
          In this case, they do not represent optionality.
