# Description of the illustration boolean_expression.eps

    [ NOT ] { boolean_constant
            | boolean_function_call
            | boolean_literal
            | boolean_variable
            | conditional_predicate
            | other_boolean_form
            }
            [ { AND | OR } [ NOT ] { boolean_constant
                                   | boolean_function_call
                                   | boolean_literal
                                   | boolean_variable
                                   | conditional_predicate
                                   | other_boolean_form
                                   }
            ]...
