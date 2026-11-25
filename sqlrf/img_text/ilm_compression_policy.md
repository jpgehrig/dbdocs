# Description of the illustration ilm_compression_policy.eps

    { table_compression { SEGMENT | GROUP }
      { { AFTER ilm_time_period OF { { NO ACCESS } | { NO MODIFICATION } | CREATION } }
      | { ON function_name } }
    }
    |
    { { ROW STORE COMPRESS ADVANCED
      | COLUMN STORE COMPRESS FOR QUERY  }
      ROW AFTER ilm_time_period OF NO MODIFICATION
    }
