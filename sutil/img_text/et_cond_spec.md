#

    et_cond_spec ::=

    {
     { condition | condition_spec { AND | OR } condition_spec }
     | ( { condition | condition_spec {AND | OR } condition_spec } )
    }
