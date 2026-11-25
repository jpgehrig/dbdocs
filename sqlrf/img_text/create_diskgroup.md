# Description of the illustration create_diskgroup

    CREATE DISKGROUP diskgroup_name
      [ { HIGH | NORMAL | FLEX | EXTENDED [ SITE site_name ] | EXTERNAL } REDUNDANCY ]
      { [ QUORUM | REGULAR ] [ FAILGROUP failgroup_name ]
        DISK qualified_disk_clause [, qualified_disk_clause]...
      }...
      [ ATTRIBUTE { 'attribute_name' = 'attribute_value' }
                  [, 'attribute_name' = 'attribute_value' ]... ]
    ;
