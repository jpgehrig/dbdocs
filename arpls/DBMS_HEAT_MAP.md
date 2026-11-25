## 83  DBMS_HEAT_MAP

The `DBMS_HEAT_MAP` package provides an interface to externalize heatmaps at various levels of storage including block, extent, segment, object and tablespace. A second set of subprograms externalize the heatmaps materialized by the background for top N tablespaces.

This chapter contains the following topics:

- Overview

- Security Model

- Summary of DBMS_HEAT_MAP Subprograms

**See Also:**

- [Heat Map](../vldbg/ilm-strategy-heatmap-ado.md) in Oracle Database VLDB and Partitioning Guide

- [DBMS_ILM](DBMS_ILM.md)

- [DBMS_ILM_ADMIN](DBMS_ILM_ADMIN.md)

### 83.1 DBMS_HEAT_MAP Overview

To implement your ILM strategy, you can use Heat Map in Oracle Database to track data access and modification. You can also use Automatic Data Optimization (ADO) to automate the compression and movement of data between different tiers of storage within the database.

The Heat Map tracks modification times at the block level, and multiple access statistics at the segment level. Objects in the `SYSTEM` and `SYSAUX` tablespaces are not tracked. `DBMS_HEAT_MAP` gives you access to the Heat Map statistics at various levels - block, extent, segment, object, and tablespace.

### 83.2 DBMS_HEAT_MAP Security Model

The execution privilege is granted to `PUBLIC`. Procedures in this package run under the caller security. The user must have `ANALYZE` privilege on the object.

### 83.3 Summary of DBMS_HEAT_MAP Subprograms

This table lists and briefly describes the `DBMS_HEAT_MAP` package subprograms.

Table 83-1 DBMS_HEAT_MAP Package Subprograms

| Subprogram                   | Description                                                                                        |
|:-----------------------------|:---------------------------------------------------------------------------------------------------|
| BLOCK_HEAT_MAP Function      | Returns last modification time for each block in a table segment                                   |
| EXTENT_HEAT_MAP Function     | Returns the extent level Heat Map statistics for a table segment                                   |
| OBJECT_HEAT_MAP Function     | Returns the minimum, maximum and average access times for all the segments belonging to the object |
| SEGMENT_HEAT_MAP Procedure   | Returns the heatmap attributes for the given segment                                               |
| TABLESPACE_HEAT_MAP Function | Returns the minimum, maximum and average access times for all the segments in the tablespace       |

#### 83.3.1 BLOCK_HEAT_MAP Function

This table function returns the last modification time for each block in a table segment. It returns no information for segment types that are not data.

##### Syntax

    DBMS_HEAT_MAP.BLOCK_HEAT_MAP (
       owner             IN VARCHAR2,
       segment_name      IN VARCHAR2,
       partition_name    IN VARCHAR2 DEFAULT NULL,
       sort_columnid     IN NUMBER DEFAULT NULL,
       sort_order        IN VARCHAR2 DEFAULT NULL)
    RETURN hm_bls_row PIPELINED;

##### Parameters

Table 83-2 BLOCK_HEAT_MAP Function Parameters

| Parameter        | Description                                                                                                                                         |
|:-----------------|:----------------------------------------------------------------------------------------------------------------------------------------------------|
| `owner`          | Owner of the segment                                                                                                                                |
| `segment_name`   | Table name of a non-partitioned table or (sub)partition of partitioned table. Returns no rows when table name is specified for a partitioned table. |
| `partition_name` | Defaults to `NULL`. For a partitioned table, specify the partition or subpartition segment name.                                                    |
| `sort_columnid`  | ID of the column on which to sort the output. Valid values 1..9. Invalid values are ignored.                                                        |
| `sort_order`     | Defaults to `NULL`. Possible values: `ASC`, `DESC`                                                                                                  |

##### Return Values

Table 83-3 BLOCK_HEAT_MAP Function Return Values (Output Parameters)

| Parameter         | Description                                      |
|:------------------|:-------------------------------------------------|
| `owner`           | Owner of the segment                             |
| `segment_name`    | Segment name of the non-partitioned table        |
| `partition_name`  | Partition or subpartition name                   |
| `tablespace_name` | Tablespace containing the segment                |
| `file_id`         | Absolute file number of the block in the segment |
| `relative_fno`    | Relative file number of the block in the segment |
| `block_id`        | Block number of the block                        |
| `write time`      | Last modification time of the block              |

#### 83.3.2 EXTENT_HEAT_MAP Function

This table function returns the extent level Heat Map statistics for a table segment. It returns no information for segment types that are not data. Aggregates at extent level, including minimum modification time and maximum modification time, are included.

##### Syntax

    DBMS_HEAT_MAP.EXTENT_HEAT_MAP (
       owner             IN VARCHAR2,
       segment_name      IN VARCHAR2,
       partition_name    IN VARCHAR2 DEFAULT NULL,
    RETURN hm_els_row PIPELINED;

##### Parameters

Table 83-4 EXTENT_HEAT_MAP Function Parameters

| Parameter        | Description                                                                                                                                         |
|:-----------------|:----------------------------------------------------------------------------------------------------------------------------------------------------|
| `owner`          | Owner of the segment                                                                                                                                |
| `segment_name`   | Table name of a non-partitioned table or (sub)partition of partitioned table. Returns no rows when table name is specified for a partitioned table. |
| `partition_name` | Defaults to `NULL`. For a partitioned table, specify the partition or subpartition segment name.                                                    |

##### Return Values

Table 83-5 EXTENT_HEAT_MAP Function Return Values (Output Parameters)

| Parameter         | Description                                      |
|:------------------|:-------------------------------------------------|
| `owner`           | Owner of the segment                             |
| `segment_name`    | Segment name of the non-partitioned table        |
| `partition_name`  | Partition or subpartition name                   |
| `tablespace_name` | Tablespace containing the segment                |
| `file_id`         | Absolute file number of the block in the segment |
| `relative_fno`    | Relative file number of the block in the segment |
| `block_id`        | Block number of the block                        |
| `blocks`          | Number of blocks in the extent                   |
| `bytes`           | Number of bytes in the extent                    |
| `min_writetime`   | Minimum of last modification time of the block   |
| `max_writetime`   | Maximum of last modification time of the block   |
| `avg_writetime`   | Average of last modification time of the block   |

#### 83.3.3 OBJECT_HEAT_MAP Function

This table function returns the minimum, maximum and average access times for all the segments belonging to the object.

The object must be a table. The table function raises an error if called on object tables other than table.

##### Syntax

    DBMS_HEAT_MAP.OBJECT_HEAT_MAP (
       object_owner      IN VARCHAR2,
       object_name       IN VARCHAR2)
     RETURN hm_object_table PIPELINED;

##### Parameters

Table 83-6 OBJECT_HEAT_MAP Function Parameters

| Parameter      | Description                         |
|:---------------|:------------------------------------|
| `object_owner` | Tablespace containing the segment   |
| `object_name`  | Segment header relative file number |

##### Return Values

Table 83-7 OBJECT_HEAT_MAP Function Return Values (Output Parameters)

| Parameter         | Description                                       |
|:------------------|:--------------------------------------------------|
| `segment_name`    | Name of the top level segment                     |
| `partition_name`  | Name of the partition                             |
| `tablespace_name` | Name of the tablespace                            |
| `segment_type`    | Type of segment as in `DBA_SEGMENTS.SEGMENT_TYPE` |
| `segment_size`    | Segment size in bytes                             |
| `min_writetime`   | Oldest write time for the segment                 |
| `max_writetime`   | Latest write time for the segment                 |
| `avg_writetime`   | Average write time for the segment                |
| `min_readtime`    | Oldest read time for the segment                  |
| `max_readtime`    | Latest read time for the segment                  |
| `avg_writetime`   | Average write time for the segment                |
| `min_lookuptime`  | Oldest index lookup time for the segment          |
| `max_lookuptime`  | Latest index lookup time for the segment          |
| `avg_lookuptime`  | Average index lookup time for the segment         |
| `min_ftstime`     | Oldest full table scan time for the segment       |
| `max_ftstime`     | Latest full table scan time for the segment       |
| `avg_ftstime`     | Average full table scan time for the segment      |

#### 83.3.4 SEGMENT_HEAT_MAP Procedure

This procedure returns the heatmap attributes for the given segment.

##### Syntax

    DBMS_HEAT_MAP.SEGMENT_HEAT_MAP (
       tablespace_id          IN  NUMBER,
       header_file            IN  NUMBER,
       header_block           IN  NUMBER,
       segment_objd           IN  NUMBER,
       min_writetime          OUT DATE,
       max_writetime          OUT DATE,
       avg_writetime          OUT DATE,
       min_readtime           OUT DATE,
       max_readtime           OUT DATE,
       avg_readtime           OUT DATE,
       min_lookuptime         OUT DATE,
       max_lookuptime         OUT DATE,
       avg_lookuptime         OUT DATE,
       min_ftstime            OUT DATE,
       max_ftstime            OUT DATE,
       avg_ftstime            OUT DATE);

##### Parameters

Table 83-8 SEGMENT_HEAT_MAP Procedure Parameters

| Parameter       | Description                         |
|:----------------|:------------------------------------|
| `tablespace_id` | Tablespace containing the segment   |
| `header_file`   | Segment header relative file number |
| `header_block`  | Segment header block number         |
| `segment_objd`  | `DATAOBJ` of the segment            |

##### Return Values

Table 83-9 SEGMENT_HEAT_MAP Procedure Return Values (Output Parameters)

| Parameter        | Description                                  |
|:-----------------|:---------------------------------------------|
| `min_writetime`  | Oldest write time for the segment            |
| `max_writetime`  | Latest write time for the segment            |
| `avg_writetime`  | Average write time for the segment           |
| `min_readtime`   | Oldest read time for the segment             |
| `max_readtime`   | Latest read time for the segment             |
| `avg_writetime`  | Average write time for the segment           |
| `min_lookuptime` | Oldest index lookup time for the segment     |
| `max_lookuptime` | Latest index lookup time for the segment     |
| `avg_lookuptime` | Average index lookup time for the segment    |
| `min_ftstime`    | Oldest full table scan time for the segment  |
| `max_ftstime`    | Latest full table scan time for the segment  |
| `avg_ftstime`    | Average full table scan time for the segment |

#### 83.3.5 TABLESPACE_HEAT_MAP Function

This table function returns the minimum, maximum and average access times for all the segments in the tablespace.

##### Syntax

    DBMS_HEAT_MAP.TABLESPACE_HEAT_MAP (
        tablespace_name      IN VARCHAR2)
      RETURN hm_tablespace_table PIPELINED;

##### Parameters

Table 83-10 TABLESPACE_HEAT_MAP Procedure Parameters

| Parameter         | Description            |
|:------------------|:-----------------------|
| `tablespace_name` | Name of the tablespace |

##### Return Values

Table 83-11 TABLESPACE_HEAT_MAP Procedure Return Values (Output Parameters)

| Parameter         | Description                                  |
|:------------------|:---------------------------------------------|
| `segment_count`   | Total number of segments in the tablespace   |
| `allocated_bytes` | Space used by the segments in the tablespace |
| `min_writetime`   | Oldest write time for the segment            |
| `max_writetime`   | Latest write time for the segment            |
| `avg_writetime`   | Average write time for the segment           |
| `min_readtime`    | Oldest read time for the segment             |
| `max_readtime`    | Latest read time for the segment             |
| `avg_writetime`   | Average write time for the segment           |
| `min_lookuptime`  | Oldest index lookup time for the segment     |
| `max_lookuptime`  | Latest index lookup time for the segment     |
| `avg_lookuptime`  | Average index lookup time for the segment    |
| `min_ftstime`     | Oldest full table scan time for the segment  |
| `max_ftstime`     | Latest full table scan time for the segment  |
| `avg_ftstime`     | Average full table scan time for the segment |
