Describes all the tables in the database using DBA_TABLES or ALL_TABLES view depending on role at runtime. A client requires SQL Administrator or SQL Developer role to invoke this service.

### Request

Supported Media Types

- application/json

Query Parameters

- limit(optional): integer(int32)
  The maximum number of records to return.
- q(optional): string
  Filtering is the process of limiting a collection resource by using a per-request dynamic filter definition across multiple page resources, where each page contains a subset of items found in the complete collection. Filtering enables efficient traversal of large collections.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

All tables in the database.

Body ()

Root Schema : DatabaseObjectsTables

Type: `object`

Show Source

- count(optional): integer
  Total number of records in the current response.
- hasMore(optional): boolean
  Indicates if there are more records to be retrieved.
- items(optional): array items
- limit(optional): integer
  The actual page size limit on number of records applied by the server.
- links(optional): array links
- offset(optional): integer
  The actual index from which the item resources are returned.

<!-- -->

    {
        "type":"object",
        "properties":{
            "items":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/DatabaseObjectsTablesItem"
                }
            },
            "hasMore":{
                "type":"boolean",
                "description":"Indicates if there are more records to be retrieved."
            },
            "limit":{
                "type":"integer",
                "description":"The actual page size limit on number of records applied by the server."
            },
            "offset":{
                "type":"integer",
                "description":"The actual index from which the item resources are returned."
            },
            "count":{
                "type":"integer",
                "description":"Total number of records in the current response."
            },
            "links":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/LinkRelation"
                }
            }
        }
    }

Nested Schema : items

Type: `array`

Show Source

- Array of: object DatabaseObjectsTablesItem
  This object describes a relational table in the database.

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/DatabaseObjectsTablesItem"
        }
    }

Nested Schema : links

Type: `array`

Show Source

- Array of: object LinkRelation

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/LinkRelation"
        }
    }

Nested Schema : DatabaseObjectsTablesItem

Type: `object`

This object describes a relational table in the database.

Show Source

- activity_tracking(optional): string
  Indicates whether Heat Map tracking is enabled on the table.
- admit_null(optional): string
  Indicates whether the table admits null CON_ID data (YES) or not (NO).
- avg_row_len(optional): integer
  Average length of a row in the table (in bytes).
- avg_space(optional): integer
  Average amount of free space, in bytes, in a data block allocated to the table.
- avg_space_freelist_blocks(optional): integer
  Average freespace of all blocks on a freelist.
- backed_up(optional): string
  Indicates whether the table has been backed up since the last modification (Y) or not (N).
- blocks(optional): integer
  Number of used data blocks in the table.
- buffer_pool(optional): string
  Buffer pool for the table.
- cache(optional): string
  Indicates whether the table is to be cached in the buffer cache (Y) or not (N).
- cell_flash_cache(optional): string
  Cell flash cache hint to be used for table blocks.
- cellmemory(optional): string
  The value for columnar compression in the storage cell flash cache.
- chain_cnt(optional): integer
  Number of rows in the table that are chained from one data block to another, or which have migrated to a new block, requiring a link to preserve the old ROWID.
- cluster_name(optional): string
  Name of the cluster, if any, to which the table belongs.
- cluster_owner(optional): string
  Owner of the cluster, if any, to which the table belongs.
- clustering(optional): string
  Indicates whether the table has the attribute clustering clause (YES) or not (NO).
- compress_for(optional): string
  Default compression for what kind of operations:.
- compression(optional): string
  Indicates whether table compression is enabled (ENABLED) or not (DISABLED); NULL for partitioned tables.
- container_data(optional): string
  Indicates whether the table contains container-specific data.
- container_map(optional): string
  Indicates whether the table is enabled for use with the container_map database property (YES) or not (NO).
- container_map_object(optional): string
  Indicates whether the table is used as the value of the container_map database property (YES) or not (NO).
- containers_default(optional): string
  Indicates whether the table is enabled for CONTAINERS() by default (YES) or not (NO).
- data_link_dml_enabled(optional): string
  Indicates whether DML is permitted on the Data Link table (YES) or not (NO).
- default_collation(optional): string
  Default collation for the table.
- degree(optional): string
  Number of threads per instance for scanning the table, or DEFAULT.
- dependencies(optional): string
  Indicates whether row-level dependency tracking is enabled (ENABLED) or disabled (DISABLED).
- dml_timestamp(optional): string
  Modification time, creation time, or both for Automatic Data Optimization.
- dropped(optional): string
  ndicates whether the table has been dropped and is in the recycle bin (YES) or not (NO); NULL for partitioned tables. This view does not return the names of tables that have been dropped.
- duplicated(optional): string
  Indicates whether this object is duplicated on this shard (Y) or not (N).
- duration(optional): string
  Indicates the duration of a temporary table.
- empty_blocks(optional): integer
  Number of empty (never used) data blocks in the table. This column is populated only if you collect statistics on the table using the DBMS_STATS package.
- extended_data_link(optional): string
  Indicates whether the table is enabled for fetching an extended data link from the root (YES) or not (NO).
- external(optional): string
  Indicates whether the table is an external table (YES) or not (NO).
- flash_cache(optional): string
  Database Smart Flash Cache hint to be used for table blocks.
- freelist_groups(optional): integer
  Number of freelist groups allocated to the segment; NULL for partitioned tables.
- freelists(optional): integer
  Number of process freelists allocated to the segment; NULL for partitioned tables.
- global_stats(optional): string
  GLOBAL_STATS will be YES if statistics are gathered or incrementally maintained, otherwise it will be NO.
- has_identity(optional): string
  Indicates whether the table has an identity column (YES) or not (NO).
- has_sensitive_column(optional): string
  Indicates whether the table has one or more sensitive columns (YES) or not (NO).
- hybrid(optional): string
  Indicates whether the table is a hybrid partitioned table (YES) or not (NO). A hybrid partitioned table can contain a mixture of partitions stored in segments and partitions stored externally.
- ini_trans(optional): integer
  Initial number of transactions; NULL for partitioned tables.
- initial_extent(optional): integer
  Size of the initial extent (in bytes); NULL for partitioned tables.
- inmemory(optional): string
  Indicates whether the In-Memory Column Store (IM column store) is enabled (ENABLED) or disabled (DISABLED) for this table
- inmemory_compression(optional): string
  Indicates the compression level for the IM column store.
- inmemory_distribute(optional): string
  Indicates how the IM column store is distributed in an Oracle Real Application Clusters (Oracle RAC) environment.
- inmemory_duplicate(optional): string
  Indicates the duplicate setting for the IM column store in an Oracle RAC environment.
- inmemory_priority(optional): string
  Indicates the priority for In-Memory Column Store (IM column store) population.
- inmemory_service(optional): string
  Indicates how the IM column store is populated on various instances.
- inmemory_service_name(optional): string
  Indicates the service name for the service on which the IM column store should be populated. This column has a value only when the corresponding INMEMORY_SERVICE is USER_DEFINED. In all other cases, this column is null.
- instances(optional): string
  Number of instances across which the table is to be scanned, or DEFAULT.
- iot_name(optional): string
  Name of the index-organized table, if any, to which the overflow or mapping table entry belongs. If the IOT_TYPE column is not NULL, then this column contains the base table name.
- iot_type(optional): string
  If the table is an index-organized table, then IOT_TYPE is IOT, IOT_OVERFLOW, or IOT_MAPPING. If the table is not an index-organized table, then IOT_TYPE is NULL.
- last_analyzed(optional): string
  Date on which this table was most recently analyzed.
- links(optional): array links
- logging(optional): string
  Indicates whether or not changes to the table are logged; YES, NO, or NULL for partitioned tables.
- logical_replication(optional): string
  Indicates whether the table is enabled for logical replication (ENABLED) or not (DISABLED). This setting is ignored if database-wide column data supplemental logging is enabled.
- max_extents(optional): integer
  Maximum number of extents allowed in the segment; NULL for partitioned tables.
- max_trans(optional): integer
  Maximum number of transactions; NULL for partitioned tables.
- memoptimize_read(optional): string
  Indicates whether the table is enabled for Fast Key Based Access (ENABLED) or not (DISABLED).
- min_extents(optional): integer
  Minimum number of extents allowed in the segment; NULL for partitioned tables.
- monitoring(optional): string
  Indicates whether the table has the MONITORING attribute set (YES) or not (NO).
- nested(optional): string
  Indicates whether the table is a nested table (YES) or not (NO).
- next_extent(optional): integer
  Size of secondary extents (in bytes); NULL for partitioned tables.
- num_freelist_blocks(optional): integer
  Number of blocks on the freelist.
- num_rows(optional): integer
  Number of rows in the table.
- owner(optional): string
  Owner of the table.
- partitioned(optional): string
  Indicates whether the table is partitioned (YES) or not (NO).
- pct_free(optional): integer
  Minimum percentage of free space in a block; NULL for partitioned tables.
- pct_increase(optional): integer
  Percentage increase in extent size; NULL for partitioned tables.
- pct_used(optional): integer
  Minimum percentage of used space in a block; NULL for partitioned tables.
- read_only(optional): string
  Indicates whether the table segment is READ-ONLY or not.
- result_cache(optional): string
  Result cache mode annotation for the table.
- row_movement(optional): string
  Indicates whether partitioned row movement is enabled (ENABLED) or disabled (DISABLED).
- sample_size(optional): integer
  Sample size used in analyzing this table.
- secondary(optional): string
  Indicates whether the table is a secondary object created by the ODCIIndexCreate method of the Oracle Data Cartridge (Y) or not (N).
- segment_created(optional): string
  Indicates whether the table segment is created.
- sharded(optional): string
  Indicates whether this object is sharded (Y) or not (N).
- skip_corrupt(optional): string
  Indicates whether Oracle Database ignores blocks marked corrupt during table and index scans (ENABLED) or raises an error (DISABLED). To enable this feature, run the DBMS_REPAIR.SKIP_CORRUPT_BLOCKS procedure.
- status(optional): string
  If a previous DROP TABLE operation failed, indicates whether the table is unusable (UNUSABLE) or valid (VALID).
- table_lock(optional): string
  Indicates whether table locking is enabled (ENABLED) or disabled (DISABLED).
- table_name(optional): string
  Name of the table.
- tablespace_name(optional): string
  Name of the tablespace containing the table; NULL for partitioned, temporary, and index-organized tables.
- temporary(optional): string
  Indicates whether the table is temporary (Y) or not (N).
- user_stats(optional): string
  Indicates whether statistics were entered directly by the user (YES) or not (NO).

<!-- -->

    {
        "type":"object",
        "description":"This object describes a relational table in the database.",
        "properties":{
            "owner":{
                "type":"string",
                "description":"Owner of the table."
            },
            "table_name":{
                "type":"string",
                "description":"Name of the table."
            },
            "tablespace_name":{
                "type":"string",
                "description":"Name of the tablespace containing the table; NULL for partitioned, temporary, and index-organized tables."
            },
            "cluster_name":{
                "type":"string",
                "description":"Name of the cluster, if any, to which the table belongs."
            },
            "iot_name":{
                "type":"string",
                "description":"Name of the index-organized table, if any, to which the overflow or mapping table entry belongs. If the IOT_TYPE column is not NULL, then this column contains the base table name."
            },
            "status":{
                "type":"string",
                "description":"If a previous DROP TABLE operation failed, indicates whether the table is unusable (UNUSABLE) or valid (VALID)."
            },
            "pct_free":{
                "type":"integer",
                "description":"Minimum percentage of free space in a block; NULL for partitioned tables."
            },
            "pct_used":{
                "type":"integer",
                "description":"Minimum percentage of used space in a block; NULL for partitioned tables."
            },
            "ini_trans":{
                "type":"integer",
                "description":"Initial number of transactions; NULL for partitioned tables."
            },
            "max_trans":{
                "type":"integer",
                "description":"Maximum number of transactions; NULL for partitioned tables."
            },
            "initial_extent":{
                "type":"integer",
                "description":"Size of the initial extent (in bytes); NULL for partitioned tables."
            },
            "next_extent":{
                "type":"integer",
                "description":"Size of secondary extents (in bytes); NULL for partitioned tables."
            },
            "min_extents":{
                "type":"integer",
                "description":"Minimum number of extents allowed in the segment; NULL for partitioned tables."
            },
            "max_extents":{
                "type":"integer",
                "description":"Maximum number of extents allowed in the segment; NULL for partitioned tables."
            },
            "pct_increase":{
                "type":"integer",
                "description":"Percentage increase in extent size; NULL for partitioned tables."
            },
            "freelists":{
                "type":"integer",
                "description":"Number of process freelists allocated to the segment; NULL for partitioned tables."
            },
            "freelist_groups":{
                "type":"integer",
                "description":"Number of freelist groups allocated to the segment; NULL for partitioned tables."
            },
            "logging":{
                "type":"string",
                "description":"Indicates whether or not changes to the table are logged; YES, NO, or NULL for partitioned tables."
            },
            "backed_up":{
                "type":"string",
                "description":"Indicates whether the table has been backed up since the last modification (Y) or not (N)."
            },
            "num_rows":{
                "type":"integer",
                "description":"Number of rows in the table."
            },
            "blocks":{
                "type":"integer",
                "description":"Number of used data blocks in the table."
            },
            "empty_blocks":{
                "type":"integer",
                "description":"Number of empty (never used) data blocks in the table. This column is populated only if you collect statistics on the table using the DBMS_STATS package."
            },
            "avg_space":{
                "type":"integer",
                "description":"Average amount of free space, in bytes, in a data block allocated to the table."
            },
            "chain_cnt":{
                "type":"integer",
                "description":"Number of rows in the table that are chained from one data block to another, or which have migrated to a new block, requiring a link to preserve the old ROWID."
            },
            "avg_row_len":{
                "type":"integer",
                "description":"Average length of a row in the table (in bytes)."
            },
            "avg_space_freelist_blocks":{
                "type":"integer",
                "description":"Average freespace of all blocks on a freelist."
            },
            "num_freelist_blocks":{
                "type":"integer",
                "description":"Number of blocks on the freelist."
            },
            "degree":{
                "type":"string",
                "description":"Number of threads per instance for scanning the table, or DEFAULT."
            },
            "instances":{
                "type":"string",
                "description":"Number of instances across which the table is to be scanned, or DEFAULT."
            },
            "cache":{
                "type":"string",
                "description":"Indicates whether the table is to be cached in the buffer cache (Y) or not (N)."
            },
            "table_lock":{
                "type":"string",
                "description":"Indicates whether table locking is enabled (ENABLED) or disabled (DISABLED)."
            },
            "sample_size":{
                "type":"integer",
                "description":"Sample size used in analyzing this table."
            },
            "last_analyzed":{
                "type":"string",
                "description":"Date on which this table was most recently analyzed."
            },
            "partitioned":{
                "type":"string",
                "description":"Indicates whether the table is partitioned (YES) or not (NO)."
            },
            "iot_type":{
                "type":"string",
                "description":"If the table is an index-organized table, then IOT_TYPE is IOT, IOT_OVERFLOW, or IOT_MAPPING. If the table is not an index-organized table, then IOT_TYPE is NULL."
            },
            "temporary":{
                "type":"string",
                "description":"Indicates whether the table is temporary (Y) or not (N)."
            },
            "secondary":{
                "type":"string",
                "description":"Indicates whether the table is a secondary object created by the ODCIIndexCreate method of the Oracle Data Cartridge (Y) or not (N)."
            },
            "nested":{
                "type":"string",
                "description":"Indicates whether the table is a nested table (YES) or not (NO)."
            },
            "buffer_pool":{
                "type":"string",
                "description":"Buffer pool for the table."
            },
            "flash_cache":{
                "type":"string",
                "description":"Database Smart Flash Cache hint to be used for table blocks."
            },
            "cell_flash_cache":{
                "type":"string",
                "description":"Cell flash cache hint to be used for table blocks."
            },
            "row_movement":{
                "type":"string",
                "description":"Indicates whether partitioned row movement is enabled (ENABLED) or disabled (DISABLED)."
            },
            "global_stats":{
                "type":"string",
                "description":"GLOBAL_STATS will be YES if statistics are gathered or incrementally maintained, otherwise it will be NO."
            },
            "user_stats":{
                "type":"string",
                "description":"Indicates whether statistics were entered directly by the user (YES) or not (NO)."
            },
            "duration":{
                "type":"string",
                "description":"Indicates the duration of a temporary table."
            },
            "skip_corrupt":{
                "type":"string",
                "description":"Indicates whether Oracle Database ignores blocks marked corrupt during table and index scans (ENABLED) or raises an error (DISABLED). To enable this feature, run the DBMS_REPAIR.SKIP_CORRUPT_BLOCKS procedure."
            },
            "monitoring":{
                "type":"string",
                "description":"Indicates whether the table has the MONITORING attribute set (YES) or not (NO)."
            },
            "cluster_owner":{
                "type":"string",
                "description":"Owner of the cluster, if any, to which the table belongs."
            },
            "dependencies":{
                "type":"string",
                "description":"Indicates whether row-level dependency tracking is enabled (ENABLED) or disabled (DISABLED)."
            },
            "compression":{
                "type":"string",
                "description":"Indicates whether table compression is enabled (ENABLED) or not (DISABLED); NULL for partitioned tables."
            },
            "compress_for":{
                "type":"string",
                "description":"Default compression for what kind of operations:."
            },
            "dropped":{
                "type":"string",
                "description":"ndicates whether the table has been dropped and is in the recycle bin (YES) or not (NO); NULL for partitioned tables. This view does not return the names of tables that have been dropped."
            },
            "read_only":{
                "type":"string",
                "description":"Indicates whether the table segment is READ-ONLY or not."
            },
            "segment_created":{
                "type":"string",
                "description":"Indicates whether the table segment is created."
            },
            "result_cache":{
                "type":"string",
                "description":"Result cache mode annotation for the table."
            },
            "clustering":{
                "type":"string",
                "description":"Indicates whether the table has the attribute clustering clause (YES) or not (NO)."
            },
            "activity_tracking":{
                "type":"string",
                "description":"Indicates whether Heat Map tracking is enabled on the table."
            },
            "dml_timestamp":{
                "type":"string",
                "description":"Modification time, creation time, or both for Automatic Data Optimization."
            },
            "has_identity":{
                "type":"string",
                "description":"Indicates whether the table has an identity column (YES) or not (NO)."
            },
            "container_data":{
                "type":"string",
                "description":"Indicates whether the table contains container-specific data."
            },
            "inmemory":{
                "type":"string",
                "description":"Indicates whether the In-Memory Column Store (IM column store) is enabled (ENABLED) or disabled (DISABLED) for this table"
            },
            "inmemory_priority":{
                "type":"string",
                "description":"Indicates the priority for In-Memory Column Store (IM column store) population."
            },
            "inmemory_distribute":{
                "type":"string",
                "description":"Indicates how the IM column store is distributed in an Oracle Real Application Clusters (Oracle RAC) environment."
            },
            "inmemory_compression":{
                "type":"string",
                "description":"Indicates the compression level for the IM column store."
            },
            "inmemory_duplicate":{
                "type":"string",
                "description":"Indicates the duplicate setting for the IM column store in an Oracle RAC environment."
            },
            "default_collation":{
                "type":"string",
                "description":"Default collation for the table."
            },
            "duplicated":{
                "type":"string",
                "description":"Indicates whether this object is duplicated on this shard (Y) or not (N)."
            },
            "sharded":{
                "type":"string",
                "description":"Indicates whether this object is sharded (Y) or not (N)."
            },
            "external":{
                "type":"string",
                "description":"Indicates whether the table is an external table (YES) or not (NO)."
            },
            "hybrid":{
                "type":"string",
                "description":"Indicates whether the table is a hybrid partitioned table (YES) or not (NO). A hybrid partitioned table can contain a mixture of partitions stored in segments and partitions stored externally."
            },
            "cellmemory":{
                "type":"string",
                "description":"The value for columnar compression in the storage cell flash cache."
            },
            "containers_default":{
                "type":"string",
                "description":"Indicates whether the table is enabled for CONTAINERS() by default (YES) or not (NO)."
            },
            "container_map":{
                "type":"string",
                "description":"Indicates whether the table is enabled for use with the container_map database property (YES) or not (NO)."
            },
            "extended_data_link":{
                "type":"string",
                "description":"Indicates whether the table is enabled for fetching an extended data link from the root (YES) or not (NO)."
            },
            "inmemory_service":{
                "type":"string",
                "description":"Indicates how the IM column store is populated on various instances."
            },
            "inmemory_service_name":{
                "type":"string",
                "description":"Indicates the service name for the service on which the IM column store should be populated. This column has a value only when the corresponding INMEMORY_SERVICE is USER_DEFINED. In all other cases, this column is null."
            },
            "container_map_object":{
                "type":"string",
                "description":"Indicates whether the table is used as the value of the container_map database property (YES) or not (NO)."
            },
            "memoptimize_read":{
                "type":"string",
                "description":"Indicates whether the table is enabled for Fast Key Based Access (ENABLED) or not (DISABLED)."
            },
            "has_sensitive_column":{
                "type":"string",
                "description":"Indicates whether the table has one or more sensitive columns (YES) or not (NO)."
            },
            "admit_null":{
                "type":"string",
                "description":"Indicates whether the table admits null CON_ID data (YES) or not (NO)."
            },
            "data_link_dml_enabled":{
                "type":"string",
                "description":"Indicates whether DML is permitted on the Data Link table (YES) or not (NO)."
            },
            "logical_replication":{
                "type":"string",
                "description":"Indicates whether the table is enabled for logical replication (ENABLED) or not (DISABLED). This setting is ignored if database-wide column data supplemental logging is enabled."
            },
            "links":{
                "type":"array",
                "items":{
                    "$ref":"#/definitions/LinkRelation"
                }
            }
        }
    }

Nested Schema : links

Type: `array`

Show Source

- Array of: object LinkRelation

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/LinkRelation"
        }
    }

Nested Schema : LinkRelation

Type: `object`

Show Source

- href: string
- rel: string

<!-- -->

    {
        "type":"object",
        "properties":{
            "rel":{
                "type":"string"
            },
            "href":{
                "type":"string"
            }
        },
        "required":[
            "rel",
            "href"
        ]
    }

Back to Top
