The processing power of Oracle Database gateways is integrated into the database.

This provides an efficient solution for information integration that enables full exploitation of the power and features of the Oracle database. This includes such features as powerful SQL parsing and distributed optimization capabilities.

These sections describe the benefits of Oracle's approach to resolving the challenges of a heterogeneous environment.

- Remote Data Can Be Accessed Transparently
  Oracle Database gateways provide the ability to transparently access data in non-Oracle databases from an Oracle environment.
- No Unnecessary Data Duplication
  Oracle Database gateways provide applications direct access to data in non-Oracle databases that reduces data duplication.
- SQL Statements Can Query Several Different Databases
  An Oracle database accepts SQL statements that query data stored in several different databases.
- Oracle's Application Development and End User Tools Can Be Used
  Oracle Database gateways extend the range of Oracle's database and application development tools.
- Users Can Communicate With a Remote Database in its Own Language
  Heterogeneous Services has a passthrough feature that enables you to bypass Oracle's query processor and to communicate with the remote database in its own language.

**Parent topic:** [Introduction to Heterogeneous Connectivity](introduction.md)

### Remote Data Can Be Accessed Transparently

Oracle Database gateways provide the ability to transparently access data in non-Oracle databases from an Oracle environment.

You can create synonyms for the objects in a non-Oracle database and refer to them without having to specify a physical location. This transparency eliminates the need for application developers to customize their applications to access data from different non-Oracle systems, thus decreasing development efforts and increasing the mobility of the application.

Instead of requiring applications to interoperate with non-Oracle systems using their native interfaces (which can result in intensive application-side processing), applications can be built upon a consistent Oracle interface for both Oracle and non-Oracle systems.

**Parent topic:** Benefits of Oracle's Solution for Synchronous Information Integration

### No Unnecessary Data Duplication

Oracle Database gateways provide applications direct access to data in non-Oracle databases that reduces data duplication.

Providing applications direct access to data in non-Oracle databases eliminates the need to upload and download large amounts of data to different locations, thus reducing data duplication and saving disk storage space. By eliminating uploading and downloading large amounts of data, there is a reduced risk for unsynchronized or inconsistent data.

**Parent topic:** Benefits of Oracle's Solution for Synchronous Information Integration

### SQL Statements Can Query Several Different Databases

An Oracle database accepts SQL statements that query data stored in several different databases.

An Oracle database with the Heterogeneous Services component processes the SQL statement and passes the appropriate SQL code directly to other Oracle databases and through gateways to non-Oracle databases. The Oracle database combines the results and returns them to the client.

**Parent topic:** Benefits of Oracle's Solution for Synchronous Information Integration

### Oracle's Application Development and End User Tools Can Be Used

Oracle Database gateways extend the range of Oracle's database and application development tools.

Oracle has tools that increase application development and user productivity by reducing prototype, development, and maintenance time.

You are not required to develop new tools or learn how to use other tools to access data stored in non-Oracle databases. Instead, you can access Oracle and non-Oracle data with a single set of Oracle tools. These tools can run on remote systems connected through Oracle Net Services to an Oracle database.

**Parent topic:** Benefits of Oracle's Solution for Synchronous Information Integration

### Users Can Communicate With a Remote Database in its Own Language

Heterogeneous Services has a passthrough feature that enables you to bypass Oracle's query processor and to communicate with the remote database in its own language.

Oracle enables you to transparently access non-Oracle systems using SQL statements. In some cases, however, it becomes necessary to use non-Oracle system SQL to access the non-Oracle system.

**Parent topic:** Benefits of Oracle's Solution for Synchronous Information Integration
