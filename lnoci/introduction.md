This chapter contains these topics:

- Overview of OCI

- Building an OCI Application

- Alternatives to OCI

- SQL Statements

- Procedural and Nonprocedural Elements

- Object Support

- Simple Oracle Document Access (SODA)

- Encapsulated Interfaces

- User Authentication and Password Management

- Features to Improve Application Performance and Scalability

- Oracle Database Advanced Queuing

- XA Library Support

### 1.1 Overview of OCI

Oracle Call Interface (OCI) is an application programming interface (API) that lets you create applications that use function calls to access an Oracle database and control all phases of SQL statement execution and data access.

OCI supports the data types, calling conventions, syntax, and semantics of C and C++.

OCI provides:

- High performance and scalability through the efficient use of system memory and network connectivity

- Consistent interfaces for dynamic session and transaction management in a two-tier client/server or multitier environment

- N-tier authentication

- Comprehensive support for application development using Oracle Database objects

- Access to external databases, such as Oracle TimesTen In-Memory Database and Oracle In-Memory Database Cache. See Oracle TimesTen In-Memory Database C Developers Guide.

- Applications that support an increasing number of users and requests without additional hardware investments

- Ways to manipulate data and schemas in an Oracle Database using the C programming language and a library of standard database access and retrieval functions in the form of a dynamic runtime library (OCI library) that can be linked in an application at run time.

- Encapsulated or opaque interfaces, whose implementation details are unknown

- Simplified user authentication and password management

- Extensions to improve application performance and scalability

- Consistent interface for transaction management

- OCI extensions to support client-side access to Oracle objects

- Significant advantages over other methods of accessing an Oracle Database:
  - More fine-grained control over all aspects of application design

  - High degree of control over program execution

  - Use of familiar third-generation language programming techniques and application development tools, such as browsers and debuggers

  - Connection pooling, session pooling, and statement caching that enable building of scalable applications

  - Support of dynamic SQL

  - Availability on the broadest range of operating systems of all the Oracle programmatic interfaces

  - Dynamic binding and defining using callbacks

  - Description functionality to expose layers of server metadata

  - Asynchronous event notification for registered client applications

  - Enhanced array data manipulation language (DML) capability for array inserts, updates, and deletes

  - Ability to associate commit requests with executes to reduce round-trips

  - Optimization of queries using transparent prefetch buffers to reduce round-trips

  - Thread safety, which eliminates the need for mutual exclusive locks (mutexes) on OCI handles

  - APIs to design a scalable, multithreaded application that can support large numbers of users securely

  - SQL access functions, for managing database access, processing SQL statements, and manipulating objects retrieved from an Oracle database

  - Data type mapping and manipulation functions, for manipulating data attributes of Oracle types

  - Data loading functions, for loading data directly into the database without using SQL statements

  - External procedure functions, for writing C callbacks from PL/SQL

**See Also:**

- [Oracle Call Interface](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=oracle_c_call_interface)

- [Related Documents](preface.md)

### 1.2 Building an OCI Application

You compile and link an OCI program in the same way that you compile and link a non-database application. There is no need for a separate preprocessing or precompilation step.

OCI supports most popular compilers. The details of linking an OCI program vary from system to system. On some operating systems, it may be necessary to include other libraries, in addition to the OCI library, to properly link your OCI programs. See your Oracle Database system-specific documentation and the installation guide for more information about compiling and linking an OCI application for your operating system.

**See Also:**

- [Building and Configuring OCI Applications](build-and-configure-oci-applications.md)

- [SDK for Oracle Instant Client](instant-client.md)

### 1.3 Alternatives to OCI

Some alternatives to using the Oracle Call Interface (OCI) include:

- Oracle Database Programming Interface for C (ODPI-C)

- Oracle C++ Call Interface (OCCI)

- Oracle Pro\*C/C++ Precompiler

- Oracle ODBC Driver

#### Oracle Database Programming Interface for C (ODPI-C)

ODPI-C is an open source library of C code that simplifies the use of common Oracle Call Interface (OCI) features for Oracle Database drivers and user applications. ODPI-C sits on top of OCI and requires Oracle client libraries. ODPI-C:

- Favors ease of use aimed at driver writers where niche special-case OCI features are not needed.

- Provides a faster implementation of drivers with considerably less code. Oracle features can be exposed to users rapidly and in a consistent way.

- Provides simpler memory management for binding variables and fetching.

- Automatically converts binding and 'defining' (for fetches) to "native" C types so that additional calls do not need to be made. This is beneficial particularly for numbers and dates. The ability to retrieve LONG and LOB columns as strings and buffers is an advantage as well.

- Provides a "safer" API in that resource handles are validated. Casts are not needed. A reference counting mechanism adds resiliency by stopping applications from destroying in-use OCI resources.

- Provides an API that simplifies connection and resource management. For example, it automatically does session pool pinging to provide better High Availability.

- Provides an alternative programming experience from OCI that uses a multiple getter and setter model for handling attributes.

- Provides a sample Makefile that builds ODPI-C as a shared library. Or, the ODPI-C source code can be included in your project and built as you would build an OCI application.

**See Also:**

[ODPI-C Home Page](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=odpi_c_interface), for a list of ODPI-C supported features and a list of references including to its home page, code location on github, and documentation

#### Oracle C++ Call Interface (OCCI)

The Oracle C++ Call Interface (OCCI) is an application programming interface (API) that allows applications written in C++ to interact with one or more Oracle database servers. OCCI gives your programs the ability to perform the full range of database operations that are possible with an Oracle database server, including SQL statement processing and object manipulation.

**See Also:**

[Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md)

#### Oracle Pro\*C/C++ Precompiler

Oracle Pro\*C/C++ Precompiler is a programming tool that enables the user to embed SQL statements in a high-level source program. The precompiler accepts the source program as input, translates the embedded SQL statements into standard Oracle runtime library calls, and generates a modified source program that you can compile, link, and execute in the usual way.

**See Also:**

[Pro\*C/C++ Programmer's Guide](../lnpcc/introduction.md)

#### Oracle ODBC Driver

The Oracle ODBC Driver enables ODBC applications on Microsoft Windows, as well as UNIX platforms like Linux, Solaris, IBM Advanced Interactive eXecutive (AIX), HP-UX Itaniutm, and IBM Linux on Platform z read and write access to Oracle® databases through the ODBC interface using Oracle Net Services software.

**See Also:**

[Oracle Database Development Guide](../adfns/index.md) for more information about the Oracle ODBC Driver

### 1.4 SQL Statements

One of the main tasks of an OCI application is to process SQL statements.

Different types of SQL statements require different processing steps in your program. It is important to take this into account when coding your OCI application. Oracle Database recognizes several types of SQL statements:

- Data Definition Language (DDL)

- Control Statements

  - Transaction Control

  - Session Control

  - System Control

- Queries

- Data Manipulation Language (DML)

- PL/SQL

- Embedded SQL

- Special OCI Terms for SQL

**See Also:**

[Using SQL Statements in OCI](using-sql_statements-in-oci.md)

#### 1.4.1 Data Definition Language

Data definition language (DDL) statements manage schema objects in the database.

DDL statements create new tables, drop old tables, and establish other schema objects. They also control access to schema objects.

The following is an example of creating and specifying access to a table:

    CREATE TABLE employees
        (name       VARCHAR2(20),
         ssn        VARCHAR2(12),
         empno      NUMBER(6),
         mgr        NUMBER(6),
         salary     NUMBER(6));

    GRANT UPDATE, INSERT, DELETE ON employees TO donna;
    REVOKE UPDATE ON employees FROM jamie;

DDL statements also allow you to work with objects in the Oracle database, as in the following series of statements that create an object table:

    CREATE TYPE person_t AS OBJECT (
        name     VARCHAR2(30),
        ssn      VARCHAR2(12),
        address  VARCHAR2(50));

    CREATE TABLE person_tab OF person_t;

#### 1.4.2 Control Statements

OCI applications treat transaction control, session control, and system control statements as if they were DML statements.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/Types-of-SQL-Statements.md) for information about these types of statements

#### 1.4.3 Data Manipulation Language

Data manipulation language (DML) statements can change data in the database tables.

For example, DML statements are used to:

- Insert new rows into a table

- Update column values in existing rows

- Delete rows from a table

- Lock a table in the database

- Explain the execution plan for a SQL statement

- Require an application to supply data to the database using input (bind) variables

  **See Also:**

  [About Binding Placeholders in OCI](using-sql_statements-in-oci.md) for more information about input bind variables

DML statements also allow you to work with objects in the Oracle database, as in the following example, which inserts an instance of type `person_t` into the object table `person_tab`:

    INSERT INTO person_tab
        VALUES (person_t('Steve May','987-65-4320','146 Winfield Street'));

#### 1.4.4 Queries

Queries are statements that retrieve data from a database.

A query can return zero, one, or many rows of data. All queries begin with the SQL keyword `SELECT`, as in the following example:

    SELECT dname FROM dept
         WHERE deptno = 42;

Queries access data in tables, and they are often classified with DML statements. However, OCI applications process queries differently, so they are considered separately in this guide.

Queries can require the program to supply data to the database using input (bind) variables, as in the following example:

    SELECT name
        FROM employees
        WHERE empno = :empnumber;

In the preceding SQL statement, `:empnumber` is a placeholder for a value that is to be supplied by the application.

When processing a query, an OCI application also must define output variables to receive the returned results. In the preceding statement, you must define an output variable to receive any `name` values returned from the query.

**See Also:**

- [Overview of Binding in OCI](binding-and-defining-in-oci.md) for more information about input bind variables

- [Overview of Defining in OCI](binding-and-defining-in-oci.md) for information about defining output variables

- [Using SQL Statements in OCI](using-sql_statements-in-oci.md) for detailed information about how SQL statements are processed in an OCI program

#### 1.4.5 PL/SQL

PL/SQL is Oracle's procedural extension to the SQL language.

PL/SQL processes tasks that are more complicated than simple queries and SQL data manipulation language statements. PL/SQL allows some constructs to be grouped into a single block and executed as a unit. Among these are:

- One or more SQL statements

- Variable declarations

- Assignment statements

- Procedural control statements (IF...THEN...ELSE statements and loops)

- Exception handling

You can use PL/SQL blocks in your OCI program to:

- Call Oracle Database stored procedures and stored functions

- Combine procedural control statements with several SQL statements, so that they are executed as a unit

- Access special PL/SQL features such as records, tables, cursor FOR loops, and exception handling

- Use cursor variables

- Take advantage of implicit result set capability that allows reuse of existing stored procedure designs that return implicit result sets

- Access and manipulate objects in an Oracle database

The following PL/SQL example issues a SQL statement to retrieve values from a table of employees, given a particular employee number. This example also demonstrates the use of placeholders in PL/SQL statements.

    BEGIN
        SELECT ename, sal, comm INTO :emp_name, :salary, :commission
        FROM emp
        WHERE empno = :emp_number;
    END;

Note that the placeholders in this statement are not PL/SQL variables. They represent input values passed to the database when the statement is processed. These placeholders must be bound to C language variables in your program.

**See Also:**

- [Oracle Database PL/SQL Language Reference](../lnpls/main-features-pl-sql.md) for information about coding PL/SQL blocks

- [About Binding Placeholders in PL/SQL](binding-and-defining-in-oci.md) for information about working with placeholders in PL/SQL

#### 1.4.6 Embedded SQL

OCI processes SQL statements as text strings that an application passes to the database on execution.

The Oracle precompilers (Pro\*C/C++, Pro\*COBOL, Pro\*FORTRAN) allow you to embed SQL statements directly into your application code. A separate precompilation step is then necessary to generate an executable application.

It is possible to mix OCI calls and embedded SQL in a precompiler program.

**See Also:**

[Pro\*C/C++ Programmer's Guide](../lnpcc/precompiler-concepts.md)

#### 1.4.7 Special OCI Terms for SQL

This guide uses special terms to refer to the different parts of a SQL statement.

For example, consider the following SQL statement:

    SELECT customer, address
    FROM customers
    WHERE bus_type = 'SOFTWARE'
    AND sales_volume = :sales;

It contains the following parts:

- A SQL command - `SELECT`

- Two select-list items - `customer` and `address`

- A table name in the `FROM` clause - `customers`

- Two column names in the `WHERE` clause - `bus_type` and `sales_volume`

- A literal input value in the `WHERE` clause - '`SOFTWARE`'

- A placeholder for an input variable in the `WHERE` clause - `:sales`

When you develop your OCI application, you call routines that specify to the Oracle database the address (location) of input and output variables of your program. In this guide, specifying the address of a placeholder variable for data input is called a bind operation. Specifying the address of a variable to receive select-list items is called a define operation.

For PL/SQL, both input and output specifications are called bind operations.

**See Also:**

- [Using SQL Statements in OCI](using-sql_statements-in-oci.md) for more information about these terms and operations

### 1.5 Procedural and Nonprocedural Elements

OCI enables you to develop scalable, multithreaded applications in a multitier architecture that combines the nonprocedural data access power of structured query language (SQL) with the procedural capabilities of C and C++.

- In a nonprocedural language program, the set of data to be operated on is specified, but what operations are to be performed, or how the operations are to be conducted, is not specified. The nonprocedural nature of SQL makes it an easy language to learn and to use to perform database transactions. It is also the standard language used to access and manipulate data in modern relational and object-relational database systems.

- In a procedural language program, the execution of most statements depends on previous or subsequent statements and on control structures, such as loops or conditional branches, that are not available in SQL. The procedural nature of these languages makes them more complex than SQL, but it also makes them more flexible and powerful.

The combination of both nonprocedural and procedural language elements in an OCI program provides easy access to an Oracle database in a structured programming environment.

OCI supports all SQL data definition, data manipulation, query, and transaction control facilities that are available through an Oracle database. For example, an OCI program can run a query against an Oracle database. The query can require the program to supply data to the database using input (bind) variables, as follows:

    SELECT name FROM employees WHERE empno = :empnumber;

In the preceding SQL statement, `:empnumber` is a placeholder for a value that is to be supplied by the application.

You can also take advantage of PL/SQL, Oracle's procedural extension to SQL. The applications you develop can be more powerful and flexible than applications written in SQL alone. OCI also provides facilities for accessing and manipulating objects in a database.

### 1.6 Object Support

OCI has facilities for working with object types and objects.

An object type is a user-defined data structure representing an abstraction of a real-world entity. For example, the database might contain a definition of a `person` object. That object might have attributes—`first_name`, `last_name`, and `age`—to represent a person's identifying characteristics.

The object type definition serves as the basis for creating objects that represent instances of the object type by using the object type as a structural definition, you could create a `person` object with the attribute values 'John', 'Bonivento', and '30'. Object types may also contain methods—programmatic functions that represent the behavior of that object type.

OCI provides a comprehensive application programming interface for programmers seeking to use Oracle Database object capabilities.

These capabilities include:

- Executing SQL statements that manipulate object data and schema information

- Passing of object references and instances as input variables in SQL statements

- Declaring object references and instances as variables to receive the output of SQL statements

- Fetching object references and instances from a database

- Describing the properties of SQL statements that return object instances and references

- Describing PL/SQL procedures or functions with object parameters or results

- Extension of commit and rollback calls to synchronize object and relational functionality

OCI object features can be divided into the following major categories:

- Client-Side Object Cache

- Associative and Navigational Interfaces to access and manipulate objects

- OCI Runtime Environment for Objects

- Type Management: Mapping and Manipulation Functions to access information about object types and control data attributes of Oracle types

- Object Type Translator (OTT) utility, for mapping internal Oracle Database schema information to client-side language bind variables

**See Also:**

- Encapsulated Interfaces which describes additional OCI calls that are provided to support manipulation of objects after they have been accessed by SQL statements

- [Oracle Database Concepts](../cncpt/tables-and-table-clusters.md)

- [Oracle Database Object-Relational Developer's Guide](../adobj/introduction-to-oracle-objects.md)

#### 1.6.1 Client-Side Object Cache

The object cache is a client-side memory buffer that provides lookup and memory management support for objects.

The object cache stores and tracks object instances that have been fetched by an OCI application from the server to the client side. The object cache is created when the OCI environment is initialized. When multiple applications run against the same server, each has its own object cache. The cache tracks the objects that are currently in memory, maintains references to objects, manages automatic object swapping, and tracks the meta-attributes or type information about objects. The object cache provides the following features to OCI applications:

- Improved application performance by reducing the number of client/server round-trips required to fetch and operate on objects

- Enhanced scalability by supporting object swapping from the client-side cache

- Improved concurrency by supporting object-level locking

#### 1.6.2 Associative and Navigational Interfaces

What are the different types of interfaces OCI applications can use to access objects?

Applications using OCI can access objects in an Oracle database through several types of interfaces:

- Using SQL `SELECT`, `INSERT`, and `UPDATE` statements

- Using a C-style pointer chasing scheme to access objects in the client-side cache by traversing the corresponding smart pointers or `REF`s

OCI provides a set of functions with extensions to support object manipulation using SQL `SELECT`, `INSERT`, and `UPDATE` statements. To access Oracle Database objects, these SQL statements use a consistent set of steps as if they were accessing relational tables. OCI provides the following sets of functions required to access objects:

- Binding and defining object type instances and references as input and output variables of SQL statements

- Executing SQL statements that contain object type instances and references

- Fetching object type instances and references

- Describing select-list items of an Oracle object type

OCI also provides a set of functions using a C-style pointer chasing scheme to access objects after they have been fetched into the client-side cache by traversing the corresponding smart pointers or `REF`s. This navigational interface provides functions for:

- Instantiating a copy of a referenceable persistent object (that is, of a persistent object with object ID in the client-side cache) by pinning its smart pointer or `REF`

- Traversing a sequence of objects that are connected to each other by traversing the `REF`s that point from one to the other

- Dynamically getting and setting values of an object's attributes

#### 1.6.3 OCI Runtime Environment for Objects

OCI provides functions for objects to manage how Oracle Database objects are used on the client side.

These functions provide for:

- Connecting to an Oracle database server to access its object functionality, including initializing a session, logging on to a database server, and registering a connection

- Setting up the client-side object cache and tuning its parameters

- Getting errors and warning messages

- Controlling transactions that access objects in the database

- Associatively accessing objects through SQL

- Describing PL/SQL procedures or functions whose parameters or results are Oracle types

#### 1.6.4 Type Management: Mapping and Manipulation Functions

OCI provides two sets of functions to work with Oracle Database objects.

- Type Mapping functions allow applications to map attributes of an Oracle schema represented in the server as internal Oracle data types to their corresponding host language types.

- Type Manipulation functions allow host language applications to manipulate individual attributes of an Oracle schema such as setting and getting their values and flushing their values to the server.

Additionally, the `OCIDescribeAny()` function provides information about objects stored in the database.

#### 1.6.5 Object Type Translator

The Object Type Translator (OTT) utility translates schema information about Oracle object types into client-side language bindings of host language variables, such as structures.

The OTT takes as input an `intype` file that contains metadata information about Oracle schema objects. It generates an `outtype` file and the header and implementation files that must be included in a C application that runs against the object schema. Both OCI applications and Pro\*C/C++ precompiler applications may include code generated by the OTT. The OTT is beneficial because it:

- Improves application developer productivity: OTT eliminates the need for you to code the host language variables that correspond to schema objects.

- Maintains SQL as the data definition language of choice: By providing the ability to automatically map Oracle schema objects that are created using SQL to host language variables, OTT facilitates the use of SQL as the data definition language of choice. This in turn allows Oracle Database to support a consistent model of data.

- Facilitates schema evolution of object types: OTT regenerates included header files when the schema is changed, allowing Oracle applications to support schema evolution.

OTT is typically invoked from the command line by specifying the `intype` file, the `outtype` file, and the specific database connection. With Oracle Database, OTT can only generate C structures that can either be used with OCI programs or with the Pro\*C/C++ precompiler programs.

### 1.7 Simple Oracle Document Access (SODA)

SODA for C is a C API that is part of Oracle Call Interface (OCI).

SODA for C implements Simple Oracle Document Access (SODA). You can use it to perform create, read (retrieve), update, and delete (CRUD) operations on documents of any kind, and you can use it to query JSON documents. You compile programs that use SODA for C the same way you compile other OCI programs. SODA is a set of NoSQL-style APIs that let you create and store collections of documents in Oracle Database, retrieve them, and query them, without needing to know Structured Query Language (SQL) or how the data in the documents is stored in the database. Oracle Database supports storing and querying JSON data. To access this functionality, you need structured query language (SQL) with special JSON SQL operators. SODA for C hides the complexities of SQL/JSON programming.

**Related Topics**

- [Oracle Database Introduction to Simple Oracle Document Access (SODA)](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDI-GUID-BE42F8D3-B86B-43B4-B2A3-5760A4DF79FB)
- [Oracle Database SODA for C Developers Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=ADSDC-GUID-6AEC7BDD-95A9-445D-AC0E-A38770C07CB8)
- [OCI SODA Functions](oci-SODA-functions-listed.md)
- [Handles](oci-programming-basics.md)
- [SODA Collection Handle Attributes](handle-and-descriptor-attributes.md)
- [SODA Document Handle Attributes](handle-and-descriptor-attributes.md)
- [SODA Operation Options Handle Attributes](handle-and-descriptor-attributes.md)
- [SODA Output Options Handle Attributes](handle-and-descriptor-attributes.md)

### 1.8 Encapsulated Interfaces

All the data structures that are used by OCI calls are encapsulated in the form of opaque interfaces that are called handles.

A handle is an opaque pointer to a storage area allocated by the OCI library that stores context information, connection information, error information, or bind information about a SQL or PL/SQL statement. A client allocates certain types of handles, populates one or more of those handles through well-defined interfaces, and sends requests to the server using those handles. In turn, applications can access the specific information contained in a handle by using accessor functions.

The OCI library manages a hierarchy of handles. Encapsulating the OCI interfaces with these handles has several benefits to the application developer, including:

- Reduction of server-side state information that must be retained, thereby reducing server-side memory usage

- Improvement of productivity by eliminating the need for global variables, making error reporting easier, and providing consistency in the way OCI variables are accessed and used

- Allows changes to be made to the underlying structure without affecting applications

### 1.9 User Authentication and Password Management

OCI provides application developers with user authentication and password management.

This is supported in several ways:

- OCI enables a single OCI application to authenticate and maintain multiple users.

- OCI enables the application to update a user's password, which is particularly helpful if an expired password message is returned by an authentication attempt.

OCI supports two types of login sessions:

- A login function for sessions by which a single user connects to the database using a login name and password

- A mechanism by which a single OCI application authenticates and maintains multiple sessions by separating the login session (the session created when a user logs in to an Oracle database) from the user sessions (all other sessions created by a user)

Privileged connections, such as `SYSDBA`, `SYSOPER`, proxy authentication, external authentication, and others, are also supported.

#### 1.9.1 Identity and Access Management (IAM) Token-Based Authentication

This section describes token-based authentication for OCI applications. OCI accepts two types of authentication credentials, password and external. External refers to Kerberos, SSL, or RADIUS credentials. An IAM database access token (DB token) is considered as an external authentication credential.

**Note:**

This feature is currently available only on the Linux x86-64 platform.

An updated Oracle Instant Client 19.13 release for Linux x64 introduces token-based authentication for OCI applications. The application obtains the DB token from IAM. See [Authenticating and Authorizing IAM Users for Oracle DBaaS Databases](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md) sections for more information. You can pass this token to the OCI using one of the following methods:

- At deployment without application change: Store the token in a token file whose location is provided as an input to OCI the functions. It is assumed that a token file contains only one token corresponding to an IAM user.
- Programmatically requiring application change: Provide the token dynamically as an attribute-value pair using the enhanced OCI API.

Currently, OCI supports Proof of Possession (PoP) access tokens of Oracle Cloud Infrastructure for IAM token-based authentication. The PoP tokens are associated with a public-private key pair.

In an Oracle Cloud Infrastructure PoP token, the public key of the client is embedded in the token as a JSON Web Key (JWK) field. The database server can verify that OCI has the corresponding private key. An Oracle Cloud Infrastructure PoP token is used for both identity and scope for resources within the tenancy or compartments. When a PoP DB token is provided for database access, the associated private key must also be provided. The client of the token can be authenticated by registering the PoP key during the Single Sign-On (SSO) flow.

**Note:**

The IAM DB token are short-lived with a default expiry time of 60 minutes. They need to be renewed after expiring.

**See also:**

- [Authentication Information Handle Attributes](handle-and-descriptor-attributes.md)
- [TAF Support for IAM Based Token Authentication in OCI](high-availability-in-oci.md)
- [TOKEN_LOCATION](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=NETRF-GUID-4408A56B-3F32-452E-8A5E-4F9D08AFDA5C)
- [TOKEN_AUTH](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=NETRF-GUID-442189CA-D703-4361-936D-22DCE83A6D2C)
- [Configuring a Client Connection for SQL\*Plus That Uses an IAM Token](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)
- [Authenticating and Authorizing IAM Users for Oracle DBaaS Databases](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)

##### 1.9.1.1 Standalone User Session

This section describes the enhancements for supporting DB tokens for standalone session creation.

The following are the only session creation APIs that are enhanced to support DB tokens:

- `OCISessionBegin()`
- `OCISessionGet()`

###### 1.9.1.1.1 Providing the DB Token Programmatically

Typically the `OCISessionBegin()` and `OCISessionGet()`functions accept a user handle with a database username and password set as attributes. With token-based authentication, instead of setting the the username and password the two new attributes, `OCI_ATTR_TOKEN` and `OCI_ATTR_IAM_PRIVKEY`, must be set on the user handle. These attributes must be set before invoking the `OCISessionBegin()` function. These attributes specify the DB token and the private key respectively.

There are other attributes that are used in IAM-based token authentication to set the callback functions for session pools.

**See Also:**

[Authentication Information Handle Attributes](handle-and-descriptor-attributes.md)

###### 1.9.1.1.2 Providing the DB Token in a File

This section explains how the DB token is provided in a file.

To provide the DB token in a file

- The DB token is a unique string of characters that you can request from IAM using the Oracle Cloud Infrastructure (OCI) Command Line Interface (CLI).

- This DB token is copied to a token file.

- The location of the token file is specified in the database connect string with a new parameter, `TOKEN_LOCATION`.

- `OCI_CRED_EXT` mode is passed to the `OCISessionBegin()` call.

- `OCI_SESSGET_CREDEXT` mode is passed to the `OCISessionGet()` call.

- No username or password is specified in the authentication handle or the user handle in the preceding calls.

**See Also:**

[Authenticating and Authorizing IAM Users for Oracle DBaaS Databases](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)

##### 1.9.1.2 Session Pool

This section describes the enhancements to `OCISessionPool` for supporting DB tokens.

Applications use OCI session pool to cache the sessions. The application can get a session from the pool, execute the database operations and return the session back to the pool.

**Note:**

DB token-based authentication is supported only by the homogeneous session pools.

###### 1.9.1.2.1 Providing the DB Token Programmatically

An authentication handle can be set on a session pool handle to specify pre-session creation attributes. The authentication handle is enhanced to support setting the DB token and private key.

Perform the following steps before creating the session pool as this feature requires the DB token and private key attributes to be set on this authentication handle.

1.  Allocate `OCIAuthInfo` and `OCISPool` handles
2.  Set the DB token and private key attributes on the authentication handle
3.  Set the authentication handle on the session pool handle
4.  Call `OCISessionPoolCreate(…, <null user/passwd arguments> …,OCI_SPC_HOMOGENEOUS)`
5.  Issue `OCISessionGet(…, OCI_SESSGET_SPOOL)` and `OCISessionRelease()` calls using the pool to check out and check in the sessions
6.  The token and the key in the authentication handle are cached by OCI after the call to the `OCISessionPoolCreate()` function
7.  When the pool needs to expand (create new connections), if the token expires, then it calls a callback function that must provide the latest token and key

OCI also provides other attributes to set the callback function and context for session pools using IAM-based token authentication. The callback attributes must be set to renew the expired tokens for the sessions in the session pool programmatically through OCI. Refer to the section "Authentication Information Handle Attributes" for more details on creating and setting the callback attributes, functions, and context for token-based authentication in OCI.

###### 1.9.1.2.2 Providing the DB Token in a File

To provide the DB token in a file:

- The location of the token file is specified in the database connect string with a new parameter `TOKEN_LOCATION`
- Call `OCISessionPoolCreate(…, <null user/passwd arguments>, .. OCI_DEFAULT)`
- Pass `OCI_SESSGET_CREDEXT` mode to the `OCISessionGet()` call
- No username or password is specified in the authentication handle or the user handle in the preceeding calls
- If the session pool has to create a new connection, and the original token has expired, session establishment succeeds if the user has replaced the original token file contents with the new token value

**See Also:**

- [TOKEN_LOCATION](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=NETRF-GUID-4408A56B-3F32-452E-8A5E-4F9D08AFDA5C)
- [TOKEN_AUTH](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/lnoci&id=NETRF-GUID-442189CA-D703-4361-936D-22DCE83A6D2C)

### 1.10 Features to Improve Application Performance and Scalability

OCI provides several feature extensions to improve application performance and scalability.

Application performance has been improved by reducing the number of client to server round-trips required, and scalability improvements have been made by reducing the amount of state information that must be retained on the server side. Some of these features include:

- Statement caching to improve performance by caching executable statements that are used repeatedly

- Client result caching to limit the number of round trips to the database server

- Implicit prefetching of `SELECT` statement result sets to eliminate the describe round-trip, reduce round-trips, and reduce memory usage

- Elimination of open and close cursor round-trips

- Support for multithreaded environments

- Session multiplexing over connections

- Consistent support for a variety of configurations, including standard two-tier client/server configurations, server-to-server transaction coordination, and three-tier transaction processing (TP)-monitor configurations

- Consistent support for local and global transactions, including support for the XA interface's TM_JOIN operation

- Improved scalability by providing the ability to concentrate connections, processes, and sessions across users on connections and by eliminating the need for separate sessions to be created for each branch of a global transaction

- Allowing applications to authenticate multiple users and allow transactions to be started on their behalf

### 1.11 Oracle Database Advanced Queuing

OCI provides an interface to Oracle Database Advanced Queuing (Database AQ) feature.

Database AQ provides message queuing as an integrated part of Oracle Database. Database AQ provides this functionality by integrating the queuing system with the database, thereby creating a message-enabled database. By providing an integrated solution, Database AQ frees you to devote your efforts to your specific business logic rather than having to construct a messaging infrastructure.

**See Also:**

[OCI and Database Advanced Queuing](notification-streams-advanced-queuing.md)

### 1.12 XA Library Support

OCI supports the Oracle XA library.

The `xa.h` header file is in the same location as all the other OCI header files. For Linux or UNIX, the path is `$ORACLE_HOME/rdbms/public`. Users of the `demo_rdbms.mk` file on Linux or UNIX are not affected because this make file includes the `$ORACLE_HOME/rdbms/public` directory.

For Windows, the path is `ORACLE_BASE\ORACLE_HOME`\\`oci\include`.

**See Also:**

- [Oracle XA Library](getting-started-with-oci-for-windows.md) for more information about Windows and XA applications

- [Oracle Database Development Guide](../adfns/xa.md) for information about developing applications with Oracle XA
