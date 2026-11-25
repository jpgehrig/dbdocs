# Description of the illustration interval_day_to_second.eps

    INTERVAL '{ integer | integer time_expr | time_expr }'
    { { DAY | HOUR | MINUTE } [ (leading_precision) ]
    | SECOND [ (leading_precision [, fractional_seconds_precision ]) ]
    }
    [ TO { DAY | HOUR | MINUTE | SECOND [ (fractional_seconds_precision) ] } ]
