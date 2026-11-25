# Description of the illustration create_pdb_clone.eps

    { { FROM { src_pdb_name [ @ dblink ] } | { NON$CDB @ dblink } }
    |
      { AS PROXY FROM src_pdb_name @ dblink }
    }
      [ using_snapshot_clause ]
      [ parallel_pdb_creation_clause ]
      [ default_tablespaces ]
      [ pdb_storage_clause ]
      [ file_name_convert ]
      [ service_name_convert ]
      [ path_prefix_clause ]
      [ tempfile_reuse_clause ]
      [ SNAPSHOT COPY ]
      [ user_tablespaces_clause ]
      [ standbys_clause ]
      [ logging_clause ]
      [ create_file_dest_clause ]
      [ keystore_clause ]
      [ pdb_refresh_mode_clause ]
      [ RELOCATE AVAILABILITY {MAX | NORMAL} pdb_refresh_mode_clause ]
      [ NO DATA ]
      [ HOST = 'hostname' ]
      [ PORT = number ]
