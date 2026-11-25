## 159 DBMS_SODA

The `DBMS_SODA` package is a `PL/SQL` package implementing Simple Oracle Document Access (`SODA`). `SODA` allows you to use the Oracle Database as a NoSQL document store. The core abstraction provided by `SODA` is that of document collections. The `DBMS_SODA` package allows you to create, list, and delete document collections from `PL/SQL`, and to perform CRUD (create, replace, update, delete) operations on documents. All `DDL` functions are encapsulated within this package.

This chapter contains the following topics:

- DBMS_SODA Security Model

- Summary of DBMS_SODA Subprograms

**See Also:**

- [Oracle Database SODA for PL/SQL Developer's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/arpls&id=ADSDP-GUID-BE42F8D3-B86B-43B4-B2A3-5760A4DF79FB)

- [SODA Types](SODA_TYPES.md)

### 159.1 DBMS_SODA Security Model

This package is available to users with the `SODA_APP` role.

All SODA types (packages and types) are `SYS` types. `PUBLIC` is granted `EXECUTE` privilege on the `DBMS_SODA` described in this chapter.

### 159.2 Summary of DBMS_SODA Subprograms

This table lists the `DBMS_SODA` subprograms in alphabetical order and briefly describes them.

Table 159-1 DBMS_SODA Package Subprograms

| Subprogram                     | Purpose                                                                                                                                                                                     |
|:-------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CREATE_COLLECTION Function     | Creates a collection using the collection name and metadata.                                                                                                                                |
| DROP_COLLECTION Function       | Drops an existing collection from the user’s schema. This also removes all the documents in the collection.                                                                                 |
| GET_AS_OF_SCN Function         | This function returns the current database SCN number.                                                                                                                                      |
| GET_AS_OF_TIMESTAMP Function   | This function returns the current database timestamp value.                                                                                                                                 |
| LIST_COLLECTION_NAMES Function | Lists the collection names in the user's schema as a table of `NVARCHAR2`.                                                                                                                  |
| OPEN_COLLECTION Function       | Opens an existing collection.                                                                                                                                                               |
| TO_UUID Function               | This function is used to remap the version column of the collection table during Data Pump Import to UUID values. This function is only for use with the `REMAP_DATA` feature of Data Pump. |

#### 159.2.1 CREATE_COLLECTION Function

Creates a collection using the collection name and metadata. Uses the settings specified in the metadata and auto-assigns the ones that are not, and returns the collection object. If the metadata argument is omitted or set to `NULL`, a collection is created with default metadata. The returned collection is open for `read` and/or `write` operations. If a collection already exists, the function just opens and returns the collection object.

##### Syntax

    DBMS_SODA.CREATE_COLLECTION (
         collection_Name      IN NVARCHAR2,
         metadata             IN VARCHAR2 DEFAULT NULL,
         create_Mode          IN PLS_INTEGER DEFAULT CREATE_MODE_DDL)
     RETURN SODA_Collection_T;

##### Parameters

Table 159-2 CREATE_COLLECTION Parameters

| Parameter         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `collection_Name` | The name of the collection.<br>The value of `collection_Name` is case-sensitive.                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `metadata`        | The metadata of the collection in `VARCHAR2` format.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| create_Mode       | Valid values are:<br>• `DBMS_SODA.CREATE_MODE_DDL` (default). First attempts to create a new table for the collection. If table exists already, tries to map that existing table to the collection. Minimal checking is performed to ensure the table shape matches supplied collection metadata (if not, then an error is returned).<br>• `DBMS_SODA.CREATE_MODE_MAP`. Tries to map an existing table to the collection. Minimal checking is performed to ensure the table shape matches supplied collection metadata (if not, then an error is returned). |

##### Return Values

The function returns a `Soda_Collection_T` object representing the collection.

##### Exceptions

- `Descriptor Error`—if the input descriptor is invalid

- `Error`—if an error occurs while creating the collection

**See Also:**

[Oracle Database SODA for PL/SQL Developer's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/arpls&id=ADSDP-GUID-AC1A88D5-8C89-492D-AC57-E6F3694F6D96)

#### 159.2.2 DROP_COLLECTION Function

Drops an existing collection from the user’s schema. This also removes all the documents in the collection.

##### Syntax

    DBMS_SODA.DROP_COLLECTION (
         collection_Name      IN NVARCHAR2,
         purge                IN BOOLEAN DEFAULT FALSE,
         drop_Mapped_Table    IN BOOLEAN DEFAULT FALSE)
     RETURN NUMBER;

##### Parameters

Table 159-3 DROP_COLLECTION Parameters

| Parameter           | Description                                                                      |
|:--------------------|:---------------------------------------------------------------------------------|
| `collection_Name`   | The name of the collection.<br>The value of `collection_Name` is case-sensitive. |
| `purge`             | The default value is `FALSE`.                                                    |
| `drop_Mapped_Table` | The default value is `FALSE`.                                                    |

##### Return values

This function returns the following values:

- `1`—if the collection was dropped successfully

- `0`—if the collection does not exist

##### Exceptions

If an error occurs while dropping the collection, for example, due to uncommitted writes to the collection or privilege issues.

**See Also:**

[Oracle Database SODA for PL/SQL Developer's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/arpls&id=ADSDP-GUID-D29C4FFF-D093-4C1B-889A-5C29B63756C6)

#### 159.2.3 GET_AS_OF_SCN Function

This function returns the current database SCN number.

##### Syntax

    DBMS_SODA.GET_AS_OF_SCN ( )
     RETURN NUMBER;

##### Return values

This function returns the current database SCN number.

#### 159.2.4 GET_AS_OF_TIMESTAMP Function

This function returns the current database timestamp value.

##### Syntax

    DBMS_SODA.GET_AS_OF_TIMESTAMP ( )
     RETURN NUMBER;

##### Return values

This function returns the current database timestamp value.

#### 159.2.5 LIST_COLLECTION_NAMES Function

This function returns a list of collection names in the user’s schema as a table of `NVARCHAR2`.

##### Syntax

    DBMS_SODA.LIST_COLLECTION_NAMES ()
     RETURN SODA_CollName_List_T;

##### Return Values

This function returns a list of collection names as a table of `NVARCHAR2(255)`. The collection list is empty if there are no collections in the schema.

##### Exceptions

`Error`—if an error occurs while listing the collection names.

**See Also:**

[Oracle Database SODA for PL/SQL Developer's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/arpls&id=ADSDP-GUID-4568B14A-C54D-459B-B8B6-114A2148C4F1)

#### 159.2.6 OPEN_COLLECTION Function

Opens an existing collection for `read` and/or `write` operations.

##### Syntax

    DBMS_SODA.OPEN_COLLECTION (
         collection_Name      IN NVARCHAR2)
     RETURN SODA_Collection_T;

##### Parameters

Table 159-4 OPEN_COLLECTION Parameters

| Parameter         | Description                                                                      |
|:------------------|:---------------------------------------------------------------------------------|
| `collection_Name` | The name of the collection.<br>The value of `collection_Name` is case-sensitive. |

##### Return Values

This function returns the following values:

- a collection object which is open

- `NULL`, if the collection does not exist

##### Exceptions

`Error`—if an error occurs while creating the collection

**See Also:**

- [Opening an Existing Document Collection with SODA for PL/SQL](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/arpls&id=ADSDP-GUID-04A5F0A1-3A3F-4DDE-AF85-324C8CE698DB)
- [Checking Whether a Given Collection Exists with SODA for PL/SQL](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/arpls&id=ADSDP-GUID-ECE58906-DD2A-4593-93B8-201946632054)

#### 159.2.7 TO_UUID Function

This function is used to remap the version column of the collection table during Data Pump Import to UUID values. This function is only for use with the `REMAP_DATA` feature of Data Pump.

##### Syntax

    DBMS_SODA.TO_UUID (
         placeholder      IN   NVARCHAR2)
     RETURN VARCHAR2;

##### Parameters

Table 159-5 TO_UUID Parameters

| Parameter     | Description                                                                                                                         |
|:--------------|:------------------------------------------------------------------------------------------------------------------------------------|
| `placeholder` | This parameter is not used and can be ignored. It is used due to the syntactic constraints for the Data Pump `REMAP_DATA` function. |

##### Return values

This function returns a hexadecimal string that can be used as a `UUID` value.

**See Also:**

[REMAP_DATA](../sutil/datapump-import-utility.md) in the Oracle® Database Utilities Guide.
