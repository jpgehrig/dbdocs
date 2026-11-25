# Description of the illustration resource_parameters.eps

    { { SESSIONS_PER_USER
      | CPU_PER_SESSION
      | CPU_PER_CALL
      | CONNECT_TIME
      | IDLE_TIME
      | LOGICAL_READS_PER_SESSION
      | LOGICAL_READS_PER_CALL
      | COMPOSITE_LIMIT
      }
      { integer | UNLIMITED | DEFAULT }
    | PRIVATE_SGA
      { size_clause | UNLIMITED | DEFAULT }
    }
