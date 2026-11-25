# Description of the illustration alter_cluster.eps

    ALTER CLUSTER [ IF EXISTS ] [ schema. ] cluster
      { physical_attributes_clause
      | SIZE size_clause
      | [ MODIFY PARTITION partition ] allocate_extent_clause
      | deallocate_unused_clause
      | { CACHE | NOCACHE }
      } ...
      [ parallel_clause ] ;
