# Description of create_table

    CREATE [ { GLOBAL | PRIVATE } TEMPORARY | SHARDED | DUPLICATED | [ IMMUTABLE ] BLOCKCHAIN
      | IMMUTABLE  ]
       TABLE [ IF NOT EXISTS ]
      [ schema. ] table
      [ SHARING = { METADATA | DATA | EXTENDED DATA | NONE } ]
      { relational_table | object_table | XMLType_table }
      [ MEMOPTIMIZE FOR READ ]
      [ MEMOPTIMIZE FOR WRITE ]
      [ PARENT [ schema. ] table ] ;
