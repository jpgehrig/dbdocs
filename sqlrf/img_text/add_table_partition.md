# Description of the illustration add_table_partition.eps

    ADD {
    PARTITION [ partition ] add_range_partition_clause
      [, PARTITION [ partition ] add_range_partition_clause ]...
    | PARTITION [ partition ] add_list_partition_clause
      [, PARTITION [ partition ] add_list_partition_clause ]...
    | PARTITION [ partition ] add_system_partition_clause
      [, PARTITION [ partition ] add_system_partition_clause ]...
      [ BEFORE { partition_name | partition_number } ]
    | PARTITION [ partition ] add_hash_partition_clause
    } [ dependent_tables_clause ]
