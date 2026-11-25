## 1  SQL Statements

This chapter presents the syntax for Oracle SQL statements.

This chapter includes the following section:

- Syntax for SQL Statements

### Syntax for SQL Statements

SQL statements are the means by which programs and users access data in an Oracle database.

The sections that follow show each SQL statement and its related syntax. Refer to [Subclauses](Subclauses.md) for the syntax of the subclauses listed in the syntax for the statements.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/SQL-Statements-ADMINISTER-KEY-MANAGEMENT-to-ALTER-JAVA.md) for detailed information about SQL statements

#### [ADMINISTER KEY MANAGEMENT](../sqlrf/ADMINISTER-KEY-MANAGEMENT.md)

    ADMINISTER KEY MANAGEMENT
      { keystore_management_clauses
      | key_management_clauses
      | secret_management_clauses
      }

#### [ALTER ANALYTIC VIEW](../sqlrf/ALTER-ANALYTIC-VIEW.md)

    ALTER ANALYTIC VIEW [ IF EXISTS ][ schema. ] analytic_view_name
      { RENAME TO new_av_name | COMPILE }

#### [ALTER ATTRIBUTE DIMENSION](../sqlrf/ALTER-ATTRIBUTE-DIMENSION.md)

    ALTER ATTRIBUTE DIMENSION [ IF EXISTS ] [ schema. ]
      attr_dim_name { RENAME TO new_attr_dim_name | COMPILE }

#### [ALTER AUDIT POLICY](../sqlrf/ALTER-AUDIT-POLICY-Unified-Auditing.md)

    ALTER AUDIT POLICY policy
      [ ADD [ privilege_audit_clause ] [ action_audit_clause ] [ role_audit_clause ] ]
      [ DROP [ privilege_audit_clause ] [ action_audit_clause ] [ role_audit_clause ] ]
      [ CONDITION { DROP | 'audit_condition'
        EVALUATE PER { STATEMENT | SESSION | INSTANCE }   } ]
      [ ONLY TOPLEVEL ]

#### [ALTER CLUSTER](../sqlrf/ALTER-CLUSTER.md)

    ALTER CLUSTER [ IF EXISTS ] [ schema. ] cluster
      { physical_attributes_clause
      | SIZE size_clause
      | [ MODIFY PARTITION partition ] allocate_extent_clause
      | deallocate_unused_clause
      | { CACHE | NOCACHE }
      } ...
      [ parallel_clause ]

#### [ALTER DATABASE](../sqlrf/ALTER-DATABASE.md)

    ALTER DATABASE [ database ]
      { startup_clauses
      | recovery_clauses
      | database_file_clauses
      | logfile_clauses
      | controlfile_clauses
      | standby_database_clauses
      | default_settings_clauses
      | instance_clauses
      | security_clause
      | prepare_clause
      | drop_mirror_copy
      | lost_write_protection
      | cdb_fleet_clauses
      | property_clause
      }

#### [ALTER DATABASE DICTIONARY](../sqlrf/ALTER-DATABASE-DICTIONARY.md)

    ALTER DATABASE DICTIONARY
    {   ENCRYPT CREDENTIALS
      | REKEY CREDENTIALS
      | DELETE CREDENTIALS KEY
    }

#### [ALTER DATABASE LINK](../sqlrf/ALTER-DATABASE-LINK.md)

    ALTER [ SHARED ] [ PUBLIC ] DATABASE LINK [ IF EXISTS ] dblink
      { CONNECT TO user IDENTIFIED BY password [ dblink_authentication ]
      | dblink_authentication
      }

#### [ALTER DIMENSION](../sqlrf/ALTER-DIMENSION.md)

    ALTER DIMENSION [ schema. ] dimension
      { ADD { level_clause
            | hierarchy_clause
            | attribute_clause
            | extended_attribute_clause
            }
      } ...
      |
      { DROP { LEVEL level [ RESTRICT | CASCADE ]
             | HIERARCHY hierarchy
             | ATTRIBUTE attribute [ LEVEL level [ COLUMN column ] ]...
             }
      } ...
      |
      COMPILE


#### [ALTER DISKGROUP](../sqlrf/ALTER-DISKGROUP.md)

    ALTER DISKGROUP
      { diskgroup_name
          { { { add_disk_clause | drop_disk_clause }
              [, { add_disk_clause | drop_disk_clause } ]...
            | resize_disk_clause
            } [ rebalance_diskgroup_clause ]
          | replace_disk_clause
          | rename_disk_clause
          | disk_online_clause
          | disk_offline_clause
          | rebalance_diskgroup_clause
          | check_diskgroup_clause
          | diskgroup_template_clauses
          | diskgroup_directory_clauses
          | diskgroup_alias_clauses
          | diskgroup_volume_clauses
          | diskgroup_attributes
          | modify_diskgroup_file
          | drop_diskgroup_file_clause
          | convert_redundancy_clause
          | usergroup_clauses
          | user_clauses
          | file_permissions_clause
          | file_owner_clause
          | scrub_clause
          | quotagroup_clauses
          | filegroup_clauses
          }
        | { diskgroup_name [, diskgroup_name ]...
          | ALL
          } { undrop_disk_clause
            | diskgroup_availability
            | enable_disable_volume
            }
      }

#### [ALTER FLASHBACK ARCHIVE](../sqlrf/ALTER-FLASHBACK-ARCHIVE.md)

    ALTER FLASHBACK ARCHIVE flashback_archive
      { SET DEFAULT
      | { ADD | MODIFY } TABLESPACE tablespace [flashback_archive_quota]
      | REMOVE TABLESPACE tablespace_name
      | MODIFY RETENTION flashback_archive_retention
      | PURGE { ALL | BEFORE { SCN expr | TIMESTAMP expr } }
      | [NO] OPTIMIZE DATA
      }

#### [ALTER FUNCTION](../sqlrf/ALTER-FUNCTION.md)

    ALTER FUNCTION [ IF EXISTS ][ schema. ] function_name
    { function_compile_clause | { EDITIONABLE | NONEDITIONABLE } }

#### [ALTER HIERARCHY](../sqlrf/ALTER-HIERARCHY.md)

    ALTER HIERARCHY [ IF EXISTS ][ schema. ] hierarchy_name
      { RENAME TO new_hier_name | COMPILE }

#### [ALTER INDEX](../sqlrf/ALTER-INDEX.md)

    ALTER INDEX [ IF EXISTS ][ schema. ]index
      { { deallocate_unused_clause
        | allocate_extent_clause
        | shrink_clause
        | parallel_clause
        | physical_attributes_clause
        | logging_clause
        | partial_index_clause
        } ...
      | rebuild_clause [ { DEFERRED | IMMEDIATE } INVALIDATION ]
      | PARAMETERS ( 'ODCI_parameters' )
      | COMPILE
      | { ENABLE | DISABLE }
      | UNUSABLE [ ONLINE ] [ { DEFERRED | IMMEDIATE } INVALIDATION ]
      | VISIBLE | INVISIBLE
      | RENAME TO new_name
      | COALESCE [ CLEANUP ] [ ONLY ] [ parallel_clause ]
      | { MONITORING | NOMONITORING } USAGE
      | UPDATE BLOCK REFERENCES
      | alter_index_partitioning
      }


#### [ALTER INDEXTYPE](../sqlrf/ALTER-INDEXTYPE.md)

    ALTER INDEXTYPE [ IF EXISTS ][ schema. ] indextype
      { { ADD | DROP } [ schema. ] operator ( parameter_types )
          [ , { ADD | DROP } [schema. ] operator ( parameter_types ) ]... [ using_type_clause ]
      | COMPILE
      }
      [ WITH LOCAL [ RANGE ] PARTITION ] [ storage_table_clause ]


#### [ALTER INMEMORY JOIN GROUP](../sqlrf/index.md)

    ALTER INMEMORY JOIN GROUP [ schema. ] join_group
      { ADD | REMOVE } ( [ schema. ] table ( column ) )

#### [ALTER JAVA](../sqlrf/ALTER-JAVA.md)

    ALTER JAVA
      { SOURCE | CLASS } [ IF EXISTS ][ schema. ]object_name
      [ RESOLVER
          ( ( match_string [, ] { schema_name | - } )... )
      ]
      { { COMPILE | RESOLVE }
      | invoker_rights_clause
      }

#### [ALTER LIBRARY](../sqlrf/ALTER-LIBRARY.md)

    ALTER LIBRARY [ IF EXISTS ][ schema. ] library_name
    { library_compile_clause | { EDITIONABLE | NONEDITIONABLE } }

#### [ALTER LOCKDOWN PROFILE](../sqlrf/ALTER-LOCKDOWN-PROFILE.md)

    ALTER LOCKDOWN PROFILE
      { lockdown_features
      | lockdown_options
      | lockdown_statements
      }

#### [ALTER MATERIALIZED VIEW](../sqlrf/ALTER-MATERIALIZED-VIEW.md)

    ALTER MATERIALIZED VIEW [ IF EXISTS ]
      [ schema. ] materialized_view
      [ physical_attributes_clause
      | modify_mv_column_clause
      | table_compression
      | inmemory_table_clause
      | LOB_storage_clause [, LOB_storage_clause ]...
      | modify_LOB_storage_clause [, modify_LOB_storage_clause ]...
      | alter_table_partitioning
      | parallel_clause
      | logging_clause
      | allocate_extent_clause
      | deallocate_unused_clause
      | shrink_clause
      | { CACHE | NOCACHE }
      ]
      [ alter_iot_clauses ]
      [ USING INDEX physical_attributes_clause ]
      [ MODIFY scoped_table_ref_constraint
      | alter_mv_refresh
      ]
      [ evaluation_edition_clause ]
      [ { ENABLE | DISABLE } ON QUERY COMPUTATION ]
      [ alter_query_rewrite_clause
      | COMPILE
      | CONSIDER FRESH
      ]

#### [ALTER MATERIALIZED VIEW LOG](../sqlrf/ALTER-MATERIALIZED-VIEW-LOG.md)

    ALTER MATERIALIZED VIEW LOG [ FORCE ]
      ON [ IF EXISTS ][ schema. ]table
      [ physical_attributes_clause
      | add_mv_log_column_clause
      | alter_table_partitioning
      | parallel_clause
      | logging_clause
      | allocate_extent_clause
      | shrink_clause
      | move_mv_log_clause
      | { CACHE | NOCACHE }
      ] [ mv_log_augmentation ] [  mv_log_purge_clause ] [ for_refresh_clause ]


#### [ALTER MATERIALIZED ZONEMAP](../sqlrf/ALTER-MATERIALIZED-ZONEMAP.md)

    ALTER MATERIALIZED ZONEMAP [ IF EXISTS ][ schema. ] zonemap_name
      { alter_zonemap_attributes
      | zonemap_refresh_clause
      | { ENABLE | DISABLE } PRUNING
      | COMPILE
      | REBUILD
      | UNUSABLE
      }

#### [ALTER OPERATOR](../sqlrf/ALTER-OPERATOR.md)

    ALTER OPERATOR [ IF EXISTS ][ schema. ] operator
      { add_binding_clause
      | drop_binding_clause
      | COMPILE
      }

#### [ALTER OUTLINE](../sqlrf/ALTER-OUTLINE.md)

    ALTER OUTLINE [ PUBLIC | PRIVATE ] outline
      { REBUILD
      | RENAME TO new_outline_name
      | CHANGE CATEGORY TO new_category_name
      | { ENABLE | DISABLE }
      } ...


#### [ALTER PACKAGE](../sqlrf/ALTER-PACKAGE.md)

    ALTER PACKAGE [ IF EXISTS ][ schema. ] package_name
    { package_compile_clause | { EDITIONABLE | NONEDITIONABLE } }

#### [ALTER PLUGGABLE DATABASE](../sqlrf/ALTER-PLUGGABLE-DATABASE.md)

    ALTER PLUGGABLE DATABASE
      { pdb_unplug_clause
      | pdb_settings_clauses
      | pdb_datafile_clause
      | pdb_recovery_clauses
      | pdb_change_state
      | pdb_change_state_from_root
      | application_clauses
      | snapshot_clauses
      | prepare_clause
      | drop_mirror_copy
      | lost_write_protection
      }

#### [ALTER PROCEDURE](../sqlrf/ALTER-PROCEDURE.md)

    ALTER PROCEDURE [ schema. ] procedure_name
    { procedure_compile_clause | { EDITIONABLE | NONEDITIONABLE } }

#### [ALTER PROFILE](../sqlrf/ALTER-PROFILE.md)

    ALTER PROFILE profile LIMIT
      { resource_parameters | password_parameters } ...
      [ CONTAINER = { CURRENT | ALL } ]

#### [ALTER RESOURCE COST](../sqlrf/ALTER-RESOURCE-COST.md)

    ALTER RESOURCE COST
      { { CPU_PER_SESSION
        | CONNECT_TIME
        | LOGICAL_READS_PER_SESSION
        | PRIVATE_SGA
        } integer
      } ...


#### [ALTER ROLE](../sqlrf/ALTER-ROLE.md)

    ALTER ROLE role
      { NOT IDENTIFIED
      | IDENTIFIED
          { BY password
          | USING [ schema. ] package
          | EXTERNALLY
          | GLOBALLY AS ' { domain_name_of_directory_group
                           | AZURE_ROLE=value
                           | IAM_GROUP_NAME=value } '
          }
      }
      [ CONTAINER = { CURRENT | ALL } ]

#### [ALTER ROLLBACK SEGMENT](../sqlrf/ALTER-ROLLBACK-SEGMENT.md)

    ALTER ROLLBACK SEGMENT rollback_segment
      { ONLINE
      | OFFLINE
      | storage_clause
      | SHRINK [ TO size_clause ]
      }

#### [ALTER SEQUENCE](../sqlrf/ALTER-SEQUENCE.md)

    ALTER SEQUENCE [ IF EXISTS ][ schema. ] sequence
      {
        { INCREMENT BY | START WITH } integer
      | { MAXVALUE integer | NOMAXVALUE }
      | { MINVALUE integer | NOMINVALUE }
      |  RESTART
      | { CYCLE | NOCYCLE }
      | { CACHE integer | NOCACHE }
      | { ORDER | NOORDER }
      | { KEEP | NOKEEP }
      | { SCALE {EXTEND | NOEXTEND} | NOSCALE }
      | { SHARD {EXTEND | NOEXTEND} | NOSHARD }
      | { SESSION | GLOBAL }
      } ...

#### [ALTER SESSION](../sqlrf/ALTER-SESSION.md)

     ALTER SESSION
      { ADVISE { COMMIT | ROLLBACK | NOTHING }
      | CLOSE DATABASE LINK dblink
      | { ENABLE | DISABLE } COMMIT IN PROCEDURE
      | { ENABLE | DISABLE } GUARD
      | { ENABLE | DISABLE | FORCE } PARALLEL
        { DML | DDL | QUERY } [ PARALLEL integer ]
      | { ENABLE RESUMABLE [ TIMEOUT integer ] [ NAME string ]
        | DISABLE RESUMABLE
        }
      | { ENABLE | DISABLE } SHARD DDL
      | SYNC WITH PRIMARY
      | alter_session_set_clause
      }

#### [ALTER SYNONYM](../sqlrf/ALTER-SYNONYM.md)

    ALTER [ PUBLIC ] SYNONYM [ IF EXISTS ][ schema. ] synonym
      { EDITIONABLE | NONEDITIONABLE | COMPILE }

#### [ALTER SYSTEM](../sqlrf/ALTER-SYSTEM.md)

    ALTER SYSTEM
      { archive_log_clause
      | checkpoint_clause
      | check_datafiles_clause
      | distributed_recov_clauses
      | FLUSH { SHARED_POOL | GLOBAL CONTEXT | BUFFER_CACHE | FLASH_CACHE
              | REDO TO target_db_name [ [ NO ] CONFIRM APPLY ] }
      | end_session_clauses
      | SWITCH LOGFILE
      | { SUSPEND | RESUME }
      | quiesce_clauses
      | rolling_migration_clauses
      | rolling_patch_clauses
      | security_clauses
      | affinity_clauses
      | shutdown_dispatcher_clause
      | REGISTER
      | SET alter_system_set_clause
            [ alter_system_set_clause ]...
      | RESET alter_system_reset_clause
              [ alter_system_reset_clause ]...
      | RELOCATE CLIENT client_id
      | cancel_sql_clause
      | FLUSH PASSWORDFILE_METADATA_CACHE
      }

#### [ALTER TABLE](../sqlrf/ALTER-TABLE.md)

    ALTER TABLE [ IF EXISTS ][ schema. ] table
      [ memoptimize_read_clause ] [ memoptimize_write_clause ]
      [ alter_table_properties
      | column_clauses
      | constraint_clauses
      | alter_table_partitioning [ { DEFERRED | IMMEDIATE } INVALIDATION ]
      | alter_external_table
      | move_table_clause
      | modify_to_partitioned
      | modify_opaque_type
      | immutable_table_clauses
      | blockchain_table_clauses
      ]
      [ enable_disable_clause
      | { ENABLE | DISABLE }
        { TABLE LOCK | ALL TRIGGERS | CONTAINER_MAP | CONTAINERS_DEFAULT }
      ] ...


#### [ALTER TABLESPACE](../sqlrf/ALTER-TABLESPACE.md)

    ALTER TABLESPACE tablespace [ IF EXISTS ] alter_tablespace_attrs

#### [ALTER TABLESPACE SET](../sqlrf/ALTER-TABLESPACE-SET.md)

    ALTER TABLESPACE SET tablespace_set alter_tablespace_attrs

#### [ALTER TRIGGER](../sqlrf/ALTER-TRIGGER.md)

    ALTER TRIGGER [ IF EXISTS ][ schema. ] trigger_name
      { trigger_compile_clause
      | { ENABLE| DISABLE }
      | RENAME TO new_name
      | { EDITIONABLE | NONEDITIONABLE }
      }

#### [ALTER TYPE](../sqlrf/ALTER-TYPE.md)

    ALTER TYPE [ IF EXISTS ][ schema. ] type_name
    { alter_type_clause | { EDITIONABLE | NONEDITIONABLE } }

#### [ALTER USER](../sqlrf/ALTER-USER.md)

    ALTER USER [ IF EXISTS ]
      { user
        { IDENTIFIED
          { BY password [ REPLACE old_password ]
          | EXTERNALLY [ AS 'certificate_DN' | AS 'kerberos_principal_name' ]
          | GLOBALLY [ AS ' { directory_DN | { {AZURE_USER | AZURE_ROLE }=value}
                               | { { IAM_GROUP_NAME | IAM_PRINCIPAL_NAME }=value}
                              }'
                     ]
          }
        | NO AUTHENTICATION
        | DEFAULT COLLATION collation_name
        | DEFAULT TABLESPACE tablespace
        | [ LOCAL ] TEMPORARY TABLESPACE { tablespace | tablespace_group_name }
        | { QUOTA { size_clause
                  | UNLIMITED
                  } ON tablespace
          } ...
        | PROFILE profile
        | DEFAULT ROLE { role [, role ]...
                       | ALL [ EXCEPT role [, role ]... ]
                       | NONE
                       }
        | PASSWORD EXPIRE
        | EXPIRE PASSWORD ROLLOVER PERIOD
        | ACCOUNT { LOCK | UNLOCK }
        | ENABLE EDITIONS [ FOR object_type [, object_type ]... ] [ FORCE ]
        | [HTTP] DIGEST { ENABLE | DISABLE }
        | CONTAINER = { CURRENT | ALL }
        | container_data_clause
        } ...
      | user [, user ]... proxy_clause
      }

#### [ALTER VIEW](../sqlrf/ALTER-VIEW.md)

    ALTER VIEW [ IF EXISTS ][ schema. ] view
      { ADD out_of_line_constraint
      | MODIFY CONSTRAINT constraint
          { RELY | NORELY }
      | DROP { CONSTRAINT constraint
             | PRIMARY KEY
             | UNIQUE (column [, column ]...)
             }
      | COMPILE
      | { READ ONLY | READ WRITE }
      | { EDITIONABLE | NONEDITIONABLE }
      }

#### [ANALYZE](../sqlrf/ANALYZE.md)

    ANALYZE
      { { TABLE [ schema. ] table
        | INDEX [ schema. ] index
        } [ partition_extension_clause ]
      | CLUSTER [ schema. ] cluster
      }
      { validation_clauses
      | LIST CHAINED ROWS [ into_clause ]
      | DELETE [ SYSTEM ] STATISTICS
      }

#### [ASSOCIATE STATISTICS](../sqlrf/ASSOCIATE-STATISTICS.md)

    ASSOCIATE STATISTICS WITH
      { column_association | function_association }
      [ storage_table_clause ]

#### [AUDIT (Traditional Auditing)](../sqlrf/AUDIT-Traditional-Auditing.md)

    AUDIT
      { audit_operation_clause [ auditing_by_clause | IN SESSION CURRENT ]
      | audit_schema_object_clause
      | NETWORK
      | DIRECT_PATH LOAD [ auditing_by_clause ]
      } [ BY { SESSION | ACCESS } ]
        [ WHENEVER [ NOT ] SUCCESSFUL ]
        [ CONTAINER = { CURRENT | ALL } ]

#### [AUDIT (Unified Auditing)](../sqlrf/AUDIT-Unified-Auditing.md)

    AUDIT
      { POLICY policy
        [ { BY user [, user]... }
        | { EXCEPT user [, user]... }
        | by_users_with_roles ]
        [ WHENEVER [ NOT ] SUCCESSFUL ]
      }
      |
      { CONTEXT NAMESPACE namespace ATTRIBUTES attribute [, attribute ]...
          [, CONTEXT NAMESPACE namespace ATTRIBUTES attribute [, attribute ]... ]...
        [ BY user [, user]... ]
      }

#### [CALL](../sqlrf/CALL.md)

    CALL
      { routine_clause
      | object_access_expression
      }
      [ INTO :host_variable
        [ [ INDICATOR ] :indicator_variable ] ]

#### [COMMENT](../sqlrf/COMMENT.md)

    COMMENT ON
      { AUDIT POLICY policy
      | COLUMN [ schema. ]
          { table. | view. | materialized_view. } column
      | EDITION edition_name
      | INDEXTYPE [ schema. ] indextype
      | MATERIALIZED VIEW materialized_view
      | MINING MODEL [ schema. ] model
      | OPERATOR [ schema. ] operator
      | TABLE [ schema. ] { table | view }
      }
      IS string

#### [COMMIT](../sqlrf/COMMIT.md)

    COMMIT [ WORK ]
      [ [ COMMENT string ]
        | [ WRITE [ WAIT | NOWAIT ] [ IMMEDIATE | BATCH ]
        ]
      | FORCE string [, integer ]
      ]

#### [CREATE ANALYTIC VIEW](../sqlrf/CREATE-ANALYTIC-VIEW.md)

    CREATE [ OR REPLACE ] [ { FORCE | NOFORCE } ]
       ANALYTIC VIEW [ IF NOT EXISTS ][ schema. ] analytic_view
        [ sharing clause ]
        [ classification_clause ]...
        using_clause
        dim_by_clause
        measures_clause
        [ default_measure_clause ]
        [ default_aggregate_clause ]
        [ cache_clause ]

#### [CREATE ATTRIBUTE DIMENSION](../sqlrf/CREATE-ATTRIBUTE-DIMENSION.md)

    CREATE [ OR REPLACE ] [ FORCE | NOFORCE ] ATTRIBUTE DIMENSION
      [ IF NOT EXISTS ] [ schema. ] attr_dimension [ sharing_clause ]
      [ classification_clause ]... ]
      [ DIMENSION TYPE { STANDARD | TIME } ]
      attr_dim_using_clause
      attributes_clause
      [ attr_dim_level_clause ]...
      [ all_clause ]

#### [CREATE AUDIT POLICY](../sqlrf/CREATE-AUDIT-POLICY-Unified-Auditing.md)

    CREATE AUDIT POLICY policy
      [ privilege_audit_clause ] [ action_audit_clause ] [ role_audit_clause ]
      [ WHEN 'audit_condition' EVALUATE PER { STATEMENT | SESSION | INSTANCE } ]
      [ ONLY TOPLEVEL ]
      [ CONTAINER = { ALL | CURRENT } ]

#### [CREATE CLUSTER](../sqlrf/CREATE-CLUSTER.md)

    CREATE CLUSTER [ IF NOT EXISTS ][ schema. ] cluster
      (column datatype [ COLLATE column_collation_name ] [ SORT ]
        [, column datatype [ COLLATE column_collation_name ] [ SORT ] ]...
      )
      [ { physical_attributes_clause
        | SIZE size_clause
        | TABLESPACE tablespace
        | { INDEX
          | [ SINGLE TABLE ]
            HASHKEYS integer [ HASH IS expr ]
          }
        }...
      ]
      [ parallel_clause ]
      [ NOROWDEPENDENCIES | ROWDEPENDENCIES ]
      [ CACHE | NOCACHE ] [ cluster_range_partitions ]

#### [CREATE CONTEXT](../sqlrf/CREATE-CONTEXT.md)

    CREATE [ OR REPLACE ] CONTEXT namespace
      USING [ schema. ] package
      [ INITIALIZED { EXTERNALLY | GLOBALLY }
      | ACCESSED GLOBALLY
      ]

#### [CREATE CONTROLFILE](../sqlrf/CREATE-CONTROLFILE.md)

    CREATE CONTROLFILE
      [ REUSE ] [ SET ] DATABASE database
      [ logfile_clause ]
      { RESETLOGS | NORESETLOGS }
      [ DATAFILE file_specification
                 [, file_specification ]... ]
      [ MAXLOGFILES integer
      | MAXLOGMEMBERS integer
      | MAXLOGHISTORY integer
      | MAXDATAFILES integer
      | MAXINSTANCES integer
      | { ARCHIVELOG | NOARCHIVELOG }
      | FORCE LOGGING
      | SET STANDBY LOGGING FOR {DATA AVAILABILITY | LOAD PERFORMANCE}
      ]...
      [ character_set_clause ]

#### [CREATE DATABASE](../sqlrf/CREATE-DATABASE.md)

    CREATE DATABASE [ database ]
      { USER SYS IDENTIFIED BY password
      | USER SYSTEM IDENTIFIED BY password
      | CONTROLFILE REUSE
      | MAXDATAFILES integer
      | MAXINSTANCES integer
      | CHARACTER SET charset
      | NATIONAL CHARACTER SET charset
      | SET DEFAULT
          { BIGFILE | SMALLFILE } TABLESPACE
      | database_logging_clauses
      | tablespace_clauses
      | set_time_zone_clause
      | [ BIGFILE | SMALLFILE ] USER_DATA TABLESPACE tablespace_name
          DATAFILE datafile_tempfile_spec [, datafile_tempfile_spec ]...
      | enable_pluggable_database
      }...

#### [CREATE DATABASE LINK](../sqlrf/CREATE-DATABASE-LINK.md)

    CREATE [ SHARED ] [ PUBLIC ] DATABASE LINK [ IF NOT EXISTS ] dblink
      [ CONNECT TO
        { CURRENT_USER
        | user IDENTIFIED BY password [ dblink_authentication ]
        }
      | dblink_authentication
      ]...
      [ USING connect_string ]

#### [CREATE DIMENSION](../sqlrf/CREATE-DIMENSION.md)

    CREATE DIMENSION [ schema. ] dimension
      level_clause ...
      { hierarchy_clause
      | attribute_clause
      | extended_attribute_clause
      }...

#### [CREATE DIRECTORY](../sqlrf/CREATE-DIRECTORY.md)

    CREATE [ OR REPLACE ] DIRECTORY [ IF NOT EXISTS ] directory
      [ SHARING = { METADATA | NONE } ]
      AS 'path_name'

#### [CREATE DISKGROUP](../sqlrf/CREATE-DISKGROUP.md)

    CREATE DISKGROUP diskgroup_name
      [ { HIGH | NORMAL | FLEX | EXTENDED [ SITE site_name ] | EXTERNAL } REDUNDANCY ]
      { [ QUORUM | REGULAR ] [ FAILGROUP failgroup_name ]
        DISK qualified_disk_clause [, qualified_disk_clause ]...
      }...
      [ ATTRIBUTE { 'attribute_name' = 'attribute_value' }
                  [, 'attribute_name' = 'attribute_value' ]... ]

#### [CREATE EDITION](../sqlrf/CREATE-EDITION.md)

    CREATE EDITION [ IF NOT EXISTS ] edition
      [ AS CHILD OF parent_edition ]

#### [CREATE FLASHBACK ARCHIVE](../sqlrf/CREATE-FLASHBACK-ARCHIVE.md)

    CREATE FLASHBACK ARCHIVE [DEFAULT] flashback_archive
      TABLESPACE tablespace
      [flashback_archive_quota]
      [ [NO] OPTIMIZE DATA ]
      flashback_archive_retention

#### [CREATE FUNCTION](../sqlrf/CREATE-FUNCTION.md)

    CREATE [ OR REPLACE ]
    [ EDITIONABLE | NONEDITIONABLE ]
    FUNCTION [ IF NOT EXISTS ] plsql_function_source

#### [CREATE HIERARCHY](../sqlrf/CREATE-HIERARCHY.md)

    CREATE [ OR REPLACE ] [ FORCE | NOFORCE ]
      HIERARCHY [ IF NOT EXISTS ][ schema. ] hierarchy
      [ sharing_clause ]
      [ classification_clause ]... ]
      hier_using_clause
      level_hier_clause
      [ hier_attrs_clause ]

#### [CREATE INDEX](../sqlrf/CREATE-INDEX.md)

    CREATE [ UNIQUE | BITMAP ] INDEX [ IF NOT EXISTS ][ schema. ] index
      ON { cluster_index_clause
         | table_index_clause
         | bitmap_join_index_clause
         }
    [ USABLE | UNUSABLE ]
    [ { DEFERRED | IMMEDIATE } INVALIDATION ]

#### [CREATE INDEXTYPE](../sqlrf/CREATE-INDEXTYPE.md)

    CREATE [ OR REPLACE ] INDEXTYPE [ IF NOT EXISTS ][ schema. ] indextype
      FOR [ schema. ] operator (parameter_type [, parameter_type ]...)
            [, [ schema. ] operator (parameter_type [, parameter_type ]...)
            ]...
      using_type_clause
      [WITH LOCAL [RANGE] PARTITION ]
      [ storage_table_clause ]

#### [CREATE INMEMORY JOIN GROUP](../sqlrf/index.md)

    CREATE INMEMORY JOIN GROUP [ schema. ] join_group
      ( [ schema. ] table ( column ) , [ schema. ] table ( column )
        [, [ schema. ] table ( column ) ]... )

#### [CREATE JAVA](../sqlrf/CREATE-JAVA.md)

    CREATE [ OR REPLACE ] [ AND { RESOLVE | COMPILE } ] [ NOFORCE ]
      JAVA [ IF NOT EXISTS ] { { SOURCE | RESOURCE } NAMED [ schema. ] primary_name
           | CLASS [ SCHEMA schema ]
           }
      [ SHARING = { METADATA | NONE } ]
      [ invoker_rights_clause ]
      [ RESOLVER ( (match_string [,] { schema_name | - })...) ]
      { USING { BFILE (directory_object_name, server_file_name)
              | { CLOB | BLOB | BFILE } subquery
              | 'key_for_BLOB'
              }
      | AS source_char
      }

#### [CREATE LIBRARY](../sqlrf/CREATE-LIBRARY.md)

    CREATE [ OR REPLACE ]
    [ EDITIONABLE | NONEDITIONABLE ]
    LIBRARY [ IF NOT EXISTS ] plsql_library_source

#### [CREATE LOCKDOWN PROFILE](../sqlrf/index.md)

    CREATE LOCKDOWN PROFILE profile_name

#### [CREATE MATERIALIZED VIEW](../sqlrf/CREATE-MATERIALIZED-VIEW.md)

    CREATE MATERIALIZED VIEW [ IF NOT EXISTS ][ schema. ] materialized_view
      [ OF [ schema. ] object_type ]
      [ ( { scoped_table_ref_constraint
          | column_alias [ENCRYPT [encryption_spec]]
          }
          [, { scoped_table_ref_constraint
             | column_alias [ENCRYPT [encryption_spec]]
             }
          ]...
        )
      ]
      [ DEFAULT COLLATION collation_name ]
      { ON PREBUILT TABLE
        [ { WITH | WITHOUT } REDUCED PRECISION ]
      | physical_properties materialized_view_props
      }
      [ USING INDEX
        [ physical_attributes_clause
        | TABLESPACE tablespace
        ]...
      | USING NO INDEX
      ]
      [ create_mv_refresh ]
      [ evaluation_edition_clause ]
      [ { ENABLE | DISABLE } ON QUERY COMPUTATION ]
      [ query_rewrite_clause ]
    AS subquery

#### [CREATE MATERIALIZED VIEW LOG](../sqlrf/CREATE-MATERIALIZED-VIEW-LOG.md)

    CREATE MATERIALIZED VIEW LOG [ IF NOT EXISTS ] ON [ schema. ] table
      [ physical_attributes_clause
      | TABLESPACE tablespace
      | logging_clause
      | { CACHE | NOCACHE }
      ]...
      [ parallel_clause ]
      [ table_partitioning_clauses ]
      [ WITH [ { OBJECT ID
             | PRIMARY KEY
             | ROWID
             | SEQUENCE
             | COMMIT SCN
             }
               [ { , OBJECT ID
                 | , PRIMARY KEY
                 | , ROWID
                 | , SEQUENCE
                 | , COMMIT SCN
                 }
               ]... ]
        (column [, column ]...)
        [ new_values_clause ]
      ] [ mv_log_purge_clause ] [ for_refresh_clause ]

#### [CREATE MATERIALIZED ZONEMAP](../sqlrf/CREATE-MATERIALIZED-ZONEMAP.md)

    { create_zonemap_on_table | create_zonemap_as_subquery }

#### [CREATE MATERIALIZED ZONEMAP ON TABLE](../sqlrf/CREATE-MATERIALIZED-ZONEMAP.md)

    CREATE MATERIALIZED ZONEMAP [ IF NOT EXISTS ]
      [ schema. ] zonemap_name
      [ zonemap_attributes ]
      [ zonemap_refresh_clause ]
      [ { ENABLE | DISABLE } PRUNING ]
      ON [ schema. ] { table | materialized_view } ( column [, column]... )

#### [CREATE MATERIALIZED ZONEMAP AS SUBQUERY](../sqlrf/CREATE-MATERIALIZED-ZONEMAP.md)

    CREATE MATERIALIZED ZONEMAP [ IF NOT EXISTS ]
      [ schema. ] zonemap_name
      [ zonemap_attributes ]
      [ zonemap_refresh_clause ]
      [ { ENABLE | DISABLE } PRUNING ]
      AS query_block

#### [CREATE OPERATOR](../sqlrf/CREATE-OPERATOR.md)

    CREATE [ OR REPLACE ] OPERATOR
       [ IF NOT EXISTS ][ schema. ] operator binding_clause

#### [CREATE OUTLINE](../sqlrf/CREATE-OUTLINE.md)

    CREATE [ OR REPLACE ]
       [ PUBLIC | PRIVATE ] OUTLINE [ outline ]
       [ FROM [ PUBLIC | PRIVATE ] source_outline ]
       [ FOR CATEGORY category ]
       [ ON statement ]

#### [CREATE PACKAGE](../sqlrf/CREATE-PACKAGE.md)

    CREATE [ OR REPLACE ]
    [ EDITIONABLE | NONEDITIONABLE ]
    PACKAGE [ IF NOT EXISTS ] plsql_package_source

#### [CREATE PACKAGE BODY](../sqlrf/CREATE-PACKAGE-BODY.md)

    CREATE [ OR REPLACE ]
    [ EDITIONABLE | NONEDITIONABLE ]
    PACKAGE BODY [ IF NOT EXISTS ] plsql_package_body_source

#### [CREATE PFILE](../sqlrf/CREATE-PFILE.md)

    CREATE PFILE [= 'pfile_name' ]
       FROM { SPFILE [= 'spfile_name']
            | MEMORY
            }

#### [CREATE PLUGGABLE DATABASE](../sqlrf/CREATE-PLUGGABLE-DATABASE.md)

    CREATE PLUGGABLE DATABASE
      { { pdb_name [ AS APPLICATION CONTAINER ] } | { AS SEED } }
      {  create_pdb_from_seed | create_pdb_clone | create_pdb_from_xml | create_pdb_from_mirror_copy
        | using_snapshot_clause | container_map_clause } pdb_snapshot_clause

#### [CREATE PROCEDURE](../sqlrf/CREATE-PROCEDURE.md)

    CREATE [ OR REPLACE ]
    [ EDITIONABLE | NONEDITIONABLE ]
    PROCEDURE [ IF NOT EXISTS ] plsql_procedure_source

#### [CREATE PROFILE](../sqlrf/CREATE-PROFILE.md)

    CREATE PROFILE profile
      LIMIT { resource_parameters
            | password_parameters
            }...
      [ CONTAINER = { CURRENT | ALL } ]

#### [CREATE RESTORE POINT](../sqlrf/CREATE-RESTORE-POINT.md)

    CREATE [ CLEAN ] RESTORE POINT restore_point
       [ FOR PLUGGABLE DATABASE pdb_name ]
       [ AS OF {TIMESTAMP | SCN} expr ]
       [ PRESERVE
       | GUARANTEE FLASHBACK DATABASE
       ]

#### [CREATE ROLE](../sqlrf/CREATE-ROLE.md)

    CREATE ROLE role
       [ NOT IDENTIFIED
       | IDENTIFIED { BY password
                    | USING [ schema. ] package
                    | EXTERNALLY
                    | GLOBALLY AS ' { domain_name_of_directory_group
                                      | AZURE_ROLE=value
                                      | IAM_GROUP_NAME=value } '
                    }
       ] [ CONTAINER = { CURRENT | ALL } ]

#### [CREATE ROLLBACK SEGMENT](../sqlrf/CREATE-ROLLBACK-SEGMENT.md)

    CREATE [ PUBLIC ] ROLLBACK SEGMENT rollback_segment
      [ TABLESPACE tablespace | storage_clause ]...]

#### [CREATE SCHEMA](../sqlrf/CREATE-SCHEMA.md)

    CREATE SCHEMA AUTHORIZATION schema
       { create_table_statement
       | create_view_statement
       | grant_statement
       }...

#### [CREATE SEQUENCE](../sqlrf/CREATE-SEQUENCE.md)

    CREATE SEQUENCE [ IF NOT EXISTS ] [ schema. ] sequence
       [ SHARING = { METADATA | DATA | NONE } ]
       [ { INCREMENT BY | START WITH } integer
       | { MAXVALUE integer | NOMAXVALUE }
       | { MINVALUE integer | NOMINVALUE }
       | { CYCLE | NOCYCLE }
       | { CACHE integer | NOCACHE }
       | { ORDER | NOORDER }
       | { KEEP | NOKEEP }
       | { SCALE {EXTEND | NOEXTEND} | NOSCALE }
       | { SHARD {EXTEND | NOEXTEND} | NOSHARD }
       | { SESSION | GLOBAL }
       ]...

#### [CREATE SPFILE](../sqlrf/CREATE-SPFILE.md)

    CREATE SPFILE [= 'spfile_name' ]
      FROM { PFILE [= 'pfile_name' ] [ AS COPY ]
           | MEMORY
           }

#### [CREATE SYNONYM](../sqlrf/CREATE-SYNONYM.md)

    CREATE [ OR REPLACE ] [ EDITIONABLE | NONEDITIONABLE ]
      [ PUBLIC ] [ IF NOT EXISTS ] SYNONYM
      [ schema. ] synonym
      [ SHARING = { METADATA | NONE } ]
      FOR [ schema. ] object [ @ dblink ]

#### [CREATE TABLE](../sqlrf/CREATE-TABLE.md)

    CREATE [ { GLOBAL | PRIVATE } TEMPORARY | SHARDED | DUPLICATED |
      [ IMMUTABLE ] BLOCKCHAIN | IMMUTABLE ] TABLE
      [ IF NOT EXISTS ] [ schema. ] table
        [ SHARING = { METADATA | DATA | EXTENDED DATA | NONE } ]
      { relational_table | object_table | XMLType_table }
      [ MEMOPTIMIZE FOR READ ]
      [ MEMOPTIMIZE FOR WRITE ]
      [ PARENT [ schema. ] table ] [ MEMOPTIMIZE FOR READ ]

#### [CREATE TABLESPACE](../sqlrf/CREATE-TABLESPACE.md)

    CREATE
       [ BIGFILE | SMALLFILE ]
       { permanent_tablespace_clause
       | temporary_tablespace_clause
       | undo_tablespace_clause
       }

#### [CREATE TABLESPACE SET](../sqlrf/CREATE-TABLESPACE-SET.md)

    CREATE TABLESPACE SET tablespace_set
      [ IN SHARDSPACE shardspace ]
      [ USING TEMPLATE
        ( { DATAFILE [, file_specification ]... ] permanent_tablespace_attrs )
      ]

#### [CREATE TRIGGER](../sqlrf/CREATE-TRIGGER.md)

    CREATE [ OR REPLACE ]
    [ EDITIONABLE | NONEDITIONABLE ]
    TRIGGER plsql_trigger_source

#### [CREATE TYPE](../sqlrf/CREATE-TYPE.md)

    CREATE [OR REPLACE]
    [ EDITIONABLE | NONEDITIONABLE ]
    TYPE [ IF NOT EXISTS ] plsql_type_source

#### [CREATE TYPE BODY](../sqlrf/CREATE-TYPE-BODY.md)

    CREATE [ OR REPLACE ]
    [ EDITIONABLE | NONEDITIONABLE ]
    TYPE BODY [ IF NOT EXISTS ] plsql_type_body_source

#### [CREATE USER](../sqlrf/CREATE-USER.md)

    CREATE USER [ IF NOT EXISTS ] user
       IDENTIFIED
            { BY password [ [HTTP] DIGEST { ENABLE | DISABLE } ]
            | EXTERNALLY [ AS 'certificate_DN' | AS 'kerberos_principal_name' ]
            | GLOBALLY [ AS ' { directory_DN | { {AZURE_USER | AZURE_ROLE }=value}
                               | { { IAM_GROUP_NAME | IAM_PRINCIPAL_NAME }=value}
                              }'
            ]
            }
       | NO AUTHENTICATION
       [ DEFAULT COLLATION collation_name
       | DEFAULT TABLESPACE tablespace
       | [ LOCAL ] TEMPORARY TABLESPACE { tablespace | tablespace_group_name }
       | { QUOTA { size_clause | UNLIMITED } ON tablespace }...
       | PROFILE profile
       | PASSWORD EXPIRE
       | ACCOUNT { LOCK | UNLOCK }
         [ DEFAULT TABLESPACE tablespace
         | TEMPORARY TABLESPACE
              { tablespace | tablespace_group_name }
         | { QUOTA { size_clause | UNLIMITED } ON tablespace }...
         | PROFILE profile
         | PASSWORD EXPIRE
         | ACCOUNT { LOCK | UNLOCK }
         | ENABLE EDITIONS
         | CONTAINER = { CURRENT | ALL }
         ]...
      ]

#### [CREATE VIEW](../sqlrf/CREATE-VIEW.md)

    CREATE [OR REPLACE]
      [[NO] FORCE]
      [ EDITIONING | EDITIONABLE [ EDITIONING ] | NONEDITIONABLE ]
      VIEW [ IF NOT EXISTS ] [schema.] view
      [ SHARING = { METADATA | DATA | EXTENDED DATA | NONE } ]
      [ ( { alias [ VISIBLE | INVISIBLE ] [ inline_constraint... ]
          | out_of_line_constraint
          }
            [, { alias [ VISIBLE | INVISIBLE ] [ inline_constraint...]
               | out_of_line_constraint
               }
            ]
        )
      | object_view_clause
      | XMLType_view_clause
      ]
      [ DEFAULT COLLATION collation_name ]
      [ BEQUEATH { CURRENT_USER | DEFINER } ]
      AS subquery [ subquery_restriction_clause ]
      [ CONTAINER_MAP | CONTAINERS_DEFAULT ]

#### [DELETE](../sqlrf/DELETE.md)

    DELETE [ hint ]
       [ FROM ]
       { dml_table_expression_clause
       | ONLY (dml_table_expression_clause)
       } [ t_alias ]
         [ where_clause ]
         [ returning_clause ]
         [error_logging_clause]

#### [DISASSOCIATE STATISTICS](../sqlrf/DISASSOCIATE-STATISTICS.md)

    DISASSOCIATE STATISTICS FROM
       { COLUMNS [ schema. ]table.column
                   [, [ schema. ]table.column ]...
       | FUNCTIONS [ schema. ]function
                     [, [ schema. ]function ]...
       | PACKAGES [ schema. ]package
                    [, [ schema. ]package ]...
       | TYPES [ schema. ]type
                 [, [ schema. ]type ]...
       | INDEXES [ schema. ]index
                   [, [ schema. ]index ]...
       | INDEXTYPES [ schema. ]indextype
                      [, [ schema. ]indextype ]...
       }
       [ FORCE ]

#### [DROP ANALYTIC VIEW](../sqlrf/DROP-ANALYTIC-VIEW.md)

    DROP ANALYTIC VIEW [ IF EXISTS ][ schema. ] analytic_view_name

#### [DROP ATTRIBUTE DIMENSION](../sqlrf/DROP-ATTRIBUTE-DIMENSION.md)

    DROP ATTRIBUTE DIMENSION [ IF EXISTS ][ schema. ] attr_dimension_name

#### [DROP AUDIT POLICY](../sqlrf/DROP-AUDIT-POLICY-Unified-Auditing.md)

    DROP AUDIT POLICY policy

#### [DROP CLUSTER](../sqlrf/DROP-CLUSTER.md)

    DROP CLUSTER [ IF EXISTS ][ schema. ] cluster
       [ INCLUDING TABLES [ CASCADE CONSTRAINTS ] ]

#### [DROP CONTEXT](../sqlrf/DROP-CONTEXT.md)

    DROP CONTEXT namespace

#### [DROP DATABASE](../sqlrf/DROP-DATABASE.md)

    DROP DATABASE

#### [DROP DATABASE LINK](../sqlrf/DROP-DATABASE-LINK.md)

    DROP [ PUBLIC ] DATABASE LINK [ IF EXISTS ] dblink

#### [DROP DIMENSION](../sqlrf/DROP-DIMENSION.md)

    DROP DIMENSION [ schema. ] dimension

#### [DROP DIRECTORY](../sqlrf/DROP-DIRECTORY.md)

    DROP DIRECTORY [ IF EXISTS ] directory_name

#### [DROP DISKGROUP](../sqlrf/DROP-DISKGROUP.md)

    DROP DISKGROUP diskgroup_name
       [  FORCE INCLUDING CONTENTS
       | { INCLUDING | EXCLUDING } CONTENTS
       ]

#### [DROP EDITION](../sqlrf/DROP-EDITION.md)

    DROP EDITION [ IF EXISTS ] edition [CASCADE]

#### [DROP FLASHBACK ARCHIVE](../sqlrf/DROP-FLASHBACK-ARCHIVE.md)

    DROP FLASHBACK ARCHIVE flashback_archive

#### [DROP FUNCTION](../sqlrf/DROP-FUNCTION.md)

    DROP FUNCTION [ IF EXISTS ][ schema. ] function_name

#### [DROP HIERARCHY](../sqlrf/DROP-HIERARCHY.md)

    DROP HIERARCHY [ IF EXISTS ][ schema. ] hierarchy_name

#### [DROP INDEX](../sqlrf/DROP-INDEX.md)

    DROP INDEX [ IF EXISTS ][ schema. ] index [ ONLINE ]
                [ FORCE ] [ { DEFERRED | IMMEDIATE } INVALIDATION ]

#### [DROP INDEXTYPE](../sqlrf/DROP-INDEXTYPE.md)

    DROP INDEXTYPE [ IF EXISTS ][ schema. ] indextype [ FORCE ]

#### [DROP INMEMORY JOIN GROUP](../sqlrf/index.md)

    DROP INMEMORY JOIN GROUP [ schema. ] join_group

#### [DROP JAVA](../sqlrf/DROP-JAVA.md)

    DROP JAVA { SOURCE | CLASS | RESOURCE }
      [ IF EXISTS ][ schema. ] object_name

#### [DROP LIBRARY](../sqlrf/DROP-LIBRARY.md)

    DROP LIBRARY [ IF EXISTS ] library_name

#### [DROP LOCKDOWN PROFILE](../sqlrf/index.md)

    DROP LOCKDOWN PROFILE profile_name

#### [DROP MATERIALIZED VIEW](../sqlrf/DROP-MATERIALIZED-VIEW.md)

    DROP MATERIALIZED VIEW [ IF EXISTS ][ schema. ] materialized_view
       [ PRESERVE TABLE ]

#### [DROP MATERIALIZED VIEW LOG](../sqlrf/DROP-MATERIALIZED-VIEW-LOG.md)

    DROP MATERIALIZED VIEW LOG ON [ IF EXISTS ][ schema. ] table

#### [DROP MATERIALIZED ZONEMAP](../sqlrf/DROP-MATERIALIZED-ZONEMAP.md)

    DROP MATERIALIZED ZONEMAP [ IF EXISTS ][ schema. ] zonemap_name

#### [DROP OPERATOR](../sqlrf/DROP-OPERATOR.md)

    DROP OPERATOR [ IF EXISTS ][ schema. ] operator [ FORCE ]

#### [DROP OUTLINE](../sqlrf/DROP-OUTLINE.md)

    DROP OUTLINE outline

#### [DROP PACKAGE](../sqlrf/DROP-PACKAGE.md)

    DROP PACKAGE [ BODY ] [ IF EXISTS ][ schema. ] package

#### [DROP PLUGGABLE DATABASE](../sqlrf/DROP-PLUGGABLE-DATABASE.md)

    DROP PLUGGABLE DATABASE pdb_name
      [ { KEEP | INCLUDING } DATAFILES ]

#### [DROP PROCEDURE](../sqlrf/DROP-PROCEDURE.md)

    DROP PROCEDURE [ IF EXISTS ][ schema. ] procedure

#### [DROP PROFILE](../sqlrf/DROP-PROFILE.md)

    DROP PROFILE profile [ CASCADE ]

#### [DROP RESTORE POINT](../sqlrf/DROP-RESTORE-POINT.md)

    DROP RESTORE POINT restore_point [ FOR PLUGGABLE DATABASE pdb_name ]

#### [DROP ROLE](../sqlrf/DROP-ROLE.md)

    DROP ROLE role

#### [DROP ROLLBACK SEGMENT](../sqlrf/DROP-ROLLBACK-SEGMENT.md)

    DROP ROLLBACK SEGMENT rollback_segment

#### [DROP SEQUENCE](../sqlrf/DROP-SEQUENCE.md)

    DROP SEQUENCE [ IF EXISTS ][ schema. ] sequence_name

#### [DROP SYNONYM](../sqlrf/DROP-SYNONYM.md)

    DROP [PUBLIC] SYNONYM [ IF EXISTS ][ schema. ] synonym [FORCE]

#### [DROP TABLE](../sqlrf/DROP-TABLE.md)

    DROP TABLE [ schema. ] table
      [ CASCADE CONSTRAINTS ] [ PURGE ]

#### [DROP TABLESPACE](../sqlrf/DROP-TABLESPACE.md)

    DROP TABLESPACE [ IF EXISTS ] tablespace
      [ { DROP | KEEP } QUOTA ]
      [ INCLUDING CONTENTS [ { AND | KEEP } DATAFILES ] [ CASCADE CONSTRAINTS ] ]


#### [DROP TABLESPACE SET](../sqlrf/DROP-TABLESPACE-SET.md)

    DROP TABLESPACE SET tablespace_set
       [ { DROP | KEEP } QUOTA ]
       [ INCLUDING CONTENTS [ { AND | KEEP } DATAFILES ] [ CASCADE CONSTRAINTS ] ]


#### [DROP TRIGGER](../sqlrf/DROP-TRIGGER.md)

    DROP TRIGGER [ IF EXISTS ][ schema. ] trigger

#### [DROP TYPE](../sqlrf/DROP-TYPE.md)

    DROP TYPE [ IF EXISTS ][ schema. ] type_name [ FORCE | VALIDATE ]

#### [DROP TYPE BODY](../sqlrf/DROP-TYPE-BODY.md)

    DROP TYPE BODY [ IF EXISTS ][ schema. ] type_name

#### [DROP USER](../sqlrf/DROP-USER.md)

    DROP USER [ IF EXISTS ] user [ CASCADE ]

#### [DROP VIEW](../sqlrf/DROP-VIEW.md)

    DROP VIEW [ IF EXISTS ][ schema. ] view [ CASCADE CONSTRAINTS ]

#### [EXPLAIN PLAN](../sqlrf/EXPLAIN-PLAN.md)

    EXPLAIN PLAN
       [ SET STATEMENT_ID = string ]
       [ INTO [ schema. ] table [ @ dblink ] ]
    FOR statement

#### [FLASHBACK DATABASE](../sqlrf/FLASHBACK-DATABASE.md)

    FLASHBACK [ STANDBY ] [ PLUGGABLE ] DATABASE [ database ]
       { TO { { SCN | TIMESTAMP } expr
            | RESTORE POINT restore_point
            }
       }
       | { TO BEFORE { { SCN | TIMESTAMP } expr
                     | RESETLOGS
                     }
       }

#### [FLASHBACK TABLE](../sqlrf/FLASHBACK-TABLE.md)

    FLASHBACK TABLE
       [ schema. ] table
         [, [ schema. ] table ]...
       TO { { { SCN | TIMESTAMP } expr
            | RESTORE POINT restore_point
            } [ { ENABLE | DISABLE } TRIGGERS ]
          | BEFORE DROP [ RENAME TO table ]
          }

#### [GRANT](../sqlrf/GRANT.md)

    GRANT
      { { { grant_system_privileges | grant_object_privileges }
          [ CONTAINER = { CURRENT | ALL } ] }
      | grant_roles_to_programs
      }

#### [INSERT](../sqlrf/INSERT.md)

    INSERT [ hint ]
       { single_table_insert | multi_table_insert }

#### [LOCK TABLE](../sqlrf/LOCK-TABLE.md)

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
       ]

#### [MERGE](../sqlrf/MERGE.md)

    MERGE [ hint ]
       INTO [ schema. ] { table | view } [ t_alias ]
       USING { [ schema. ] { table | view }
             | ( subquery )
             } [ t_alias ]
       ON ( condition )
       [ merge_update_clause ]
       [ merge_insert_clause ]
       [ error_logging_clause ]

#### [NOAUDIT (Traditional Auditing)](../sqlrf/NOAUDIT-Traditional-Auditing.md)

    NOAUDIT
       { audit_operation_clause [ auditing_by_clause ]
       | audit_schema_object_clause
       | NETWORK
       | DIRECT_PATH LOAD [ auditing_by_clause ]
       }
       [ WHENEVER [ NOT ] SUCCESSFUL ]
       [ CONTAINER = { CURRENT | ALL } ]

#### [NOAUDIT (Unified Auditing)](../sqlrf/NOAUDIT-Unified-Auditing.md)

    NOAUDIT
      { POLICY policy [ { BY user [, user]... } | by_users_with_roles ]
        [ WHENEVER  [ NOT ]  SUCCESSFUL ] }
      |
      { CONTEXT NAMESPACE namespace ATTRIBUTES attribute [, attribute ]...
          [, CONTEXT NAMESPACE namespace ATTRIBUTES attribute [, attribute ]... ]...
        [ BY user [, user]... ]
      }

#### [PURGE](../sqlrf/PURGE.md)

    PURGE
      { TABLE table
      | INDEX index
      | TABLESPACE tablespace [ USER username ]
      | TABLESPACE SET tablespace_set [ USER username ]
      | RECYCLEBIN
      | DBA_RECYCLEBIN
      }

#### [RENAME](../sqlrf/RENAME.md)

    RENAME old_name TO new_name

#### [REVOKE](../sqlrf/REVOKE.md)

    REVOKE
      { { revoke_system_privileges | revoke_object_privileges }
        [ CONTAINER = { CURRENT | ALL } ] }
      | revoke_roles_from_programs

#### [ROLLBACK](../sqlrf/ROLLBACK.md)

    ROLLBACK [ WORK ]
       [ TO [ SAVEPOINT ] savepoint
       | FORCE string
       ]

#### [SAVEPOINT](../sqlrf/SAVEPOINT.md)

    SAVEPOINT savepoint

#### [SELECT](../sqlrf/SELECT.md)

    subquery [ for_update_clause ]

#### [SET CONSTRAINT\[S\]](../sqlrf/SET-CONSTRAINTS.md)

    SET { CONSTRAINT | CONSTRAINTS }
        { constraint [, constraint ]...
        | ALL
        }
        { IMMEDIATE | DEFERRED }

#### [SET ROLE](../sqlrf/SET-ROLE.md)

    SET ROLE
       { role [ IDENTIFIED BY password ]
         [, role [ IDENTIFIED BY password ] ]...
       | ALL [ EXCEPT role [, role ]... ]
       | NONE
       }

#### [SET TRANSACTION](../sqlrf/SET-TRANSACTION.md)

    SET TRANSACTION
       { { READ { ONLY | WRITE }
         | ISOLATION LEVEL
           { SERIALIZABLE | READ COMMITTED }
         | USE ROLLBACK SEGMENT rollback_segment
         } [ NAME string ]
       | NAME string
       }

#### [TRUNCATE CLUSTER](../sqlrf/TRUNCATE-CLUSTER.md)

    TRUNCATE CLUSTER [schema.] cluster
      [ {DROP | REUSE} STORAGE ]

#### [TRUNCATE TABLE](../sqlrf/TRUNCATE-TABLE.md)

    TRUNCATE TABLE [schema.] table
      [ {PRESERVE | PURGE} MATERIALIZED VIEW LOG ]
      [ {DROP [ ALL ] | REUSE} STORAGE ] [ CASCADE ]

#### [UPDATE](../sqlrf/UPDATE.md)

    UPDATE [ hint ]
       { dml_table_expression_clause
       | ONLY (dml_table_expression_clause)
       } [ t_alias ]
       update_set_clause
       [ where_clause ]
       [ returning_clause ]
       [error_logging_clause]
