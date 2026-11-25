## 109 DBMS_MEMOPTIMIZE_ADMIN

The `DBMS_MEMOPTIMIZE_ADMIN` package provides the interface for flushing the Memoptimized Rowstore data buffered in the large pool to disk.

This chapter contains the following topics:

- DBMS_MEMOPTIMIZE_ADMIN Overview

- Summary of DBMS_MEMOPTIMIZE_ADMIN Subprograms

### 109.1 DBMS_MEMOPTIMIZE_ADMIN Overview

The `DBMS_MEMOPTIMIZE_ADMIN` package provides the interface for flushing the Memoptimized Rowstore data that is buffered in the large pool to disk.

The Memoptimized Rowstore provides the following functionality:

- Fast Ingest

  Fast ingest optimizes the processing of high-frequency, single-row data inserts. Fast ingest uses the large pool in the SGA for buffering the inserts before writing them to disk.

- Fast Lookup

  Fast lookup enables fast retrieval of data for high-frequency queries. Fast lookup uses a separate memory area in the SGA called the memoptimize pool for buffering the data queried from tables.

The `DBMS_MEMOPTIMIZE_ADMIN` package provides the following operation related to fast ingest of the Memoptimized Rowstore:

- Flush fast ingest data from the large pool to disk for all sessions.

### 109.2 Summary of DBMS_MEMOPTIMIZE_ADMIN Subprograms

This table lists the `DBMS_MEMOPTIMIZE_ADMIN` subprograms and briefly describes them.

Table 109-1 DBMS_MEMOPTIMIZE_ADMIN Package Subprograms

| Procedure              | Description                                                                                                    |
|:-----------------------|:---------------------------------------------------------------------------------------------------------------|
| WRITES_FLUSH Procedure | Flushes all the fast ingest data of the Memoptimize Rowstore from the large pool to disk for all the sessions. |

#### 109.2.1 WRITES_FLUSH Procedure

This procedure flushes all the fast ingest data of the Memoptimized Rowstore from the large pool to disk for all the sessions.

##### Syntax

    DBMS_MEMOPTIMIZE_ADMIN.WRITES_FLUSH;
