Using the Entity Framework Code First modeling path, developers define the application domain model using source code rather than working directly with a designer or an XML-based configuration file. The classes defined within the source code become the model. The Code First model path offers an alternative to the existing Entity Framework Database First and Model First paths. Within Code First, the classes defined in code that comprise the model are known as Plain Old CLR Objects (POCOs). This name derives from the fact that these classes have no dependency upon Entity Framework itself and are independent of it.

Oracle's support for the Code First modeling path enables .NET developers to take advantage of Oracle Database benefits.

**See Also:**

[Configuring for Entity Framework Code First](InstallEntityConfig.md)

### Mapping of .NET Types to Oracle Types

When using the Code First path, the model is defined by the application's classes and properties. The property data types need to be mapped to the Oracle Database table data types. The following table lists the default mapping of supported .NET types to Oracle types as well as how to map a String property to non-default Oracle types:

Table 4-24 Mapping of .NET Data Types to Oracle Data Types

| .NET Data Type   | Oracle Data Type           | Mapping Method                                                                                                                                                                               |
|:-----------------|:---------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Boolean`        | `number(1, 0)`             | Use EDM Mapping<br>Note: Requires use of EDM Mapping configuration. Reference the EDM Mapping sections in the documentation for additional information.                                      |
| `Byte`           | `number(3, 0)`             | Use EDM Mapping<br>Note: Requires use of EDM Mapping configuration. Reference the EDM Mapping sections in the documentation for additional information.                                      |
| `Byte[]`         | `blob`                     | Default                                                                                                                                                                                      |
| `Int16`          | `number(5, 0)`             | Default<br>Note: The default mapping of integer types may be specified in the EDM Mapping configuration. Reference the EDM Mapping sections in the documentation for additional information. |
| `Int32`          | `number(10, 0)`            | Default<br>Note: The default mapping of integer types may be specified in the EDM Mapping configuration. Reference the EDM Mapping sections in the documentation for additional information. |
| `Int64`          | `number(19, 0)`            | Default<br>Note: The default mapping of integer types may be specified in the EDM Mapping configuration. Reference the EDM Mapping sections in the documentation for additional information. |
| `Decimal`        | `number(18, 2)`            | Default                                                                                                                                                                                      |
| `Single`         | `binary_float`             | Default                                                                                                                                                                                      |
| `Double`         | `binary_double`            | Default                                                                                                                                                                                      |
| `Guid`           | `raw(16)`                  | Default                                                                                                                                                                                      |
| `DateTime`       | `date`                     | Default                                                                                                                                                                                      |
| `DateTimeOffset` | t`imestamp with time zone` | Default                                                                                                                                                                                      |
| `String`         | `nclob`                    | Default                                                                                                                                                                                      |
| `String`         | `clob`                     | Set Unicode to false using `IsUnicode()` fluent API                                                                                                                                          |
| `String`         | `nvarchar2`                | Set Max Length to `<= 2000` using `HasMaxLength()` fluent API or `MaxLength` data annotation                                                                                                 |
| `String`         | `varchar2`                 | Set Max Length to `<= 4000` using `HasMaxLength()` fluent API or `MaxLength` data annotation and set Unicode to false using `IsUnicode()` fluent API                                         |
| `String`         | `nchar`                    | Set Max Length to `<= 1000` using HasMaxLength() fluent API or MaxLength annotation and Set Column Type to `NCHAR` using HasColumnType() fluent API or Column data annotation                |
| `String`         | `char`                     | Set Max Length to `<= 2000 `using `HasMaxLength()` fluent API or `MaxLength` annotation and Set Column Type to `CHAR` using `HasColumnType()` fluent API or `Column` data annotation         |
| `String`         | `Long`                     | Set Column Type to `LONG` using `HasColumnType()` fluent API or `Column` data annotation<br>Note: The long data type is deprecated and not recommended.                                      |
| String           | rowid                      | Set Column Type to `ROWID` using `HasColumnType()` fluent API or `Column` data annotation                                                                                                    |
| String           | urowid                     | Set Column Type to `UROWID` using `HasColumnType()` fluent API or `Column` data annotation                                                                                                   |

**Note:**

The character based columns, namely, `CHAR`, `NCHAR`, `VARCHAR2`, `NVARCHAR2` will be created using character semantics to be able to store the specified `Max Length` amount of characters. However, due to the Oracle database limit, these columns can store only up to `4000` bytes. As such, these columns may not be able to store `4000` characters even if `Max Length` is set to `4000` characters since one character may require multiple number of bytes of storage, depending on the data and the database character set. If the character data can be longer than `4000` bytes, it may be more appropriate to use `CLOB` or `NCLOB` column.

#### Influencing the Oracle Data Type Characteristics

The type mappings listed in the previous table represent the mappings that occur by default or what is known as convention in Entity Framework. As illustrated with the `String` type, you can influence the resulting Oracle Data Type for a property as well as characteristics of that data type. There are two Entity Framework methods to influence the resulting Oracle Data Type: Data Annotations and the Code First Fluent API. Data Annotations permit you to explicitly mark a class property with one or more attributes, whereas the Code First Fluent API permits you to use code rather than attributes to achieve the same goal. For additional information regarding the use of Data Annotations and the Code First Fluent API refer to the MSDN Entity Framework documentation.

The following table illustrates the available functionality:

Table 4-25 Mapping of Data Annotations and the Code First Fluent APIs

| Data Annotation    | Fluent API           | Purpose                                                                                                                                                                                                                                                                                                  | Applies To       |
|:-------------------|:---------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------|
| `Key`              | `HasKey`             | Set a property as the Primary Key.                                                                                                                                                                                                                                                                       | All Scalar Types |
| `Required`         | `IsRequired`         | Set the database column as `NOT NULL`.                                                                                                                                                                                                                                                                   | All              |
| `MaxLength`        | `HasMaxLength`       | Specifies the maximum length of the property.                                                                                                                                                                                                                                                            | `String`         |
| `NotMapped`        | `Ignore`             | Indicates the property is not mapped to a database column.                                                                                                                                                                                                                                               | All              |
| `ConcurrencyCheck` | `IsConcurrencyToken` | Indicates the column should be used for optimistic concurrency checking.<br>Note: Do not use with an unbounded (no maximum length specified) string property as this will create a LOB column. Use of a LOB column in the concurrency check will result in an `ORA-00932: inconsistent datatypes` error. | All              |
| `TimeStamp`        | `IsRowVersion`       | Indicates to create the column as a `rowversion` column.                                                                                                                                                                                                                                                 | Not Supported    |
| `Column`           | `HasColumnType`      | Indicates the provider-specific type to use for the database column.<br>Note: Must be a legal compatible type. For example a `Date` property is not legal to map to a number column. Use the `TypeName` property with the `Column` Data Annotation to specify the type.                                  | All              |
| N/A                | `IsUnicode`          | Indicates to create the column as an N-type, that is, `nvarchar2` or `nclob`. Default is true.<br>Note: There is no Data Annotation equivalent for `IsUnicode`.                                                                                                                                          | `String`         |
| N/A                | `HasPrecision`       | Indicates the precision and scale for a decimal property.<br>Note: There is no Data Annotation equivalent for `HasPrecision`.                                                                                                                                                                            | `Decimal`        |

### Code First Migrations

The Oracle Data Provider for .NET supports Code First Migrations functionality. The use of Code First Migrations with Oracle Database is supported through the Package Manager Console window migrations commands. For information on these commands, refer to the MSDN Code First Migrations documentation:

[`http://msdn.microsoft.com/en-us/data/jj591621.aspx`](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/odpnt&id=msdn_ef_codefirst_migration)

Code First Migrations utilizes a table known as the Migration History table for tracking migration operations as well as model changes. ODP.NET creates this table, by default, in the user schema specified in the context connection string. This table is named \_\_MigrationHistory.

This table can be created in another user schema besides the user specified in the context connection string. This is accomplished through a process known as Migration History Table Customization, which is described in the following MSDN documentation.

[`http://msdn.microsoft.com/en-us/data/dn456841`](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/odpnt&id=msdn_migrationshistory)

**Note:**

- Changing the user schema for the table is the only supported customization.

- Code First Automatic Migrations is limited to working with the `dbo` schema only. Due to this limitation it is recommended to use code-based migrations, that is, add explicit migrations through the Add-Migration command.

#### Code First Migrations With No Supporting Code Migration File

When using Code First Migrations with ODP.NET, the migration history table may be dropped if no supporting code migration file existed prior to updating the database. Developers should ensure the supporting code migration file has been added prior to updating the database.

The following steps can remove the migration history table:

1.  Execute application to create database objects

2.  Enable-Migrations in the Package Manager Console

3.  Make code change to POCO

4.  Update-Database in the Package Manager Console

The following steps ensure the code migration file is created:

1.  Execute application to create database objects

2.  Enable-Migrations in the Package Manager Console

3.  Make code change to POCO

4.  Add-Migration in the Package Manager Console. This step will create the necessary code migration file.

5.  Update-Database in the Package Manager Console

### Code First Database Initialization

ODP.NET supports the following Code First Database Initializer methods:

- `CreateDatabaseIfNotExists` (default if none specified)

- `DropCreateDatabaseAlways`

- `DropCreateDatabaseIfModelChanges`

- `NullDatabaseInitializer`

- `MigrateDatabaseToLatestVersion`

These methods are documented on MSDN.

Due to differences in how Oracle and SQL Server define a database, database initialization actions work on all of the Oracle objects in the model. An Oracle Database is not created or dropped, rather the objects that compose the model are considered to be the database for these operations.

### Oracle Database Object Creation

In order to support the client application, ODP.NET will create and maintain the required database objects. The following are the database objects created and maintained by the provider:

- Table

- Table Column

- Primary Key

- Foreign Key

- Index

- Sequence

- Trigger

**Note:**

Sequences and triggers may be created in Oracle Database 11g Release 2 and earlier databases to support identity columns.

For objects which directly relate to a client application object, namely, a table which represents an application class and a table column which represents a class property, the object names used are those provided by the client. These object names must conform to the object identifier length limits for Oracle Database. For example, if a class name length exceeds the valid object identifier length in Oracle Database then the `ORA-00972: identifier is too long` exception will be raised at object creation time.

For the remaining objects, ODP.NET utilizes a name generation algorithm if the supplied name length exceeds the database identifier length limit. If the supplied name length does not exceed the database limit the name is used as-is. In all cases, the object name is created as a quoted identifier in order to preserve case and any special characters which may be part of the identifier.

In cases where the provider generates a name to comply with database identifier length limits, the name is composed of the following underscore separated elements:

- A substring of the original name (from the first character)

- A numeric suffix value calculated from the original name

The following example illustrates the results of the name generation algorithm using a simple POCO in the client application:

    public class LongSamplePocoTestClassName
    {
      [Key]
      public int Id { get; set; }

      [MaxLength(64)]
      public string Name { get; set; }
    }

The default name for the Primary Key for the resulting table will be:

    PK_LongSamplePocoTestClassNames

As this name contains 31 characters (single byte per character), it violates the database identifier restrictions. The rewritten Primary Key name will resemble the following value:

    PK_LongSamplePocoTes_730795129

The algorithm is designed to utilize as many characters as possible from the original name such that the new name does not violate the identifier length restrictions.

#### Controlling Table Name and Owner

Through the use of Data Annotations or the Entity Framework Fluent API you may control the table name, as well as the table owner. For example, you may choose to explicitly set the table name to conform to your organization's naming standards or if you do not wish to, use the name Entity Framework provides. The `Table` Data Annotation is used to control both the table name and the owner. When using the Fluent API, the `ToTable` method is used to control the table name and the owner within the `OnModelCreating` override in your class which derives from `DbContext`.

The following examples use an incomplete class definition to illustrate these actions.

Setting the table name using a Data Annotation:

    [Table("Employee")]
    public class Employee

Setting the table name using the Fluent API:

    protected override void OnModelCreating(DbModelBuilder modelBuilder)
    {
      modelBuilder.Entity<Employee>().ToTable("Employee");
    }

Setting the table name and the owner using a Data Annotation:

    [Table("Employee ", Schema="TESTUSER")]
    public class Employee

Setting the table name and the owner using the Fluent API:

    protected override void OnModelCreating(DbModelBuilder modelBuilder)
    {
      modelBuilder.Entity<Employee>().ToTable("Employee", "TESTUSER");
    }

**Note:**

When using Data Annotations or the Fluent API as above to set the owner, it is required to also set the name.

#### Setting the Default Table Owner

Rather than set the table owner for each user table, Entity Framework 6 and higher allows you to set the default owner to be used. This is done by invoking the `HasDefaultSchema` method within the `OnModelCreating` override in your class, which derives from `DbContext`.

For example, the following code will cause all user tables to be created within the `TESTUSER` schema by default:

    protected override void OnModelCreating(DbModelBuilder modelBuilder)
    {
      modelBuilder.HasDefaultSchema("TESTUSER");
    }

**Note:**

The owner name is case-sensitive.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/creating-and-configuring-an-oracle-database.md).

### Using the Default Connection Factory

The default connection factory allows ODP.NET connections to be created by providing an Oracle connection string to the `DbContext` constructor. For example, the following entry could be used to configure the ODP.NET, Managed Driver default connection factory:

    <defaultConnectionFactory type="Oracle.ManagedDataAccess.EntityFramework.OracleConnectionFactory,
    Oracle.ManagedDataAccess.EntityFramework,
    Version=6.121.2.0,
    Culture=neutral,
    PublicKeyToken=89b483f429c47342" />

When using the default connection factory, the application supplies an Oracle connection string to the `DbContext` base constructor as follows:

    public class TestContext : DbContext
    {
      public TestContext()
        : base("<connection string>")
      {
      }
    }

Where `<connection string>` is the ODP.NET connection string. This allows the application to connect to the database using code similar to the following:

    using (var ctx = new TestContext())
    {
      ...
    }

For additional information please see the MSDN documentation for the `IDbConnectionFactory` interface:

[`http://msdn.microsoft.com/en-us/library/system.data.entity.infrastructure.idbconnectionfactory%28v=vs.113%29.aspx`](https://www.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/odpnt&id=msdn_idbconnection)
