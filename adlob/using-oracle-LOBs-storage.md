## 3  Using Oracle LOB Storage

Oracle LOB storage has two types, SecureFiles LOB storage and BasicFiles LOB storage, which are used with different types of tablespaces.

You design, create, and modify tables with LOB column types.

Topics:

- LOB Storage

- CREATE TABLE with LOB Storage

- ALTER TABLE with LOB Storage

- Initialization\_ Compatibility\_ and Upgrading

- Migrating Columns from BasicFiles LOBs to SecureFiles LOBs

- PL/SQL Packages for LOBs and DBFS

<!-- -->

- LOB Storage
  Earlier Oracle database releases supported only one type of LOB storage. In Oracle Database 11g, SecureFiles LOB storage was introduced; the original storage type was given the name BasicFiles LOB storage and became the default.
- CREATE TABLE with LOB Storage
  The `CREATE` `TABLE` statement works with LOB storage using parameters that are specific to SecureFiles or BasicFiles LOB storage, or both.
- ALTER TABLE with LOB Storage
  You can modify LOB storage with an `ALTER` `TABLE` statement and specific LOB-related parameters.
- Initialization, Compatibility, and Upgrading
  You must perform LOB initialization using appropriate compatibility parameters.
- Migrating Columns from BasicFiles LOBs to SecureFiles LOBs
- PL/SQL Packages for LOBs and DBFS
  There are PL/SQL packages that can be used with BasicFiles LOBs and SecureFiles LOBs.

**Parent topic:** [Getting Started](getting-started.md)

### 3.1 LOB Storage

Earlier Oracle database releases supported only one type of LOB storage. In Oracle Database 11g, SecureFiles LOB storage was introduced; the original storage type was given the name BasicFiles LOB storage and became the default.

LOBs created using BasicFiles LOB storage became known as BasicFiles LOBs and LOBs created using SecureFiles LOB storage were named SecureFiles LOBs. The `CREATE` `TABLE` statement added new keywords to indicate the differences: `BASICFILE` specifies BasicFiles LOB storage and `SECUREFILE` specifies SecureFiles LOB storage.

Beginning with Oracle Database 12c, SecureFiles LOB storage became the default in the `CREATE` `TABLE` statement. If no storage type is explicitly specified, new LOB columns use SecureFiles LOB storage.

The term LOB can represent LOBs of either storage type unless the storage type is explicitly indicated, by name or by reference to archiving or linking (can only apply to the SecureFiles LOB storage type).

**See Also:**

Initialization, Compatibility, and Upgrading for more information about Initialization and compatibility.

The following sections discuss the two storage types in detail:

- BasicFiles LOB Storage

- SecureFiles LOB Storage

<!-- -->

- BasicFiles LOB Storage
  You must use BasicFiles LOB storage for LOB storage in tablespaces that are not managed with Automatic Segment Space Management (ASSM).
- SecureFiles LOB Storage
  SecureFiles LOBs can only be created in tablespaces managed with Automatic Segment Space Management (ASSM), unlike BasicFiles LOB storage.

**Parent topic:** Using Oracle LOB Storage

#### 3.1.1 BasicFiles LOB Storage

You must use BasicFiles LOB storage for LOB storage in tablespaces that are not managed with Automatic Segment Space Management (ASSM).

**Parent topic:** LOB Storage

#### 3.1.2 SecureFiles LOB Storage

SecureFiles LOBs can only be created in tablespaces managed with Automatic Segment Space Management (ASSM), unlike BasicFiles LOB storage.

SecureFiles LOB storage is designed to provide much better performance and scalability compared to BasicFiles LOBs and to meet or exceed the performance capabilities of traditional network file systems.

SecureFiles LOB storage supports three features that are not available with the BasicFiles LOB storage option: compression, deduplication, and encryption.

Oracle recommends that you enable compression, deduplication, and encryption through the `CREATE TABLE` statement. If you enable these features through the `ALTER TABLE` statement, all SecureFiles LOB data in the table is read, modified, and written; this can cause the database to lock the table during a potentially lengthy operation, though there are online capabilities in the `ALTER` `TABLE` statement which can help you avoid this issue.

Topics:

- About Advanced LOB Compression

- About Advanced LOB Deduplication

- About SecureFiles Encryption

<!-- -->

- About Advanced LOB Compression
  Advanced LOB Compression transparently analyzes and compresses SecureFiles LOB data to save disk space and improve performance.
- About Advanced LOB Deduplication
  Advanced LOB Deduplication enables Oracle Database to automatically detect duplicate LOB data within a LOB column or partition, and conserve space by storing only one copy of the data.
- About SecureFiles Encryption
  SecureFiles Encryption introduces a new encryption facility for LOBs. The data is encrypted using Transparent Data Encryption (TDE), which allows the data to be stored securely, and still allows for random read and write access.

**Parent topic:** LOB Storage

##### 3.1.2.1 About Advanced LOB Compression

Advanced LOB Compression transparently analyzes and compresses SecureFiles LOB data to save disk space and improve performance.

License Requirement: You must have a license for the Oracle Advanced Compression Option to implement Advanced LOB Compression.

**See Also:**

- "CREATE TABLE with Advanced LOB Compression"

- "ALTER TABLE with Advanced LOB Compression"

**Parent topic:** SecureFiles LOB Storage

##### 3.1.2.2 About Advanced LOB Deduplication

Advanced LOB Deduplication enables Oracle Database to automatically detect duplicate LOB data within a LOB column or partition, and conserve space by storing only one copy of the data.

License Requirement: You must have a license for the Oracle Advanced Compression Option to implement Advanced LOB Deduplication.

**See Also:**

- "CREATE TABLE with Advanced LOB Deduplication"

- "ALTER TABLE with Advanced LOB Deduplication"

**Parent topic:** SecureFiles LOB Storage

##### 3.1.2.3 About SecureFiles Encryption

SecureFiles Encryption introduces a new encryption facility for LOBs. The data is encrypted using Transparent Data Encryption (TDE), which allows the data to be stored securely, and still allows for random read and write access.

License Requirement: You must have a license for the Oracle Advanced Security Option to implement SecureFiles Encryption.

**See Also:**

- "CREATE TABLE with SecureFiles Encryption"

- "ALTER TABLE with SecureFiles Encryption"

**Parent topic:** SecureFiles LOB Storage

### 3.2 CREATE TABLE with LOB Storage

The `CREATE` `TABLE` statement works with LOB storage using parameters that are specific to SecureFiles or BasicFiles LOB storage, or both.

Example 3-1 provides the syntax for `CREATE` `TABLE` in Backus Naur (BNF) notation, with LOB-specific parameters in bold.

The `SHRINK` option is not supported for SecureFiles LOBs.

**See Also:**

- CREATE TABLE LOB Storage Parameters for parameter descriptions and the `CREATE TABLE` statement

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md)

Example 3-1 BNF for CREATE TABLE

    CREATE [ GLOBAL TEMPORARY ] TABLE
       [ schema.]table OF
       [ schema.]object_type
       [ ( relational_properties ) ]
       [ ON COMMIT { DELETE | PRESERVE } ROWS ]
       [ OID_clause ]
       [ OID_index_clause ]
       [ physical_properties ]
       [ table_properties ] ;
    <relational_properties> ::=
    { column_definition
    | { out_of_line_constraint
      | out_of_line_ref_constraint
      | supplemental_logging_props
      }
    }
      [, { column_definition
         | { out_of_line_constraint
           | out_of_line_ref_constraint
           | supplemental_logging_props
           }
      ]...
     <column_definition> ::=
    column data_type [ SORT ]
          [ DEFAULT expr ]
          [ ENCRYPT encryption_spec ]
          [ ( inline_constraint [ inline_constraint ] ... )
          | inline_ref_constraint
          ]
    <data_type> ::=
    { Oracle_built_in_datatypes
    | ANSI_supported_datatypes
    | user_defined_types
    | Oracle_supplied_types
    }

    <Oracle_built_in_datatypes> ::=
    { character_datatypes
    | number_datatypes
    | long_and_raw_datatypes
    | datetime_datatypes
    | large_object_datatypes
    | rowid_datatypes
    }
    <large_object_datatypes> ::=
    { BLOB | CLOB | NCLOB| BFILE }
    <table_properties> ::=
      [ column_properties ]
      [ table_partitioning_clauses ]
      [ CACHE | NOCACHE ]
      [ parallel_clause ]
      [ ROWDEPENDENCIES | NOROWDEPENDENCIES ]
      [ enable_disable_clause ]
      [ enable_disable_clause ]...
      [ row_movement_clause ]
      [ AS subquery ]
    <column_properties> ::=
      { object_type_col_properties
      | nested_table_col_properties
      | { varray_col_properties | LOB_storage_clause }
        [ (LOB_partition_storage
            [, LOB_partition_storage ]...
          )
        ]
      | XMLType_column_properties
      }
      [ { object_type_col_properties
        | nested_table_col_properties
        | { varray_col_properties | LOB_storage_clause }
          [ ( LOB_partition_storage
              [, LOB_partition_storage ]...
            )
          ]
        | XMLType_column_properties
        }
      ]...
    <LOB_partition_storage> ::=
      PARTITION partition
      { LOB_storage_clause | varray_col_properties }
        [ LOB_storage_clause | varray_col_properties ]...
      [ ( SUBPARTITION subpartition
         { LOB_storage_clause | varray_col_properties }
           [ LOB_storage_clause
           | varray_col_properties
           ]...
        )
      ]
    <LOB_storage_clause> ::=
      LOB
      { (LOB_item [, LOB_item ]...)
          STORE AS [ SECUREFILE | BASICFILE ] (LOB_storage_parameters)
      | (LOB_item)
          STORE AS [ SECUREFILE | BASICFILE ]
            { LOB_segname (LOB_storage_parameters)
            | LOB_segname
            | (LOB_storage_parameters)
            }
      }
    <LOB_storage_parameters> ::=
      { TABLESPACE tablespace
      | { LOB_parameters [ storage_clause ]
        }
      | storage_clause
      }
        [ TABLESPACE tablespace
        | { LOB_parameters [ storage_clause ]
          }
        ]...
    <LOB_parameters> ::=
      [ { ENABLE | DISABLE } STORAGE IN ROW
      | CHUNK integer
      | PCTVERSION integer
      | RETENTION [ { MAX | MIN integer | AUTO | NONE } ]
      | FREEPOOLS integer
      | LOB_deduplicate_clause
      | LOB_compression_clause
      | LOB_encryption_clause
      | { CACHE |  NOCACHE | CACHE READS } [ logging_clause ] } }
      ]
    <logging_clause> ::=
      { LOGGING | NOLOGGING | FILESYSTEM_LIKE_LOGGING }
    <storage_clause> ::=
      STORAGE
      ({ INITIAL integer [ K | M ]
       | NEXT integer [ K | M ]
       | MINEXTENTS integer
       | MAXEXTENTS { integer | UNLIMITED }
       | PCTINCREASE integer
       | FREELISTS integer
       | FREELIST GROUPS integer
       | OPTIMAL [ integer [ K | M ]
                 | NULL
                 ]
       | BUFFER_POOL { KEEP | RECYCLE | DEFAULT }
       }
         [ INITIAL integer [ K | M ]
         | NEXT integer [ K | M ]
         | MINEXTENTS integer
         | MAXEXTENTS { integer | UNLIMITED }
         | MAXSIZE { { integer { K | M | G | T | P } } | UNLIMITED }
         | PCTINCREASE integer
         | FREELISTS integer
         | FREELIST GROUPS integer
         | OPTIMAL [ integer [ K | M ]
                   | NULL
                   ]
         | BUFFER_POOL { KEEP | RECYCLE | DEFAULT }
         ]...
      )
    <LOB_deduplicate_clause> ::=
      { DEDUPLICATE
      | KEEP_DUPLICATES
      }
    <LOB_compression_clause> ::=
      { COMPRESS [ HIGH | MEDIUM | LOW ]
      | NOCOMPRESS
      }
    <LOB_encryption_clause> ::=
      { ENCRYPT [ USING 'encrypt_algorithm' ]
        [ IDENTIFIED BY password ]
      | DECRYPT
      }
    <XMLType_column_properties> ::=
    XMLTYPE [ COLUMN ] column
       [ XMLType_storage ]
       [ XMLSchema_spec ]
    <XMLType_storage> ::=
           STORE AS
       { OBJECT RELATIONAL
       | [ SECUREFILE | BASICFILE ] { CLOB | BINARY XML }
           [ { LOB_segname [ (LOB_parameters) ]
             | LOB_parameters
             }
             ]
    <varray_col_properties> ::=

            VARRAY varray_item
       { [ substitutable_column_clause ]
         STORE AS [ SECUREFILE | BASICFILE ] LOB
            { [ LOB_segname ] (LOB_parameters)
            | LOB_segname
            }
       | substitutable_column_clause
       }

- CREATE TABLE LOB Storage Parameters
  The `CREATE TABLE` statement uses parameters relating to LOB storage, and more specifically to either BasicFiles LOB or SecureFiles LOB.
- CREATE TABLE and SecureFiles LOB Features
  Note usage notes and examples for SecureFiles LOBs used with the`CREATE` `TABLE`.

**Parent topic:** Using Oracle LOB Storage

#### 3.2.1 CREATE TABLE LOB Storage Parameters

The `CREATE TABLE` statement uses parameters relating to LOB storage, and more specifically to either BasicFiles LOB or SecureFiles LOB.

Table 3-1 summarizes the parameters of the `CREATE TABLE` statement that relate to LOB storage, where necessary noting whether a parameter is specific to BasicFiles LOB or SecureFiles LOB storage.

Table 3-1 Parameters of CREATE TABLE Statement Related to LOBs

| Parameter                                            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-----------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `BASICFILE`                                          | Specifies BasicFiles LOB storage, the original architecture for LOBs.<br>If you set the compatibility mode to Oracle Database 11g, then `BASICFILE` functionality is enabled by default and specified for completeness.<br>Starting with Oracle Database 12c, you must explicitly specify the parameter `BASICFILE` to use the BasicFiles LOB storage type. Otherwise, the `CREATE` `TABLE` statement uses SecureFiles LOB, the current default.<br>For BasicFiles LOBs, specifying any of the SecureFiles LOB options results in an error.<br>**See Also:**<br>Initialization, Compatibility, and Upgrading                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `SECUREFILE`                                         | Specifies SecureFiles LOBs storage.<br>Starting with Oracle Database 12c, the SecureFiles LOB storage type, specified by the parameter `SECUREFILE`, is the default.<br>A SecureFiles LOB can only be created in a tablespace managed with Automatic Segment Space Management (ASSM).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `CHUNK`                                              | For BasicFiles LOBs, specifies the chunk size when creating a table that stores LOBs.<br>`CHUNK` is one or more Oracle blocks and corresponds to the data size used by Oracle Database when accessing or modifying the LOB.<br>For SecureFiles LOBs, it is an advisory size provided for backward compatibility.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `RETENTION`                                          | Configures the LOB column to store old versions of LOB data in a specified manner.<br>In Oracle Database Release 12c, this parameter specifies the retention policy.<br>`RETENTION` has these possible values:<br>• `MAX` specifies that the system keep old versions of LOB data blocks until the space used by the segment has reached the size specified in the `MAXSIZE` parameter. If `MAXSIZE` is not specified, `MAX` behaves like `AUTO`.<br>• `MIN` specifies that the system keep old versions of LOB data blocks for the specified number of seconds.<br>• `NONE` specifies that there is no retention period and space can be reused in any way deemed necessary.<br>• `AUTO` specifies that the system manage the space as efficiently as possible weighing both time and space needs.<br>**See Also:**<br>[RETENTION Parameter for BasicFiles LOBs](LOB-storage-with-applications.md) for more information about `RETENTION` parameter used with BasicFiles LOBs.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `MAXSIZE`                                            | Specifies the upper limit of storage space that a LOB may use.<br>If this amount of space is consumed, new LOB data blocks are taken from the pool of old versions of LOB data blocks as needed, regardless of time requirements.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `FREEPOOLS`                                          | Specifies the number of `FREELIST` groups for BasicFiles LOBs, if the database is in automatic undo mode. Under Release 12c compatibility, this parameter is ignored when SecureFiles LOBs are created.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `LOGGING`, `NOLOGGING`, or `FILESYSTEM_LIKE_LOGGING` | Specifies logging options:<br>• `LOGGING` specifies logging the creation of the LOB and subsequent inserts into the LOB, in the redo log file. `LOGGING` is the default.<br>• `NOLOGGING` specifies no logging.<br>• `FILESYSTEM_LIKE_LOGGING` specifies that the system only logs the metadata. This is similar to metadata journaling of file systems, which reduces mean time to recovery from failures. `FILESYSTEM_LIKE_LOGGING` ensures that data is completely recoverable (an instance recovery) after a server failure.<br>• This option is invalid for BasicFiles LOBs.<br>For SecureFiles LOBs, the following applies:<br>• The `NOLOGGING` setting is converted internally to `FILESYSTEM_LIKE_LOGGING.`<br>• The `LOGGING` setting is similar to the data journaling of file systems.<br>• Both the `LOGGING` and `FILESYSTEM_LIKE_LOGGING` settings provide a complete transactional file system.<br>For a non-partitioned object, the value specified for this clause is the actual physical attribute of the segment associated with the object.<br>For partitioned objects, the value specified for this clause is the default physical attribute of the segments associated with all partitions specified in the `CREATE` statement (and in subsequent `ALTER` ... `ADD PARTITION` statements), unless you specify the logging attribute in the `PARTITION` description.<br>CAUTION:<br>For LOB segments with `NOLOGGING` or `FILESYSTEM_LIKE_LOGGING` settings, it is possible that data can change on the disk during a backup operation. This results in read inconsistency. To avoid this situation, ensure that changes to LOB segments are saved in the redo log file by setting `LOGGING` for LOB storage.<br>`NOLOGGING` and `FILESYSTEM_LIKE_LOGGING` SecureFiles are recoverable after an instance failure, but not after a media failure. `LOGGING` SecureFiles are recoverable after both instance and media failures.<br>**See Also:**<br>• [Oracle Database Backup and Recovery User’s Guide](../bradv/introduction-backup-recovery.md) for a discussion of data protection, media failure, and instance failure.<br>• [LOGGING / NOLOGGING Parameter for BasicFiles LOBs](LOB-storage-with-applications.md)<br>• [Ensuring Read Consistency](using-LOB-APIs.md) |
| `FREELISTS` or `FREELIST` `GROUPS`                   | Specifies the number of process freelists or freelist groups, respectively, allocated to the segment; `NULL` for partitioned tables. Under Release 12c compatibility, these parameters are ignored when SecureFiles LOBs are created.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `PCTVERSION`                                         | Specifies the percentage of used BasicFiles LOB data space that may be occupied by old versions of the LOB data pages.<br>Under Release 12c compatibility, this parameter is ignored when SecureFiles LOBs are created.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `COMPRESS` or `NOCOMPRESS`                           | The `COMPRESS` option turns on Advanced LOB Compression, and `NOCOMPRESS` turns it off.<br>Note that setting table or index compression does not affect Advanced LOB Compression.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `DEDUPLICATE` or `KEEP_DUPLICATES`                   | The `DEDUPLICATE` option enables Advanced LOB Deduplication; it specifies that SecureFiles LOB data that is identical in two or more rows in a LOB column, partition or subpartition must share the same data blocks. The database combines SecureFiles LOBs with identical content into a single copy, reducing storage and simplifying storage management. The opposite of this option is `KEEP_DUPLICATES`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `ENCRYPT` or `DECRYPT`                               | The `ENCRYPT` option turns on SecureFiles Encryption, and encrypts all SecureFiles LOB data using Oracle Transparent Data Encryption (TDE). The `DECRYPT` options turns off SecureFiles Encryption.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |

**Parent topic:** CREATE TABLE with LOB Storage

#### 3.2.2 CREATE TABLE and SecureFiles LOB Features

Note usage notes and examples for SecureFiles LOBs used with the`CREATE` `TABLE`.

This section provides usage notes and examples for features specific to SecureFiles LOBs used with `CREATE` `TABLE`.

**Note:**

Clauses in example discussions refer to the Backus Naur (BNF) notation Example 3-1.

**See Also:**

CREATE TABLE LOB Storage Parameters for more information about parameters

Topics:

- CREATE TABLE with Advanced LOB Compression

- CREATE TABLE with Advanced LOB Deduplication

- CREATE TABLE with SecureFiles Encryption

<!-- -->

- CREATE TABLE with Advanced LOB Compression
  You can use Advanced LOB Compression with the `CREATE TABLE` statement under certain circumstances.
- CREATE TABLE with Advanced LOB Deduplication
  You can use Advanced LOB Deduplication with the `CREATE TABLE` statement.
- CREATE TABLE with SecureFiles Encryption
  You can use SecureFiles Encryption with the `CREATE TABLE` statement.

**Parent topic:** CREATE TABLE with LOB Storage

##### 3.2.2.1 CREATE TABLE with Advanced LOB Compression

You can use Advanced LOB Compression with the `CREATE TABLE` statement under certain circumstances.

Topics:

- Usage Notes for Advanced LOB Compression

- Examples of CREATE TABLE and Advanced LOB Compression

<!-- -->

- Usage Notes for Advanced LOB Compression
  Consider these issues when using the `CREATE` `TABLE` statement and Advanced LOB Compression.
- Examples of CREATE TABLE and Advanced LOB Compression
  These examples demonstrate how to issue `CREATE TABLE` statements for specific compression scenarios.

**Parent topic:** CREATE TABLE and SecureFiles LOB Features

###### 3.2.2.1.1 Usage Notes for Advanced LOB Compression

Consider these issues when using the `CREATE` `TABLE` statement and Advanced LOB Compression.

- Advanced LOB Compression is performed on the server and enables random reads and writes to LOB data. Compression utilities on the client, like `utl_compress`, cannot provide random access.

- Advanced LOB Compression does not enable table or index compression. Conversely, table and index compression do not enable Advanced LOB Compression.

- The `LOW`, `MEDIUM`, and `HIGH` options provide varying degrees of compression. The higher the compression, the higher the latency incurred. The `HIGH` setting incurs more work, but compresses the data better. The default is `MEDIUM`.

  The `LOW` compression option uses an extremely lightweight compression algorithm that removes the majority of the CPU cost that is typical with file compression. Compressed SecureFiles LOBs at the `LOW` level provide a very efficient choice for SecureFiles LOB storage. SecureFiles LOBs compressed at `LOW` generally consume less CPU time and less storage than BasicFiles LOBs, and typically help the application run faster because of a reduction in disk I/O.

- Compression can be specified at the partition level. The `CREATE` `TABLE` `lob_storage_clause` enables specification of compression for partitioned tables on a per-partition basis.

- The `DBMS_LOB.SETOPTIONS` procedure can enable and disable compression on individual SecureFiles LOBs.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md) for more information about `DBMS_LOB.SETOPTIONS` procedure

**Parent topic:** CREATE TABLE with Advanced LOB Compression

###### 3.2.2.1.2 Examples of CREATE TABLE and Advanced LOB Compression

These examples demonstrate how to issue `CREATE TABLE` statements for specific compression scenarios.

Example 3-2 Creating a SecureFiles LOB Column with LOW Compression

    CREATE TABLE t1 (a CLOB)
        LOB(a) STORE AS SECUREFILE(
        COMPRESS LOW
        CACHE
        NOLOGGING
      );

Example 3-3 Creating a SecureFiles LOB Column with MEDIUM (default) Compression

    CREATE TABLE t1 ( a CLOB)
        LOB(a) STORE AS SECUREFILE (
             COMPRESS
             CACHE
             NOLOGGING
        );

Example 3-4 Creating a SecureFiles LOB Column with HIGH Compression

    CREATE TABLE t1 ( a CLOB)
        LOB(a) STORE AS SECUREFILE (
             COMPRESS HIGH
             CACHE
        );

Example 3-5 Creating a SecureFiles LOB Column with Disabled Compression

    CREATE TABLE t1 ( a CLOB)
        LOB(a) STORE AS SECUREFILE (
             NOCOMPRESS
             CACHE
        );

Example 3-6 Creating a SecureFiles LOB Column with Compression on One Partition

    CREATE TABLE t1 ( REGION VARCHAR2(20), a BLOB)
         LOB(a) STORE AS SECUREFILE (
            CACHE
         )
         PARTITION BY LIST (REGION) (
              PARTITION p1 VALUES ('x', 'y')
                   LOB(a) STORE AS SECUREFILE (
                       COMPRESS
                    ),
              PARTITION p2 VALUES (DEFAULT)
         );

**Parent topic:** CREATE TABLE with Advanced LOB Compression

##### 3.2.2.2 CREATE TABLE with Advanced LOB Deduplication

You can use Advanced LOB Deduplication with the `CREATE TABLE` statement.

Topics:

- Usage Notes for Advanced LOB Deduplication

- Examples of CREATE TABLE and Advanced LOB Deduplication

<!-- -->

- Usage Notes for Advanced LOB Deduplication
  Consider these issues when using `CREATE` `TABLE` and Advanced LOB Deduplication.
- Examples of CREATE TABLE and Advanced LOB Deduplication
  These examples demonstrate how to issue `CREATE TABLE` statements for specific deduplication scenarios.

**Parent topic:** CREATE TABLE and SecureFiles LOB Features

###### 3.2.2.2.1 Usage Notes for Advanced LOB Deduplication

Consider these issues when using `CREATE` `TABLE` and Advanced LOB Deduplication.

- Identical LOBs are good candidates for deduplication. Copy operations can avoid data duplication by enabling deduplication.

- Duplicate detection happens within a LOB segment. Duplicate detection does not span partitions or subpartitions for partitioned and subpartitioned LOB columns.

- Deduplication can be specified at a partition level. The `CREATE` `TABLE` `lob_storage_clause` enables specification for partitioned tables on a per-partition basis.

- The `DBMS_LOB.SETOPTIONS` procedure can enable or disable deduplication on individual LOBs.

**Parent topic:** CREATE TABLE with Advanced LOB Deduplication

###### 3.2.2.2.2 Examples of CREATE TABLE and Advanced LOB Deduplication

These examples demonstrate how to issue `CREATE TABLE` statements for specific deduplication scenarios.

Example 3-7 Creating a SecureFiles LOB Column with Deduplication

    CREATE TABLE t1 ( a CLOB)
        LOB(a) STORE AS SECUREFILE (
            DEDUPLICATE
            CACHE
        );

Example 3-8 Creating a SecureFiles LOB Column with Disabled Deduplication

    CREATE TABLE t1 ( a CLOB)
        LOB(a) STORE AS SECUREFILE (
             KEEP_DUPLICATES
             CACHE
        );

Example 3-9 Creating a SecureFiles LOB Column with Deduplication on One Partition

    CREATE TABLE t1 ( REGION VARCHAR2(20), a BLOB)
         LOB(a) STORE AS SECUREFILE (
               CACHE
    )
    PARTITION BY LIST (REGION) (
         PARTITION p1 VALUES ('x', 'y')
              LOB(a) STORE AS SECUREFILE (
                   DEDUPLICATE
              ),
         PARTITION p2 VALUES (DEFAULT)
    );

Example 3-10 Creating a SecureFiles LOB column with Deduplication Disabled on One Partition

    CREATE TABLE t1 ( REGION VARCHAR2(20), ID NUMBER, a BLOB)
         LOB(a) STORE AS SECUREFILE (
               DEDUPLICATE
               CACHE
    )
    PARTITION BY RANGE (REGION)
          SUBPARTITION BY HASH(ID) SUBPARTITIONS 2 (
            PARTITION p1 VALUES LESS THAN (51)
               lob(a) STORE AS a_t2_p1
               (SUBPARTITION t2_p1_s1 lob(a) STORE AS a_t2_p1_s1,
                SUBPARTITION t2_p1_s2 lob(a) STORE AS a_t2_p1_s2),
            PARTITION p2 VALUES LESS THAN (MAXVALUE)
               lob(a) STORE AS a_t2_p2 ( KEEP_DUPLICATES )
               (SUBPARTITION t2_p2_s1 lob(a) STORE AS a_t2_p2_s1,
                SUBPARTITION t2_p2_s2 lob(a) STORE AS a_t2_p2_s2)
          );

**Parent topic:** CREATE TABLE with Advanced LOB Deduplication

##### 3.2.2.3 CREATE TABLE with SecureFiles Encryption

You can use SecureFiles Encryption with the `CREATE TABLE` statement.

Topics:

- Usage Notes for SecureFiles Encryption

- Examples of CREATE TABLE and SecureFiles Encryption

<!-- -->

- Usage Notes for SecureFiles Encryption
  Consider these issues when using `CREATE` `TABLE` and SecureFiles Encryptions
- Examples of CREATE TABLE and SecureFiles Encryption
  These examples demonstrate how to issue `CREATE TABLE` statements for specific encryption scenarios.

**Parent topic:** CREATE TABLE and SecureFiles LOB Features

###### 3.2.2.3.1 Usage Notes for SecureFiles Encryption

Consider these issues when using `CREATE` `TABLE` and SecureFiles Encryptions

- Transparent Data Encryption (TDE) supports encryption of LOB data types.

- Encryption is performed at the block level.

- The `encrypt_algorithm` indicates the name of the encryption algorithm. Valid algorithms are: `AES192` (default), `AES128`, and `AES256`.

- The column encryption key is derived from `PASSWORD`, if specified.

- The default for LOB encryption is `SALT`. `NO` `SALT` is not supported.

- All LOBs in the LOB column are encrypted.

- `DECRYPT` keeps the LOBs in clear text.

- LOBs can be encrypted only on a per-column basis, similar to TDE. All partitions within a LOB column are encrypted.

- Key management controls the ability to encrypt or decrypt.

- TDE is not supported by the traditional `import` and `export` utilities or by transportable-tablespace-based `export`. Use the Data Pump `expdb` and `impdb` utilities with encrypted columns instead.

  **See Also:**

  "[Oracle Database Advanced Security Guide ](../asoag/asopart1.md)for information about using the `ADMINISTER` `KEY` `MANAGEMENT` statement to create TDE keystores

**Parent topic:** CREATE TABLE with SecureFiles Encryption

###### 3.2.2.3.2 Examples of CREATE TABLE and SecureFiles Encryption

These examples demonstrate how to issue `CREATE TABLE` statements for specific encryption scenarios.

Example 3-11 Creating a SecureFiles LOB Column with a Specific Encryption Algorithm

    CREATE TABLE t1 ( a CLOB ENCRYPT USING 'AES128')
        LOB(a) STORE AS SECUREFILE (
             CACHE
        );

Example 3-12 Creating a SecureFiles LOB column with encryption for all partitions

    CREATE TABLE t1 ( REGION VARCHAR2(20), a BLOB)
      LOB(a) STORE AS SECUREFILE (
      ENCRYPT USING 'AES128'
      NOCACHE
      FILESYSTEM_LIKE_LOGGING
    )
    PARTITION BY LIST (REGION) (
    PARTITION p1 VALUES ('x', 'y'),
    PARTITION p2 VALUES (DEFAULT)
    );

Example 3-13 Creating a SecureFiles LOB Column with Encryption Based on a Password Key

    CREATE TABLE t1 ( a CLOB ENCRYPT IDENTIFIED BY foo)
        LOB(a) STORE AS SECUREFILE (
            CACHE
        );

The following example has the same result because the encryption option can be set in the `LOB_deduplicate_clause` section of the statement:

    CREATE TABLE t1 (a CLOB)
        LOB(a) STORE AS SECUREFILE (
            CACHE
            ENCRYPT
            IDENTIFIED BY foo
        );

Example 3-14 Creating a SecureFiles LOB Column with Disabled Encryption

    CREATE TABLE t1 ( a CLOB )
        LOB(a) STORE AS SECUREFILE (
            CACHE DECRYPT
        );

**Parent topic:** CREATE TABLE with SecureFiles Encryption

### 3.3 ALTER TABLE with LOB Storage

You can modify LOB storage with an `ALTER` `TABLE` statement and specific LOB-related parameters.

Topics:

- About ALTER TABLE and LOB Storage

- BNF for the ALTER TABLE Statement

- ALTER TABLE LOB Storage Parameters

- ALTER TABLE SecureFiles LOB Features

<!-- -->

- About ALTER TABLE and LOB Storage
  You can use `ALTER` `TABLE` to enable compression, deduplication, or encryption features for a LOB column.
- BNF for the ALTER TABLE Statement
  This Backus Naur (BNF) notation provides the syntax for `ALTER` `TABLE` with LOB-specific parameters in bold.
- ALTER TABLE LOB Storage Parameters
  You must use specific parameters of the `ALTER TABLE` statement that relate to LOB storage.
- ALTER TABLE SecureFiles LOB Features
  Certain features specific to SecureFiles LOBs work with the `ALTER` `TABLE`statement.

**Parent topic:** Using Oracle LOB Storage

#### 3.3.1 About ALTER TABLE and LOB Storage

You can use `ALTER` `TABLE` to enable compression, deduplication, or encryption features for a LOB column.

The `ALTER` `TABLE` statement supports online operations and Oracle Database supports parallel operations on SecureFiles LOBs columns, making this a resource-efficient approach.

As an alternative to `ALTER` `TABLE`, you can use online redefinition to enable one or more of these features. As with `ALTER` `TABLE`, online redefinition of SecureFiles LOB columns can be executed in parallel.

Note that the `SHRINK` option is not supported for SecureFiles LOBs.

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md) for more information about `ALTER` `TABLE` statement

- Migrating Columns from BasicFiles LOBs to SecureFiles LOBs for more information about online redefinition

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_REDEFINITION.md) for more information about `DBMS_REDEFINITION` package

**Parent topic:** ALTER TABLE with LOB Storage

#### 3.3.2 BNF for the ALTER TABLE Statement

This Backus Naur (BNF) notation provides the syntax for `ALTER` `TABLE` with LOB-specific parameters in bold.

**See Also:**

- CREATE TABLE LOB Storage Parameters for parameter descriptions

- [Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md) for more information about `ALTER TABLE` statement

<!-- -->

    ALTER TABLE [ schema.]table
    [ alter_table_properties
    | column_clauses
    | constraint_clauses
    | alter_table_partitioning
    | alter_external_table_clauses
    | move_table_clause
    ]
    [ enable_disable_clause
    | { ENABLE | DISABLE }
    { TABLE LOCK | ALL TRIGGERS }
    [ enable_disable_clause
    | { ENABLE | DISABLE }
    { TABLE LOCK | ALL TRIGGERS }
    ]...
    ] ;
    <column_clauses> ::=
    { { add_column_clause
    | modify_column_clause
    | drop_column_clause
    }
    [ add_column_clause
    | modify_column_clause
    | drop_column_clause
    ]...
    | rename_column_clause
    | modify_collection_retrieval
    [ modify_collection_retrieval ]...
    | modify_LOB_storage_clause
    [ modify_LOB_storage_clause ] ...
    | alter_varray_col_properties
    [ alter_varray_col_properties ]
    }
    <modify_LOB_storage_clause> ::=
    MODIFY LOB (LOB_item) ( modify_LOB_parameters )
    <modify_LOB_parameters> ::=
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

**Parent topic:** ALTER TABLE with LOB Storage

#### 3.3.3 ALTER TABLE LOB Storage Parameters

You must use specific parameters of the `ALTER TABLE` statement that relate to LOB storage.

Parameters may be specific to BasicFiles LOB or SecureFiles LOB storage, as indicated.

Table 3-2 Parameters of ALTER TABLE Statement Related to LOBs

| Parameter                          | Description                                                                                                                                                                                                                                                                                                                                                                     |
|:-----------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `RETENTION`                        | Configures the LOB column to store old versions of LOB data in a specified manner. Altering `RETENTION` only affects space created after the `ALTER` `TABLE` statement runs.                                                                                                                                                                                                    |
| `COMPRESS` or `NOCOMPRESS`         | Enables or disables Advanced LOB Compression. All LOBs in the LOB segment are altered with the new setting.                                                                                                                                                                                                                                                                     |
| `DEDUPLICATE` or `KEEP_DUPLICATES` | Enables or disables Advanced LOB Deduplication.<br>The option `DEDUPLICATE` enables you to specify that LOB data that is identical in two or more rows in a LOB column share the same data blocks. The database combines LOBs with identical content into a single copy, reducing storage and simplifying storage management. The opposite of this option is `KEEP_DUPLICATES`. |
| `ENCRYPT` or `DECRYPT`             | Enables or disables SecureFiles LOB encryption. Alters all LOBs in the LOB segment with the new setting. A LOB segment can be only altered to enable or disable LOB encryption. That is, `ALTER` cannot be used to update the encryption algorithm or the encryption key. Update the encryption algorithm or encryption key using the `ALTER TABLE REKEY` syntax.               |

**Parent topic:** ALTER TABLE with LOB Storage

#### 3.3.4 ALTER TABLE SecureFiles LOB Features

Certain features specific to SecureFiles LOBs work with the `ALTER` `TABLE`statement.

These SecureFiles LOBs features work with `ALTER` `TABLE` as described in the usage notes and examples.

**Note:**

Clauses in example discussions refer to the Backus Naur (BNF) notation "BNF for the ALTER TABLE Statement".

Parameters are described in "ALTER TABLE LOB Storage Parameters".

Topics:

- ALTER TABLE with Advanced LOB Compression

- ALTER TABLE with Advanced LOB Deduplication

- ALTER TABLE with SecureFiles Encryption

<!-- -->

- ALTER TABLE with Advanced LOB Compression
  Advanced LOB Compression works with the `ALTER TABLE` statement.
- ALTER TABLE with Advanced LOB Deduplication
  Advanced LOB Deduplication works with the `ALTER TABLE` statement.
- ALTER TABLE with SecureFiles Encryption
  SecureFiles Encryption works with the `ALTER TABLE` statement.

**Parent topic:** ALTER TABLE with LOB Storage

##### 3.3.4.1 ALTER TABLE with Advanced LOB Compression

Advanced LOB Compression works with the `ALTER TABLE` statement.

Topics:

- Usage Notes for Advanced LOB Compression

- Examples of ALTER TABLE and Advanced LOB Compression

<!-- -->

- Usage Notes for Advanced LOB Compression
  Consider these issues when using `ALTER` `TABLE` and Advanced LOB Compression.
- Examples of ALTER TABLE and Advanced LOB Compression
  These examples demonstrate how to issue `ALTER TABLE` statements for specific compression scenarios.

**Parent topic:** ALTER TABLE SecureFiles LOB Features

###### 3.3.4.1.1 Usage Notes for Advanced LOB Compression

Consider these issues when using `ALTER` `TABLE` and Advanced LOB Compression.

- This syntax alters the compression mode of the LOB column.

- The `DBMS_LOB.SETOPTIONS` procedure can enable or disable compression on individual LOBs.

- Compression may be specified either at the table level or the partition level.

- The `LOW`, `MEDIUM`, and `HIGH` options provide varying degrees of compression. The higher the compression, the higher the latency incurred. The `HIGH` setting incurs more work, but compresses the data better. The default is `MEDIUM`.

**See Also:**

CREATE TABLE with Advanced LOB Compression

**Parent topic:** ALTER TABLE with Advanced LOB Compression

###### 3.3.4.1.2 Examples of ALTER TABLE and Advanced LOB Compression

These examples demonstrate how to issue `ALTER TABLE` statements for specific compression scenarios.

Example 3-15 Altering a SecureFiles LOB Column to Enable LOW Compression

    ALTER TABLE t1 MODIFY
       LOB(a) (
               COMPRESS LOW
       );

Example 3-16 Altering a SecureFiles LOB Column to Disable Compression

    ALTER TABLE t1 MODIFY
        LOB(a) (
             NOCOMPRESS
        );

Example 3-17 Altering a SecureFiles LOB Column to Enable HIGH Compression

    ALTER TABLE t1 MODIFY
        LOB(a) (
             COMPRESS HIGH
        );

Example 3-18 Altering a SecureFiles LOB Column to Enable Compression on One partition

    ALTER TABLE t1 MODIFY PARTITION p1
        LOB(a) (
             COMPRESS HIGH
        );

**Parent topic:** ALTER TABLE with Advanced LOB Compression

##### 3.3.4.2 ALTER TABLE with Advanced LOB Deduplication

Advanced LOB Deduplication works with the `ALTER TABLE` statement.

Topics:

- Usage Notes for Advanced LOB Deduplication

- Examples of ALTER TABLE and Advanced LOB Deduplication

<!-- -->

- Usage Notes for Advanced LOB Deduplication
  Consider these issues when using `ALTER` `TABLE` and Advanced LOB Deduplication.
- Examples of ALTER TABLE and Advanced LOB Deduplication
  These examples demonstrate how to issue `ALTER TABLE` statements for specific deduplication scenarios.

**Parent topic:** ALTER TABLE SecureFiles LOB Features

###### 3.3.4.2.1 Usage Notes for Advanced LOB Deduplication

Consider these issues when using `ALTER` `TABLE` and Advanced LOB Deduplication.

- The `ALTER` `TABLE` syntax can enable or disable LOB-level deduplication.

- This syntax alters the deduplication mode of the LOB column.

- The `DBMS_LOB.SETOPTIONS` procedure can enable or disable deduplication on individual LOBs.

- Deduplication can be specified at a table level or partition level. Deduplication does not span across partitioned LOBs.

**Parent topic:** ALTER TABLE with Advanced LOB Deduplication

###### 3.3.4.2.2 Examples of ALTER TABLE and Advanced LOB Deduplication

These examples demonstrate how to issue `ALTER TABLE` statements for specific deduplication scenarios.

Example 3-19 Altering a SecureFiles LOB Column to Disable Deduplication

    ALTER TABLE t1 MODIFY
         LOB(a) (
             KEEP_DUPLICATES
        );

Example 3-20 Altering a SecureFiles LOB Column to Enable Deduplication

    ALTER TABLE t1 MODIFY
        LOB(a) (
             DEDUPLICATE
        );

Example 3-21 Altering a SecureFiles LOB Column to Enable Deduplication on One Partition

    ALTER TABLE t1 MODIFY PARTITION p1
        LOB(a) (
             DEDUPLICATE
        );

**Parent topic:** ALTER TABLE with Advanced LOB Deduplication

##### 3.3.4.3 ALTER TABLE with SecureFiles Encryption

SecureFiles Encryption works with the `ALTER TABLE` statement.

Topics:

- Usage Notes for SecureFiles Encryption

- Examples of ALTER TABLE and SecureFiles Encryption

<!-- -->

- Usage Notes for SecureFiles Encryption
  Consider these issues when using `ALTER` `TABLE` and SecureFiles Encryption.
- Examples of ALTER TABLE and SecureFiles Encryption
  These examples demonstrate how to issue `ALTER TABLE` statements for specific encryption scenarios.

**Parent topic:** ALTER TABLE SecureFiles LOB Features

###### 3.3.4.3.1 Usage Notes for SecureFiles Encryption

Consider these issues when using `ALTER` `TABLE` and SecureFiles Encryption.

- `ALTER` `TABLE` enables and disables SecureFiles Encryption. This syntax also allows the user to re-key LOB columns with a new key or algorithm.

- `ENCRYPT` and `DECRYPT` options enable or disable encryption on all LOBs in the specified SecureFiles LOB column.

- The default for LOB encryption is `SALT`. `NO` `SALT` is not supported.

- The `DECRYPT` option converts encrypted columns to clear text form.

- Key management controls the ability to encrypt or decrypt.

- LOBs can be encrypted only on a per-column basis. A partitioned LOB has either all partitions encrypted or not encrypted.

**Parent topic:** ALTER TABLE with SecureFiles Encryption

###### 3.3.4.3.2 Examples of ALTER TABLE and SecureFiles Encryption

These examples demonstrate how to issue `ALTER TABLE` statements for specific encryption scenarios.

Example 3-22 Altering a SecureFiles LOB Column by Encrypting Based on a Specific Algorithm

Enable LOB encryption using `AES256`.

    ALTER TABLE t1 MODIFY
          ( a CLOB ENCRYPT USING 'AES256');

This is another example of enabling LOB encryption using `AES256`.

    ALTER TABLE t1 MODIFY LOB(a)
          (ENCRYPT USING 'AES256');

Example 3-23 Altering a SecureFiles LOB Column by Encrypting Based on a Password Key

Enable encryption on a SecureFiles LOB column and build the encryption key using a password.

    ALTER TABLE t1 MODIFY
        ( a CLOB ENCRYPT IDENTIFIED BY foo);

Example 3-24 Altering a SecureFiles LOB Column by Re-keying the Encryption

To re-encrypt the LOB column with a new key, re-key the table.

    ALTER TABLE t1 REKEY USING 'AES256';

**Parent topic:** ALTER TABLE with SecureFiles Encryption

### 3.4 Initialization, Compatibility, and Upgrading

You must perform LOB initialization using appropriate compatibility parameters.

Topics:

- Compatibility and Upgrading

- Initialization Parameter for SecureFiles LOBs

<!-- -->

- Compatibility and Upgrading
  All features described in this document are enabled with compatibility set to `11.2.0.0.0` or higher. There is no downgrade capability after `11.2.0.0.0` is set.
- Initialization Parameter for SecureFiles LOBs
  You, as database administrator, using the `DB_SECUREFILE` initialization parameter, can modify the initial settings that the `COMPATIBILITY` parameter sets as default.

**Parent topic:** Using Oracle LOB Storage

#### 3.4.1 Compatibility and Upgrading

All features described in this document are enabled with compatibility set to `11.2.0.0.0` or higher. There is no downgrade capability after `11.2.0.0.0` is set.

If you want to upgrade BasicFiles LOBs to SecureFiles LOBs, you must use typical methods for upgrading data (CTAS/ITAS, online redefinition, export/import, column to column copy, or using a view and a new column). Most of these solutions require twice the disk space used by the data in the input LOB column. However, partitioning and taking these actions on a partition-by-partition basis lowers the disk space requirements.

**Parent topic:** Initialization, Compatibility, and Upgrading

#### 3.4.2 Initialization Parameter for SecureFiles LOBs

You, as database administrator, using the `DB_SECUREFILE` initialization parameter, can modify the initial settings that the `COMPATIBILITY` parameter sets as default.

By changing the intial settings, you change the circumstances under which SecureFiles LOBs or BasicFiles LOBs are created or allowed. The `DB_SECUREFILE` parameter is typically set in the file `init.ora`.

**See Also:**

- [Oracle Database Reference](../refrn/DB_SECUREFILE.md)

- Compatibility and Upgrading

The `DB_SECUREFILE` initialization parameter is dynamic and can be modified with the `ALTER` `SYSTEM` statement. Example 3-25 shows the format for changing the parameter value:

The valid values for `DB_SECUREFILE` are:

- `NEVER` prevents SecureFiles LOBs from being created. If `NEVER` is specified, any LOBs that are specified as SecureFiles LOBs are created as BasicFiles LOBs. If storage options are not specified, the BasicFiles LOB defaults are used. All SecureFiles LOB-specific storage options and features such as compress, encrypt, or deduplicate throw an exception.

- `IGNORE` disallows SecureFiles LOBs and ignores any errors that forcing BasicFiles LOBs with SecureFiles LOBs options might cause. If `IGNORE` is specified, the `SECUREFILE` keyword and all SecureFiles LOB options are ignored.

- `PERMITTED` allows SecureFiles LOBs to be created, if specified by users. Otherwise, BasicFiles LOBs are created.

- `PERFERRED` attempts to create a SecureFiles LOB unless BasicFiles LOB is explicitly specified for the LOB or the parent LOB (if the LOB is in a partition or sub-partition). `PREFERRED` is the default value starting with Oracle Database 12c.

- `ALWAYS` attempts to create SecureFiles LOBs but creates any LOBs not in `ASSM` tablespaces as BasicFiles LOBs, unless the `SECUREFILE` parameter is explicitly specified. Any BasicFiles LOB storage options specified are ignored, and the SecureFiles LOB defaults are used for all storage options not specified.

- `FORCE` attempts to create all LOBs as SecureFiles LOBs even if users specify `BASICFILE`. This option is not recommended. Instead, `PREFERRED` or `ALWAYS` should be used.

Example 3-25 Setting DB_SECUREFILE parameter through ALTER SYSTEM

    ALTER SYSTEM SET DB_SECUREFILE = 'ALWAYS';

**Parent topic:** Initialization, Compatibility, and Upgrading

### 3.5 Migrating Columns from BasicFiles LOBs to SecureFiles LOBs

You can use several methods of migrating LOBs columns.

Topics:

- Preventing Generation of REDO Data When Migrating to SecureFiles LOBs

- Online Redefinition for BasicFiles LOBs

- Online Redefinition Example for Migrating Tables with BasicFiles LOBs

- Redefining a SecureFiles LOB in Parallel

<!-- -->

- Preventing Generation of REDO Data When Migrating to SecureFiles LOBs
  Migrating BasicFiles LOB columns generates redo data, which can cause performance problems.
- Online Redefinition for BasicFiles LOBs
  Online redefinition is the recommended method for migration of BasicFiles LOBs to SecureFiles LOBs.
- Online Redefinition Example for Migrating Tables with BasicFiles LOBs
  You can migrate a table using Online Redefinition.
- Redefining a SecureFiles LOB in Parallel
  You can redefine a SecureFiles LOB column in parallel, if the system has sufficient resources for parallel execution.

**Parent topic:** Using Oracle LOB Storage

#### 3.5.1 Preventing Generation of REDO Data When Migrating to SecureFiles LOBs

Migrating BasicFiles LOB columns generates redo data, which can cause performance problems.

Redo changes for the table are logged during the migration process if the `CREATE` `TABLE` statement had the `LOGGING` clause set.

Redo changes for a column being converted from BasicFiles LOB to SecureFiles LOB are logged if `LOGGING` is the storage setting for the SecureFiles LOB column. The logging setting (`LOGGING` or `NOLOGGING`) for the LOB column is inherited from the tablespace in which the LOB is created.

You can prevent redo space generation during migration to SecureFiles LOB.

- Specify the `NOLOGGING` storage parameter for any new SecureFiles LOB columns.

  You may turn `LOGGING` on when the migration is complete.

**Parent topic:** Migrating Columns from BasicFiles LOBs to SecureFiles LOBs

#### 3.5.2 Online Redefinition for BasicFiles LOBs

Online redefinition is the recommended method for migration of BasicFiles LOBs to SecureFiles LOBs.

You can perform online redefinition at the table or partition level.

##### Online Redefinition Advantage

- No requirement to take the table or partition offline

- Can be done in parallel

##### Online Redefinition Disadvantages

- Additional storage equal to the entire table or partition required and all LOB segments must be available

- Global indexes must be rebuilt

**Parent topic:** Migrating Columns from BasicFiles LOBs to SecureFiles LOBs

#### 3.5.3 Online Redefinition Example for Migrating Tables with BasicFiles LOBs

You can migrate a table using Online Redefinition.

Online Redefinition has the advantage of not requiring the table to be off line, but it requires additional free space equal to or even slightly greater than the space used by the table. Example 3-26 demonstrates how to migrate a table using Online Redefinition.

Example 3-26 Example of Online Redefinition

    REM Grant privileges required for online redefinition.
    GRANT EXECUTE ON DBMS_REDEFINITION TO pm;
    GRANT ALTER ANY TABLE TO pm;
    GRANT DROP ANY TABLE TO pm;
    GRANT LOCK ANY TABLE TO pm;
    GRANT CREATE ANY TABLE TO pm;
    GRANT SELECT ANY TABLE TO pm;
    REM Privileges required to perform cloning of dependent objects.
    GRANT CREATE ANY TRIGGER TO pm;
    GRANT CREATE ANY INDEX TO pm;
    CONNECT pm
    //  ALTER SESSION FORCE parallel dml;
    DROP TABLE cust;
    CREATE TABLE cust(c_id NUMBER PRIMARY KEY,
        c_zip NUMBER,
        c_name VARCHAR(30) DEFAULT NULL,
        c_lob CLOB
    );
    INSERT INTO cust VALUES(1, 94065, 'hhh', 'ttt');
    -- Creating Interim Table
    -- There is no requirement to specify constraints because they are
    -- copied over from the original table.
    CREATE TABLE cust_int(c_id NUMBER NOT NULL,
        c_zip NUMBER,
        c_name VARCHAR(30) DEFAULT NULL,
        c_lob CLOB
    ) LOB(c_lob) STORE AS SECUREFILE (NOCACHE FILESYSTEM_LIKE_LOGGING);
    DECLARE
        col_mapping VARCHAR2(1000);
    BEGIN
    -- map all the columns in the interim table to the original table
        col_mapping :=
        'c_id c_id , '||
        'c_zip c_zip , '||
        'c_name c_name, '||
        'c_lob c_lob';
    DBMS_REDEFINITION.START_REDEF_TABLE('pm', 'cust', 'cust_int', col_mapping);
    END;
    /
    DECLARE
        error_count pls_integer := 0;
    BEGIN
        DBMS_REDEFINITION.COPY_TABLE_DEPENDENTS('pm', 'cust', 'cust_int',
          1, TRUE,TRUE,TRUE,FALSE, error_count);
        DBMS_OUTPUT.PUT_LINE('errors := ' || TO_CHAR(error_count));
    END;
    /
    EXEC DBMS_REDEFINITION.FINISH_REDEF_TABLE('pm', 'cust', 'cust_int');
    -- Drop the interim table
    DROP TABLE cust_int;
    DESC cust;
    -- The following insert statement fails. This illustrates
    -- that the primary key constraint on the c_id column is
    -- preserved after migration.
    INSERT INTO cust VALUES(1, 94065, 'hhh', 'ttt');
    SELECT * FROM cust;

**Parent topic:** Migrating Columns from BasicFiles LOBs to SecureFiles LOBs

#### 3.5.4 Redefining a SecureFiles LOB in Parallel

You can redefine a SecureFiles LOB column in parallel, if the system has sufficient resources for parallel execution.

To set up parallel execution of online redefinition, run `ALTER SESSION.`

- Add the following statement after the connect statementExample 3-26 in the last section:

      ALTER SESSION FORCE PARALLEL DML;

**Parent topic:** Migrating Columns from BasicFiles LOBs to SecureFiles LOBs

### 3.6 PL/SQL Packages for LOBs and DBFS

There are PL/SQL packages that can be used with BasicFiles LOBs and SecureFiles LOBs.

Changes made to accommodate SecureFiles LOBs and DBFS are emphasized.

Topics:

- The DBMS_LOB Package Used with SecureFiles LOBs and DBFS

- DBMS_LOB Constants Used with SecureFiles LOBs and DBFS

- DBMS_LOB Subprograms Used with SecureFiles LOBs and DBFS

- DBMS_SPACE Package

<!-- -->

- The DBMS_LOB Package Used with SecureFiles LOBs and DBFS
  The `DBMS_LOB` package provides subprograms to operate on, or access and manipulate specific parts of a LOB or complete LOBs.
- DBMS_LOB Constants Used with SecureFiles LOBs and DBFS
  Certain constants support DBFS link interfaces.
- DBMS_LOB Subprograms Used with SecureFiles LOBs and DBFS
  You should note that some changes have been made to the `DBMS_LOB` subprograms over time.
- DBMS_SPACE Package
  You can analyze segment growth and space requirements using the `DBMS_SPACE` PL/SQL package.

**Parent topic:** Using Oracle LOB Storage

#### 3.6.1 The DBMS_LOB Package Used with SecureFiles LOBs and DBFS

The `DBMS_LOB` package provides subprograms to operate on, or access and manipulate specific parts of a LOB or complete LOBs.

The `DBMS_LOB` package applies to both SecureFiles LOB and BasicFiles LOB.

DBMS_LOB Constants Used with SecureFiles LOBs and DBFS and DBMS_LOB Subprograms Used with SecureFiles LOBs and DBFS describe modifications made to the `DBMS_LOB` constants and subprograms with the addition of SecureFiles LOB and Database File System (DBFS).

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md) for more information about `DBMS_LOB` package

- [Introducing the Database File System](introducing-database-file-system.md)

**Parent topic:** PL/SQL Packages for LOBs and DBFS

#### 3.6.2 DBMS_LOB Constants Used with SecureFiles LOBs and DBFS

Certain constants support DBFS link interfaces.

Table 3-3 lists constants that support [DBFS Link](glossary.md) interfaces.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md) for complete information about constants used in the PL/SQL `DBMS_LOB` package

Table 3-3 DBMS_LOB Constants That Support DBFS Link Interfaces

| Constant                  | Description                                                  |
|:--------------------------|:-------------------------------------------------------------|
| `DBFS_LINK_NEVER`         | DBFS link state value                                        |
| `DBFS_LINK_YES`           | DBFS link state value                                        |
| `DBFS_LINK_NO`            | DBFS link state value                                        |
| `DBFS_LINK_CACHE`         | Flag used by `COPY_DBFS_LINK()` and `MOVE_DBFS_LINK()`.      |
| `DBFS_LINK_NOCACHE`       | Flag used by `COPY_DBFS_LINK()` and `MOVE_DBFS_LINK()`.      |
| `DBFS_LINK_PATH_MAX_SIZE` | The maximum length of DBFS pathnames; `1024`.                |
| `CONTENTTYPE_MAX_SIZE`    | The maximum 1-byte ASCII characters for content type; `128`. |

**Parent topic:** PL/SQL Packages for LOBs and DBFS

#### 3.6.3 DBMS_LOB Subprograms Used with SecureFiles LOBs and DBFS

You should note that some changes have been made to the `DBMS_LOB` subprograms over time.

Table 3-4 summarizes changes made to PL/SQL package `DBMS_LOB` subprograms.

Be aware that some of the `DBMS_LOB` operations that existed before Oracle Database 11g Release 2 throw an exception error if the LOB is a DBFS link. To remedy this problem, modify your applications to explicitly replace the DBFS link with a LOB by calling the `DBMS_LOB.COPY_FROM_LINK` procedure before they make these calls. When the call completes, then the application can move the updated LOB back to DBFS using the `DBMS_LOB.MOVE_TO_DBFS_LINK` procedure, if necessary.

Other `DBMS_LOB` operations that existed before Oracle Database 11g Release 2 work transparently if the DBFS Link is in a file system that supports streaming. Note that these operations fail if streaming is either not supported or disabled.

Table 3-4 DBMS_LOB Subprograms

| Subprogram                    | Description                                                                                                                                                                                                                                                                                                                                                         |
|:------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `APPEND`                      | Appends the contents of the source LOB to the destination LOB<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                       |
| `COMPARE`                     | Compares two LOBs in full or in parts<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                                               |
| `CONVERTTOBLOB`               | Converts the character data of a `CLOB` or `NCLOB` into the specified character set and writes it in binary format to a destination `BLOB`<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                          |
| `CONVERTTOCLOB`               | Converts the binary data of a `BLOB` into the specified character set and writes it in character format to a destination `CLOB` or `NCLOB`<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                          |
| `COPY`                        | Copies all or part of the source LOB to the destination LOB<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                         |
| `COPY_DBFS_LINK`              | Copies an existing DBFS link into a new LOB<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                                         |
| `COPY_FROM_DBFS_LINK`         | Copies the specified LOB data from DBFS HSM Store into the database<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                 |
| `DBFS_LINK_GENERATE_PATHNAME` | Returns a unique file path name for creating a DBFS Link<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                            |
| `ERASE`                       | Erases all or part of a LOB<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                                                         |
| `FRAGMENT_DELETE`             | Deletes a specified fragment of the LOB<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                                             |
| `FRAGMENT_INSERT`             | Inserts a fragment of data into the LOB<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                                             |
| `FRAGMENT_MOVE`               | Moves a fragment of a LOB from one location in the LOB to another location<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                          |
| `FRAGMENT_REPLACE`            | Replaces a fragment of a LOB with new data<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                                          |
| `GET_DBFS_LINK`               | Returns the DBFS path name for a LOB<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                                                |
| `GET_DBFS_LINK_STATE`         | Returns the linking state of a LOB<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                                                  |
| `GETCONTENTTYPE`              | Retrieves the content type string of the LOB data<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                                   |
| `GETOPTIONS`                  | Retrieves the previously set options of a specific LOB<br>**See Also:**<br>• [Oracle Database PL/SQL Packages and Types Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)<br>• [Oracle Call Interface Programmer's Guide](../lnoci/lob-functions.md)for more information on the corresponding `OCILobGetContentType()` an OCI LOB function |
| `ISSECUREFILE`                | Determines if a LOB is a SecureFiles LOB<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                                            |
| `LOADBLOBFROMFILE`            | Loads `BFILE` data into a `BLOB`<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                                                    |
| `LOADCLOBFROMFILE`            | Loads `BFILE` data into a `CLOB`<br>If the `CLOB` is linked, an exception is thrown.<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                |
| `LOADFROMFILE`                | Loads `BFILE` data into a LOB<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                                                       |
| `MOVE_TO_DBFS_LINK`           | Moves the specified LOB data from the database into DBFS HSM Store<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                  |
| `READ`                        | Reads data from a LOB<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                                                               |
| `SET_DBFS_LINK`               | Links a LOB with a DBFS path name<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                                                   |
| `SETCONTENTTYPE`              | Sets the content type string of the LOB data<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                                        |
| `SETOPTIONS`                  | Sets new options for a specific LOB<br>**See Also:**<br>• [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)<br>• [Oracle Call Interface Programmer's Guide](../lnoci/lob-functions.md)for more information on the corresponding `OCILobSetContentType()`<br>• (OCI LOB function)                                                          |
| `SUBSTR`                      | Returns a fragment of a LOB<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                                                         |
| `TRIM`                        | Trims the LOB to a specified length<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                                                 |
| `WRITE`                       | Writes data to a LOB<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                                                                |
| `WRITEAPPEND`                 | Appends data to the end of a LOB<br>**See Also:**<br>[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md)                                                                                                                                                                                                                                    |

**Parent topic:** PL/SQL Packages for LOBs and DBFS

#### 3.6.4 DBMS_SPACE Package

You can analyze segment growth and space requirements using the `DBMS_SPACE` PL/SQL package.

The `DBMS_SPACE` PL/SQL package enables you to analyze segment growth and space requirements.

- DBMS_SPACE.SPACE_USAGE()
  The existing `DBMS_SPACE.SPACE_USAGE` procedure is overloaded to return information about LOB space usage.

**Parent topic:** PL/SQL Packages for LOBs and DBFS

##### 3.6.4.1 DBMS_SPACE.SPACE_USAGE()

The existing `DBMS_SPACE.SPACE_USAGE` procedure is overloaded to return information about LOB space usage.

It returns the amount of disk space in blocks used by all the SecureFiles LOBs in the LOB segment.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_SPACE.md)

**Parent topic:** DBMS_SPACE Package
