# Description of the illustration add_list_partition_clause.eps

    list_values_clause
    [ table_partition_description ]
    [ external_part_subpart_data_props ]
    [ ( { range_subpartition_desc [, range_subpartition_desc] ...
        | list_subpartition_desc [, list_subpartition_desc] ...
        | individual_hash_subparts [, individual_hash_subparts] ...
        }
      ) | hash_subparts_by_quantity ]
    [ update_index_clauses ]
