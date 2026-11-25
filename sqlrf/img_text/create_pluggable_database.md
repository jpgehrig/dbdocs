# Description of create_pluggable_database

    CREATE PLUGGABLE DATABASE
      { { pdb_name [ AS APPLICATION CONTAINER ] | using_snapshot_clause} | { AS SEED } }
      { create_pdb_from_seed | create_pdb_clone | create_pdb_from_xml | create_pdb_from_mirror_copy
        | container_map_clause } pdb_snapshot_clause ;
