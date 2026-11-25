# Description of the illustration list_partition_desc.eps

    PARTITION [partition]
    list_values_clause
    table_partition_description
      [ ( range_subpartition_desc [, range_subpartition_desc]...
          | list_subpartition_desc, [, list_subpartition_desc]...
          | individual_hash_subparts [, individual_hash_subparts]...
        )
        | hash_subparts_by_quantity
      ]
