This section describes several Oracle utilities that provide support for Oracle objects.

This section contains these topics:

- Import/Export of Object Types

- SQL\*Loader

### 4.9.1 Import/Export of Object Types

Export and Import utilities move data into and out of Oracle databases. They also back up or archive data and aid migration to different releases of the Oracle RDBMS.

Export and Import support object types. Export writes object type definitions and all of the associated data to the dump file. Import then re-creates these items from the dump file.

When you import object tables, by default, `OID`s are preserved.

**See Also:**

[Oracle Database Utilities](../sutil/oracle-data-pump-export-utility.md) for instructions on how to use the Import and Export utilities

#### 4.9.1.1 Types

The definition statements for derived types are exported. On an Import, a subtype may be created before the supertype definition has been imported. In this case, the subtype is created with compilation errors, which may be ignored. The type is revalidated after its supertype is created.

#### 4.9.1.2 Object View Hierarchies

View definitions for all views belonging to a view hierarchy are exported.

### 4.9.2 SQL\*Loader

The SQL\*Loader utility moves data from external files into tables in an Oracle database.

The files SQL\*Loader moves may contain data consisting of basic scalar data types, such as `INTEGER`, `CHAR`, or `DATE`, as well as complex user-defined data types such as row and column objects (including objects that have object, collection, or `REF` attributes), collections, and LOBs. Currently, SQL\*Loader supports single-level collections only: you cannot yet use SQL\*Loader to load multilevel collections, that is, collections whose elements are, or contain, other collections. SQL\*Loader uses control files, which contain SQL\*Loader data definition language (DDL) statements, to describe the format, content, and location of the datafiles.

SQL\*Loader provides two approaches to loading data:

- Conventional path loading, which uses the `SQL` `INSERT` statement and a bind array buffer to load data into database tables

- Direct path loading, which uses the Direct Path Load API to write data blocks directly to the database on behalf of the SQL\*Loader client.

  Direct path loading does not use a SQL interface and thus avoids the overhead of processing the associated SQL statements. Consequently, direct path loading generally provides much better performance than conventional path loading.

Either approach can be used to load data of supported object and collection data types.

**See Also:**

[Oracle Database Utilities](../sutil/oracle-sql-loader.md) for instructions on how to use SQL\*Loader
