# Description of the illustration parallel_enable_clause.eps

    PARALLEL_ENABLE
    [ (PARTITION argument BY
        { ANY
        | { HASH | RANGE } (column [, column ]...) [ streaming_clause ]
        | VALUE (column)
        }
      )
