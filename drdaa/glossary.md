### adapter

A real-time, proprietary tool used to enable access to data stored in one database from another database. Adapters are commonly used to translate SQL, map data types, and facilitate the integration of SQL statements, triggers, and stored procedures.

### custom SQL translation

A scenario in which users can register their customer-specific translations of SQL statements with the SQL Translation Profile. During the translation of non-Oracle statements, the profile looks up the custom translations first. Then, if no match is found, it invokes the SQL Translator.

### data integration

The exchange of data between different databases, either asynchronously in real-time transactions or synchronously as batch processes.

### data integration framework

A set of tools and processes used to enable data exchanges between different databases. Traditional frameworks include many nightly processes such as large batch extractions and feeds, and bulk loading of data. Newer frameworks can include small daily processes and feeds occurring in near real time.

### database schema migration

The process of identifying and converting tables, columns, and other objects in a non-Oracle schema to conform to the naming, size, and other conventions required by Oracle Database.

### error translation

A scenario in which users can register vendor-specific translations of error codes and messages with the SQL Translation Profile. During SQL execution, client applications rely on vendor-specific error codes and messages. When errors occur, the translated error codes and messages are returned instead of the Oracle error codes and messages.

### migration

The process of modifying a non-Oracle application, including all of its components (such as architecture, data, SQL code, and client) to use the Oracle RDBMS rather than a proprietary database management system.

### migration repository

A data store in Oracle Database that Oracle SQL Developer uses to manage the metadata for the source and target schema models during a migration. Multiple migration repositories can be used to migrate from several databases to Oracle Database at the same time.

### Oracle Database Gateways

A set of Oracle products that support data integration with non-Oracle systems synchronously using consistent APIs.

### Oracle GoldenGate

An Oracle product that supports modular, transaction-level data integration between diverse data sources that are stored in SQL Server, Sybase, DB2, Oracle, and other databases.

### Oracle SQL\*Loader

A fast, flexible, and free Oracle utility that supports loading data from flat files into Oracle Database. It supports several data formats and many different encodings. It also supports parallel data loading.

### Oracle SQL Developer Migration Wizard

An Oracle tool that enables the migration of a third-party database to an Oracle database in batch mode. Migration includes data, schemas, objects, triggers, and stored procedures.

### SQL dialect

A variation or extension of SQL implemented by a database vendor. When migrating client applications from third-party databases to Oracle, all non-Oracle SQL statements must be translated into Oracle SQL. Because these non-Oracle SQL statements are embedded within the source code of client applications, locating and translating them is a time-consuming, manual task. This release enhances the Oracle database to accept non-Oracle SQL statements from external vendors, and translate them automatically at run time before execution.

### SQL Translation Profile

A database schema object that directs how non-Oracle SQL statements are translated into Oracle SQL dialects. This schema also contains translations of error codes, SQLSTATEs, and error messages to be returned when errors occur during the SQL execution.

When migrating a client application with non-Oracle SQL statements to Oracle, the user creates a SQL Translation Profile and configures it to translate the SQL statements and errors for the application. At run time, the application sets the translation profile in the Oracle database to translate its SQL statements and errors.

### SQL Translator

The SQL Translator is a software component, provided by Oracle or third-party vendors, which can be installed in Oracle Database. It translates the SQL statements of a client program before they are processed by the Oracle Database SQL compiler. If an error results from translated SQL statement execution, then Oracle Database SQL compiler generates an Oracle error message.

### SQLSTATE

A status parameter defined by the ANSI SQL standard. It is a 5-character string that indicates the status of a SQL operation. Some of these values are:

- `00``XXX`: Unqualified Successful Completion

- `01``XXX`: Warning

- `02``XXX`: No Data

- `07``XXX`: Dynamic SQL Error

- `08``XXX`: Connection Exception

- `09``XXX`: Triggered Action Exception
