## 177 DBMS_TABLE_DATA

The `DBMS_TABLE_DATA` package provides procedures that can be used to retrieve the byte value of a single column, or a series of columns, in any table. These procedures, along with a publicly documented meta-data structure for columns, can be used to retrieve the row content for row data on which the hash or user signature is computed.

This chapter contains the following topics:

- DBMS_TABLE_DATA Overview
- DBMS_TABLE_DATA Security Model
- Summary of DBMS_TABLE_DATA Subprograms

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/managing-tables.md)

- [Oracle Database Concepts](../cncpt/tables-and-table-clusters.md)

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md)

- [Oracle Database Reference](../refrn/index.md)

### 177.1 DBMS_TABLE_DATA Overview

The `DBMS_TABLE_DATA` package can be used to retrieve the byte value of a single column, or a series of columns, in any table.

These procedures, along with a publicly documented meta-data structure for columns, can be used to retrieve the `row content` for row data on which the hash or user signature is computed.

The procedures provide platform-neutral binary values for columns.

The procedures give you fine-grained control over the scope of a digital signature or cryptographic hash in terms of the columns you extract and the order in which you assemble the results.

### 177.2 DBMS_TABLE_DATA Security Model

The `DBMS_TABLE_DATA` package is owned by `SYS` and is installed as part of database installation. The routines in the package are run with invokers' rights (run with the privileges of the current user). The current user needs `SELECT` privileges on the table to extract column data.

### 177.3 Summary of DBMS_TABLE_DATA Subprograms

The `DBMS_TABLE_DATA` package uses `GET_BYTES_FOR_COLUMN`, `GET_BYTES_FOR_COLUMNS`, and `GET_BYTES_FOR_ROW` subprograms to perform various functions.

Table 177-1 DBMS_TABLE_DATA Package Subprograms

| Subprogram                      | Description                                                                                                                                                         |
|:--------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GET_BYTES_FOR_COLUMN Procedure  | Returns the `column_data` in bytes for the particular column with name `column_name for row_id` row in the particular table identified by `schema_name.table_name`. |
| GET_BYTES_FOR_COLUMNS Procedure | Returns a concatenated array of column byte values in `column_data` in the order of columns specified in the `column_names` array.                                  |
| GET_BYTES_FOR_ROW Procedure     | Returns a concatenated array of column byte values in `column_data` in the order of column positions for the particular row identified by `row_id`.                 |

#### 177.3.1 GET_BYTES_FOR_COLUMN Procedure

This procedure returns the `column_data` in bytes for the particular column with name `column_name` for `row_id` row in the particular table identified by `schema_name.table_name`.

##### Syntax

    DBMS_TABLE_DATA.GET_BYTES_FOR_COLUMN(
       schema_name       IN VARCHAR2,
       table_name            IN VARCHAR2,
       row_id                IN ROWID,
       column_name          IN VARCHAR2,
       column_data          IN OUT BLOB);

##### Parameters

Table 177-2 GET_BYTES_FOR_COLUMN Procedure Parameters

| Parameter     | Description             |
|:--------------|:------------------------|
| `schema_name` | The name of the schema. |
| `table_name`  | The name of the table.  |
| `row_id`      | The row id.             |
| `column_name` | The column name.        |
| `column_data` | The data in the column. |

##### Usage Notes

All arguments are required.

#### 177.3.2 GET_BYTES_FOR_COLUMNS Procedure

This procedure returns a concatenated array of column byte values in `column_data` in the order of columns specified in the `column_names` array.

##### Syntax

    DBMS_TABLE_DATA.GET_BYTES_FOR_COLUMNS(
       schema_name       IN VARCHAR2,
       table_name            IN VARCHAR2,
       row_id                IN ROWID,
       column_names         IN VARCHAR2,
       column_data          IN OUT BLOB);

##### Parameters

Table 177-3 GET_BYTES_FOR_COLUMNS Procedure Parameters

| Parameter      | Description               |
|:---------------|:--------------------------|
| `schema_name`  | The name of the schema.   |
| `table_name`   | The name of the table.    |
| `row_id`       | The row id.               |
| `column_names` | The names of the columns. |
| `column_data`  | The data in the columns.  |

##### Usage Notes

All arguments are required.

#### 177.3.3 GET_BYTES_FOR_ROW Procedure

This procedure returns a concatenated array of column byte values in `column_data` in the order of column positions for the particular row identified by `row_id`.

##### Syntax

    DBMS_TABLE_DATA.GET_BYTES_FOR_ROW(
       schema_name       IN VARCHAR2,
       table_name            IN VARCHAR2,
       row_id                IN ROWID,
       column_data          IN OUT BLOB);

##### Parameters

Table 177-4 GET_BYTES_FOR_ROW Procedure Parameters

| Parameter     | Description             |
|:--------------|:------------------------|
| `schema_name` | The name of the schema. |
| `table_name`  | The name of the table.  |
| `row_id`      | The row id.             |
| `column_data` | The data in the row.    |

##### Usage Notes

All arguments are required.
