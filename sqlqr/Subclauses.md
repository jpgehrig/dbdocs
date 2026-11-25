## 5  Subclauses

This chapter presents the syntax for the subclauses found in the syntax for SQL statements, functions, expressions and conditions.

This chapter includes the following section:

- Syntax for Subclauses

### Syntax for Subclauses

The sections that follow show the syntax for each subclause found in:

- [SQL Statements](SQL-Statements.md)

- [SQL Functions](SQL-Functions.md)

- [SQL Expressions](SQL-Expressions.md)

- [SQL Conditions](SQL-Conditions.md)

  **See Also:**

  [Oracle Database SQL Language Reference](../sqlrf/SQL-Statements-ADMINISTER-KEY-MANAGEMENT-to-ALTER-JAVA.md) for detailed information about SQL subclauses

#### action_audit_clause

    { standard_actions | component_actions }...

#### activate_standby_db_clause

    ACTIVATE
         [ PHYSICAL | LOGICAL ]
         STANDBY DATABASE
         [ FINISH APPLY ]

#### add_binding_clause

    ADD BINDING
      (parameter_type [, parameter_type ]...)
      RETURN (return_type)
      [ implementation_clause ]
      using_function_clause

#### add_column_clause

    ADD
        { column_definition | virtual_column_definition }
         | ( { column_definition | virtual_column_definition }
             [, { column_definition | virtual_column_definition } ]...
           )
       [ column_properties ]
       [ ( out_of_line_part_storage [, out_of_line_part_storage]... ) ]

#### add_disk_clause

    ADD
      { SITE sitename [ QUORUM | REGULAR ] [ FAILGROUP failgroup_name ]
        DISK qualified_disk_clause [, qualified_disk_clause ]...
      }...

#### add_external_partition_attrs

    ADD EXTERNAL PARTITION ATTRIBUTES external_table_clause
     [ REJECT LIMIT ]

#### add_filegroup_clause

    ADD FILEGROUP filegroup_name
      { DATABASE database_name
      | CLUSTER cluster_name
      | VOLUME asm_volume
      }
    [ SET '[ file_type. ] property_name' = 'property_value' ]

#### add_hash_index_partition

    ADD PARTITION
       [ partition_name ]
       [ TABLESPACE tablespace_name ]
       [ index_compression ]
       [ parallel_clause ]

#### add_hash_partition_clause

    partitioning_storage_clause
    [ update_index_clauses ]
    [ parallel_clause ]
    [ read_only_clause ]
    [ indexing_clause ]

#### add_hash_subpartition

    ADD individual_hash_subparts
       [ dependent_tables_clause ]
       [ update_index_clauses ]
       [ parallel_clause ]

#### add_list_partition_clause

    list_values_clause
    [ table_partition_description ]
    [ external_part_subpart_data_props ]
    [ ( { range_subpartition_desc [, range_subpartition_desc] ...
        | list_subpartition_desc [, list_subpartition_desc] ...
        | individual_hash_subparts [, individual_hash_subparts] ...
        }
      ) | hash_subparts_by_quantity ]
    [ update_index_clauses ]

#### add_list_subpartition

    ADD list_subpartition_desc [, list_subpartition_desc ]...
    [ dependent_tables_clause ] [ update_index_clauses ]

#### add_logfile_clauses

    ADD [ STANDBY ] LOGFILE
       {
         { [ INSTANCE 'instance_name' ] | [ THREAD 'integer' ] }
         [ GROUP integer ] redo_log_file_spec
           [, [ GROUP integer ] redo_log_file_spec ]...
       | MEMBER 'filename' [ REUSE ] [, 'filename' [ REUSE ] ]...
            TO logfile_descriptor [, logfile_descriptor ]...
       }

#### add_mv_log_column_clause

    ADD (column)

#### add_overflow_clause

    ADD OVERFLOW [ segment_attributes_clause ]
      [ ( PARTITION [ segment_attributes_clause ]
        [, PARTITION [ segment_attributes_clause ] ]...
        )
      ]

#### add_period_clause

    ADD ( period_definition )

#### add_range_partition_clause

    range_values_clause
    [ table_partition_description ]
    [ external_part_subpart_data_props ]
    [ ( { range_subpartition_desc [, range_subpartition_desc] ...
        | list_subpartition_desc [, list_subpartition_desc] ...
        | individual_hash_subparts [, individual_hash_subparts] ...
        }
      ) | hash_subparts_by_quantity ]
    [ update_index_clauses ]

#### add_range_subpartition

    ADD range_subpartition_desc [, range_subpartition_desc ]...
    [ dependent_tables_clause ] [ update_index_clauses ]

#### add_system_partition_clause

    [table_partition_description]
    [update_index_clauses]

#### add_table_partition

    ADD {
    PARTITION [ partition ] add_range_partition_clause
      [, PARTITION [ partition ] add_range_partition_clause ]...
    | PARTITION [ partition ] add_list_partition_clause
      [, PARTITION [ partition ] add_list_partition_clause ]...
    | PARTITION [ partition ] add_system_partition_clause
      [, PARTITION [ partition ] add_system_partition_clause ]...
      [ BEFORE { partition_name | partition_number } ]
    | PARTITION [ partition ] add_hash_partition_clause
    } [ dependent_tables_clause ]

#### add_update_secret

    { ADD | UPDATE } SECRET 'secret' FOR CLIENT 'client_identifier'
      [ USING TAG 'tag' ]
      [ FORCE KEYSTORE ]
      IDENTIFIED BY { EXTERNAL STORE | keystore_password }
       WITH BACKUP [ USING 'backup_identifier' ]

#### add_update_secret_seps

    { ADD | UPDATE } SECRET 'secret' FOR CLIENT 'client_identifier'
      [ USING TAG 'tag' ]
       TO [ LOCAL ] AUTO_LOGIN KEYSTORE directory

#### add_volume_clause

    ADD VOLUME asm_volume SIZE size_clause [redundancy_clause]
      [ STRIPE_WIDTH integer {K | M} ]
      [ STRIPE_COLUMNS integer ]
      [ ATTRIBUTE (disk_region_clause) ]

#### advanced_index_compression

    { COMPRESS ADVANCED [ LOW | HIGH ] } | NOCOMPRESS

#### affinity_clauses

    { ENABLE AFFINITY [ schema.]table [SERVICE service_name ]
    |
    DISABLE AFFINITY [ schema.]table
    }

#### alias_file_name

    +diskgroup_name [ (template_name) ] /alias_name

#### all_clause

    ALL  MEMBER { NAME expression [ MEMBER CAPTION expression ]
                | CAPTION expression [ MEMBER DESCRIPTION expression ]
                | DESCRIPTION expression
                }

#### allocate_extent_clause

    ALLOCATE EXTENT
      [ ( { SIZE size_clause
          | DATAFILE 'filename'
          | INSTANCE integer
          } ...
        )
      ]

#### allow_disallow_clustering

    { ALLOW | DISALLOW } CLUSTERING

#### alter_automatic_partitioning

    { SET PARTITIONING { AUTOMATIC | MANUAL }
    | SET STORE IN ( tablespace [, tablespace ]... )
    }

#### alter_datafile_clause

    DATAFILE
       { 'filename' | filenumber }
         [, 'filename' | filenumber ]...
       }
       { ONLINE
       | OFFLINE [ FOR DROP ]
       | RESIZE size_clause
       | autoextend_clause
       | END BACKUP
       | ENCRYPT
       | DECRYPT
       }

#### alter_external_table

    { add_column_clause
    | modify_column_clauses
    | drop_column_clause
    | parallel_clause
    | external_table_data_props
    | REJECT LIMIT { integer | UNLIMITED }
    | PROJECT COLUMN { ALL | REFERENCED }
    }
      [ add_column_clause
      | modify_column_clauses
      | drop_column_clause
      | parallel_clause
      | external_table_data_props
      | REJECT LIMIT { integer | UNLIMITED }
      | PROJECT COLUMN { ALL | REFERENCED }
      ]...

#### alter_index_partitioning

    { modify_index_default_attrs
    | add_hash_index_partition
    | modify_index_partition
    | rename_index_partition
    | drop_index_partition
    | split_index_partition
    | coalesce_index_partition
    | modify_index_subpartition
    }

#### alter_interval_partitioning

    { SET INTERVAL ( [ expr ] )
    | SET STORE IN ( tablespace [, tablespace]... )
    }

#### alter_iot_clauses

    { index_org_table_clause
    | alter_overflow_clause
    | alter_mapping_table_clauses
    | COALESCE
    }

#### alter_keystore_password

    ALTER KEYSTORE PASSWORD
      [ FORCE KEYSTORE ]
      IDENTIFIED BY old_keystore_password
      SET new_keystore_password
      WITH BACKUP [ USING 'backup_identifier' ]

#### alter_mapping_table_clauses

    MAPPING TABLE
      { allocate_extent_clause
      | deallocate_unused_clause
      }

#### alter_mv_refresh

    REFRESH
       { { FAST | COMPLETE | FORCE }
       | ON { DEMAND | COMMIT }
       | { START WITH | NEXT } date
       | WITH PRIMARY KEY
       | USING
            { DEFAULT MASTER ROLLBACK SEGMENT
            | MASTER ROLLBACK SEGMENT rollback_segment
            }
       | USING { ENFORCED | TRUSTED } CONSTRAINTS
       }

#### alter_overflow_clause

    { add_overflow_clause
    | OVERFLOW
         { segment_attributes_clause
         | allocate_extent_clause
         | shrink_clause
         | deallocate_unused_clause
         }...
    }

#### alter_query_rewrite_clause

    [ ENABLE | DISABLE ] QUERY REWRITE [ unusable_editions_clause ]

#### alter_session_set_clause

    SET { { parameter_name = parameter_value }...
        | EDITION = edition_name
        | CONTAINER = container_name [ SERVICE = service_name ]
        | ROW ARCHIVAL VISIBILITY = { ACTIVE | ALL }
        | DEFAULT_COLLATION = { collation_name | NONE }
        }

#### alter_system_reset_clause

    parameter_name
       [ { SCOPE = { MEMORY | SPFILE | BOTH }
         | SID = { 'sid' | '*' }
         }...
       ]

#### alter_system_set_clause

    { set_parameter_clause
    | USE_STORED_OUTLINES = (TRUE | FALSE | category_name)
    | GLOBAL_TOPIC_ENABLED = (TRUE | FALSE)
    }

#### alter_table_partitioning

    { modify_table_default_attrs
    | alter_automatic_partitioning
    | alter_interval_partitioning
    | set_subpartition_template
    | modify_table_partition
    | modify_table_subpartition
    | move_table_partition
    | move_table_subpartition
    | add_external_partition_attrs
    | add_table_partition
    | coalesce_table_partition
    | drop_external_partition_attrs
    | drop_table_partition
    | drop_table_subpartition
    | rename_partition_subpart
    | truncate_partition_subpart
    | split_table_partition
    | split_table_subpartition
    | merge_table_partitions
    | merge_table_subpartitions
    | exchange_partition_subpart
    }

#### alter_table_properties

    { { { physical_attributes_clause
        | logging_clause
        | table_compression
        | inmemory_table_clause
        | ilm_clause
        | supplemental_table_logging
        | allocate_extent_clause
        | deallocate_unused_clause
        | { CACHE | NOCACHE }
        | RESULT_CACHE ( MODE {DEFAULT | FORCE} )
        | upgrade_table_clause
        | records_per_block_clause
        | parallel_clause
        | row_movement_clause
        | flashback_archive_clause
        }...
      | RENAME TO new_table_name
      } [ alter_iot_clauses ] [ alter_XMLSchema_clause ]
    | { shrink_clause
      | READ ONLY
      | READ WRITE
      | REKEY encryption_spec
      | DEFAULT COLLATION collation_name
      | [NO] ROW ARCHIVAL
      | ADD attribute_clustering_clause
      | MODIFY CLUSTERING [ clustering_when ] [ zonemap_clause ]
      | DROP CLUSTERING
      | annotations_clause
      }
    }

#### alter_tablespace_attrs

    { default_tablespace_params
    | MINIMUM EXTENT size_clause
    | RESIZE size_clause
    | COALESCE
    | SHRINK SPACE [ KEEP size_clause ]
    | RENAME TO new_tablespace_name
    | { BEGIN | END } BACKUP
    | datafile_tempfile_clauses
    | tablespace_logging_clauses
    | tablespace_group_clause
    | tablespace_state_clauses
    | autoextend_clause
    | flashback_mode_clause
    | tablespace_retention_clause
    | alter_tablespace_encryption
    }

#### alter_tablespace_encryption

    ENCRYPTION
      { { OFFLINE [ tablespace_encryption_spec ] { ENCRYPT | DECRYPT } }
      | { ONLINE { { [ tablespace_encryption_spec ] { ENCRYPT | REKEY } }
                   | DECRYPT }
                 [ ts_file_name_convert ] }
      | { FINISH { ENCRYPT | REKEY | DECRYPT } [ ts_file_name_convert ] }
      }

#### alter_tempfile_clause

    TEMPFILE
       { 'filename' [, 'filename' ]...
       | filenumber [, filenumber ]...
       }
       { RESIZE size_clause
       | autoextend_clause
       | DROP [ INCLUDING DATAFILES ]
       | ONLINE
       | OFFLINE
       }

#### alter_varray_col_properties

    MODIFY VARRAY varray_item
       ( modify_LOB_parameters )

#### alter_XMLSchema_clause

    { ALLOW ANYSCHEMA
    | ALLOW NONSCHEMA
    | DISALLOW NONSCHEMA
    }

#### alter_zonemap_attributes

    { PCTFREE integer
    | PCTUSED integer
    | { CACHE | NOCACHE }
    }...

#### alternate_key_clause

    ALTERNATE KEY { [ ( ] attribute [ ) ]
                    |
                    ( attribute [, attribute ]... )
                  }

#### analytic_clause

    [ query_partition_clause ] [ order_by_clause [ windowing_clause ] ]

#### application_clauses

    APPLICATION
    { { app_name
        { BEGIN INSTALL 'app_version' [ COMMENT 'comment' ]
        | END INSTALL [ 'app_version' ]
        | BEGIN PATCH number [ MINIMUM VERSION 'app_version' ] [ COMMENT 'comment' ]
        | END PATCH [ number ]
        | BEGIN UPGRADE [ 'start_app_version' ] TO 'end_app_version' [ COMMENT 'comment' ]
        | END UPGRADE [ TO 'end_app_version' ]
        | BEGIN UNINSTALL
        | END UNINSTALL
        | SET PATCH number
        | SET VERSION 'app_version'
        | SET COMPATIBILITY VERSION { 'app_version' | CURRENT }
        | SYNC TO { 'app_version' | PATCH 'patch_number' }
        | SYNC
        }
      }
      |
      { ALL SYNC }
    }

#### archive_log_clause

    ARCHIVE LOG
       [  INSTANCE 'instance_name' ]
       { { SEQUENCE integer
         | CHANGE integer
         | CURRENT [ NOSWITCH ]
         | GROUP integer
         | LOGFILE 'filename'
              [ USING BACKUP CONTROLFILE ]
         | NEXT
         | ALL
         }
         [ TO 'location' ]
       }

#### array_DML_clause

    [ WITH | WITHOUT ]
    ARRAY DML
    [ ([ schema. ]type
       [, [ schema. ]varray_type ])
        [, ([ schema. ]type
            [, [ schema. ]varray_type ])...
    ]

#### array_step

    [ { integer | integer TO integer [, integer | integer TO integer ]... } | * ]

    Note: The outside square brackets shown in boldface type are part of
          the syntax. In this case, they do not represent optionality.

#### ASM_filename

    { fully_qualified_file_name
    | numeric_file_name
    | incomplete_file_name
    | alias_file_name
    }

#### attr_dim_attributes_clause

    [ alias. ] column [ [ AS ] attribute_name ] [ classification_clause ]...

#### attr_dim_level_clause

    LEVEL level [ { NOT NULL  |  SKIP WHEN NULL } ]
      [ classification_clause [ classification_clause ]...
      [ LEVEL TYPE
          {   STANDARD
            | YEARS
            | HALF_YEARS
            | QUARTERS
            | MONTHS
            | WEEKS
            | DAYS
            | HOURS
            | MINUTES
            | SECONDS
          }
      ]
      key_clause [ alternate_key_clause ]
      [ MEMBER NAME expression ]
      [ MEMBER CAPTION expression ]
      [ MEMBER DESCRIPTION expression ]
      [ ORDER BY  [ MIN | MAX ] dim_order_clause
                        [, [ MIN | MAX ] dim_order_clause ]... ]
      ]
      [ DETERMINES ( attribute [, attribute]... ) ]

#### attr_dim_using_clause

    USING [ schema. ] dim_source [ [ AS ] alias]

#### attribute_clause

    ATTRIBUTE level DETERMINES
       { dependent_column
       | ( dependent_column
           [, dependent_column ]... )
       }

#### attribute_clustering_clause

    CLUSTERING [ clustering_join ] cluster_clause
               [ clustering_when ] [ zonemap_clause ]

#### attributes_clause

    ATTRIBUTES ( attr_dim_attribute_clause [, attr_dim_attribute_clause ]... )

#### audit_operation_clause

    { { sql_statement_shortcut
      | ALL
      | ALL STATEMENTS
      } [, { sql_statement_shortcut
           | ALL
           }
        ]
    | { system_privilege
      | ALL PRIVILEGES
      } [, { system_privilege
           | ALL PRIVILEGES
           }
        ]
    }

#### audit_schema_object_clause

    { sql_operation [, sql_operation ]
    | ALL
    } auditing_on_clause

#### auditing_by_clause

    BY user [, user ]...

#### auditing_on_clause

    ON { [ schema. ] object
       | DIRECTORY directory_name
       | MINING MODEL [ schema. ] model
       | SQL TRANSLATION PROFILE [ schema. ] profile
       | DEFAULT
       }

#### autoextend_clause

    AUTOEXTEND
       { OFF
       | ON [ NEXT size_clause ]
            [ maxsize_clause ]
       }

#### av_meas_expression

    {  lead_lag_expression
     | window_expression
     | share_of_expression
     | qdr_expression
    }

#### av_measure

    meas_name  [{ base_measure_clause | calc_measure_clause }]
      [ classification_clause ]...

#### av_simple_expression

    { string | number | NULL | measure_ref }

#### backup_keystore

    BACKUP KEYSTORE [ USING 'backup_identifier' ]
      [ FORCE KEYSTORE ]
      IDENTIFIED BY { EXTERNAL STORE | keystore_password }
      [ TO 'keystore_location' ]

#### base_measure_clause

    [ FACT [alias.] ] column [ meas_aggregate_clause ]

#### binding_clause

    BINDING
       (parameter_type [, parameter_type ]...)
       RETURN return_type
       [ implementation_clause ]
       using_function_clause
        [, (parameter_type [, parameter_type ]...)
           RETURN return_type
           [ implementation_clause ]
           using_function_clause
        ]...

#### bitmap_join_index_clause

    [ schema.]table
       ( [ [ schema. ]table. | t_alias. ]column
         [ ASC | DESC  ]
           [, [ [ schema. ]table. | t_alias. ]column
              [ ASC | DESC ]
           ]...
       )
       FROM [ schema. ]table [ t_alias ]
              [, [ schema. ]table [ t_alias ]
            ]...
       WHERE condition
          [ local_partitioned_index ] index_attributes

#### blockchain_drop_table_clause

    NO DROP [ UNTIL integer DAYS IDLE ]

#### blockchain_hash_and_data_format_clause

    HASHING USING sha2_512 VERSION v1

#### blockchain_row_retention_clause

    NO DELETE ( ([ LOCKED ]) | (UNTIL integer DAYS AFTER INSERT [ LOCKED ]) )

#### blockchain_table_clauses

    blockchain_drop_table_clause
                blockchain_row_retention_clause
             blockchain_hash_and_data_format_clause

#### build_clause

    BUILD { IMMEDIATE | DEFERRED }

#### by_users_with_roles

    BY USERS WITH GRANTED ROLES role [, role]...

#### cache_clause

    CACHE cache_specification [, cache_specification]...

#### cache_specification

    MEASURE GROUP
     {    ALL
       | ( measure_name [, measure_name ]... ) [ levels_clause  MATERIALIZED ]...
     }

#### calc_meas_order_by_clause

    calc_meas_expression [ { ASC | DESC } ]  [ NULLS { FIRST | LAST } ]

#### calc_measure_clause

    AS ( calc_meas_expression )

#### cancel_sql_clause

    CANCEL SQL ' session_id , serial_number [ , @ instance_id ] [ , sql_id ] '

#### cell_assignment

    measure_column [ { { condition
                       | expr
                       | single_column_for_loop
                       }
                         [, { condition
                            | expr
                            | single_column_for_loop
                            }
                         ]...
                     | multi_column_for_loop
                     }
                   ]

    Note: The outer square brackets are part of the syntax.
          In this case, they do not indicate optionality.

#### cell_reference_options

    [ { IGNORE | KEEP } NAV ]
    [ UNIQUE { DIMENSION | SINGLE REFERENCE } ]

#### character_set_clause

    CHARACTER SET character_set

#### check_datafiles_clause

    CHECK DATAFILES [ GLOBAL | LOCAL ]

#### check_diskgroup_clause

    CHECK [ REPAIR | NOREPAIR ]

#### checkpoint_clause

    CHECKPOINT [ GLOBAL | LOCAL ]

#### classification_clause

    [ CAPTION caption ]
    [ DESCRIPTION description ]
    [ CLASSIFICATION classification_name
      [ VALUE classification_value ]
      [ LANGUAGE language ]
    ]...

#### clause_options

    OPTION
    { { = ( 'clause_option' | 'clause_option_pattern'
            [, 'clause_option' | 'clause_option_pattern' ]... ) }
    | { = ( 'clause_option' ) option_values }
    | { ALL [ EXCEPT = ( 'clause_option' | 'clause_option_pattern'
                         [, 'clause_option' | 'clause_option_pattern' ]... ) ] }
    }

#### clear_free_space_clause

    CLEAR FREE SPACE

#### close_keystore

    SET KEYSTORE CLOSE
      [ IDENTIFIED BY { EXTERNAL STORE | keystore_password } ]
      [ CONTAINER = { ALL | CURRENT } ]

#### cluster_clause

    BY [ LINEAR | INTERLEAVED ] ORDER clustering_columns

#### cluster_index_clause

    CLUSTER [ schema. ] cluster index_attributes

#### cluster_range_partitions

    PARTITION BY RANGE (column[, column ]...)
    ( PARTITION [ partition ]
        range_values_clause table_partition_description
          [, PARTITION [ partition ]
            range_values_clause table_partition_description
          ]...
    )

#### clustering_column_group

    ( column [, column ]... )

#### clustering_columns

    clustering_column_group
    | ( clustering_column_group [, clustering_column_group ]... )

#### clustering_join

    [ schema. ] table JOIN [ schema. ] table ON ( equijoin_condition )
                        [, JOIN [ schema. ] table ON ( equijoin_condition ) ]...

#### clustering_when

    [ { YES | NO } ON LOAD ] [ { YES | NO } ON DATA MOVEMENT ]

#### coalesce_index_partition

    COALESCE PARTITION [ parallel_clause ]

#### coalesce_table_partition

    COALESCE PARTITION
      [ update_index_clauses ]
      [ parallel_clause ]
      [ allow_disallow_clustering ]

#### coalesce_table_subpartition

    COALESCE SUBPARTITION subpartition
      [update_index_clauses]
      [parallel_clause]
      [allow_disallow_clustering]

#### column_association

    COLUMNS [ schema. ]table.column
              [, [ schema. ]table.column ]...
       using_statistics_type

#### column_clauses

    { { add_column_clause
      | modify_column_clauses
      | drop_column_clause
      | add_period_clause
      | drop_period_clause
      }...
    | rename_column_clause
    | { modify_collection_retrieval }...
    | { modify_LOB_storage_clause }...
    | { alter_varray_col_properties }...
    }

#### column_definition

    column [ datatype [ COLLATE column_collation_name ] ]
      [ SORT ] [ VISIBLE | INVISIBLE ]
      [ DEFAULT [ ON NULL ] expr | identity_clause ]
      [ ENCRYPT encryption_spec ]
      [ { inline_constraint }...
      | inline_ref_constraint
      | annotations_clause
      ]

#### column_properties

    { object_type_col_properties
    | nested_table_col_properties
    | { varray_col_properties | LOB_storage_clause }
        [ (LOB_partition_storage [, LOB_partition_storage ]...) ]
    | XMLType_column_properties
    }...

#### commit_switchover_clause

    { PREPARE | COMMIT } TO SWITCHOVER
    [ TO { { [ PHYSICAL | LOGICAL ] PRIMARY
         | [ PHYSICAL ] STANDBY
         } [ { WITH | WITHOUT } SESSION SHUTDOWN
             { WAIT | NOWAIT }
           ]
         | LOGICAL STANDBY
         }
    | CANCEL
    ]

#### component_actions

    ACTIONS COMPONENT =
      { DATAPUMP | DIRECT_LOAD | OLS | XS } component_action [, component_action ]...
      |
      DV component_action ON object_name [, component_action ON object_name ]...
      | PROTOCOL { FTP | HTTP | AUTHENTICATION }

#### composite_hash_partitions

    PARTITION BY HASH (column [, column ] ...)
      { subpartition_by_range
      | subpartition_by_list
      | subpartition_by_hash
      }
      { individual_hash_partitions
      | hash_partitions_by_quantity
      }

#### composite_list_partitions

    PARTITION BY LIST ( column [, column]... )
    [ AUTOMATIC [ STORE IN ( tablespace [, tablespace ]... ) ] ]
      { subpartition_by_range
      | subpartition_by_list
      | subpartition_by_hash
      }
    ( list_partition_desc [, list_partition_desc]... )

#### composite_range_partitions

    PARTITION BY RANGE ( column [, column]... )
      [ INTERVAL ( expr ) [ STORE IN ( tablespace [, tablespace]... ) ]]
      { subpartition_by_range
      | subpartition_by_list
      | subpartition_by_hash
      }
    ( range_partition_desc [, range_partition_desc]... )

#### conditional_insert_clause

    [ ALL | FIRST ]
    WHEN condition
    THEN insert_into_clause
      [ values_clause ]
      [ error_logging_clause ]
      [ insert_into_clause [ values_clause ] [ error_logging_clause ] ]...
    [ WHEN condition
      THEN insert_into_clause
        [ values_clause ]
        [ error_logging_clause ]
        [ insert_into_clause [ values_clause ] [ error_logging_clause ] ]...
    ]...
    [ ELSE insert_into_clause
      [ values_clause ]
      [ error_logging_clause ]
       [ insert_into_clause [ values_clause ] [ error_logging_clause ] ]...
    ]

#### consistent_hash_partitions

    PARTITION BY CONSISTENT HASH (column [, column ]...)
      [ PARTITIONS AUTO ] TABLESPACE SET tablespace_set

#### consistent_hash_with_subpartitions

    PARTITION BY CONSISTENT HASH (column [, column ]...)
      { subpartition_by_range
      | subpartition_by_list
      | subpartition_by_hash
      }
      [ PARTITIONS AUTO ]

#### constraint

    { inline_constraint
    | out_of_line_constraint
    | inline_ref_constraint
    | out_of_line_ref_constraint
    }

#### constraint_clauses

    { ADD { { out_of_line_constraint }...
          | out_of_line_REF_constraint
          }
    | MODIFY { CONSTRAINT constraint_name
             | PRIMARY KEY
             | UNIQUE (column [, column ]...)
             } constraint_state [ CASCADE ]
    | RENAME CONSTRAINT old_name TO new_name
    | { drop_constraint_clause }...
    }

#### constraint_state

    [ [NOT] DEFERRABLE [INITIALLY {IMMEDIATE | DEFERRED}] ]
     |  INITIALLY { IMMEDIATE | DEFERRED } [ NOT ] [ DEFERRABLE ]
    ]
    [  RELY | NORELY  ]
    [ using_index_clause ]
    [ ENABLE | DISABLE ]
    [ VALIDATE | NOVALIDATE ]
    [ exceptions_clause

#### container_data_clause

    {
    SET CONTAINER_DATA = { ALL | DEFAULT | ( container_name [, container_name ]... ) }
    |
    ADD CONTAINER_DATA = ( container_name [, container_name ]... )
    |
    REMOVE CONTAINER_DATA = ( container_name [, container_name ]... )
    }
    [ FOR [ schema. ] container_data_object ]

#### container_map_clause

    CONTAINER_MAP UPDATE { add_table_partition | split_table_partition }

#### containers_clause

    CONTAINERS( [schema.] { table | view } )

#### context_clause

    [ WITH INDEX CONTEXT,
      SCAN CONTEXT implementation_type
      [ COMPUTE ANCILLARY DATA ]
    ]
    [ WITH COLUMN CONTEXT ]

#### controlfile_clauses

    CREATE { [ LOGICAL | PHYSICAL ] STANDBY | FAR SYNC INSTANCE }
      CONTROLFILE AS
      'filename' [ REUSE ]
    | BACKUP CONTROLFILE TO
      { 'filename' [ REUSE ]
      | trace_file_clause
      }

#### convert_database_clause

    CONVERT TO ( PHYSICAL | SNAPSHOT ) STANDBY

#### convert_redundancy_clause

    CONVERT TO FLEX REDUNDANCY

#### cost_matrix_clause

    COST
      { MODEL [AUTO]
      | ( class_value [, class_value]... )
            VALUES ( ( cost_value [, cost_value]...)
                     [ , (cost_value [, cost_value]... ) ]...
                   )
      }

#### create_datafile_clause

    CREATE DATAFILE
       { 'filename' | filenumber }
         [, 'filename' | filenumber ]...
       }
       [ AS { file_specification
              [, file_specification ]...
            | NEW
            }
       ]

#### create_file_dest_clause

    CREATE_FILE_DEST = { NONE | 'directory_path_name' | diskgroup_name }

#### create_key

    CREATE [ ENCRYPTION ] KEY
      [ USING TAG 'tag' ]
      [ USING ALGORITHM 'encrypt_algorithm' ]
      [ FORCE KEYSTORE ]
      IDENTIFIED BY { EXTERNAL STORE | keystore_password }
      WITH BACKUP [ USING 'backup_identifier' ]
      [ CONTAINER = { ALL | CURRENT } ]

#### create_keystore

    CREATE
      { KEYSTORE ['keystore_location']
      | [ LOCAL ] AUTO_LOGIN KEYSTORE FROM KEYSTORE ['keystore_location']
      }
      IDENTIFIED BY keystore_password

#### create_mv_refresh

    { REFRESH
      { { FAST | COMPLETE | FORCE }
      | { ON DEMAND
        | ON COMMIT
        | ON STATEMENT
        }
      | { START WITH date |
          NEXT date
        }...
      | WITH { PRIMARY KEY | ROWID }
      | USING
         { DEFAULT [ MASTER | LOCAL ] ROLLBACK SEGMENT
         | [ MASTER | LOCAL ] ROLLBACK SEGMENT rollback_segment
         }...
      | USING
         { ENFORCED | TRUSTED } CONSTRAINTS
      }...
    | NEVER REFRESH
    }

#### create_pdb_clone

    { { FROM { src_pdb_name [ @ dblink ] } | { NON$CDB @ dblink } }
    |
      { AS PROXY FROM src_pdb_name @ dblink }
    }
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
      [ RELOCATE ]
      [ NO DATA ]
      [ HOST = 'hostname' ]
      [ PORT = number ]

#### create_pdb_from_mirror_copy

    new_pdb_name FROM base_pdb_name USING MIRROR COPY mirror_name

#### create_pdb_from_seed

    ADMIN USER admin_user_name IDENTIFIED BY password
      [ pdb_dba_roles ]
      [ parallel_pdb_creation_clause ]
      [ default_tablespace ]
      [ pdb_storage_clause ]
      [ file_name_convert ]
      [ service_name_convert ]
      [ path_prefix_clause ]
      [ tempfile_reuse_clause ]
      [ user_tablespaces_clause ]
      [ standbys_clause ]
      [ logging_clause ]
      [ create_file_dest_clause ]
      [ HOST = 'hostname' ]
      [ PORT = number ]

#### create_pdb_from_xml

    [ AS CLONE ] USING filename
      [ source_file_name_convert | source_file_directory ]
      [ { [ COPY | MOVE ] file_name_convert } | NOCOPY ]
      [ service_name_convert ]
      [ default_tablespace ]
      [ pdb_storage_clause ]
      [ path_prefix_clause ]
      [ tempfile_reuse_clause ]
      [ user_tablespaces_clause ]
      [ standbys_clause ]
      [ logging_clause ]
      [ create_file_dest_clause ]
      [ HOST = 'hostname' ]
      [ PORT = number ]

#### create_zonemap_as_subquery

    CREATE MATERIALIZED ZONEMAP
      [ schema. ] zonemap_name
      [ zonemap_attributes ]
      [ zonemap_refresh_clause ]
      [ { ENABLE | DISABLE } PRUNING ]
      AS query_block

#### create_zonemap_on_table

    CREATE MATERIALIZED ZONEMAP
      [ schema. ] zonemap_name
      [ zonemap_attributes ]
      [ zonemap_refresh_clause ]
      [ { ENABLE | DISABLE } PRUNING ]
      ON [ schema. ] { table | materialized_view } ( column [, column]... )

#### cross_outer_apply_clause

    { CROSS | OUTER } APPLY { table_reference | collection_expression }

#### cycle_clause

    {CYCLE c_alias [, c_alias]...
        SET cycle_mark_c_alias TO cycle_value
        DEFAULT no_cycle_value
    }

#### database_file_clauses

    { RENAME FILE  'filename' [, 'filename' ]...
       TO 'filename'
    | create_datafile_clause
    | alter_datafile_clause
    | alter_tempfile_clause
    | move_datafile_clause
    }

#### database_logging_clauses

    { LOGFILE
        [ GROUP integer ] file_specification
          [, [ GROUP integer ] file_specification ]...
    | MAXLOGFILES integer
    | MAXLOGMEMBERS integer
    | MAXLOGHISTORY integer
    | { ARCHIVELOG | NOARCHIVELOG }
    | FORCE LOGGING
    | SET STANDBY NOLOGGING FOR {DATA AVAILABILITY | LOAD PERFORMANCE}
    }

#### datafile_tempfile_clauses

    { ADD { DATAFILE | TEMPFILE }
       [ file_specification [, file_specification ]... ]
    | DROP {DATAFILE | TEMPFILE } { 'filename' | file_number }
    | SHRINK TEMPFILE { 'filename' | file_number } [KEEP size_clause]
    | RENAME DATAFILE 'filename' [, 'filename' ]...
        TO 'filename' [, 'filename' ]...
    | { DATAFILE | TEMPFILE } { ONLINE | OFFLINE }
    }

#### datafile_tempfile_spec

    [ 'filename' | 'ASM_filename' ]
    [ SIZE size_clause ]
    [ REUSE ]
    [ autoextend_clause ]

#### db_user_proxy_clauses

    [ WITH
      { ROLE { role_name [, role_name]...
             | ALL EXCEPT role_name [, role_name]...
             }
      | NO ROLES
      }
    ]
    [ AUTHENTICATION REQUIRED ]

#### dblink

    database[.domain [.domain ]... ] [ @ connection_qualifier ]

#### dblink_authentication

    { AUTHENTICATED BY user IDENTIFIED BY password
                  | WITH CREDENTIAL }

#### deallocate_unused_clause

    DEALLOCATE UNUSED [ KEEP size_clause ]

#### default_aggregate_clause

    DEFAULT AGGREGATE BY aggr_function

#### default_cost_clause

    DEFAULT COST (cpu_cost, io_cost, network_cost)

#### default_index_compression

    INDEX { COMPRESS ADVANCED { LOW | HIGH }
          | NOCOMPRESS
          }

#### default_measure_clause

    DEFAULT MEASURE measure

#### default_selectivity_clause

    DEFAULT SELECTIVITY default_selectivity

#### default_settings_clauses

    { DEFAULT EDITION = edition_name
    | SET DEFAULT { BIGFILE | SMALLFILE } TABLESPACE
    | DEFAULT TABLESPACE tablespace
    | DEFAULT [ LOCAL ] TEMPORARY TABLESPACE { tablespace | tablespace_group_name }
    | RENAME GLOBAL_NAME TO database.domain [.domain ]...
    | ENABLE BLOCK CHANGE TRACKING [ USING FILE 'filename' [ REUSE ] ]
    | DISABLE BLOCK CHANGE TRACKING
    | [NO] FORCE FULL DATABASE CACHING
    | CONTAINERS DEFAULT TARGET = { (container_name) | NONE }
    | flashback_mode_clause
    | undo_mode_clause
    | set_time_zone_clause
    }

#### default_table_compression

    TABLE { COMPRESS FOR OLTP
          | COMPRESS FOR QUERY { LOW | HIGH }
          | COMPRESS FOR ARCHIVE { LOW | HIGH }
          | NOCOMPRESS
          }

#### default_tablespace

    DEFAULT TABLESPACE tablespace
    [ DATAFILE datafile_tempfile_spec ]
    [ extent_management_clause ]

#### default_tablespace_params

    DEFAULT [ default_table_compression ] [ default_index_compression ]
            [ inmemory_clause ] [ ilm_clause ] [ storage_clause ]

#### default_temp_tablespace

    [ BIGFILE | SMALLFILE ] DEFAULT
    { { TEMPORARY TABLESPACE }
    | { LOCAL TEMPORARY TABLESPACE FOR { ALL | LEAF } }
    } tablespace
    [ TEMPFILE file_specification [, file_specification ]...]
    [ extent_management_clause ]

#### deferred_segment_creation

    SEGMENT CREATION { IMMEDIATE | DEFERRED }

#### delete_secret

    DELETE SECRET FOR CLIENT 'client_identifier'
      [ FORCE KEYSTORE ]
      IDENTIFIED BY { EXTERNAL STORE | keystore_password }
       WITH BACKUP [ USING 'backup_identifier' ]

#### delete_secret_seps

    DELETE SECRET FOR CLIENT 'client_identifier'
       FROM [LOCAL] AUTO_LOGIN KEYSTORE directory

#### dependent_tables_clause

    DEPENDENT TABLES
    ( table ( partition_spec [, partition_spec]...
              [, table ( partition_spec [, partition_spec]... ]
            )
    )

#### dim_by_clause

    DIMENSION BY ( dim_key [, dim_key ]... )

#### dim_key

    dim_ref
      [classification_clause]...
      KEY
        {[(] [alias.] fact_column  [)]
         |
         (  [alias.] fact_column [, [alias.] fact_column]... )
        }
      REFERENCES
         {[(]  attribute  [)]
          |
          ( attribute [, attribute]... )
         }
      HIERARCHIES ( hier_ref [, hier_ref]... )

#### dim_order_clause

    attribute [ ASC | DESC ] [ NULLS { FIRST | LAST } ]

#### dim_ref

    [ schema. ] attr_dim_name [ [AS] dim__alias ]

#### dimension_join_clause

    { JOIN KEY
       { child_key_column
       | (child_key_column [, child_key_column ]...)
       }
      REFERENCES parent_level
    }...

#### disk_offline_clause

    OFFLINE
      { [ QUORUM | REGULAR ] DISK disk_name [, disk_name ]...
      | DISKS IN [ QUORUM | REGULAR ] FAILGROUP failgroup_name [, failgroup_name ]...
      }... [ timeout_clause ]

#### disk_online_clause

    ONLINE
      { { [ QUORUM | REGULAR ] DISK disk_name [, disk_name ]...
        | DISKS IN [ QUORUM | REGULAR ] FAILGROUP failgroup_name [, failgroup_name ]...
        }...
      | ALL
      } [ POWER integer ] [ WAIT | NOWAIT ]

#### disk_region_clause

    [ HOT | COLD ] [ MIRRORHOT | MIRRORCOLD ]

#### diskgroup_alias_clauses

    { ADD ALIAS
        'alias_name' FOR 'filename'
        [, 'alias_name' FOR 'filename' ]...
    | DROP ALIAS 'alias_name' [, 'alias_name' ]...
    | RENAME ALIAS
        'old_alias_name' TO 'new_alias_name'
        [, 'old_alias_name' TO 'new_alias_name' ]...
    }

#### diskgroup_attributes

    SET ATTRIBUTE 'attribute_name' = 'attribute_value'

#### diskgroup_availability

    { MOUNT [ RESTRICTED | NORMAL ]
               [ FORCE | NOFORCE ]
    | DISMOUNT [ FORCE | NOFORCE ]
    }

#### diskgroup_directory_clauses

    { ADD DIRECTORY 'filename' [, 'filename' ]...
    | DROP DIRECTORY
        'filename' [ FORCE | NOFORCE ]
        [, 'filename' [ FORCE | NOFORCE ] ]...
    | RENAME DIRECTORY
        'old_dir_name' TO 'new_dir_name'
        [, 'old_dir_name' TO 'new_dir_name' ]...
    }

#### diskgroup_template_clauses

    { { ADD | MODIFY } TEMPLATE template_name qualified_template_clause
          [, template_name qualified_template_clause ]...
    | DROP TEMPLATE template_name [, template_name ]...
    }

#### diskgroup_volume_clauses

    { add_volume_clause
    | modify_volume_clause
    | RESIZE VOLUME asm_volume SIZE size_clause
    | DROP VOLUME asm_volume
    }

#### distributed_recov_clauses

    { ENABLE | DISABLE } DISTRIBUTED RECOVERY

#### dml_table_expression_clause

    { [ schema. ]
      { table
        [ partition_extension_clause
        | @ dblink
        ]
      | { view | materialized view } [ @ dblink ]
      }
    | ( subquery [ subquery_restriction_clause ] )
    | table_collection_expression
    }

#### domain_index_clause

    indextype
       [ local_domain_index_clause ]
       [ parallel_clause ]
       [ PARAMETERS ('ODCI_parameters') ]

#### drop_binding_clause

    DROP BINDING (parameter_type [, parameter_type ]...)
      [ FORCE ]

#### drop_column_clause

    { SET UNUSED { COLUMN column
                 | (column [, column ]...)
                 }
      [ { CASCADE CONSTRAINTS | INVALIDATE }... ]
      [ ONLINE ]
    | DROP { COLUMN column
           | (column [, column ]...)
           }
      [ { CASCADE CONSTRAINTS | INVALIDATE }... ]
      [ CHECKPOINT [ integer ] ]
    | DROP { UNUSED COLUMNS
           | COLUMNS CONTINUE
           }
      [ CHECKPOINT [ integer ] ]
    }

#### drop_constraint_clause

    DROP (
            ( PRIMARY KEY
             | UNIQUE "(" (column)... ")"
             | CONSTRAINT constraint_name )
             [ CASCADE ] [( KEEP | DROP ) INDEX ]
           )
           [ ONLINE ]

#### drop_disk_clause

    DROP
    { [ QUORUM | REGULAR ] DISK
        disk_name [ FORCE | NOFORCE ]
        [, disk_name [ FORCE | NOFORCE ] ]...
    | DISKS IN [ QUORUM | REGULAR ] FAILGROUP
        failgroup_name [ FORCE | NOFORCE ]
        [, failgroup_name [ FORCE | NOFORCE ] ]...
    }

#### drop_diskgroup_file_clause

    DROP FILE 'filename' [, 'filename' ]...

#### drop_external_partition_attrs

    DROP EXTERNAL PARTITION ATTRIBUTES


#### drop_filegroup_clause

    DROP FILEGROUP filegroup_name [ CASCADE ]

#### drop_index_partition

    DROP PARTITION partition_name

#### drop_logfile_clauses

    DROP [ STANDBY ] LOGFILE
       { logfile_descriptor
         [, logfile_descriptor ]...
       | MEMBER 'filename'
                [, 'filename' ]...
       }

#### drop_mirror_copy

      DROP MIRROR COPY mirror_name

#### drop_period_clause

    DROP ( PERIOD FOR valid_time_column )

#### drop_table_partition

    DROP partition_extended_names
      [ update_index_clauses [ parallel_clause ] ]

#### drop_table_subpartition

    DROP subpartition_extended_names
      [ update_index_clauses [ parallel_clause ] ]

#### ds_iso_format

    [-] P [days D]
      [T [hours H] [minutes M] [seconds [. frac_secs] S ] ]

#### dynamic_base_profile

    INCLUDING base_profile

#### else_clause

    ELSE else_expr

#### enable_disable_clause

    { ENABLE | DISABLE }
    [ VALIDATE | NOVALIDATE ]
    { UNIQUE (column [, column ]...)
    | PRIMARY KEY
    | CONSTRAINT constraint_name
    }
    [ using_index_clause ]
    [ exceptions_clause ]
    [ CASCADE ]
    [ { KEEP | DROP } INDEX ]

#### enable_disable_volume

    { ENABLE | DISABLE } VOLUME
      { asm_volume [, asm_volume]...
      | ALL
      }

#### enable_pluggable_database

    ENABLE PLUGGABLE DATABASE
      [ SEED
        [ file_name_convert ]
        [ SYSTEM tablespace_datafile_clauses ]
        [ SYSAUX tablespace_datafile_clauses ]
      ]
      [ undo_mode_clause ]

#### encryption_spec

      [ USING 'encrypt_algorithm' ]
      [ IDENTIFIED BY password ]
      [ 'integrity_algorithm' ]
      [ [ NO ] SALT ]

#### end_session_clauses

    { DISCONNECT SESSION 'session_id, serial_number'
         [ POST_TRANSACTION ]
    | KILL SESSION 'session_id, serial_number [, @ instance_id ]'
    }
    [ IMMEDIATE | NOREPLAY ]

#### entry

    ( regular_entry [ format_clause ] ) | wildcard

#### error_logging_clause

    LOG ERRORS
      [ INTO [schema.] table ]
      [ (simple_expression) ]
      [ REJECT LIMIT { integer | UNLIMITED } ]

#### evaluation_edition_clause

    EVALUATE USING { CURRENT EDITION | EDITION edition | NULL EDITION }

#### exceptions_clause

    EXCEPTIONS INTO [ schema. ] table

#### exchange_partition_subpart

    EXCHANGE { partition_extended_name
             | subpartition_extended_name
             }
       WITH TABLE [ schema. ] table
       [ { INCLUDING | EXCLUDING } INDEXES ]
       [ { WITH | WITHOUT } VALIDATION ]
       [ exceptions_clause ]
       [ update_index_clauses [ parallel_clause ] ]
       [ CASCADE ]

#### export_keys

    EXPORT [ ENCRYPTION ] KEYS WITH SECRET secret
      TO 'filename'
      [ FORCE KEYSTORE ]
      IDENTIFIED BY keystore_password
      [ WITH IDENTIFIER IN { 'key_id' [, 'key_id' ]... | ( subquery ) } ]

#### expr

    { simple_expression
    | compound_expression
    | calc_meas_expression
    | case_expression
    | cursor_expression
    | datetime_expression
    | function_expression
    | interval_expression
    | JSON_object_access_expr
    | model_expression
    | object_access_expression
    | scalar_subquery_expression
    | type_constructor_expression
    | variable_expression
    }

#### expression_list

    { expr [, expr ]...
    | ( [expr [, expr ]] ...)
    }

#### extended_attribute_clause

    ATTRIBUTE attribute
      { LEVEL level
        DETERMINES { dependent_column
                   | (dependent_column [, dependent_column ]... )
                   }
      }...

#### extent_management_clause

    EXTENT MANAGEMENT LOCAL
      [ AUTOALLOCATE
      | UNIFORM [ SIZE size_clause ]
      ]

#### external_part_subpart_data_props

    [ DEFAULT DIRECTORY directory ]
    [ LOCATION
       ([ directory: ] 'location_specifier'
          [, [ directory: ] 'location_specifier' ]...
       )
    ]

#### external_table_clause

    ([ TYPE access_driver_type ]
     [ external_table_data_props ]
    )
    [ REJECT LIMIT { integer | UNLIMITED } ]
    [ inmemory_table_clause ]

#### external_table_data_props

    [ DEFAULT DIRECTORY directory ]
    [ ACCESS PARAMETERS
      { ('opaque_format_spec')
      | ( opaque_format_spec )
      | USING CLOB subquery
      }
    ]
    [ LOCATION
       ([ directory: ] 'location_specifier'
          [, [ directory: ] 'location_specifier' ]...
       )
    ]

#### failover_clause

    FAILOVER TO target_db_name [ FORCE ]

#### file_name_convert

    FILE_NAME_CONVERT =
      { ( 'filename_pattern', 'replacement_filename_pattern'
          [, 'filename_pattern', 'replacement_filename_pattern' ]... )
        |
        NONE
      }

#### file_owner_clause

    SET OWNERSHIP { OWNER = 'user' | GROUP = 'usergroup'
                      [, OWNER = 'user' | GROUP = 'usergroup' ]...
                  } FOR FILE 'filename' [, 'filename']...

#### file_permissions_clause

    SET PERMISSION { OWNER | GROUP | OTHER }
      = { NONE | READ ONLY | READ WRITE }
      [, { OWNER | GROUP | OTHER | ALL }
        = { NONE | READ ONLY | READ WRITE } ]...
        FOR FILE 'filename' [, 'filename']...

#### file_specification

    { datafile_tempfile_spec
    | redo_log_file_spec
    }

#### filegroup_clauses

    { add_filegroup_clause
    | modify_filegroup_clause
    | move_to_filegroup_clause
    | drop_filegroup_clause
    }

#### filter_condition

    INCLUDING ROWS where_clause

#### flashback_archive_clause

    FLASHBACK ARCHIVE [flashback_archive] | NO FLASHBACK ARCHIVE

#### flashback_archive_quota

    QUOTA integer { M | G | T | P | E }

#### flashback_archive_retention

    RETENTION integer {YEAR | MONTH | DAY}

#### flashback_mode_clause

    FLASHBACK { ON | OFF }

#### flashback_query_clause

    { VERSIONS BETWEEN { SCN | TIMESTAMP }
        { expr | MINVALUE } AND { expr | MAXVALUE }
    | VERSIONS PERIOD FOR valid_time_column BETWEEN
        { expr | MINVALUE } AND { expr | MAXVALUE }
    | AS OF { SCN | TIMESTAMP } expr
    | AS OF PERIOD FOR valid_time_column expr
    }

#### following_boundary

    { CURRENT MEMBER | offset_expr FOLLOWING }
    AND
    { offset_expr FOLLOWING | UNBOUNDED FOLLOWING }

#### for_refresh_clause

    { FOR SYNCHRONOUS REFRESH USING staging_log_name
    | FOR FAST REFRESH
    }

#### for_update_clause

    FOR UPDATE
      [ OF [ [ schema. ] { table | view } . ] column
             [, [ [ schema. ] { table | view } . ] column
             ]...
      ]
      [ { NOWAIT | WAIT integer
        |  SKIP LOCKED
        }
      ]

#### format_clause

    FORMAT JSON

#### full_database_recovery

    [ STANDBY ] DATABASE
    [ { UNTIL { CANCEL
              | TIME date
              | CHANGE integer
              | CONSISTENT
              }
      | USING BACKUP CONTROLFILE
      }...
    ]

#### fully_qualified_file_name

    +diskgroup_name/db_name/file_type/
       file_type_tag.filenumber.incarnation_number

#### function_association

    { FUNCTIONS
         [ schema. ]function [, [ schema. ]function ]...
    | PACKAGES
         [ schema. ]package [, [ schema. ]package ]...
    | TYPES
         [ schema. ]type [, [ schema. ]type ]...
    | INDEXES
         [ schema. ]index [, [ schema. ]index ]...
    | INDEXTYPES
         [ schema. ]indextype [, [ schema. ]indextype ]...
    }
    { using_statistics_type
    | { default_cost_clause [, default_selectivity_clause ]
      | default_selectivity_clause [, default_cost_clause ]
      }
    }

#### general_recovery

    RECOVER
    [ AUTOMATIC ]
    [ FROM 'location' ]
    { { full_database_recovery
      | partial_database_recovery
      | LOGFILE 'filename'
      }
      [ { TEST
        | ALLOW integer CORRUPTION
        | parallel_clause
        }...
      ]
    | CONTINUE [ DEFAULT ]
    | CANCEL
    }

#### global_partitioned_index

    GLOBAL PARTITION BY
       { RANGE (column_list)
            (index_partitioning_clause)
       | HASH (column_list)
            { individual_hash_partitions
            | hash_partitions_by_quantity
            }
       }

#### grant_object_privileges

    { object_privilege | ALL [ PRIVILEGES ] }
      [ (column [, column ]...) ]
        [, { object_privilege | ALL [ PRIVILEGES ] }
           [ (column [, column ]...) ]
        ]...
    on_object_clause
    TO grantee_clause
      [ WITH HIERARCHY OPTION ]
      [ WITH GRANT OPTION ]

#### grant_roles_to_programs

    role [, role ]... TO program_unit [, program_unit ]...

#### grant_system_privileges

    { system_privilege | role | ALL PRIVILEGES }
      [, { system_privilege | role | ALL PRIVILEGES } ]...
    TO { grantee_clause | grantee_identified_by } [ WITH { ADMIN | DELEGATE } OPTION ]

#### grantee_clause

    { user | role | PUBLIC }
      [, { user | role | PUBLIC } ]...

#### grantee_identified_by

    user [, user ]... IDENTIFIED BY password [, password ]...

#### group_by_clause

    GROUP BY
       { expr
       | rollup_cube_clause
       | grouping_sets_clause
       }
         [, { expr
            | rollup_cube_clause
            | grouping_sets_clause
            }
         ]...
       [ HAVING condition ]

#### grouping_expression_list

    expression_list [, expression_list ]...

#### grouping_sets_clause

    GROUPING SETS
    ({ rollup_cube_clause | grouping_expression_list })

#### hash_partitions

    PARTITION BY HASH (column [, column ] ...)
    { individual_hash_partitions
    | hash_partitions_by_quantity
    }

#### hash_partitions_by_quantity

    PARTITIONS hash_partition_quantity
    [ STORE IN (tablespace [, tablespace ]...) ]
    [ table_compression | index_compression ]
    [ OVERFLOW STORE IN (tablespace [, tablespace ]...) ]

#### hash_subparts_by_quantity

    SUBPARTITIONS integer [STORE IN ( tablespace [, tablespace]... )]

#### heap_org_table_clause

    [ table_compression ] [ inmemory_table_clause ] [ ilm_clause ]

#### hier_ancestor_expression

    HIER_ANCESTOR ( member_expression AT
                           {   LEVEL level_ref
                             | DEPTH depth_expression
                           }
                         )

#### hier_attr_clause

    hier_attr_name [ classification_clause ]...

#### hier_attr_name

    {   MEMBER_NAME
      | MEMBER_UNIQUE_NAME
      | MEMBER_CAPTION
      | MEMBER_DESCRIPTION
      | LEVEL_NAME
      | HIER_ORDER
      | DEPTH
      | IS_LEAF
      | PARENT_LEVEL_NAME
      | PARENT_UNIQUE_NAME
    }

#### hier_attrs_clause

    HIERARCHICAL ATTRIBUTES ( hier_attr_clause [, hier_attr_clause ]... )

#### hier_lead_lag_clause

    member_expression  OFFSET offset_expr
      [ WITHIN
        {  { LEVEL | PARENT }
        | ACROSS ANCESTOR AT LEVEL level_ref [ POSITION FROM { BEGINNING | END } ]
        }
      ]

#### hier_lead_lag_expression

    { HIER_LEAD | HIER_LAG } ( hier_lead_lag_clause )

#### hier_navigation_expression

    {
        hier_ancestor_expression
      | hier_parent_expression
      | hier_lead_lag_expression
    }

#### hier_parent_expression

    HIER_PARENT ( member_expression )

#### hier_ref

    [ schema. ] hier_name [ [ AS ] hier_alias ] [ DEFAULT ]

#### hier_using_clause

    USING [ schema. ] attribute_dimension level_hier_clause

#### hierarchical_query_clause

    { CONNECT BY [ NOCYCLE ] condition [ START WITH condition ]
    | START WITH condition CONNECT BY [ NOCYCLE ] condition
    }

#### hierarchy_clause

    HIERARCHY hierarchy
    (child_level { CHILD OF parent_level }...
      [ dimension_join_clause ]
    )

#### hierarchy_ref

    [ attr_dim_alias. ] hier_alias

#### identity_clause

    GENERATED
    [ ALWAYS | BY DEFAULT [ ON NULL ] ]
    AS IDENTITY [ ( identity_options ) ]

#### identity_options

    { START WITH ( integer | LIMIT VALUE )
    | INCREMENT BY integer
    | ( MAXVALUE integer | NOMAXVALUE )
    | ( MINVALUE integer | NOMINVALUE )
    | ( CYCLE | NOCYCLE )
    | ( CACHE integer | NOCACHE )
    | ( ORDER | NOORDER ) }...

#### ilm_clause

    ILM
    { ADD POLICY ilm_policy_clause
    | { DELETE | ENABLE | DISABLE } POLICY ilm_policy_name
    | DELETE_ALL | ENABLE_ALL | DISABLE_ALL
    }

#### ilm_compression_policy

    { table_compression { SEGMENT | GROUP }
      { { AFTER ilm_time_period OF { { NO ACCESS } | { NO MODIFICATION } | CREATION } }
      | { ON function_name } }
    }
    |
    { { ROW STORE COMPRESS ADVANCED
      | COLUMN STORE COMPRESS FOR QUERY
      }
      ROW AFTER ilm_time_period OF NO MODIFICATION
    }

#### ilm_inmemory_policy

    { SET INMEMORY [ inmemory_attributes ]
    | MODIFY INMEMORY inmemory_memcompress
    | NO INMEMORY
    }
    [ SEGMENT ]
    { AFTER ilm_time_period OF { NO ACCESS | NO MODIFICATION | CREATION }
            | ON function_name
            }

#### ilm_policy_clause

    { ilm_compression_policy | ilm_tiering_policy | ilm_inmemory_policy }

#### ilm_tiering_policy

    { TIER TO tablespace [ SEGMENT | GROUP ] [ ON function_name ] }
    |
    { TIER TO tablespace READ ONLY [ SEGMENT | GROUP ]
      { { AFTER ilm_time_period OF { { NO ACCESS } | { NO MODIFICATION } | CREATION } }
      | { ON function_name } } }

#### ilm_time_period

    integer { { DAY | DAYS } | { MONTH | MONTHS } | { YEAR | YEARS } }

#### immutable_table_clauses

    immutable_table_no_drop_clause immutable_table_no_delete_clause

#### immutable_table_no_delete_clause

    NO DELETE ( [ LOCKED ] | ( UNTIL integer DAYS AFTER INSERT [LOCKED] ) )

#### immutable_table_no_drop_clause

    NO DROP [ UNTIL integer DAYS IDLE ]

#### implementation_clause

    { ANCILLARY TO primary_operator
        ( parameter_type [, parameter_type ]...)
          [, primary_operator
             ( parameter_type [, parameter_type ]...)
          ]...
    | context_clause
    }

#### import_keys

    IMPORT [ ENCRYPTION ] KEYS WITH SECRET secret
      FROM 'filename'
      [ FORCE KEYSTORE ]
      IDENTIFIED BY keystore_password
      WITH BACKUP [ USING 'backup_identifier' ]

#### incomplete_file_name

    +diskgroup_name [ (template_name) ]

#### index_attributes

    [ { physical_attributes_clause
      | logging_clause
      | ONLINE
      | TABLESPACE { tablespace | DEFAULT }
      | index_compression
      | { SORT | NOSORT }
      | REVERSE
      | VISIBLE | INVISIBLE
      | partial_index_clause
      | parallel_clause
      | annotations_clause
      }...
    ]

#### index_compression

    { prefix_compression
    | advanced_index_compression
    }

#### index_expr

    { column | column_expression }

#### index_org_overflow_clause

      [ INCLUDING column_name ]
    OVERFLOW [ segment_attributes_clause ]

#### index_org_table_clause

    [ { mapping_table_clause
      | PCTTHRESHOLD integer
      | prefix_compression
      }...
    ]
    [ index_org_overflow_clause ]

#### index_partition_description

    PARTITION
    [ partition
       [ { segment_attributes_clause
         | index_compression
         }...
       | PARAMETERS ( 'ODCI_parameters' )
       ]
       [ USABLE | UNUSABLE ]
    ]

#### index_partitioning_clause

    PARTITION [ partition ]
       VALUES LESS THAN (literal[, literal]... )
       [ segment_attributes_clause ]

#### index_properties

    [ { { global_partitioned_index
        | local_partitioned_index
        }
      | index_attributes
      }...
    | INDEXTYPE IS { domain_index_clause
                   | XMLIndex_clause
                   }
    ]

#### index_subpartition_clause

    { STORE IN (tablespace[, tablespace ]...)
    | (SUBPARTITION
          [ subpartition ][ TABLESPACE tablespace ] [ index_compression ] [ USABLE | UNUSABLE ]
       [, SUBPARTITION
             [ subpartition ][ TABLESPACE tablespace ] [ index_compression ] [ USABLE | UNUSABLE ]
       ]...
      )
    }

#### indexing_clause

    INDEXING { ON | OFF }

#### individual_hash_partitions

    ( PARTITION [partition] [read_only_clause] [indexing_clause] [partitioning_storage_clause]
      [, PARTITION [partition] [read_only_clause] [indexing_clause] [partitioning_storage_clause]]... )

#### individual_hash_subparts

    SUBPARTITION [subpartition] [read_only_clause] [indexing_clause] [partitioning_storage_clause]

#### inline_constraint

    [ CONSTRAINT constraint_name ]
    { [ NOT ] NULL
    | UNIQUE
    | PRIMARY KEY
    | references_clause
    | CHECK (condition)
    }
    [ constraint_state ]

#### inline_external_table

     EXTERNAL '(' '(' column_definition ',' ')' inline_external_table_properties ')'

#### inline_external_table_properties

     TYPE [ access_driver_type ] external_table_data_props
      [ REJECT LIMIT { integer | UNLIMITED }

#### inline_ref_constraint

    { SCOPE  IS [ schema. ] scope_table
    | WITH ROWID
    | [ CONSTRAINT constraint_name ]
      references_clause
      [ constraint_state ]
    }

#### inmemory_attributes

    [ inmemory_memcompress ] [ inmemory_priority ] [ inmemory_distribute ] [ inmemory_duplicate ]

#### inmemory_clause

    INMEMORY [ inmemory_attributes ]
    | NO INMEMORY

#### inmemory_column_clause

    { INMEMORY [ inmemory_memcompress ] | NO INMEMORY } ( column [, column ]... )
     [ { INMEMORY [ inmemory_memcompress ] | NO INMEMORY } ( column [, column ]... ) ]...

#### inmemory_distribute

    DISTRIBUTE [ AUTO | BY { ROWID RANGE | PARTITION | SUBPARTITION } ]
               [ FOR SERVICE { DEFAULT | ALL | service_name | NONE } ]

#### inmemory_duplicate

    DUPLICATE | DUPLICATE ALL | NO DUPLICATE

#### inmemory_memcompress

    MEMCOMPRESS FOR { DML | QUERY [ LOW | HIGH ] | CAPACITY [ LOW | HIGH ] }
    | NO MEMCOMPRESS

#### inmemory_priority

    PRIORITY { NONE | LOW | MEDIUM | HIGH | CRITICAL }

#### inmemory_table_clause

    [ { INMEMORY [ inmemory_attributes ] } | { NO INMEMORY } ]
    [ inmemory_column_clause ]

#### inner_cross_join_clause

    { [ INNER ] JOIN table_reference
        { ON condition
        | USING (column [, column ]...)
        }
    | { CROSS
      | NATURAL [ INNER ]
      }
      JOIN table_reference
    }

#### insert_into_clause

    INTO dml_table_expression_clause [ t_alias ]
    [ (column [, column ]...) ]

#### instance_clauses

    { ENABLE | DISABLE } INSTANCE 'instance_name'

#### instances_clause

    INSTANCES = { ( 'instance_name' [, 'instance_name' ]... )
                | ALL [ EXCEPT ( 'instance_name' [, 'instance_name' ]... ) ] }

#### integer

    [ + | - ] digit [ digit ]...

#### interval_day_to_second

    INTERVAL '{ integer | integer time_expr | time_expr }'
    { { DAY | HOUR | MINUTE } [ (leading_precision) ]
    | SECOND [ (leading_precision [, fractional_seconds_precision ]) ]
    }
    [ TO { DAY | HOUR | MINUTE | SECOND [ (fractional_seconds_precision) ] } ]

#### interval_year_to_month

    INTERVAL 'integer [- integer ]'
    { YEAR | MONTH } [ (precision) ] [ TO { YEAR | MONTH } ]

#### into_clause

    INTO [ schema. ] table

#### invoker_rights_clause

    AUTHID { CURRENT_USER | DEFINER }

#### isolate_keystore

    ISOLATE KEYSTORE INDENTIFIED BY isolated_keystore_password
    FROM ROOT KEYSTORE [ FORCE KEYSTORE ]
    IDENTIFIED BY { EXTERNAL STORE | united_keystore_password }
     WITH BACKUP [ USING 'backup_identifier' ]

#### join_clause

    table_reference
      { inner_cross_join_clause | outer_join_clause | cross_outer_apply_clause }...

#### JSON_agg_returning_clause

    RETURNING { VARCHAR2 [ ( size [BYTE | CHAR] ) ]
              | CLOB
              | BLOB          }

#### JSON_ARRAY_content

        ( , [ JSON_ARRAY_element ] ... )
        [ JSON_on_null_clause ] [ JSON_returning_clause ]
        [ STRICT ]



#### JSON_ARRAY_element

    expr [ format_clause ]

#### JSON_column_definition

    JSON_exists_column
    | JSON_query_column
    | JSON_value_column
    | JSON_nested_path
    | ordinality_column

#### JSON_columns_clause

    COLUMNS ( JSON_column_definition [, JSON_column_definition ]... )

#### JSON_exists_column

    column_name [ JSON_value_return_type ]
    EXISTS [ PATH ] [ JSON_path ] [ JSON_exists_on_error_clause ]
    [ JSON_exists_on_empty_clause ]

#### JSON_exists_on_empty_clause

    { ERROR | TRUE | FALSE } ON EMPTY

#### JSON_exists_on_error_clause

    { ERROR | TRUE | FALSE } ON ERROR

#### JSON_nested_path

    NESTED [ PATH ] JSON_path  JSON_columns_clause

#### JSON_object_content

    ( "*" | [ entry ] ... )
        [ JSON_on_null_clause ] [ JSON_returning_clause ]
        [ STRICT ]
        [ WITH UNIQUE KEYS ]

#### JSON_on_null_clause

    { NULL | ABSENT } ON NULL

#### JSON_on_null_clause

    { NULL | ABSENT } ON NULL

#### JSON_passing_clause

    PASSING expr AS identifier [, expr AS identifier ]...

#### JSON_path

    JSON_basic_path_expression | JSON_relative_object_access

#### JSON_query_column

    column_name JSON_query_return_type { TRUNCATE ]
      FORMAT JSON [ JSON_query_wrapper_clause ]
      PATH JSON_basic_path_expression [ JSON_query_on_error_clause ]
      [ JSON_query_on_empty_clause ]

#### JSON_query_on_empty_clause

    { ERROR
    | NULL
    | EMPTY
    | EMPTY ARRAY
    | EMPTY OBJECT
    } ON EMPTY

#### JSON_query_on_error_clause

    { ERROR
    | NULL
    | EMPTY
    | EMPTY ARRAY
    | EMPTY OBJECT
    } ON ERROR

#### JSON_query_return_type

    VARCHAR2 [ ( size [BYTE | CHAR] [ TRUNCATE ] ) ]
    | CLOB
    | BLOB

#### JSON_query_returning_clause

    [ RETURNING JSON_query_return_type ] [ PRETTY ] [ ASCII ]

#### JSON_query_wrapper_clause

    WITHOUT [ ARRAY ] WRAPPER
    | WITH [ UNCONDITIONAL | CONDITIONAL ] [ ARRAY ] WRAPPER

#### JSON_relative_object_access

    JSON_object_key [ array_step ]
     ( "." JSON_object_key [ array_step ] )...

#### JSON_returning_clause

    RETURNING VARCHAR2 [ ( size [BYTE | CHAR] ) ] | CLOB | BLOB

#### JSON_table_on_empty_clause

    { ERROR | NULL | DEFAULT literal } ON EMPTY

#### JSON_table_on_error_clause

    { ERROR | NULL | DEFAULT literal } ON ERROR

#### JSON_value_column

    column_name [ JSON_value_return_type ] [ TRUNCATE ]
      [ PATH ] [ JSON_path ] [ JSON_value_on_error_clause ]
      [ JSON_value_on_empty_clause ]

#### JSON_value_mapper_clause

    USING CASE_SENSITIVE MAPPING

#### JSON_value_on_empty_clause

    { ERROR | NULL | DEFAULT literal } ON EMPTY

#### JSON_value_on_error_clause

    { ERROR | NULL | DEFAULT literal } ON ERROR

#### JSON_value_on_mismatch_clause

    JSON_value_on_mismatch (
       ( IGNORE | ERROR | NULL )
        ON MISMATCH
       [ (  (MISSING DATA) | (EXTRA DATA) | (TYPE ERROR)  ) ]
      ) ...

#### JSON_value_return_object_instance

    object_type_name [ JSON_value_mapper_clause ]

#### JSON_value_return_type

    { VARCHAR2 [ ( size [BYTE | CHAR] ) TRUNCATE ]
    | CLOB
    | NUMBER [ ( precision [, scale] ) ]
    | DATE
    | TIMESTAMP
    | TIMESTAMP WITH TIME ZONE
    | SDO_GEOMETRY
    | JSON_value_return_object_instance
     }

#### JSON_value_returning_clause

     RETURNING JSON_value_return_type  [ ASCII ]

#### key_clause

    KEY { [(] attribute [)] | ( attribute [, attribute]... ) }

#### key_management_clauses

    { set_key
    | create_key
    | use_key
    | set_key_tag
    | export_keys
    | import_keys
    | migrate_key
    | reverse_migrate_key
    | move_keys
    }

#### keystore_clause

    KEYSTORE IDENTIFIED BY
       { EXTERNAL STORE | keystore_password }
       [ NO REKEY | REKEY USING algorithm ]

#### keystore_management_clauses

    { create_keystore
    | open_keystore
    | close_keystore
    | backup_keystore
    | alter_keystore_password
    | merge_into_new_keystore
    | merge_into_existing_keystore
    | isolate_keystore
    | unite_keystore
    }

#### lead_lag_clause

    HIERARCHY hierarchy_ref OFFSET offset_expr
      [ {
          WITHIN { LEVEL | PARENT }
        | ACROSS ANCESTOR AT LEVEL level_ref [ POSITION FROM { BEGINNING | END }
        }
      ]

#### lead_lag_expression

    lead_lag_function_name ( calc_meas_expression ) OVER ( lead_lag_clause )

#### lead_lag_function_name

    { LAG | LAG_DIFF | LAG_DIFF_PERCENT | LEAD | LEAD_DIFF | LEAD_DIFF_PERCENT }

#### level_clause

    LEVEL level IS
       { level_table.level_column
       | (level_table.level_column
          [, level_table.level_column ]...
         )
       } [ SKIP WHEN NULL ]

#### level_hier_clause

    ( level [ CHILD  OF level ]... )

#### level_member_literal

    level_ref { pos_member_keys | named_member_keys }

#### level_specification

    ( [ [ dim_name. ] hier_name. ] level_name )

#### levels_clause

    LEVELS ( level_specification [, level_specification ]... )

#### list_partition_desc

    PARTITION [partition]
    list_values_clause
    table_partition_description
      [ ( range_subpartition_desc [, range_subpartition_desc]...
          | list_subpartition_desc, [, list_subpartition_desc]...
          | individual_hash_subparts [, individual_hash_subparts]...
        )
        | hash_subparts_by_quantity
      ]

#### list_partitions

    PARTITION BY LIST ( column [, column]... )
    [ AUTOMATIC [ STORE IN ( tablespace [, tablespace ]... ) ] ]
    (PARTITION [ partition ]
        list_values_clause table_partition_description
      [, PARTITION [ partition ]
            list_values_clause table_partition_description
            [ external_part_subpart_data_props ]
      ]...
    )

#### list_partitionset_clause

    PARTITIONSET BY LIST (column)
      PARTITION BY CONSISTENT HASH (column [, column]...)
      [ SUBPARTITION BY { { RANGE | HASH } (column [, column]...)
                        | LIST (column)
                        }
      [ subpartition_template ]
      ]
      PARTITIONS AUTO ( list_partitionset_desc [, list_partitionset_desc]... )

#### list_partitionset_desc

    PARTITIONSET partition_set list_values_clause
      [ TABLESPACE SET tablespace_set ]
      [ LOB_storage_clause ]
      [ SUBPARTITIONS STORE IN ( tablespace_set )... ]

#### list_subpartition_desc

    SUBPARTITION [subpartition] list_values_clause
      [read_only_clause] [indexing_clause] [partitioning_storage_clause]
      [external_part_subpart_data_props]

#### list_values

    list_values
    { { literal | NULL } [, { literal | NULL } ]... }
    | { ( { literal | NULL } [, { literal | NULL } ]... )
            [, ( { literal | NULL } [, { literal | NULL } ]... ) ] }

#### list_values_clause

    VALUES ( list_values | DEFAULT )

#### listagg_overflow_clause

    { ON OVERFLOW ERROR }
    |
    { ON OVERFLOW TRUNCATE 'truncation-indicator' [ { WITH | WITHOUT } COUNT ] }

#### LOB_compression_clause

    { COMPRESS [HIGH | MEDIUM | LOW ]
    | NOCOMPRESS
    }

#### LOB_deduplicate_clause

    { DEDUPLICATE
    | KEEP_DUPLICATES
    }

#### LOB_parameters

    { { ENABLE | DISABLE } STORAGE IN ROW
      | CHUNK integer
      | PCTVERSION integer
      | FREEPOOLS integer
      | LOB_retention_clause
      | LOB_deduplicate_clause
      | LOB_compression_clause
      | { ENCRYPT encryption_spec | DECRYPT }
      | { CACHE | NOCACHE | CACHE READS } [ logging_clause ]
    }...

#### LOB_partition_storage

    PARTITION partition
    { LOB_storage_clause | varray_col_properties }...
      [ (SUBPARTITION subpartition
         { LOB_partitioning_storage | varray_col_properties }...
        )
    ]

#### LOB_partitioning_storage

    LOB (LOB_item) STORE AS [BASICFILE | SECUREFILE]
      [ LOB_segname [ ( TABLESPACE tablespace | TABLESPACE SET tablespace_set ) ]
      | ( TABLESPACE tablespace | TABLESPACE SET tablespace_set )
      ]

#### LOB_retention_storage

    RETENTION [ MAX | MIN integer | AUTO | NONE ]

#### LOB_storage_clause

    LOB
    { (LOB_item [, LOB_item ]...)
         STORE AS { {SECUREFILE | BASICFILE}
                  | (LOB_storage_parameters)
                  }...
    | (LOB_item)
         STORE AS { {SECUREFILE | BASICFILE}
                  | LOB_segname
                  | (LOB_storage_parameters)
                  }...
    }

#### LOB_storage_parameters

    { { { TABLESPACE tablespace | TABLESPACE SET tablespace_set }
      | LOB_parameters [storage_clause]
      }...
    | storage_clause

#### local_domain_index_clause

    LOCAL
      [ ( PARTITION partition [ PARAMETERS ( 'ODCI_parameters' ) ]
          [,  PARTITION partition [ PARAMETERS ('ODCI_parameters') ]]...
        )
      ]

#### local_partitioned_index

    LOCAL
    [ on_range_partitioned_table
    | on_list_partitioned_table
    | on_hash_partitioned_table
    | on_comp_partitioned_table
    ]

#### local_XMLIndex_clause

    LOCAL
      [ ( PARTITION partition [ XMLIndex_parameters_clause ]
          [, PARTITION partition [ XMLIndex_parameters_clause ] ]...
        )
      ]

#### lockdown_features

    { DISABLE | ENABLE } FEATURE
    { { = ( 'feature' [, 'feature' ]... ) }
    | { ALL [ EXCEPT = ( 'feature' [, 'feature' ]... ) ] }
    }

#### lockdown_options

    { DISABLE | ENABLE } OPTION
    { { = ( 'option' [, 'option' ]... ) }
    | { ALL [ EXCEPT = ( 'option' [, 'option' ]... ) ] }
    }

#### lockdown_statements

    { DISABLE | ENABLE } STATEMENT
    { { = ( 'SQL_statement' [, 'SQL_statement' ]... ) }
    | { = ( 'SQL_statement' ) statement_clauses }
    | { ALL [ EXCEPT = ( 'SQL_statement' [, 'SQL_statement' ]... ) ] }
    }

#### logfile_clause

    LOGFILE
    [ GROUP integer ] file_specification
      [, [ GROUP integer ] file_specification ]...

#### logfile_clauses

    { { ARCHIVELOG [ MANUAL ]
      | NOARCHIVELOG
      }
    | [ NO ] FORCE LOGGING
    | SET STANDBY NOLOGGING FOR {DATA AVAILABILITY | LOAD PERFORMANCE}
    | RENAME FILE 'filename' [, 'filename' ]...
        TO 'filename'
    | CLEAR [ UNARCHIVED ]
        LOGFILE logfile_descriptor [, logfile_descriptor ]...
        [ UNRECOVERABLE DATAFILE ]
    | add_logfile_clauses
    | drop_logfile_clauses
    | switch_logfile_clause
    | supplemental_db_logging
    }

#### logfile_descriptor

    { GROUP integer
    | ('filename' [, 'filename' ]...)
    | 'filename'
    }

#### logging_clause

    { LOGGING | NOLOGGING |  FILESYSTEM_LIKE_LOGGING }

#### lost_write_protection

     [  ENABLE | REMOVE | SUSPEND  ] LOST WRITE PROTECTION

#### main_model

    [ MAIN main_model_name ]
    model_column_clauses
    [ cell_reference_options ]
    model_rules_clause

#### managed_standby_recovery

    RECOVER
    { MANAGED STANDBY DATABASE
        [ { USING ARCHIVED LOGFILE
          | DISCONNECT [FROM SESSION]
          | NODELAY
          | UNTIL CHANGE integer
          | UNTIL CONSISTENT
          | USING INSTANCES { ALL | integer }
          | parallel_clause
          }...
        | FINISH
        | CANCEL
        ]
    | TO LOGICAL STANDBY { db_name | KEEP IDENTITY }
    }

#### mapping_table_clauses

    { MAPPING TABLE | NOMAPPING }

#### materialized_view_props

    [ column_properties ]
    [ table_partitioning_clauses ]
    [ CACHE | NOCACHE ]
    [ parallel_clause ]
    [ build_clause ]

#### maximize_standby_db_clause

    SET STANDBY DATABASE TO MAXIMIZE
    { PROTECTION | AVAILABILITY | PERFORMANCE }

#### maxsize_clause

    MAXSIZE { UNLIMITED | size_clause }

#### meas_aggregate_clause

    AGGREGATE BY aggr_function

#### measure_ref

    [ MEASURES. ] meas_name

#### measures_clause

    MEASURES  ( av_measure [, av_measure]... )

#### member_expression

    { level_member_literal
      | hier_navigation_expression
      | CURRENT MEMBER
      | NULL
      | ALL
    }

#### memoptimize_read_clause

    [ { (MEMOPTIMIZE FOR READ) | (NO MEMOPTIMIZE FOR READ) } ]

#### memoptimize_write_clause

    [ { (MEMOPTIMIZE FOR WRITE) | (NO MEMOPTIMIZE FOR WRITE) } ]

#### merge_insert_clause

    WHEN NOT MATCHED THEN
    INSERT [ (column [, column ]...) ]
    VALUES ({ expr | DEFAULT }
               [, { expr | DEFAULT } ]...
           )
    [ where_clause ]

#### merge_into_existing_keystore

    MERGE KEYSTORE 'keystore1_location' [ IDENTIFIED BY keystore1_password ]
      INTO EXISTING KEYSTORE 'keystore2_location' IDENTIFIED BY keystore2_password
      WITH BACKUP [ USING 'backup_identifier' ]

#### merge_into_new_keystore

    MERGE KEYSTORE 'keystore1_location' [ IDENTIFIED BY keystore1_password ]
      AND KEYSTORE 'keystore2_location' [ IDENTIFIED BY keystore2_password ]
      INTO NEW KEYSTORE 'keystore3_location' IDENTIFIED BY keystore3_password

#### merge_table_partitions

    MERGE PARTITIONS partition_or_key_value
       { , partition_or_key_value [, partition_or_key_value ]...
       | TO partition_or_key_value }
       [ INTO partition_spec ]
       [ filter_condition ]
       [ dependent_tables_clause ]
       [ update_index_clauses ]
       [ parallel_clause ]
       [ ONLINE ]
       [ allow_disallow_clustering ]

#### merge_table_subpartitions

    MERGE SUBPARTITIONS subpartition_or_key_value
       { , subpartition_or_key_value [, subpartition_or_key_value ]...
       | TO subpartition_or_key_value }
       [ INTO { range_subpartition_desc
              | list_subpartition_desc
              }
       ]
       [ filter_condition ]
       [ dependent_tables_clause ]
       [ update_index_clauses ]
       [ parallel_clause ]
       [ ONLINE ]
       [ allow_disallow_clustering ]

#### merge_update_clause

    WHEN MATCHED THEN
    UPDATE SET column = { expr | DEFAULT }
               [, column = { expr | DEFAULT } ]...
    [ where_clause ]
    [ DELETE where_clause ]

#### migrate_key

    { USE | SET } [ ENCRYPTION ] KEY [ 'key_id' ]
      IDENTIFIED BY OKV_password
      [ FORCE KEYSTORE ]
       MIGRATE USING software_keystore_password

#### mining_analytic_clause

    [ query_partition_clause ] [ order_by_clause ]

#### mining_attribute_clause

    USING
    { *
    | { [ schema . ] table . *
      | expr [ AS alias ]
      }
        [, { [ schema . ] table . *
           | expr [ AS alias ]
           }
        ]...
    }

#### model_clause

    MODEL
       [ cell_reference_options ]
       [ return_rows_clause ]
       [ reference_model ]...
    main_model

#### model_column_clauses

    [ PARTITION BY (expr [ c_alias ] [, expr [c_alias] ]...) ]
    DIMENSION BY (expr [c_alias] [, expr [c_alias] ]...)
    MEASURES (expr [c_alias] [, expr [c_alias] ]...)

#### model_iterate_clause

    ITERATE ( number ) [ UNTIL ( condition ) ]

#### model_rules_clause

    [ RULES
      [ { UPDATE | UPSERT [ ALL ] } ]
      [ { AUTOMATIC | SEQUENTIAL } ORDER ]
      [ model_iterate_clause ]
    ]
    ( [ { UPDATE | UPSERT [ ALL ] } ]
    cell_assignment [ order_by_clause ] = expr
      [,  [ { UPDATE | UPSERT [ ALL ] } ]
        cell_assignment [ order_by_clause ] = expr
      ]...
    )

#### modified_external_table

     EXTERNAL MODIFY modify_external_table_properties

#### modify_col_properties

    column [ datatype ]
           [ COLLATE column_collation_name ]
           [ DEFAULT [ ON NULL ] expr | identity_clause | DROP IDENTITY ]
           [ { ENCRYPT encryption_spec } | DECRYPT ]
           [ inline_constraint ... ]
           [ LOB_storage_clause ]
           [ alter_XMLSchema_clause ]

#### modify_col_substitutable

    COLUMN column
    [ NOT ] SUBSTITUTABLE AT ALL LEVELS
    [ FORCE ]

#### modify_col_visibility

    column { VISIBLE | INVISIBLE }

#### modify_collection_retrieval

    MODIFY NESTED TABLE collection_item
    RETURN AS { LOCATOR | VALUE }

#### modify_column_clauses

    MODIFY
    { ( modify_col_properties | modify_virtcol_properties
        [, modify_col_properties | modify_virtcol_properties ]... )
    | ( modify_col_visibility [, modify_col_visibility ]... )
    | modify_col_substitutable
    }

#### modify_diskgroup_file

    MODIFY FILE 'filename' ATTRIBUTE ( disk_region_clause )
      [, 'filename' ATTRIBUTE ( disk_region_clause ) ]...

#### modify_external_table_properties

    DEFAULT DIRECTORY directory
     [ LOCATION '(' directory ':' ''' location_specifier ''' ')' ]
     [ ACCESS PARAMETERS
       [ BADFILE filename ]
       [ LOGFILE filename ]
       [ DISCARDFILE filename ] ]
     [ REJECT LIMIT { integer | UNLIMITED ]

#### modify_filegroup_clause

    MODIFY FILEGROUP filegroup_name
      SET '[ file_type. ] property_name' = 'property_value'

#### modify_hash_partition

    MODIFY partition_extended_name
      { partition_attributes
      | coalesce_table_subpartition
      | alter_mapping_table_clause
      | [ REBUILD ] UNUSABLE LOCAL INDEXES
      | read_only_clause
      | indexing_clause
      }

#### modify_index_default_attrs

    MODIFY DEFAULT ATTRIBUTES
       [ FOR PARTITION partition ]
       { physical_attributes_clause
       | TABLESPACE { tablespace | DEFAULT }
       | logging_clause
       }...

#### modify_index_partition

    MODIFY PARTITION partition
    { { deallocate_unused_clause
      | allocate_extent_clause
      | physical_attributes_clause
      | logging_clause
      | index_compression
      }...
    | PARAMETERS ('ODCI_parameters')
    | COALESCE [ CLEANUP ] [ parallel_clause ]
    | UPDATE BLOCK REFERENCES
    | UNUSABLE
    }

#### modify_index_subpartition

    MODIFY SUBPARTITION subpartition
    { UNUSABLE
    | allocate_extent_clause
    | deallocate_unused_clause
    }

#### modify_list_partition

    MODIFY partition_extended_name
      { partition_attributes
      | { ADD | DROP } VALUES ( list_values )
      | { add_range_subpartition
        | add_list_subpartition
        | add_hash_subpartition
        }
      | coalesce_table_subpartition
      | [ REBUILD ] UNUSABLE LOCAL INDEXES
      | read_only_clause
      | indexing_clause
      }

#### modify_LOB_parameters

    { storage_clause
    | PCTVERSION integer
    | FREEPOOLS integer
    | REBUILD FREEPOOLS
    | LOB_retention_clause
    | LOB_deduplicate_clause
    | LOB_compression_clause
    | { ENCRYPT encryption_spec | DECRYPT }
    | { CACHE
      | { NOCACHE | CACHE READS } [ logging_clause ]
      }
    | allocate_extent_clause
    | shrink_clause
    | deallocate_unused_clause
    } ...

#### modify_LOB_storage_clause

    MODIFY LOB (LOB_item)
       (modify_LOB_parameters)

#### modify_mv_column_clause

    MODIFY ( column [ ENCRYPT encryption_spec
           | DECRYPT ]
           )

#### modify_opaque_type

    MODIFY OPAQUE TYPE anydata_column
    STORE ( type_name [, type_name ]... ) UNPACKED

#### modify_range_partition

    MODIFY partition_extended_name
       { partition_attributes
       | { add_range_subpartition
         | add_hash_subpartition
         | add_list_subpartition
         }
       | coalesce_table_subpartition
       | alter_mapping_table_clause
       | [ REBUILD ] UNUSABLE LOCAL INDEXES
       | read_only_clause
       | indexing_clause
       }

#### modify_table_default_attrs

    MODIFY DEFAULT ATTRIBUTES
       [ FOR partition_extended_name ]
       [ deferred_segment_creation ]
       [ read_only_clause ]
       [ indexing_clause ]
       [ segment_attributes_clause ]
       [ table_compression ]
       [ inmemory_clause ]
       [ PCTTHRESHOLD integer ]
       [ prefix_compression ]
       [ alter_overflow_clause ]
       [ { LOB (LOB_item) | VARRAY varray } (LOB_parameters) ]...

#### modify_table_partition

    { modify_range_partition
    | modify_hash_partition
    | modify_list_partition
    }

#### modify_table_subpartition

    MODIFY subpartition_extended_name
    { allocate_extent_clause
    | deallocate_unused_cluse
    | shrink_clause
    | { { LOB LOB_item | VARRAY varray } (modify_LOB_parameters) }...
    | [ REBUILD ] UNUSABLE LOCAL INDEXES
    | { ADD | DROP } VALUES ( list_values )
    | read_only_clause
    | indexing_clause
    }

#### modify_to_partitioned

    MODIFY [ table_partitioning_clauses | NONPARTITIONED ]
      [ filter_condition ]
      [ ONLINE ]
      [ UPDATE INDEXES
        [ ( index { local_partitioned_index | global_partitioned_index | GLOBAL }
            [, index { local_partitioned_index | global_partitioned_index | GLOBAL } ]... )
        ]
      ]

#### modify_virtcol_properties

    column [ datatype ]
    [ COLLATE column_collation_name ]
    [ GENERATED ALWAYS ] AS (column_expression) [ VIRTUAL ]
    evaluation_edition_clause [ unusable_editions_clause ]

#### modify_volume_clause

    MODIFY VOLUME asm_volume
      [ ATTRIBUTE (disk_region_clause) ]
      [ MOUNTPATH 'mountpath_name' ]
      [ USAGE 'usage_name' ]

#### modify_table_default_attrs

    MODIFY DEFAULT ATTRIBUTES
       [ FOR partition_extended_name ]
       [ DEFAULT DIRECTORY directory ]
       [ deferred_segment_creation ]
       [ read_only_clause ]
       [ indexing_clause ]
       [ segment_attributes_clause ]
       [ table_compression ]
       [ inmemory_clause ]
       [ PCTTHRESHOLD integer ]
       [ prefix_compression ]
       [ alter_overflow_clause ]
       [ { LOB (LOB_item) | VARRAY varray } (LOB_parameters) ]...

#### move_datafile_clause

    MOVE DATAFILE ( 'filename' | 'ASM_filename' | file_number )
     [ TO ( 'filename' | 'ASM_filename' ) ]
     [ REUSE ] [ KEEP ]

#### move_mv_log_clause

    MOVE segment_attributes_clause [parallel_clause]

#### move_table_clause

    MOVE
       [ filter_condition ]
       [ ONLINE ]
       [ segment_attributes_clause ]
       [ table_compression ]
       [ index_org_table_clause ]
       [ { LOB_storage_clause | varray_col_properties }... ]
       [ parallel_clause ]
       [ allow_disallow_clustering ]
       [ UPDATE INDEXES
         [ ( index { segment_attributes_clause
                   | update_index_partition }
             [, index { segment_attributes_clause
                      | update_index_partition } ]...
           )
         ]
       ]

#### move_table_partition

    MOVE partition_extended_name
       [ MAPPING TABLE ]
       [ table_partition_description ]
       [ filter_condition ]
       [ update_index_clauses ]
       [ parallel_clause ]
       [ allow_disallow_clustering ]
       [ ONLINE ]

#### move_table_subpartition

    MOVE subpartition_extended_name [ indexing_clause ]
         [ partitioning_storage_clause ]
         [ update_index_clauses ]
         [ filter_condition ]
         [ parallel_clause ]
         [ allow_disallow_clustering ]
         [ ONLINE ]

#### move_to_filegroup_clause

    MOVE FILE 'ASM_filename' TO FILEGROUP filegroup_name

#### move_keys

    MOVE [ENCRYPTION] KEYS
        TO NEW KEYSTORE keystore_location1
        IDENTIFIED BY keystore1_password
        FROM [FORCE] KEYSTORE
        IDENTIFIED BY keystore_password
        [WITH IDENTIFIER IN
          { 'key_identifier' [, 'key_identifier']... | ( subquery ) } ]
        WITH BACKUP [USING 'backup_identifier']

#### multi_column_for_loop

    FOR (dimension_column
          [, dimension_column ]...)
    IN ( { (literal [, literal ]...)
           [ (literal [, literal ]...) ]...
         | subquery
         }
       )

#### multi_table_insert

    { ALL
      { insert_into_clause [ values_clause ] [error_logging_clause] }...
    | conditional_insert_clause
    } subquery

#### multiset_except

    nested_table1
    MULTISET EXCEPT [ ALL | DISTINCT ]
    nested_table2

#### multiset_intersect

    nested_table1
    MULTISET INTERSECT [ ALL | DISTINCT ]
    nested_table2

#### multiset_union

    nested_table1
    MULTISET UNION [ ALL | DISTINCT ]
    nested_table2

#### mv_log_augmentation

    ADD { { OBJECT ID
          | PRIMARY KEY
          | ROWID
          | SEQUENCE
          } [ (column [, column ]...) ]
        | (column [, column ]... )
        } [, { { OBJECT ID
               | PRIMARY KEY
               | ROWID
               | SEQUENCE
               }
               [ (column [, column ]...) ]
             | (column [, column ]...)
             }
          ]...
        [ new_values_clause ]

#### mv_log_purge_clause

    PURGE { IMMEDIATE [ SYNCHRONOUS | ASYNCHRONOUS ]  )
          | START WITH datetime_expr
              [ NEXT datetime_expr
              | REPEAT INTERVAL interval_expr
              ]
          | [ START WITH datetime_expr ] { NEXT datetime_expr
                                         | REPEAT INTERVAL interval_expr
                                         }
          }

#### named_member_keys

    '['  attr_name = [, attr_name = member_key_expr ]... ']'

#### nested_clause

    table_reference (NESTED [PATH]) identifier
    [
    ("." [ JSON_object_key array_step ] ) |
    ("," JSON_basic_path_expression )
    ]
    [ JSON_table_on_error_clause ]
    [ JSON_table_on_empty_clause ]
     JSON_columns_clause

#### nested_table_col_properties

    NESTED TABLE
    { nested_item | COLUMN_VALUE }
    [ substitutable_column_clause ]
    [ LOCAL | GLOBAL ]
    STORE AS storage_table
    [ ( { (object_properties)
        | [ physical_properties ]
        | [ column_properties ]
        }...
      )
    ]
    [ RETURN [ AS ] { LOCATOR | VALUE } ]

#### nested_table_partition_spec

    PARTITION partition [segment_attributes_clause]

#### new_values_clause

    { INCLUDING | EXCLUDING } NEW VALUES

#### number

    [ + | - ]
    { digit [ digit ]... [ . ] [ digit [ digit ]... ]
    | . digit [ digit ]...
    }
    [ [ e | E ] [ + | - ] digit [ digit ]... ] [ f | F | d | D ]

#### numeric_file_name

    +diskgroup_name.filenumber.incarnation_number

#### object_properties

    { { column | attribute }
        [ DEFAULT expr ]
        [ { inline_constraint }...  | inline_ref_constraint ]
    | { out_of_line_constraint
      | out_of_line_ref_constraint
      | supplemental_logging_props
      }
    }

#### object_step

    .{ simple_name | "complex_name"  | * }

#### object_table

    OF
       [ schema. ] object_type
       [ object_table_substitution ]
       [ (object_properties) ]
       [ ON COMMIT { DELETE | PRESERVE } ROWS ]
       [ OID_clause ]
       [ OID_index_clause ]
       [ physical_properties ]
       [ table_properties ]

#### object_table_substitution

    [ NOT ] SUBSTITUTABLE AT ALL LEVELS

#### object_type_col_properties

    COLUMN column substitutable_column_clause

#### object_view_clause

    OF [ schema. ] type_name
    { WITH OBJECT { IDENTIFIER | ID }
      { DEFAULT | ( attribute [, attribute ]... ) }
    | UNDER [ schema. ] superview
    }
    [ ( { out_of_line_constraint
        | attribute { inline_constraint }...
        }  [, { out_of_line_constraint
              | attribute { inline_constraint }...
              }
           ]...
      )
    ]

#### OID_clause

    OBJECT IDENTIFIER IS
    { SYSTEM GENERATED | PRIMARY KEY }

#### OID_index_clause

    OIDINDEX [ index ]
    ({ physical_attributes_clause
     | TABLESPACE tablespace
     }...
    )

#### on_comp_partitioned_table

    [ STORE IN ( tablespace [, tablespace ]... ) ]
    ( PARTITION
        [ partition ]
        [ { segment_attributes_clause
          | index_compression
          }...
        ] [ USABLE | UNUSABLE ] [ index_subpartition_clause ]
          [, PARTITION
               [ partition ]
               [ { segment_attributes_clause
                 | index_compression
                 }...
               ] [ USABLE | UNUSABLE ] [ index_subpartition_clause ]
           ]...
    )

#### on_error_clause

     ( ERROR | NULL ) ON ERROR

#### on_hash_partitioned_table

    { STORE IN (tablespace[, tablespace ]...)
    | (PARTITION [ partition ] [ TABLESPACE tablespace ]
        [ index_compression ] [ USABLE | UNUSABLE ]
      [, PARTITION [ partition ] [ TABLESPACE tablespace ]
        [ index_compression ] [ USABLE | UNUSABLE ]] ...
      )
    }

#### on_list_partitioned_table

    ( PARTITION
        [ partition ]
        [ { segment_attributes_clause
          | index_compression
          }...
        ] [ USABLE | UNUSABLE ]
          [, PARTITION
               [ partition ]
               [ { segment_attributes_clause
                 | index_compression
                 }...
               ] [ USABLE | UNUSABLE ]
          ]...
    )

#### on_object_clause

    ON { [ schema. ] object
       | USER user [, user]...
       | DIRECTORY directory_name
       | EDITION edition_name
       | MINING MODEL [ schema. ] mining_model_name
       | JAVA { SOURCE | RESOURCE } [ schema. ] object
       | SQL TRANSLATION PROFILE [ schema. ] profile
       }

#### on_range_partitioned_table

    ( PARTITION
        [ partition ]
        [ { segment_attributes_clause
          | index_compression
          }...
        ] [ USABLE | UNUSABLE ]
          [, PARTITION
              [ partition ]
              [ { segment_attributes_clause
                | index_compression
                }...
              ] [ USABLE | UNUSABLE ]
         ]...
    )

#### open_keystore

    SET KEYSTORE OPEN
      [ FORCE KEYSTORE ]
      IDENTIFIED BY { EXTERNAL STORE | keystore_password }
      [ CONTAINER = { ALL | CURRENT } ]

#### option_values

    { { VALUE = ( 'option_value' [, 'option_value' ]... ) }
      |
      { MINVALUE = 'option_value' }
      |
      { MAXVALUE = 'option_value' }
    }...

#### order_by_clause

    ORDER [ SIBLINGS ] BY
    { expr | position | c_alias }
    [ ASC | DESC ]
    [ NULLS FIRST | NULLS LAST ]
      [, { expr | position | c_alias }
         [ ASC | DESC ]
         [ NULLS FIRST | NULLS LAST ]
      ]...

#### ordinality_column

    column_name FOR ORDINALITY

#### out_of_line_constraint

      [ CONSTRAINT constraint_name ]
    { UNIQUE (column [, column ]...)
    | PRIMARY KEY (column [, column ]...)
    | FOREIGN KEY (column [, column ]...) references_clause
    | CHECK (condition)
    } [ constraint_state ]

#### out_of_line_part_storage

    PARTITION partition
      { nested_table_col_properties | LOB_storage_clause | varray_col_properties }
        [ nested_table_col_properties | LOB_storage_clause | varray_col_properties ]...
    [ ( SUBPARTITION subpartition
       { nested_table_col_properties | LOB_storage_clause | varray_col_properties }
         [ nested_table_col_properties | LOB_storage_clause | varray_col_properties
         ]...
        [, SUBPARTITION subpartition
         { nested_table_col_properties | LOB_storage_clause | varray_col_properties }
           [ nested_table_col_properties | LOB_storage_clause | varray_col_properties
           ]...
        ]...
      )
    ]

#### out_of_line_ref_constraint

    { SCOPE FOR ({ ref_col | ref_attr })
        IS [ schema. ] scope_table
    | REF ({ ref_col | ref_attr }) WITH ROWID
    | [ CONSTRAINT constraint_name ] FOREIGN KEY
        ( { ref_col [, ref_col ] | ref_attr [, ref_attr ] } ) references_clause
        [ constraint_state ]
    }

#### outer_join_clause

      [ query_partition_clause ] [ NATURAL ]
    outer_join_type JOIN table_reference
      [ query_partition_clause ]
      [ ON condition
      | USING ( column [, column ]...)
      ]

#### outer_join_type

    { FULL | LEFT | RIGHT } [ OUTER ]

#### parallel_clause

    { NOPARALLEL | PARALLEL [ integer ] }

#### parallel_pdb_creation_clause

    PARALLEL [ integer ]

#### partial_database_recovery

    { TABLESPACE tablespace [, tablespace ]...
    | DATAFILE { 'filename' | filenumber }
                 [, 'filename' | filenumber ]...
    }

#### partial_index_clause

    INDEXING { PARTIAL | FULL }

#### partition_attributes

    [ { physical_attributes_clause
      | logging_clause
      | allocate_extent_clause
      | deallocate_unused_clause
      | shrink_clause
      }...
    ]
    [ OVERFLOW
      { physical_attributes_clause
      | logging_clause
      | allocate_extent_clause
      | deallocate_unused_clause
      }...
    ]
    [ table_compression ]
    [ inmemory_clause ]
    [ { { LOB LOB_item | VARRAY varray } (modify_LOB_parameters) }...]

#### partition_extended_name

    PARTITION partition
    |
    PARTITION FOR ( partition_key_value [, partition_key_value]... )

#### partition_extended_names

    { PARTITION | PARTITIONS }
    partition | { FOR ( partition_key_value [, partition_key_value ]... ) }
      [, partition | { FOR ( partition_key_value [, partition_key_value ]... ) } ]...

#### partition_extension_clause

    { PARTITION (partition)
    | PARTITION FOR (partition_key_value [, partition_key_value]...)
    | SUBPARTITION (subpartition)
    | SUBPARTITION FOR (subpartition_key_value [, subpartition_key_value]...)
    }

#### partition_or_key_value

    partition
    |
    FOR ( partition_key_value [, partition_key_value ]... )

#### partition_spec

    PARTITION [ partition ] [ table_partition_description ]

#### partitioning_storage_clause

    [ { { TABLESPACE tablespace | TABLESPACE SET tablespace_set }
      | OVERFLOW [ TABLESPACE tablespace] | TABLESPACE SET tablespace_set ]
      | table_compression
      | index_compression
      | inmemory_clause
      | ilm_clause
      | LOB_partitioning_storage
      | VARRAY varray_item STORE AS [SECUREFILE | BASICFILE] LOB LOB_segname
      }...
    ]

#### partitionset_clauses

    { range_partitionset_clause | list_partitionset_clause }

#### password_parameters

    { { FAILED_LOGIN_ATTEMPTS
      | PASSWORD_LIFE_TIME
      | PASSWORD_REUSE_TIME
      | PASSWORD_REUSE_MAX
      | PASSWORD_LOCK_TIME
      | PASSWORD_GRACE_TIME
      | INACTIVE_ACCOUNT_TIME
      }
      { expr | UNLIMITED | DEFAULT }
      | PASSWORD_VERIFY_FUNCTION
      { function | NULL | DEFAULT }
      | PASSWORD_ROLLOVER_TIME
    }

#### patch_common

    target_expr [ json_query_returning_clause ] [ pretty ]
     [ ASCII ] [ TRUNCATE ] [ json_query_on_error_clause ]

#### path_prefix_clause

    PATH_PREFIX = { 'path_name' | directory_object_name | NONE }

#### pdb_change_state

    [ pdb_name ] { pdb_open | pdb_close | pdb_save_or_discard_state }

#### pdb_change_state_from_root

    { pdb_name [, pdb_name ]... | ALL [ EXCEPT pdb_name [, pdb_name ]... ] }
    { pdb_open | pdb_close | pdb_save_or_discard_state }

#### pdb_close

    CLOSE [ IMMEDIATE ] [ instances_clause | relocate_clause ]

#### pdb_datafile_clause

    [ pdb_name ] DATAFILE
      { { { 'filename' | filenumber } [, 'filename' | filenumber ]... } | ALL }
      { ONLINE | OFFLINE }

#### pdb_dba_roles

    ROLES = ( role [, role ]... )

#### pdb_force_logging_clause

    { ENABLE | DISABLE } FORCE { LOGGING | NOLOGGING }
    | SET STANDBY NOLOGGING FOR {DATA AVAILABILITY | LOAD PERFORMANCE}

#### pdb_general_recovery

    RECOVER [ AUTOMATIC ]  [ FROM 'location' ]
      [ DATABASE
      |
      TABLESPACE tablespace [, tablespace ]...
      |
      DATAFILE { 'filename' | filenumber }
                 [, 'filename' | filenumber ]...
      |
      LOGFILE 'filename'
      |
      CONTINUE [ DEFAULT ]
      ]

#### pdb_logging_clauses

    { logging_clause
    | pdb_force_logging_clause
    }

#### pdb_open

    OPEN
      { [ READ WRITE | READ ONLY ] [ RESTRICTED ] [ FORCE ]
      | [ READ WRITE ] UPGRADE [ RESTRICTED ]
      | RESETLOGS
      }
      [ instances_clause ]
      [ services_clause ]

#### pdb_recovery_clauses

    [ pdb_name ] { pdb_general_recovery
                 | { BEGIN | END } BACKUP
                 | { ENABLE | DISABLE } RECOVERY
                 }

#### pdb_refresh_mode_clause

    REFRESH MODE { MANUAL | EVERY refresh_interval { MINUTES | HOURS} | NONE }

#### pdb_save_or_discard_state

    { SAVE | DISCARD } STATE [ instances_clause ]

#### pdb_settings_clauses

    { [ pdb_name ]
      { DEFAULT EDITION = edition_name
      | SET DEFAULT ( BIGFILE | SMALLFILE ) TABLESPACE
      | DEFAULT TABLESPACE tablespace_name
      | DEFAULT TEMPORARY TABLESPACE { tablespace | tablespace_group_name }
      | RENAME GLOBAL_NAME TO database.domain [. domain ]...
      | set_time_zone_clause
      | database_file_clauses
      | supplemental_db_logging
      | pdb_storage_clause
      | pdb_logging_clauses
      | pdb_refresh_mode_clause
      | REFRESH
      | SET CONTAINER_MAP = 'map_object'
      }
    }
    | CONTAINERS DEFAULT TARGET = { (container_name) | NONE
                 |  HOST "=" "'" hostname "'"
            |  PORT "=" number
                                  }

#### pdb_storage_clause

    STORAGE
      { ( { MAXSIZE { UNLIMITED | size_clause }
            |
            MAX_AUDIT_SIZE { UNLIMITED | size_clause }
            |
            MAX_DIAG_SIZE { UNLIMITED | size_clause }
          }...
        )
      |
      UNLIMITED
      }

#### pdb_snapshot_clause

    ENABLE SNAPSHOT { MANUAL | EVERY snapshot_interval { HOURS | MINUTES } | NONE}

#### pdb_unplug_clause

    pdb_name UNPLUG INTO 'filename'

#### period_definition

    PERIOD FOR valid_time_column [ ( start_time_column, end_time_column ) ]

#### permanent_tablespace_attrs

    { MINIMUM EXTENT size_clause
    | BLOCKSIZE integer [ K ]
    | logging_clause
    | FORCE LOGGING
    | tablespace_encryption_clause
    | default_tablespace_params
    | { ONLINE | OFFLINE }
    | extent_management_clause
    | segment_management_clause
    | flashback_mode_clause
    | lost_write_protection
    }...

#### permanent_tablespace_clause

    TABLESPACE [ IF NOT EXISTS ] tablespace
      [ DATAFILE file_specification [, file_specification ]... ]
      [ permanent_tablespace_attrs ]

#### physical_attributes_clause

    [ { PCTFREE integer
      | PCTUSED integer
      | INITRANS integer
      | storage_clause
      }...
    ]

#### physical_properties

    { [ deferred_segment_creation ] segment_attributes_clause [ table_compression ]
        [ inmemory_table_clause ] [ ilm_clause ]
    | [ deferred_segment_creation ] ORGANIZATION
      { HEAP [ segment_attributes_clause ] heap_org_table_clause
      | INDEX [ segment_attributes_clause ] index_org_table_clause
      | EXTERNAL PARTITION ATTRIBUTES external_table_clause [ REJECT LIMIT ]
      }
    | CLUSTER cluster (column [, column ]...)
    }

#### pivot_clause

    PIVOT [ XML ]
      ( aggregate_function ( expr ) [[AS] alias ]
          [, aggregate_function ( expr ) [[AS] alias ] ]...
        pivot_for_clause
        pivot_in_clause
      )

#### pivot_for_clause

    FOR { column
        | ( column [, column]... )
        }

#### pivot_in_clause

    IN ( { { { expr
             | ( expr [, expr]... )
             } [ [ AS] alias]
           }...
         | subquery
         | ANY [, ANY]...
         }
       )

#### plsql_declarations

    { function_declaration | procedure_declaration }...

#### pos_member_keys

    '['  member_key_expr [, member_key_expr]...']'

#### preceding_boundary

    { UNBOUNDED PRECEDING | offset_expr PRECEDING }
    AND
    { CURRENT MEMBER
      | offset_expr  { PRECEDING | FOLLOWING }
      | UNBOUNDED FOLLOWING
    }

#### prefix_compression

    COMPRESS [ integer ] | NOCOMPRESS

#### prepare_clause

       PREPARE MIRROR COPY copy_name
       WITH { EXTERNAL | NORMAL | HIGH } REDUNDANCY

#### privilege_audit_clause

    PRIVILEGES system_privilege [, system_privilege ]...

#### program_unit

    { FUNCTION [ schema. ] function_name
    |
    PROCEDURE [ schema. ] procedure_name
    |
    PACKAGE [ schema. ] package_name }

#### property_clause

    PROPERTY { SET | REMOVE } DEFAULT_CREDENTIAL = SYSTEM.OPCTEST

#### proxy_clause

    { GRANT CONNECT THROUGH { ENTERPRISE USERS | db_user_proxy db_user_proxy_clauses }
    | REVOKE CONNECT THROUGH { ENTERPRISE USERS | db_user_proxy }}

#### qdr_expression

    QUALIFY ( calc_meas_expression, qualifier )

#### qualified_disk_clause

    search_string
    [ NAME disk_name ]
    [ SIZE size_clause ]
    [ FORCE | NOFORCE ]

#### qualified_template_clause

    ATTRIBUTE
    ( redundancy_clause
      striping_clause
      disk_region_clause
    )

#### qualifier

    hierarchy_ref = member_expression

#### query_block

      [ with_clause ]
    SELECT [ hint ] [ { { DISTINCT | UNIQUE } | ALL } ] select_list
      FROM { table_reference | join_clause | ( join_clause ) }
             [ , { table_reference | join_clause | (join_clause) } ] ...
      [ where_clause ]
      [ hierarchical_query_clause ]
      [ group_by_clause ]
      [ model_clause ]

#### query_partition_clause

    PARTITION BY
      { expr[, expr ]...
      | ( expr[, expr ]... )
      }

#### query_rewrite_clause

    { ENABLE | DISABLE } QUERY REWRITE [ unusable_editions_clause ]

#### query_table_expression

    { query_name
    | [ schema. ]
      { table [ modified_external_table
              | partition_extension_clause
              | @ dblink
              ]
      | { view | materialized view } [ @ dblink ]
      | hierarchy
      | analytic_view [ HIERARCHIES
        ( [ [ attr_dim. ] hierarchy [, [ attr_dim. ] hierarchy ]... ] ) ]
      | inline_external_table
      } [sample_clause]
    | [ LATERAL ] (subquery [ subquery_restriction_clause ])
    | table_collection_expression
    }

#### quiesce_clauses

    QUIESCE RESTRICTED | UNQUIESCE

#### quotagroup_clauses

    { ADD QUOTAGROUP quotagroup_name [ SET property_name = property_value ]
    | MODIFY QUOTAGROUP quotagroup_name SET property_name = property_value
    | MOVE FILEGROUP filegroup_name TO quotagroup_name
    | DROP QUOTAGROUP quotagroup_name
    }

#### range_partition_desc

    PARTITION [partition]
    range_values_clause
    table_partition_description
    [ ( { range_subpartition_desc [, range_subpartition_desc] ...
        | list_subpartition_desc [, list_subpartition_desc] ...
        | individual_hash_subparts [, individual_hash_subparts] ...
        }
      ) | hash_subparts_by_quantity ]

#### range_partitions

    PARTITION BY RANGE (column[, column ]...)
      [ INTERVAL (expr) [ STORE IN ( tablespace [, tablespace]...) ]]
    ( PARTITION [ partition ]
        range_values_clause table_partition_description
          [, PARTITION [ partition ]
            range_values_clause table_partition_description
            [ external_part_subpart_data_props ]
          ]...
    )

#### range_partitionset_clause

    PARTITIONSET BY RANGE (column [, column]...)
      PARTITION BY CONSISTENT HASH (column [, column]...)
      [ SUBPARTITION BY { { RANGE | HASH } (column [, column]...)
                        | LIST (column)
                        }
      [ subpartition_template ]
      ]
      PARTITIONS AUTO ( range_partitionset_desc [, range_partitionset_desc]... )

#### range_partitionset_desc

    PARTITIONSET partition_set range_values_clause
      [ TABLESPACE SET tablespace_set ]
      [ LOB_storage_clause ]
      [ SUBPARTITIONS STORE IN ( tablespace_set )... ]

#### range_subpartition_desc

    SUBPARTITION [subpartition] range_values_clause
      [read_only_clause] [indexing_clause] [partitioning_storage_clause]
      [external_part_subpart_data_props]

#### range_values_clause

    VALUES LESS THAN
      ({ literal | MAXVALUE }
         [, { literal | MAXVALUE } ]...
      )

#### read_only_clause

    { READ ONLY } | { READ WRITE }

#### rebalance_diskgroup_clause

    REBALANCE
      [ { [ { WITH | WITHOUT } phase [, phase]... ] [ POWER integer ] [ WAIT | NOWAIT ] }
        |
        { MODIFY POWER [ integer ] }
      ]

#### rebuild_clause

    REBUILD
      [ { PARTITION partition
        | SUBPARTITION subpartition
        }
      | { REVERSE | NOREVERSE }
      ]
      [ parallel_clause
      | TABLESPACE tablespace
      | PARAMETERS ( 'ODCI_parameters' )
      | XMLIndex_parameters_clause
      | ONLINE
      | physical_attributes_clause
      | index_compression
      | logging_clause
      | partial_index_clause
      ]...

#### records_per_block_clause

    { MINIMIZE | NOMINIMIZE } RECORDS_PER_BLOCK

#### recovery_clauses

    { general_recovery
    | managed_standby_recovery
    | BEGIN BACKUP
    | END BACKUP
    }

#### redo_log_file_spec

    [ 'filename | ASM_filename'
    | ('filename | ASM_filename'
       [, 'filename | ASM_filename' ]...)
    ]
    [ SIZE size_clause ]
    [ BLOCKSIZE size_clause
    [ REUSE ]

#### redundancy_clause

    [ MIRROR | HIGH | UNPROTECTED | PARITY ]

#### reference_model

    REFERENCE reference_model_name ON (subquery)
      model_column_clauses [ cell_reference_options ]

#### reference_partition_desc

    PARTITION [partition] [table_partition_description] )

#### reference_partitioning

    PARTITION BY REFERENCE ( constraint )
      [ (reference_partition_desc...) ]

#### references_clause

    REFERENCES [ schema. ] object [ (column [, column ]...) ]
      [ON DELETE { CASCADE | SET NULL } ]

#### register_logfile_clause

    REGISTER [ OR REPLACE ]
      [ PHYSICAL | LOGICAL ]
    LOGFILE [ file_specification  [, file_specification ]...
      [ FOR logminer_session_name ]

#### regular_entry

    [ KEY ] expr VALUE expr
                           | expr [ ":" expr ]

#### relational_properties

    { column_definition
    | virtual_column_definition
    | period_definition
    | { out_of_line_constraint | out_of_line_ref_constraint }
    | supplemental_logging_props
    }
      [, { column_definition
         | virtual_column_definition
         | period_definition
         | { out_of_line_constraint | out_of_line_ref_constraint }
         | supplemental_logging_props
         }
      ]...

#### relational_table

    [ (relational_properties) ]
    [ immutable_table_clauses ]
    [ blockchain_table_clauses ]
    [ DEFAULT COLLATION collation_name ]
    [ ON COMMIT { DROP | PRESERVE } DEFINITION ]
    [ ON COMMIT { DELETE | PRESERVE } ROWS ]
    [ physical_properties ]
    [ table_properties ]

#### relocate_clause

    RELOCATE [ TO 'instance_name' ]
    | NORELOCATE

#### rename_column_clause

    RENAME COLUMN old_name TO new_name

#### rename_disk_clause

    RENAME
      { DISK old_disk_name TO new_disk_name [, old_disk_name TO new_disk_name ]...
      | DISKS ALL }

#### rename_index_partition

    RENAME
      { PARTITION partition | SUBPARTITION subpartition }
    TO new_name

#### rename_partition_subpart

    RENAME { partition_extended_name
           | subpartition_extended_name
           } TO new_name

#### replace_disk_clause

    REPLACE DISK disk_name WITH 'path_name' [ FORCE | NOFORCE ]
      [, disk_name WITH 'path_name' [ FORCE | NOFORCE ] ]...
    [ POWER integer ] [ WAIT | NOWAIT ]

#### resize_disk_clause

    RESIZE ALL [ SIZE size_clause ]

#### resource_parameters

    { { SESSIONS_PER_USER
      | CPU_PER_SESSION
      | CPU_PER_CALL
      | CONNECT_TIME
      | IDLE_TIME
      | LOGICAL_READS_PER_SESSION
      | LOGICAL_READS_PER_CALL
      | COMPOSITE_LIMIT
      }
      { integer | UNLIMITED | DEFAULT }
    | PRIVATE_SGA
      { size_clause | UNLIMITED | DEFAULT }
    }

#### return_rows_clause

    RETURN { UPDATED | ALL } ROWS

#### returning_clause

    { RETURN | RETURNING } expr [, expr ]...
    INTO data_item [, data_item ]...

#### reverse_migrate_key

    SET [ ENCRYPTION ] KEY
      IDENTIFIED BY software_keystore_password
      [ FORCE KEYSTORE ]
      REVERSE MIGRATE USING { HSM_auth_string | OKV_password }
      WITH BACKUP [ USING 'backup_identifier']

#### revoke_object_privileges

    { object_privilege | ALL [ PRIVILEGES ] }
      [, { object_privilege | ALL [ PRIVILEGES ] } ]...
    on_object_clause
    FROM revokee_clause
    [ CASCADE CONSTRAINTS | FORCE ]

#### revoke_roles_from_programs

    { role [, role ]... | ALL } FROM program_unit [, program_unit ]...

#### revoke_system_privileges

    { system_privilege | role | ALL PRIVILEGES }
      [, { system_privilege | role | ALL PRIVILEGES } ]...
    FROM revokee_clause

#### revokee_clause

    { user | role | PUBLIC }
      [, { user | role | PUBLIC } ]...

#### role_audit_clause

    ROLES role [, role ]...

#### rolling_migration_clauses

    { START ROLLING MIGRATION TO 'ASM_version'
    | STOP ROLLING MIGRATION
    }

#### rolling_patch_clauses

    { START ROLLING PATCH
    | STOP ROLLING PATCH
    }

#### rollup_cube_clause

    { ROLLUP | CUBE } (grouping_expression_list)

#### routine_clause

    [ schema. ] [ type. | package. ]
    { function | procedure | method }
    [ @dblink_name ]
    ( [ argument [, argument ]... ] )

#### row_limiting_clause

    [ OFFSET offset { ROW | ROWS } ]
    [ FETCH { FIRST | NEXT } [ { rowcount | percent PERCENT } ]
        { ROW | ROWS } { ONLY | WITH TIES } ]

#### row_movement_clause

    { ENABLE | DISABLE } ROW MOVEMENT

#### row_pattern

    [ row_pattern | ] row_pattern_term

    Note: The vertical bar is part of the syntax rather than BNF notation.

#### row_pattern_aggregate_func

    [ RUNNING | FINAL ] aggregate_function

#### row_pattern_classifier_func

    CLASSIFIER()

#### row_pattern_clause

    MATCH_RECOGNIZE (
      [ row_pattern_partition_by ]
      [ row_pattern_order_by ]
      [ row_pattern_measures ]
      [ row_pattern_rows_per_match ]
      [ row_pattern_skip_to ]
      PATTERN (row_pattern)
      [ row_pattern_subset_clause ]
      DEFINE row_pattern_definition_list
      )

#### row_pattern_definition

    variable_name AS condition

#### row_pattern_definition_list

    row_pattern_definition [, row_pattern_definition ]...

#### row_pattern_factor

    row_pattern_primary [ row_pattern_quantifier ]

#### row_pattern_match_num_func

    MATCH_NUMBER()

#### row_pattern_measure_column

    expr AS c_alias

#### row_pattern_measures

    MEASURES row_pattern_measure_column [, row_pattern_measure_column ]...

#### row_pattern_nav_compound

    { PREV | NEXT }
    ( [ RUNNING | FINAL ] { FIRST | LAST } ( expr [, offset ] ) [, offset] )

#### row_pattern_nav_logical

    [ RUNNING | FINAL ] { FIRST | LAST } ( expr [, offset ] )

#### row_pattern_nav_physical

    { PREV | NEXT } ( expr [, offset ] )

#### row_pattern_navigation_func

    row_pattern_nav_logical
    | row_pattern_nav_physical
    | row_pattern_nav_compound

#### row_pattern_order_by

    ORDER BY column [, column ]...

#### row_pattern_partition_by

    PARTITION BY column [, column ]...

#### row_pattern_permute

    PERMUTE ( row_pattern [, row_pattern ]...)

#### row_pattern_primary

    variable_name
    | $
    | ^
    | ( [ row_pattern ] )
    | {- row_pattern -}
    | row_pattern_permute

    Note: The curly brackets are part of the syntax rather than BNF notation.

#### row_pattern_quantifier

    * [ ? ]
    | + [ ? ]
    | ? [ ? ]
    | { [ unsigned_integer ] , [ unsigned_integer ] } [ ? ]
    | { unsigned_integer }

    Note: The curly brackets are part of the syntax rather than BNF notation.

#### row_pattern_rec_func

    row_pattern_classifier_func
    | row_pattern_match_num_func
    | row_pattern_navigation_func
    | row_pattern_aggregate_func

#### row_pattern_rows_per_match

    ONE ROW PER MATCH
    | ALL ROWS PER MATCH

#### row_pattern_skip_to

    AFTER MATCH {
      SKIP TO NEXT ROW
      | SKIP PAST LAST ROW
      | SKIP TO FIRST variable_name
      | SKIP TO LAST variable_name
      | SKIP TO variable_name
      }

#### row_pattern_subset_clause

    SUBSET row_pattern_subset_item [, row_pattern_subset_item ]...

#### row_pattern_subset_item

    variable_name = ( variable_name [, variable_name ] )

#### row_pattern_term

    [ row_pattern_term ] row_pattern_factor

#### sample_clause

    SAMPLE [ BLOCK ]
           (sample_percent)
           [ SEED (seed_value) ]

#### scoped_table_ref_constraint

    { SCOPE FOR ({ ref_column | ref_attribute })
      IS [ schema. ] { scope_table_name | c_alias }
    }

#### scrub_clause

    SCRUB [ FILE 'ASM_filename' | DISK disk_name ]
      [ REPAIR | NOREPAIR ]
      [ POWER { AUTO | LOW | HIGH | MAX } ]
      [ WAIT | NOWAIT ]
      [ FORCE | NOFORCE ]
      [ STOP ]

#### search_clause

    { SEARCH
            { DEPTH FIRST BY c_alias [, c_alias]...
                [ ASC | DESC ]
                [ NULLS FIRST | NULLS LAST ]
             | BREADTH FIRST BY c_alias [, c_alias]...
                [ ASC | DESC ]
                [ NULLS FIRST | NULLS LAST ]
            }
            SET ordering_column
    }

#### searched_case_expression

    { WHEN condition THEN return_expr }...

#### secret_management_clauses

    { add_update_secret
    | delete_secret
    | add_update_secret_seps
    | delete_secret_seps
    }

#### security_clause

    GUARD { ALL | STANDBY | NONE }

#### security_clauses

    { ENABLE | DISABLE } RESTRICTED SESSION

#### segment_attributes_clause

    { physical_attributes_clause
    | { TABLESPACE tablespace | TABLESPACE SET tablespace_set }
    | logging_clause
    }...

#### segment_management_clause

    SEGMENT SPACE MANAGEMENT { AUTO | MANUAL }

#### select_list

    { *
    | { query_name.*
      | [ schema. ] { table | view | materialized view } .*
      | t_alias.*
      | expr [ [ AS ] c_alias ]
      }
        [, { query_name.*
           | [ schema. ] { table | view | materialized view } .*
           | t_alias.*
           | expr [ [ AS ] c_alias ]
           }
        ]...
    }

#### service_name_convert

    SERVICE_NAME_CONVERT =
      { ( 'service_name', 'replacement_service_name'
          [, 'service_name', 'replacement_service_name' ]... )
        |
        NONE
      }

#### set_encryption_key

    { SET ENCRYPTION KEY
      {
        [ "certificate_id" ] IDENTIFIED BY "wallet_password"
        |
        IDENTIFIED BY "HSM_auth_string" [ MIGRATE USING "wallet_password" ]
      }
    }

#### set_key

    SET [ ENCRYPTION ] KEY { mkid:mk | mk }
      [ USING TAG 'tag' ]
      [ USING ALGORITHM 'encrypt_algorithm' ]
      [ FORCE KEYSTORE ]
      IDENTIFIED BY { EXTERNAL STORE | keystore_password }
      WITH BACKUP [ USING 'backup_identifier' ]
      [ CONTAINER = { ALL | CURRENT } ]

#### set_key_tag

    SET TAG 'tag' FOR 'key_id'
      [ FORCE KEYSTORE ]
      IDENTIFIED BY { EXTERNAL STORE | keystore_password }
      [ WITH BACKUP [ USING 'backup_identifier' ] ]

#### set_parameter_clause

    parameter_name =
       parameter_value [, parameter_value ]...
       [ COMMENT = string ]
       [ DEFERRED ]
       [ CONTAINER = { CURRENT | ALL } ]
       [ { SCOPE = { MEMORY | SPFILE | BOTH }
         | SID = { 'sid' | '*' }
         }...
       ]

#### set_subpartition_template

    SET SUBPARTITION TEMPLATE
       { ( range_subpartition_desc [, range_subpartition_desc]... )
       | ( list_subpartition_desc [, list_subpartition_desc]... )
       | ( individual_hash_subparts [, individual_hash_subparts]... )
       | ()
       | hash_subpartition_quantity
       }

#### set_time_zone_clause

    SET TIME_ZONE =
       '{ { + | - } hh : mi | time_zone_region }'

#### shards_clause

    SHARDS ( [schema.] { table | view } )

#### share_clause

    HIERARCHY hierarchy_ref
      { PARENT
      | LEVEL level_ref
      | MEMBER member_expression
      }

#### share_of_expression

    SHARE_OF ( calc_meas_expression  share_clause )

#### sharing_clause

    SHARING = { METADATA | DATA | NONE }

#### shrink_clause

    SHRINK SPACE [ COMPACT ] [ CASCADE ]

#### shutdown_dispatcher_clause

    SHUTDOWN [ IMMEDIATE ] dispatcher_name

#### simple_case_expression

    expr
      { WHEN comparison_expr THEN return_expr }...

#### single_column_for_loop

    FOR dimension_column
      { IN ( { literal [, literal ]...
             | subquery
             }
           )
      | [ LIKE pattern ] FROM literal TO literal
          { INCREMENT | DECREMENT } literal
      }

#### single_table_insert

    insert_into_clause
    { values_clause [ returning_clause ]
    | subquery
    } [ error_logging_clause ]

#### size_clause

    integer [ K | M | G | T | P | E ]

#### source_file_directory

    SOURCE_FILE_DIRECTORY = { 'directory_path_name' | NONE }

#### source_file_name_convert

    SOURCE_FILE_NAME_CONVERT =
      { ( 'filename_pattern', 'replacement_filename_pattern'
          [, 'filename_pattern', 'replacement_filename_pattern' ]... )
        |
        NONE
      }

#### split_index_partition

    SPLIT PARTITION partition_name_old
       AT (literal [, literal ]...)
       [ INTO (index_partition_description,
               index_partition_description
              )
       ]
       [ parallel_clause ]

#### split_nested_table_part

    NESTED TABLE column INTO
      ( nested_table_partition_spec, nested_table_partition_spec
        [split_nested_table_part]
      ) [split_nested_table_part]

#### split_table_partition

    SPLIT partition_extended_name
      { AT (literal [, literal]... )
        [ INTO ( range_partition_desc, range_partition_desc ) ]
      | VALUES ( list_values )
        [ INTO ( list_partition_desc, list_partition_desc ) ]
      | INTO ( { range_partition_desc [, range_partition_desc ]...
               | list_partition_desc [, list_partition_desc ]... }
             , partition_spec )
      } [ split_nested_table_part ]
        [ filter_condition ]
        [ dependent_tables_clause ]
        [ update_index_clauses ]
        [ parallel_clause ]
        [ allow_disallow_clustering ]
        [ ONLINE ]

#### split_table_subpartition

    SPLIT subpartition_extended_name
      { AT ( literal [, literal]... )
        [ INTO ( range_subpartition_desc, range_subpartition_desc ) ]
      | VALUES ( list_values )
        [ INTO ( list_subpartition_desc, list_subpartition_desc ) ]
      | INTO ( { range_subpartition_desc [, range_subpartition_desc ]...
               | list_subpartition_desc [, list_subpartition_desc ]... }
             , subpartition_spec )
      } [ filter_condition ]
        [ dependent_tables_clause ]
        [ update_index_clauses ]
        [ parallel_clause ]
        [ allow_disallow_clustering ]
        [ ONLINE ]

#### sql_format

    [+ | -] days hours : minutes : seconds [. frac_secs ]

#### standard_actions

    ACTIONS
      { { object_action | ALL }
        ON { DIRECTORY directory_name
           | MINING MODEL [ schema. ] object_name
           | [ schema. ] object_name }
      | { system_action | ALL }
      }
        [ { object_action | ALL }
          ON { DIRECTORY directory_name
             | MINING MODEL [ schema. ] object_name
             | [ schema. ] object_name }
        | { system_action | ALL } ]...

#### standby_database_clauses

    { { activate_standby_db_clause
    | maximize_standby_db_clause
    | register_logfile_clause
    | commit_switchover_clause
    | start_standby_clause
    | stop_standby_clause
    | convert_database_clause
    } [ parallel_clause ] }
    |
    { switchover_clause | failover_clause }

#### standbys_clause

    STANDBYS = { ( 'cdb_name' [, 'cdb_name' ]... )
               | { ALL [ EXCEPT ( 'cdb_name' [, 'cdb_name' ]... ) ] }
               | NONE
               }

#### start_standby_clause

    START LOGICAL STANDBY APPLY
    [ IMMEDIATE ]
    [ NODELAY ]
    [ NEW PRIMARY dblink
    | INITIAL [ scn_value ]
    | { SKIP FAILED TRANSACTION | FINISH }
    ]

#### startup_clauses

    { MOUNT [ { STANDBY | CLONE } DATABASE ]
    | OPEN
      { [ READ WRITE ]
          [ RESETLOGS | NORESETLOGS ]
            [ UPGRADE | DOWNGRADE ]
      | READ ONLY
      }
    }

#### statement_clauses

    CLAUSE
    { { = ( 'clause' [, 'clause' ]... ) }
    | { = ( 'clause' ) clause_options }
    | { ALL [ EXCEPT = ( 'clause' [, 'clause' ]... ) ] }
    }

#### static_base_profile

    FROM base_profile

#### still_image_object_types

    { SI_StillImage
    | SI_AverageColor
    | SI_PositionalColor
    | SI_ColorHistogram
    | SI_Texture
    | SI_FeatureList
    | SI_Color
    }

#### stop_standby_clause

    { STOP | ABORT } LOGICAL STANDBY APPLY

#### storage_clause

    STORAGE
    ({ INITIAL size_clause
     | NEXT size_clause
     | MINEXTENTS integer
     | MAXEXTENTS { integer | UNLIMITED }
     | maxsize_clause
     | PCTINCREASE integer
     | FREELISTS integer
     | FREELIST GROUPS integer
     | OPTIMAL [ size_clause | NULL ]
     | BUFFER_POOL { KEEP | RECYCLE | DEFAULT }
     | FLASH_CACHE { KEEP | NONE | DEFAULT }
     | CELL_FLASH_CACHE { KEEP | NONE | DEFAULT }
     | ENCRYPT
     } ...
    )

#### storage_table_clause

    WITH {SYSTEM | USER} MANAGED STORAGE TABLES

#### string

    [ {N | n} ]
    { '[ c ]...'
    | { Q | q } 'quote_delimiter c [ c ]... quote_delimiter'
    }

#### striping_clause

    [ FINE | COARSE ]

#### subpartition_by_hash

    SUBPARTITION BY HASH (column [, column ]...)
       [ SUBPARTITIONS integer
            [ STORE IN (tablespace [, tablespace ]...) ]
       | subpartition_template
       ]

#### subpartition_by_list

    SUBPARTITION BY LIST ( column [, column]... ) [ subpartition_template ]

#### subpartition_by_range

    SUBPARTITION BY RANGE ( column [, column]... ) [subpartition_template]

#### subpartition_extended_name

    SUBPARTITION subpartition
    |
    SUBPARTITION FOR ( subpartition_key_value [, subpartition_key_value]... )

#### subpartition_extended_names

    { SUBPARTITION | SUBPARTITIONS }
    subpartition | { FOR ( subpartition_key_value [, subpartition_key_value ]... ) }
      [, subpartition | { FOR ( subpartition_key_value [, subpartition_key_value ]... ) } ]...

#### subpartition_or_key_value

    subpartition
    |
    FOR ( subpartition_key_value [, subpartition_key_value ]... )

#### subpartition_spec

    SUBPARTITION [ subpartition ] [ partitioning_storage_clause ]

#### subpartition_template

    SUBPARTITION TEMPLATE
      ( { range_subpartition_desc [, range_subpartition_desc] ...
        | list_subpartition_desc [, list_subpartition_desc] ...
        | individual_hash_subparts [, individual_hash_subparts] ...
        }
      ) | hash_subpartition_quantity

#### subquery

    { query_block
    | subquery { UNION [ALL] | INTERSECT | MINUS } subquery
        [ { UNION [ALL] | INTERSECT | MINUS } subquery ]...
    | ( subquery )
    } [ order_by_clause ] [ row_limiting_clause ]

#### subquery_factoring_clause

    query_name ([c_alias [, c_alias]...]) AS (subquery) [search_clause] [cycle_clause]
    [, query_name ([c_alias [, c_alias]...]) AS (subquery) [search_clause] [cycle_clause]]...

#### subquery_restriction_clause

    WITH { READ ONLY
         | CHECK OPTION
         } [ CONSTRAINT constraint ]

#### substitutable_column_clause

    { [ ELEMENT ] IS OF [ TYPE ] ( ONLY type )
    | [ NOT ] SUBSTITUTABLE AT ALL LEVELS
    }

#### supplemental_db_logging

    { ADD | DROP } SUPPLEMENTAL LOG
    { DATA
    | supplemental_id_key_clause
    | supplemental_plsql_clause
    | supplemental_subset_replication_clause
    }

#### supplemental_id_key_clause

    DATA
    ( { ALL | PRIMARY KEY | UNIQUE | FOREIGN KEY }
        [, { ALL | PRIMARY KEY | UNIQUE | FOREIGN KEY } ]...
    )
    COLUMNS

#### supplemental_log_grp_clause

    GROUP log_group
    (column [ NO LOG ]
      [, column [ NO LOG ] ]...)
      [ ALWAYS ]

#### supplemental_logging_props

    SUPPLEMENTAL LOG { supplemental_log_grp_clause
                     | supplemental_id_key_clause
                     }

#### supplemental_plsql_clause

    DATA FOR PROCEDURAL REPLICATION

#### supplemental_subset_replication_clause

     DATA SUBSET DATABASE REPLICATION

#### supplemental_table_logging

    { ADD SUPPLEMENTAL LOG
      { supplemental_log_grp_clause | supplemental_id_key_clause }
        [, SUPPLEMENTAL LOG
           { supplemental_log_grp_clause | supplemental_id_key_clause }
        ]...
    | DROP SUPPLEMENTAL LOG
      { supplemental_id_key_clause | GROUP log_group }
        [, SUPPLEMENTAL LOG
           { supplemental_id_key_clause | GROUP log_group }
        ]...
    }

#### switch_logfile_clause

    SWITCH ALL LOGFILES TO BLOCKSIZE integer

#### switchover_clause

    SWITCHOVER TO target_db_name [ VERIFY | FORCE ]

#### system_partitioning

    PARTITION BY SYSTEM [ PARTITIONS integer
                        | reference_partition_desc
                           [, reference_partition_desc ...]
                        ]

#### table_collection_expression

    TABLE (collection_expression) [ (+) ]

#### table_compression

    COMPRESS
    | ROW STORE COMPRESS [ BASIC | ADVANCED ]
    | COLUMN STORE COMPRESS [  FOR { QUERY | ARCHIVE } [ LOW | HIGH ] ]
      [ [NO] ROW LEVEL LOCKING ]
    | NOCOMPRESS

#### table_index_clause

    [ schema. ] table [ t_alias ]
    (index_expr [ ASC | DESC ]
      [, index_expr [ ASC | DESC ] ]...)
      [ index_properties ]

#### table_partition_description

     [ { INTERNAL | EXTERNAL } ]
    [ deferred_segment_creation ]
    [ read_only_clause ]
    [ indexing_clause ]
    [ segment_attributes_clause ]
    [ table_compression | prefix_compression ]
    [ inmemory_clause ]
    [ ilm_clause ]
    [ OVERFLOW [ segment_attributes_clause ] ]
    [ { LOB_storage_clause
      | varray_col_properties
      | nested_table_col_properties
      }...
    ]

#### table_partitioning_clauses

    { range_partitions
    | list_partitions
    | hash_partitions
    | composite_range_partitions
    | composite_list_partitions
    | composite_hash_partitions
    | reference_partitioning
    | system_partitioning
    | consistent_hash_partitions
    | consistent_hash_with_subpartitions
    | partitionset_clauses
    }

#### table_properties

    [ column_properties ]
    [ read_only_clause ]
    [ indexing_clause ]
    [ table_partitioning_clauses ]
    [ attribute_clustering_clause ]
    [ CACHE | NOCACHE ]
    [ RESULT_CACHE ( MODE {DEFAULT | FORCE } ) ]
    [ parallel_clause ]
    [ ROWDEPENDENCIES | NOROWDEPENDENCIES ]
    [ enable_disable_clause ]...
    [ row_movement_clause ]
    [ flashback_archive_clause ]
    [ ROW ARCHIVAL ]
    [ { AS subquery } | { FOR EXCHANGE WITH TABLE [ schema .] table } ]

#### table_reference

    { { { ONLY (query_table_expression) | query_table_expression }
      [ flashback_query_clause ]
      [ pivot_clause | unpivot_clause | row_pattern_clause ] }
    | containers_clause
    | shards_clause
    }
    [ t_alias ]

#### tablespace_clauses

    { EXTENT MANAGEMENT LOCAL
    | DATAFILE file_specification [, file_specification ]...
    | SYSAUX DATAFILE file_specification [, file_specification ]...
    | default_tablespace
    | default_temp_tablespace
    | undo_tablespace
    }

#### tablespace_datafile_clauses

    DATAFILES { SIZE size_clause | autoextend_clause }...

#### tablespace_encryption_clause

    ENCRYPTION [ { [ tablespace_encryption_spec ] ENCRYPT } | DECRYPT ]

#### tablespace_encryption_spec

    USING 'encrypt_algorithm'

#### tablespace_group_clause

    TABLESPACE GROUP { tablespace_group_name | '' }

#### tablespace_logging_clauses

    { logging_clause
    | [ NO ] FORCE LOGGING
    }

#### tablespace_retention_clause

    RETENTION { GUARANTEE | NOGUARANTEE }

#### tablespace_state_clauses

    { { ONLINE
      | OFFLINE [ NORMAL | TEMPORARY | IMMEDIATE ]
      }
      | READ { ONLY | WRITE }
      | { PERMANENT | TEMPORARY }
    }

#### tempfile_reuse_clause

    TEMPFILE REUSE

#### temporary_tablespace_clause

    { { TEMPORARY TABLESPACE }
    | { LOCAL TEMPORARY TABLESPACE FOR { ALL | LEAF } }
    } tablespace
    [ TEMPFILE file_specification [, file_specification ]... ]
    [ tablespace_group_clause ]
    [ extent_management_clause ]
    [ tablespace_encryption_clause ]

#### timeout_clause

    DROP AFTER integer { M | H }

#### trace_file_clause

    TRACE
      [ AS 'filename' [ REUSE ] ]
      [ RESETLOGS | NORESETLOGS ]

#### truncate_partition_subpart

    TRUNCATE { partition_extended_names | subpartition_extended_names }
       [ { DROP [ ALL ] | REUSE } STORAGE ]
       [ update_index_clauses [ parallel_clause ] ] [ CASCADE ]

#### ts_file_name_convert

    FILE_NAME_CONVERT =
      ( 'filename_pattern', 'replacement_filename_pattern'
          [, 'filename_pattern', 'replacement_filename_pattern' ]... )
      [ KEEP ]

#### undo_mode_clause

    LOCAL UNDO { ON | OFF }

#### undo_tablespace

      [ BIGFILE | SMALLFILE ]
    UNDO TABLESPACE tablespace
      [ DATAFILE file_specification [, file_specification ]...]

#### undo_tablespace_clause

    UNDO TABLESPACE tablespace
      [ DATAFILE file_specification [, file_specification ]... ]
      [ extent_management_clause ]
      [ tablespace_retention_clause ]
      [ tablespace_encryption_clause ]

#### undrop_disk_clause

    UNDROP DISKS

#### unite_keystore

    UNITE KEYSTORE INDENTIFIED BY isolated_keystore_password
    WITH ROOT KEYSTORE [ FORCE KEYSTORE ]
    IDENTIFIED BY { EXTERNAL STORE | united_keystore_password }
     WITH BACKUP [ USING 'backup_identifier' ]

#### unpivot_clause

    UNPIVOT [ {INCLUDE | EXCLUDE} NULLS ]
    ( { column | ( column [, column]... ) }
      pivot_for_clause
      unpivot_in_clause
    )

#### unpivot_in_clause

    IN
    ( { column | ( column [, column]... ) }
          [  AS { literal | ( literal [, literal]... ) } ]
            [, { column | ( column [, column]... ) }
              [  AS {literal | ( literal [, literal]... ) } ]
            ]...
    )

#### unusable_editions_clause

    [ UNUSABLE BEFORE { CURRENT EDITION | EDITION edition } ]
    [ UNUSABLE BEGINNING WITH { CURRENT EDITION | EDITION edition | NULL EDITION } ]

#### update_all_indexes_clause

    UPDATE INDEXES
       [ ( index ( update_index_partition
                 | update_index_subpartition
                 )
            [, index ( update_index_partition
                     | update_index_subpartition
                     )
            ]...
          )
       ]

#### update_global_index_clause

    { UPDATE | INVALIDATE } GLOBAL INDEXES

#### update_index_clauses

    { update_global_index_clause
    | update_all_indexes_clause
    }

#### update_index_partition

    index_partition_description [ index_subpartition_clause ]
      [, index_partition_description [ index_subpartition_clause ] ]...

#### update_index_subpartition

    SUBPARTITION [ subpartition ]
       [ TABLESPACE tablespace ]
    [, SUBPARTITION [ subpartition ]
          [ TABLESPACE tablespace ]
    ]...

#### update_set_clause

    SET
    { { (column [, column ]...) = (subquery)
      | column = { expr | (subquery) | DEFAULT }
      }
         [, { (column [, column]...) = (subquery)
            | column = { expr | (subquery) | DEFAULT }
            }
         ]...
    | VALUE (t_alias) = { expr | (subquery) }
    }

#### upgrade_table_clause

    UPGRADE [ [NOT ] INCLUDING DATA ]
       [ column_properties ]

#### use_key

    USE [ ENCRYPTION ] KEY 'key_id'
      [ USING TAG 'tag' ]
      [ FORCE KEYSTORE ]
      IDENTIFIED BY { EXTERNAL STORE | keystore_password }
      [ WITH BACKUP [ USING 'backup_identifier' ]]

#### user_clauses

    { ADD USER user [, 'user']...
    | DROP USER user [, 'user']... [CASCADE]
    | REPLACE USER 'old_user' WITH 'new_user' [, 'old_user' WITH 'new_user']...
    }

#### user_tablespaces_clause

    USER_TABLESPACES =
      { ( 'tablespace' [, 'tablespace' ]... )
      | ALL [ EXCEPT ( 'tablespace' [, 'tablespace' ]... ) ]
      | NONE
      }
      [ SNAPSHOT COPY | NO DATA | COPY | MOVE | NOCOPY ]

#### usergroup_clauses

    { ADD USERGROUP 'usergroup' WITH MEMBER 'user' [, 'user']...
    | MODIFY USERGROUP 'usergroup' { ADD | DROP } MEMBER 'user' [, 'user']...
    | DROP USERGROUP 'usergroup'
    }

#### using_clause

    USING [ schema. ] fact_table_or_view  [ [ AS ] alias ]

#### using_function_clause

    USING [ schema. ] [ package. | type. ] function_name

#### using_index_clause

    USING INDEX
      { [ schema. ] index
      | (create_index_statement)
      | index_properties
      }

#### using_snapshot_clause

    USING SNAPSHOT { snapshot_name | AT SCN snapshot_SCN | AT snapshot_timestamp }

#### using_statistics_type

    USING { [ schema. ] statistics_type | NULL }

#### using_type_clause

    USING [ schema. ] implementation_type [ array_DML_clause ]

#### validation_clauses

    { VALIDATE REF UPDATE [ SET DANGLING TO NULL ]
    | VALIDATE STRUCTURE
         [ CASCADE { FAST | COMPLETE { OFFLINE | ONLINE } [ into_clause ] } ]
    }

#### values_clause

    VALUES ({ expr | DEFAULT }
              [, { expr | DEFAULT } ]...
           )

#### varray_col_properties

    VARRAY varray_item
    { [ substitutable_column_clause ] varray_storage_clause
    | substitutable_column_clause
    }

#### varray_storage_clause

    STORE AS [SECUREFILE | BASICFILE] LOB
    { [LOB_segname] ( LOB_storage_parameters )
    | LOB_segname
    }

#### virtual_column_definition

    column [ datatype [ COLLATE column_collation_name ] ]
      [ VISIBLE | INVISIBLE ]
      [ GENERATED ALWAYS ] AS (column_expression) [ VIRTUAL ]
      [ evaluation_edition_clause ] [ unusable_editions_clause ]
      [ inline_constraint [ inline_constraint ]... ]

#### where_clause

    WHERE condition

#### wildcard

    [ id "." ] id "." "*"

#### window_clause

    HIERARCHY hierarchy_ref
      BETWEEN { preceding_boundary | following_boundary }
    [ WITHIN {   LEVEL
               | PARENT
               | ANCESTOR AT LEVEL level_name
             }

#### window_expression

    aggregate_function OVER ( window_clause )

#### windowing_clause

    { ROWS | RANGE }
    { BETWEEN
      { UNBOUNDED PRECEDING
      | CURRENT ROW
      | value_expr { PRECEDING | FOLLOWING }
      }
      AND
      { UNBOUNDED FOLLOWING
      | CURRENT ROW
      | value_expr { PRECEDING | FOLLOWING }
      }
    | { UNBOUNDED PRECEDING
      | CURRENT ROW
      | value_expr PRECEDING
      }
    }

#### with_clause

    WITH [ plsql_declarations ] [ subquery_factoring_clause ]

#### XML_attributes_clause

    XMLATTRIBUTES
      ( [ ENTITYESCAPING | NOENTITYESCAPING ]
        [ SCHEMACHECK | NOSCHEMACHECK ]
        value_expr [ { [AS] c_alias } | { AS EVALNAME value_expr } ]
          [, value_expr [ { [AS] c_alias } | { AS EVALNAME value_expr } ] ]...
      )

#### XMLnamespaces_clause

    XMLNAMESPACES
      ( { string AS identifier } | { DEFAULT string }
          [, { string AS identifier } | { DEFAULT string } ]...
      )

#### XML_passing_clause

    PASSING [ BY VALUE ]
        expr [ AS identifier ]
          [, expr [ AS identifier ]
          ]...

#### XML_table_column

    column
         { FOR ORDINALITY
         | { datatype | XMLTYPE [ (SEQUENCE) BY REF ] }
         [ PATH string ] [ DEFAULT expr ]
         }

#### XMLIndex_clause

    [XDB.] XMLINDEX [ local_XMLIndex_clause ]
                    [ parallel_clause ]
      [ XMLIndex_parameters_clause ]

#### XMLSchema_spec

      [ XMLSCHEMA XMLSchema_URL ]
    ELEMENT { element | XMLSchema_URL # element }
      [ STORE ALL VARRAYS AS { LOBS | TABLES } ]
      [ { ALLOW | DISALLOW } NONSCHEMA ]
      [ { ALLOW | DISALLOW } ANYSCHEMA ]

#### XMLTABLE_options

    [ XML_passing_clause ]
    [ RETURNING SEQUENCE BY REF ]
    [ COLUMNS XML_table_column [, XML_table_column]...]

#### XMLType_column_properties

    XMLTYPE [ COLUMN ] column
       [ XMLType_storage ]
       [ XMLSchema_spec ]

#### XMLType_storage

    STORE
    { AS
    { OBJECT RELATIONAL
    | [SECUREFILE | BASICFILE]
      { CLOB | BINARY XML }
        [ { LOB_segname [ (LOB_parameters) ]
          | (LOB_parameters)
          }
        ]
    }
    | { ALL VARRAYS AS { LOBS | TABLES } }
    }

#### XMLType_table

    OF XMLTYPE
      [ (oject_properties) ]
      [ XMLTYPE XMLType_storage ]
      [ XMLSchema_spec ]
      [ XMLType_virtual_columns ]
      [ ON COMMIT { DELETE | PRESERVE } ROWS ]
      [ OID_clause ]
      [ OID_index_clause ]
      [ physical_properties ]
      [ table_properties ]

#### XMLType_view_clause

    OF XMLTYPE [ XMLSchema_spec ]
    WITH OBJECT { IDENTIFIER | ID }
      { DEFAULT | ( expr [, expr ]...) }

#### XMLType_virtual_columns

    VIRTUAL COLUMNS ( column AS (expr) [, column AS (expr) ]... )

#### ym_iso_format

    [-] P [ years Y ] [months M] [days D]
      [T [hours H] [minutes M] [seconds [. frac_secs] S ] ]

#### zonemap_attributes

    { TABLESPACE tablespace
    | SCALE integer
    | { CACHE | NOCACHE }
    }...

#### zonemap_clause

    { WITH MATERIALIZED ZONEMAP [ ( zonemap_name ) ] }
    |
    { WITHOUT MATERIALIZED ZONEMAP }

#### zonemap_refresh_clause

    REFRESH
    [ FAST | COMPLETE | FORCE ]
    [ ON { DEMAND | COMMIT | LOAD | DATA MOVEMENT | LOAD DATA MOVEMENT } ]
