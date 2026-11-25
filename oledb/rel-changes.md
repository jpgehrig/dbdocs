This preface contains:

- Changes in Oracle Provider for OLE DB in 12c Release 2 (12.2.0.1)

- Changes in Oracle Provider for OLE DB in ODAC 12c Release 4

- Changes in Oracle Provider for OLE DB in 12c Release 1 (12.1.0.2)

### Changes in Oracle Provider for OLE DB in 12c Release 2 (12.2.0.1)

The following are changes in Oracle Provider for OLE DB Developer's Guide for Oracle Database 12c Release 2 (12.2.0.1):

#### New Features

The following feature is new in this release:

- Longer Schema Identifiers

  Oracle Provider for OLE DB now supports schema objects names, such as tables, columns, views, stored procedures, and functions, up to 128 characters in length.

  Through the use of longer schema object identifier names, this feature increases database development flexibility and makes database migration to Oracle easier.

### Changes in Oracle Provider for OLE DB in ODAC 12c Release 4

The following are changes in Oracle Provider for OLE DB Developer's Guide for ODAC 12c Release 4:

#### New Features

The following feature is new in this release:

- Tracing Enhancements

  Oracle Provider for OLE DB includes new tracing features. Traces can now be output to a specific directory, rather than a file name. The default directory is the Windows temporary files directory.

  See "[OraOLEDB Tracing](provider-specific-info.md)" for more information.

### Changes in Oracle Provider for OLE DB in 12c Release 1 (12.1.0.2)

The following are changes in Oracle Provider for OLE DB Developer's Guide for Oracle Database 12c Release 1 (12.1.0.2):

#### New Features

The following feature is new in this release:

- IRowsetFastLoad and SQL Server Integration Services Fast-Load

  Oracle Provider for OLE DB now supports the `IRowsetFastLoad` interface, which enables fast memory-based bulk-copy operations in the Oracle database. This interface also works with the SQL Server Integration Services fast-load functionality to permit rapid ingestion of large amounts of data using the provider to the Oracle database.

  See "[Performing a Fast Load with SQL Server Integration Services](features-of-oledb.md)" for more information.
