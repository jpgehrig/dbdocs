# Description of the illustration modify_to_partitioned.eps

    MODIFY [ table_partitioning_clauses | NONPARTITIONED ]
      [ filter_condition ]
      [ ONLINE ]
      [ UPDATE INDEXES [ ( index { local_partitioned_index | global_partitioned_index | GLOBAL }
                         [, index { local_partitioned_index | global_partitioned_index | GLOBAL } ]... )
                       ]
      ]
