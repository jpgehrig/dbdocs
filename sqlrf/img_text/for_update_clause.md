# Description of the illustration for_update_clause.eps

    FOR UPDATE
      [ OF [ [ schema. ] { table | view } . ] column
             [, [ [ schema. ] { table | view } . ] column
             ]...
      ]
      [ { NOWAIT | WAIT integer
        |  SKIP LOCKED
        }
      ]
