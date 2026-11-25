Returns records from DBA_SEGMENTS for a specific tablespace. A client requires SQL Administrator role to invoke this service.

### Request

Supported Media Types

- application/json

Path Parameters

- tablespace_name: string
  Name of the tablespace.

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

Collection of records from DBA_SEGMENTS for the specified tablespace.

Body ()

Root Schema : DatabaseTablespaceSegments

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
                    "$ref":"#/definitions/DatabaseTablespaceSegmentsItem"
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

- Array of: object DatabaseTablespaceSegmentsItem
  Describes the storage allocated for a segments in the database.

<!-- -->

    {
        "type":"array",
        "items":{
            "$ref":"#/definitions/DatabaseTablespaceSegmentsItem"
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

Nested Schema : DatabaseTablespaceSegmentsItem

Type: `object`

Describes the storage allocated for a segments in the database.

Show Source

- blocks(optional): integer
  Size, in Oracle blocks, of the segment.
- buffer_pool(optional): string
  Buffer pool to be used for segment blocks.
- bytes(optional): integer
  Size, in bytes, of the segment.
- cell_flash_cache(optional): string
  Cell flash cache hint to be used for segment blocks.
- cellmemory(optional): string
  The value for columnar compression in the storage cell flash cache.
- extents(optional): integer
  Number of extents allocated to the segment.
- flash_cache(optional): string
  Database Smart Flash Cache hint to be used for segment blocks.
- freelist_groups(optional): integer
  Number of freelist groups allocated to this segment.
- freelists(optional): integer
  Number of process freelists allocated to this segment.
- header_block(optional): integer
  ID of the block containing the segment header.
- header_file(optional): integer
  ID of the file containing the segment header.
- initial_extent(optional): integer
  Size in bytes requested for the initial extent of the segment at create time. Oracle rounds the extent size to multiples of 5 blocks if the requested size is greater than 5 blocks.
- inmemory(optional): string
  Indicates whether the In-Memory Column Store (IM column store) is enabled (ENABLED) or disabled (DISABLED) for this segment.
- inmemory_compression(optional): string
  Indicates the compression level for the IM column store.
- inmemory_distribute(optional): string
  ndicates how the IM column store is distributed in an Oracle Real Application Clusters (Oracle RAC) environment.
- inmemory_duplicate(optional): string
  ndicates the duplicate setting for the IM column store in an Oracle RAC environment.
- inmemory_priority(optional): string
  Indicates the priority for In-Memory Column Store (IM column store) population.
- links(optional): array links
- max_extents(optional): integer
  Maximum number of extents allowed in the segment.
- max_size(optional): integer
  Maximum number of blocks allowed in the segment.
- min_extents(optional): integer
  Minimum number of extents allowed in the segment.
- minretention(optional): integer
  Minimum retention duration for SECUREFILE segment.
- next_extent(optional): integer
  Size in bytes of the next extent to be allocated to the segment.
- owner(optional): string
  Username of the segment owner.
- partition_name(optional): string
  Object Partition Name (Set to NULL for nonpartitioned objects).
- pct_increase(optional): integer
  Percent by which to increase the size of the next extent to be allocated.
- relative_fno(optional): integer
  Relative file number of the segment header.
- retention(optional): string
  Retention option for SECUREFILE segment.
- segment_name(optional): string
  Name, if any, of the segment.
- segment_subtype(optional): string
  Subtype of LOB segment: SECUREFILE, ASSM, MSSM, and NULL.
- segment_type(optional): string
  Type of segment.
- tablespace_name(optional): string
  Name of the tablespace containing the segment.

<!-- -->

    {
        "type":"object",
        "description":"Describes the storage allocated for a segments in the database.",
        "properties":{
            "owner":{
                "type":"string",
                "description":"Username of the segment owner."
            },
            "segment_name":{
                "type":"string",
                "description":"Name, if any, of the segment."
            },
            "partition_name":{
                "type":"string",
                "description":"Object Partition Name (Set to NULL for nonpartitioned objects)."
            },
            "segment_type":{
                "type":"string",
                "description":"Type of segment."
            },
            "segment_subtype":{
                "type":"string",
                "description":"Subtype of LOB segment: SECUREFILE, ASSM, MSSM, and NULL."
            },
            "tablespace_name":{
                "type":"string",
                "description":"Name of the tablespace containing the segment."
            },
            "header_file":{
                "type":"integer",
                "description":"ID of the file containing the segment header."
            },
            "header_block":{
                "type":"integer",
                "description":"ID of the block containing the segment header."
            },
            "bytes":{
                "type":"integer",
                "description":"Size, in bytes, of the segment."
            },
            "blocks":{
                "type":"integer",
                "description":"Size, in Oracle blocks, of the segment."
            },
            "extents":{
                "type":"integer",
                "description":"Number of extents allocated to the segment."
            },
            "initial_extent":{
                "type":"integer",
                "description":"Size in bytes requested for the initial extent of the segment at create time. Oracle rounds the extent size to multiples of 5 blocks if the requested size is greater than 5 blocks."
            },
            "next_extent":{
                "type":"integer",
                "description":"Size in bytes of the next extent to be allocated to the segment."
            },
            "min_extents":{
                "type":"integer",
                "description":"Minimum number of extents allowed in the segment."
            },
            "max_extents":{
                "type":"integer",
                "description":"Maximum number of extents allowed in the segment."
            },
            "max_size":{
                "type":"integer",
                "description":"Maximum number of blocks allowed in the segment."
            },
            "retention":{
                "type":"string",
                "description":"Retention option for SECUREFILE segment."
            },
            "minretention":{
                "type":"integer",
                "description":"Minimum retention duration for SECUREFILE segment."
            },
            "pct_increase":{
                "type":"integer",
                "description":"Percent by which to increase the size of the next extent to be allocated."
            },
            "freelists":{
                "type":"integer",
                "description":"Number of process freelists allocated to this segment."
            },
            "freelist_groups":{
                "type":"integer",
                "description":"Number of freelist groups allocated to this segment."
            },
            "relative_fno":{
                "type":"integer",
                "description":"Relative file number of the segment header."
            },
            "buffer_pool":{
                "type":"string",
                "description":"Buffer pool to be used for segment blocks."
            },
            "flash_cache":{
                "type":"string",
                "description":"Database Smart Flash Cache hint to be used for segment blocks."
            },
            "cell_flash_cache":{
                "type":"string",
                "description":"Cell flash cache hint to be used for segment blocks."
            },
            "inmemory":{
                "type":"string",
                "description":"Indicates whether the In-Memory Column Store (IM column store) is enabled (ENABLED) or disabled (DISABLED) for this segment."
            },
            "inmemory_priority":{
                "type":"string",
                "description":"Indicates the priority for In-Memory Column Store (IM column store) population."
            },
            "inmemory_distribute":{
                "type":"string",
                "description":"ndicates how the IM column store is distributed in an Oracle Real Application Clusters (Oracle RAC) environment."
            },
            "inmemory_duplicate":{
                "type":"string",
                "description":"ndicates the duplicate setting for the IM column store in an Oracle RAC environment."
            },
            "inmemory_compression":{
                "type":"string",
                "description":"Indicates the compression level for the IM column store."
            },
            "cellmemory":{
                "type":"string",
                "description":"The value for columnar compression in the storage cell flash cache."
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
