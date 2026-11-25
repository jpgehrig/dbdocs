# Description of the illustration lock_table.eps

    LOCK TABLE [ schema. ] { table | view }
       [ partition_extension_clause
       | @ dblink
       ] [, [ schema. ] { table | view }
          [ partition_extension_clause
          | @ dblink
          ]
         ]...
       IN lockmode MODE
       [ NOWAIT
       | WAIT integer
       ] ;
