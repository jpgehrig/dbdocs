#

    HIERARCHY hierarchy_ref
      ORDER BY calc_meas_order_by_clause [ , calc_meas_order_by_clause ]…
      [ WITHIN { LEVEL | PARENT | ANCESTOR AT LEVEL level_ref } ]
      [ {INCLUDE | SKIP} WHEN NULL
