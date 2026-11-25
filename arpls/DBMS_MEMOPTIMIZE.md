## 108 DBMS_MEMOPTIMIZE

The `DBMS_MEMOPTIMIZE` package provides the interface for managing the Memoptimized Rowstore data buffered in the large pool and the memoptimize pool.

This chapter contains the following topics:

- DBMS_MEMOPTIMIZE Overview

- Summary of DBMS_MEMOPTIMIZE Subprograms

### 108.1 DBMS_MEMOPTIMIZE Overview

The `DBMS_MEMOPTIMIZE` package provides the interface for managing Memoptimized Rowstore data buffered in the large pool and the memoptimize pool.

The Memoptimized Rowstore provides the following functionality:

- Fast Ingest

  Fast ingest optimizes the processing of high-frequency, single-row data inserts. Fast ingest uses the large pool in the SGA for buffering the inserts before writing them to disk.

- Fast Lookup

  Fast lookup enables fast retrieval of data for high-frequency queries. Fast lookup uses a separate memory area in the SGA called the memoptimize pool for buffering data queried from tables.

The `DBMS_MEMOPTIMIZE` package provides the following operations related to the Memoptimized Rowstore:

- Fast ingest operations:

  - Provide the low high-water mark (low HWM) of the sequence numbers of rows that have been successfully written from the large pool to disk across all the sessions.

  - Provide the high-water mark (HWM) sequence number of the row that has been written to the large pool for the current session.

  - Flush all the fast ingest data from the large pool to disk for the current session.

- Fast lookup operations:

  - Remove data for a table from the memoptimize pool.

  - Populate data for a table in the memoptimize pool.

### 108.2 Summary of DBMS_MEMOPTIMIZE Subprograms

This table lists the `DBMS_MEMOPTIMIZE` subprograms and briefly describes them.

Table 108-1 DBMS_MEMOPTIMIZE Package Subprograms Related to Fast Ingest

| Procedure                    | Description                                                                                                                                             |
|:-----------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------|
| GET_APPLY_HWM_SEQID Function | Returns the low high-water mark (low HWM) of the sequence numbers of rows that have been successfully written to disk globally across all the sessions. |
| GET_WRITE_HWM_SEQID Function | Returns the high-water mark (HWM) sequence number of the row that has been written to the large pool for the current session.                           |
| WRITE_END Procedure          | Flushes all the fast ingest data from the large pool to disk for the current session.                                                                   |

Table 108-2 DBMS_MEMOPTIMIZE Package Subprograms Related to Fast Lookup

| Procedure             | Description                                         |
|:----------------------|:----------------------------------------------------|
| DROP_OBJECT Procedure | Removes data for a table from the memoptimize pool. |
| POPULATE Procedure    | Populates data for a table in the memoptimize pool. |

#### 108.2.1 DROP_OBJECT Procedure

This procedure removes data for a table from the memoptimize pool.

##### Syntax

    DBMS_MEMOPTIMIZE.DROP_OBJECT (
       schema_name        IN VARCHAR2,
       table_name         IN VARCHAR2,
       partition_name     IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table 108-3 DROP_OBJECT Procedure Parameters

| Parameter        | Description                                                                                                                                                     |
|:-----------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `schema_name`    | Name of the schema.                                                                                                                                             |
| `table_name`     | Name of the table for which the data needs to be removed from the memoptimize pool.                                                                             |
| `partition_name` | Name of the table partition for which the data needs to be removed from the memoptimize pool.<br>This is an optional parameter and its default value is `NULL`. |

#### 108.2.2 GET_APPLY_HWM_SEQID Function

This function returns the low high-water mark (low HWM) of sequence numbers of the records that have been successfully written to disk across all the sessions.

##### Syntax

    DBMS_MEMOPTIMIZE.GET_APPLY_HWM_SEQID
      RETURN number;

##### Return Value

Returns the low high-water mark (low HWM) of sequence numbers of the records that have been successfully written to disk across all the sessions.

#### 108.2.3 GET_WRITE_HWM_SEQID Function

This function returns the high-water mark (HWM) sequence number of the record that has been written to the large pool for the current session.

##### Syntax

    DBMS_MEMOPTIMIZE.GET_WRITE_HWM_SEQID
      RETURN number;

##### Return Value

Returns the high-water mark (HWM) sequence number of the record that has been written to the large pool for the current session.

#### 108.2.4 POPULATE Procedure

This procedure populates the data for a table in the memoptimize pool.

##### Syntax

    DBMS_MEMOPTIMIZE.POPULATE (
       schema_name        IN VARCHAR2,
       table_name         IN VARCHAR2,
       partition_name     IN VARCHAR2 DEFAULT NULL);

##### Parameters

Table 108-4 POPULATE Procedure Parameters

| Parameter        | Description                                                                                                                                                     |
|:-----------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `schema_name`    | Name of the schema.                                                                                                                                             |
| `table_name`     | Name of the table for which the data needs to be populated in the memoptimize pool.                                                                             |
| `partition_name` | Name of the table partition for which the data needs to be populated in the memoptimize pool.<br>This is an optional parameter and its default value is `NULL`. |

#### 108.2.5 WRITE_END Procedure

This procedure flushes all the fast ingest data from the large pool to disk for the current session.

##### Syntax

    DBMS_MEMOPTIMIZE.WRITE_END;
