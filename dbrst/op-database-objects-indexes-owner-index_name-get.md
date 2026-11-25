Returns the corresponding record from DBA_INDEXES or ALL_INDEXES view depending on role at runtime. A client requires SQL Administrator or SQL Developer role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- index_name: string
  Name of the index.
- owner: string
  Owner for the index.

Back to Top

### Response

Supported Media Types

- application/json

#### 200 Response

Information on a specific index.

Body ()

Root Schema : DatabaseObjectsIndexesItem

Type: `object`

Describes an index in the database.

Show Source

- avg_data_blocks_per_key(optional): integer
  Average number of data blocks in the table that are pointed to by a distinct value in the index rounded to the nearest integer.
- avg_leaf_blocks_per_key(optional): integer
  Average number of leaf blocks in which each distinct value in the index appears, rounded to the nearest integer.
- blevel(optional): integer
  B\*-Tree level (depth of the index from its root block to its leaf blocks). A depth of 0 indicates that the root block and leaf block are the same.
- buffer_pool(optional): string
  Buffer pool to be used for index blocks.
- cell_flash_cache(optional): string
  Cell flash cache hint to be used for index blocks.
- clustering_factor(optional): number
  Indicates the amount of order of the rows in the table based on the values of the index.
- compression(optional): string
  The type of compression being used for the index.
- degree(optional): string
  Number of threads per instance for scanning the index, or DEFAULT.
- distinct_keys(optional): integer
  Number of distinct indexed values.
- domidx_management(optional): string
  If this is a domain index, indicates whether the domain index is system-managed (SYSTEM_MANAGED) or user-managed (USER_MANAGED).
- domidx_opstatus(optional): string
  Status of the operation on a domain index.
- domidx_status(optional): string
  Status of a domain index.
- dropped(optional): string
  Indicates whether redundant primary key columns are eliminated from secondary indexes on index-organized tables (YES) or not (NO).
- duration(optional): string
  Indicates the duration of a temporary table.
- flash_cache(optional): string
  Database Smart Flash Cache hint to be used for index blocks.
- freelist_groups(optional): integer
  Number of freelist groups allocated to this segment.
- freelists(optional): integer
  Number of process freelists allocated to this segment.
- funcidx_status(optional): string
  Status of a function-based index.
- generated(optional): string
  Indicates whether the name of the index is system-generated (Y) or not (N).
- global_stats(optional): string
  GLOBAL_STATS will be YES if statistics are gathered or incrementally maintained, otherwise it will be NO.
- include_column(optional): integer
  Column ID of the last column to be included in index-organized table primary key (non-overflow) index.
- index_name(optional): string
  Name of the index.
- index_type(optional): string
  Type of the index.
- indexing(optional): string
  Indicates whether a global index is decoupled from the underlying table.
- ini_trans(optional): integer
  Initial number of transactions.
- initial_extent(optional): integer
  Size of the initial extent.
- instances(optional): string
  Number of instances across which the indexes to be scanned, or DEFAULT.
- iot_redundant_pkey_elim(optional): string
  Indicates whether redundant primary key columns are eliminated from secondary indexes on index-organized tables (YES) or not (NO).
- ityp_name(optional): string
  For a domain index, the name of the indextype.
- ityp_owner(optional): string
  For a domain index, the owner of the indextype.
- join_index(optional): string
  Indicates whether the index is a join index (YES) or not (NO).
- last_analyzed(optional): string
  Date on which this index was most recently analyzed.
- leaf_blocks(optional): integer
  Number of leaf blocks in the index.
- links(optional): array links
- logging(optional): string
  Indicates whether or not changes to the index are logged.
- max_extents(optional): integer
  Maximum number of extents allowed in the segment.
- max_trans(optional): integer
  Maximum number of transactions.
- min_extents(optional): integer
  Minimum number of extents allowed in the segment.
- next_extent(optional): integer
  Size of secondary extents.
- num_rows(optional): integer
  Number of rows in the index.
- orphaned_entries(optional): string
  Indicates whether a global index contains stale entries because of deferred index maintenance during DROP/TRUNCATE PARTITION, or MODIFY PARTITION INDEXING OFF operations.
- owner(optional): string
  Owner of the index.
- parameters(optional): string
  For a domain index, the parameter string.
- partitioned(optional): string
  Indicates whether the index is partitioned (YES) or not (NO).
- pct_direct_access(optional): number
  For a secondary index on an index-organized table, the percentage of rows with VALID guess.
- pct_free(optional): integer
  Minimum percentage of free space in a block.
- pct_increase(optional): number
  Percentage increase in extent size.
- pct_threshold(optional): number
  Threshold percentage of block space allowed per index entry.
- prefix_length(optional): integer
  Number of columns in the prefix of the compression key.
- sample_size(optional): integer
  Size of the sample used to analyze the index.
- secondary(optional): string
  Indicates whether the index is a secondary object created by the ODCIIndexCreate method of the Oracle Data Cartridge (Y) or not (N).
- segment_created(optional): string
  Indicates whether the index segment has been created (YES) or not (NO).
- status(optional): string
  Indicates whether a nonpartitioned index is VALID or UNUSABLE.
- table_name(optional): string
  Name of the indexed object.
- table_owner(optional): string
  Owner of the indexed object.
- table_type(optional): string
  Type of the indexed object.
- tablespace_name(optional): string
  Name of the tablespace containing the index.
- temporary(optional): string
  Indicates whether the index is on a temporary table (Y) or not (N).
- uniqueness(optional): string
  Indicates whether the index is unique (UNIQUE) or nonunique (NONUNIQUE).
- user_stats(optional): string
  Indicates whether statistics were entered directly by the user (YES) or not (NO).
- visibility(optional): string
  Indicates whether the index is VISIBLE or INVISIBLE to the optimizer.

<!-- -->

    {
        "type":"object",
        "description":"Describes an index in the database.",
        "properties":{
            "owner":{
                "type":"string",
                "description":"Owner of the index."
            },
            "index_name":{
                "type":"string",
                "description":"Name of the index."
            },
            "index_type":{
                "type":"string",
                "description":"Type of the index."
            },
            "table_owner":{
                "type":"string",
                "description":"Owner of the indexed object."
            },
            "table_name":{
                "type":"string",
                "description":"Name of the indexed object."
            },
            "table_type":{
                "type":"string",
                "description":"Type of the indexed object."
            },
            "uniqueness":{
                "type":"string",
                "description":"Indicates whether the index is unique (UNIQUE) or nonunique (NONUNIQUE)."
            },
            "compression":{
                "type":"string",
                "description":"The type of compression being used for the index."
            },
            "prefix_length":{
                "type":"integer",
                "description":"Number of columns in the prefix of the compression key."
            },
            "tablespace_name":{
                "type":"string",
                "description":"Name of the tablespace containing the index."
            },
            "ini_trans":{
                "type":"integer",
                "description":"Initial number of transactions."
            },
            "max_trans":{
                "type":"integer",
                "description":"Maximum number of transactions."
            },
            "initial_extent":{
                "type":"integer",
                "description":"Size of the initial extent."
            },
            "next_extent":{
                "type":"integer",
                "description":"Size of secondary extents."
            },
            "min_extents":{
                "type":"integer",
                "description":"Minimum number of extents allowed in the segment."
            },
            "max_extents":{
                "type":"integer",
                "description":"Maximum number of extents allowed in the segment."
            },
            "pct_increase":{
                "type":"number",
                "description":"Percentage increase in extent size."
            },
            "pct_threshold":{
                "type":"number",
                "description":"Threshold percentage of block space allowed per index entry."
            },
            "include_column":{
                "type":"integer",
                "description":"Column ID of the last column to be included in index-organized table primary key (non-overflow) index."
            },
            "freelists":{
                "type":"integer",
                "description":"Number of process freelists allocated to this segment."
            },
            "freelist_groups":{
                "type":"integer",
                "description":"Number of freelist groups allocated to this segment."
            },
            "pct_free":{
                "type":"integer",
                "description":"Minimum percentage of free space in a block."
            },
            "logging":{
                "type":"string",
                "description":"Indicates whether or not changes to the index are logged."
            },
            "blevel":{
                "type":"integer",
                "description":"B*-Tree level (depth of the index from its root block to its leaf blocks). A depth of 0 indicates that the root block and leaf block are the same."
            },
            "leaf_blocks":{
                "type":"integer",
                "description":"Number of leaf blocks in the index."
            },
            "distinct_keys":{
                "type":"integer",
                "description":"Number of distinct indexed values."
            },
            "avg_leaf_blocks_per_key":{
                "type":"integer",
                "description":"Average number of leaf blocks in which each distinct value in the index appears, rounded to the nearest integer."
            },
            "avg_data_blocks_per_key":{
                "type":"integer",
                "description":"Average number of data blocks in the table that are pointed to by a distinct value in the index rounded to the nearest integer."
            },
            "clustering_factor":{
                "type":"number",
                "description":"Indicates the amount of order of the rows in the table based on the values of the index."
            },
            "status":{
                "type":"string",
                "description":"Indicates whether a nonpartitioned index is VALID or UNUSABLE."
            },
            "num_rows":{
                "type":"integer",
                "description":"Number of rows in the index."
            },
            "sample_size":{
                "type":"integer",
                "description":"Size of the sample used to analyze the index."
            },
            "last_analyzed":{
                "type":"string",
                "description":"Date on which this index was most recently analyzed."
            },
            "degree":{
                "type":"string",
                "description":"Number of threads per instance for scanning the index, or DEFAULT."
            },
            "instances":{
                "type":"string",
                "description":"Number of instances across which the indexes to be scanned, or DEFAULT."
            },
            "partitioned":{
                "type":"string",
                "description":"Indicates whether the index is partitioned (YES) or not (NO)."
            },
            "temporary":{
                "type":"string",
                "description":"Indicates whether the index is on a temporary table (Y) or not (N)."
            },
            "generated":{
                "type":"string",
                "description":"Indicates whether the name of the index is system-generated (Y) or not (N)."
            },
            "secondary":{
                "type":"string",
                "description":"Indicates whether the index is a secondary object created by the ODCIIndexCreate method of the Oracle Data Cartridge (Y) or not (N)."
            },
            "buffer_pool":{
                "type":"string",
                "description":"Buffer pool to be used for index blocks."
            },
            "flash_cache":{
                "type":"string",
                "description":"Database Smart Flash Cache hint to be used for index blocks."
            },
            "cell_flash_cache":{
                "type":"string",
                "description":"Cell flash cache hint to be used for index blocks."
            },
            "user_stats":{
                "type":"string",
                "description":"Indicates whether statistics were entered directly by the user (YES) or not (NO)."
            },
            "duration":{
                "type":"string",
                "description":"Indicates the duration of a temporary table."
            },
            "pct_direct_access":{
                "type":"number",
                "description":"For a secondary index on an index-organized table, the percentage of rows with VALID guess."
            },
            "ityp_owner":{
                "type":"string",
                "description":"For a domain index, the owner of the indextype."
            },
            "ityp_name":{
                "type":"string",
                "description":"For a domain index, the name of the indextype."
            },
            "parameters":{
                "type":"string",
                "description":"For a domain index, the parameter string."
            },
            "global_stats":{
                "type":"string",
                "description":"GLOBAL_STATS will be YES if statistics are gathered or incrementally maintained, otherwise it will be NO."
            },
            "domidx_status":{
                "type":"string",
                "description":"Status of a domain index."
            },
            "domidx_opstatus":{
                "type":"string",
                "description":"Status of the operation on a domain index."
            },
            "funcidx_status":{
                "type":"string",
                "description":"Status of a function-based index."
            },
            "join_index":{
                "type":"string",
                "description":"Indicates whether the index is a join index (YES) or not (NO)."
            },
            "iot_redundant_pkey_elim":{
                "type":"string",
                "description":"Indicates whether redundant primary key columns are eliminated from secondary indexes on index-organized tables (YES) or not (NO)."
            },
            "dropped":{
                "type":"string",
                "description":"Indicates whether redundant primary key columns are eliminated from secondary indexes on index-organized tables (YES) or not (NO)."
            },
            "visibility":{
                "type":"string",
                "description":"Indicates whether the index is VISIBLE or INVISIBLE to the optimizer."
            },
            "domidx_management":{
                "type":"string",
                "description":"If this is a domain index, indicates whether the domain index is system-managed (SYSTEM_MANAGED) or user-managed (USER_MANAGED)."
            },
            "segment_created":{
                "type":"string",
                "description":"Indicates whether the index segment has been created (YES) or not (NO)."
            },
            "orphaned_entries":{
                "type":"string",
                "description":"Indicates whether a global index contains stale entries because of deferred index maintenance during DROP/TRUNCATE PARTITION, or MODIFY PARTITION INDEXING OFF operations."
            },
            "indexing":{
                "type":"string",
                "description":"Indicates whether a global index is decoupled from the underlying table."
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
