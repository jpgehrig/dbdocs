ODP.NET provides a Bulk Copy feature which enables applications to efficiently load large amounts of data from a table in one database to another table in the same or a different database.

The ODP.NET Bulk Copy feature uses a direct path load approach, which is similar to, but not the same as Oracle SQL\*Loader. Using direct path load is faster than conventional loading (using conventional SQL `INSERT` statements). Conventional loading formats Oracle data blocks and writes the data blocks directly to the data files. Bulk Copy eliminates considerable processing overhead.

The ODP.NET Bulk Copy feature can load data into older Oracle databases.

**Note:**

ODP.NET, Managed Driver and ODP.NET Core do not support Bulk Copy.

The ODP.NET Bulk Copy feature is subject to the same basic restrictions and integrity constraints for direct path loads, as discussed in the next few sections.

**See Also:**

"[System Requirements](InstallSystemRequirements.md)" to learn which versions of the Oracle Database ODP.NET interoperates with

### Data Types Supported by Bulk Copy

Bulk Copy supports the following Oracle database data types:

- `NUMBER`

- `BINARY_DOUBLE`

- `BINARY_FLOAT`

- `CHAR`

- `NCHAR`

- `VARCHAR2`

- `NVARCHAR2`

- `LONG`

- `CLOB`

- `BLOB`

- `DATE`

- `TIMESTAMP`

- `TIMESTAMP WITH TIME ZONE`

- `TIMESTAMP WITH LOCAL TIME ZONE`

- `INTERVAL YEAR TO MONTH`

- `INTERVAL DAY TO SECOND`

Bulk copy does not support overwrites.

### Restrictions on Oracle Bulk Copy of a Single Partition

- The table that contains the partition cannot have any global indexes defined on it.

- The tables that the partition is a member of cannot have referential and check constraints enabled.

- Enabled triggers are not allowed.

### Integrity Constraints Affecting Oracle Bulk Copy

During a Oracle bulk copy, some integrity constraints are automatically enabled or disabled, as follows:

#### Enabled Constraints

During an Oracle bulk copy, the following constraints are automatically enabled by default:

- `NOT` `NULL`

- `UNIQUE`

- `PRIMARY` `KEY` (unique-constraints on not-null columns)

`NOT` `NULL` constraints are checked at column array build time. Any row that violates the `NOT` `NULL` constraint is rejected.

`UNIQUE` constraints are verified when indexes are rebuilt at the end of the load. The index is left in an Index Unusable state if it violates a `UNIQUE` constraint.

#### Disabled Constraints

During an Oracle bulk copy, the following constraints are automatically disabled by default:

- `CHECK` constraints

- Referential constraints (`FOREIGN` `KEY`)

If the `EVALUATE` `CHECK_CONSTRAINTS` clause is specified, then `CHECK` constraints are not automatically disabled. The `CHECK` constraints are evaluated during a direct path load and any row that violates the `CHECK` constraint is rejected.

### Database Insert Triggers

Table insert triggers are disabled when a direct path load begins. After the rows are loaded and indexes rebuilt, any triggers that were disabled are automatically reenabled. The log file lists all triggers that were disabled for the load. There should be no errors reenabling triggers.

Unlike integrity constraints, insert triggers are not reapplied to the whole table when they are enabled. As a result, insert triggers do not fire for any rows loaded on the direct path. When using the direct path, the application must ensure that any behavior associated with insert triggers is carried out for the new rows.

### Field Defaults

Default column specifications defined in the database are not available with direct path loading. Fields for which default values are desired must be specified with the `DEFAULTIF` clause. If a `DEFAULTIF` clause is not specified and the field is `NULL`, then a null value is inserted into the database.

**See Also:**

[Oracle Data Provider for .NET Bulk Copy Classes](bulk-copy-classes.md)
