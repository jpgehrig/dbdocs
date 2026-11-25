# Description of the illustration windowing_clause.eps

    { ROWS | RANGE }
    { BETWEEN
      { UNBOUNDED PRECEDING
      | CURRENT ROW
      | value_expr { PRECEDING | FOLLOWING }
      }
      AND
      { UNBOUNDED FOLLOWING
      | CURRENT ROW
      | value_expr { PRECEDING | FOLLOWING }
      }
    | { UNBOUNDED PRECEDING
      | CURRENT ROW
      | value_expr PRECEDING
      }
    }
