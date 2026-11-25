# Description of the illustration list_partitionset_clause.eps

    PARTITIONSET BY LIST (column)
      PARTITION BY CONSISTENT HASH (column [, column]...)
      [ SUBPARTITION BY { { RANGE | HASH } (column [, column]...)
                        | LIST (column)
                        }
      [ subpartition_template ]
      ]
      PARTITIONS AUTO ( list_partitionset_desc [, list_partitionset_desc]... )
