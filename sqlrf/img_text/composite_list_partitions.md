# Description of the illustration composite_list_partitions.eps

    PARTITION BY LIST ( column [, column]... )
    [ AUTOMATIC [ STORE IN ( tablespace [, tablespace ]... ) ] ]
      { subpartition_by_range
      | subpartition_by_list
      | subpartition_by_hash
      }
    ( list_partition_desc [, list_partition_desc]... )
