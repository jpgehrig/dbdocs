# Description of the illustration ilm_tiering_policy.eps

    { TIER TO tablespace [ SEGMENT | GROUP ] [ ON function_name ] }
    |
    { TIER TO tablespace READ ONLY [ SEGMENT | GROUP ]
      { { AFTER ilm_time_period OF { { NO ACCESS } | { NO MODIFICATION } | CREATION } }
      | { ON function_name } } }
