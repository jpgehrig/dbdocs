# Description of the illustration range_partitionset_clause.eps

    PARTITIONSET BY RANGE (column [, column]...)
      PARTITION BY CONSISTENT HASH (column [, column]...)
      [ SUBPARTITION BY { { RANGE | HASH } (column [, column]...)
                        | LIST (column)
                        }
      [ subpartition_template ]
      ]
      PARTITIONS AUTO ( range_partitionset_desc [, range_partitionset_desc]... )
