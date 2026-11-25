# Description of the illustration exchange_partition_subpart.eps

    EXCHANGE { partition_extended_name
             | subpartition_extended_name
             }
       WITH TABLE [ schema. ] table
       [ { INCLUDING | EXCLUDING } INDEXES ]
       [ { WITH | WITHOUT } VALIDATION ]
       [ exceptions_clause ]
       [ update_index_clauses [ parallel_clause ] ]
       [ CASCADE ]
