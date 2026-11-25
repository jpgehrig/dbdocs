Table 13-1 provides a brief description of all the OCCI classes. This section is followed by detailed descriptions of each class and its methods.

Table 13-1 Summary of OCCI Classes

| Class                                                             | Description                                                                                                                                                                                                                                                                                     |
|:------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Agent Class](agent-class.md)                                     | Represents an agent in the Advanced Queuing context.                                                                                                                                                                                                                                            |
| [AnyData Class](anydata-class.md)                                 | Provides methods for the Object Type Translator (OTT) utility, read and write SQL methods for linearization of objects, and conversions to and from other data types.                                                                                                                           |
| [BatchSQLException Class](batchsqlexcept-class.md)                | Provides methods for handling batch processing errors; extends the [SQLException Class](sqlexecption-class.md).                                                                                                                                                                                 |
| [Bfile Class](bfile-class.md)                                     | Provides access to a SQL `BFILE` value.                                                                                                                                                                                                                                                         |
| [Blob Class](blob-class.md)                                       | Provides access to a SQL `BLOB` value.                                                                                                                                                                                                                                                          |
| [Bytes Class](bytes-class.md)                                     | Examines individual bytes of a sequence for comparing bytes, searching bytes, and extracting bytes.                                                                                                                                                                                             |
| [Clob Class](clob-class.md)                                       | Provides access to a SQL `CLOB` value.                                                                                                                                                                                                                                                          |
| [Connection Class](connection-class.md)                           | Represents a connection with a specific database.                                                                                                                                                                                                                                               |
| [ConnectionPool Class](connectionpool-class.md)                   | Represents a connection pool with a specific database.                                                                                                                                                                                                                                          |
| [Consumer Class](consumer-class.md)                               | Supports dequeuing of `Message`s and controls the dequeuing options.                                                                                                                                                                                                                            |
| [Date Class](date-class.md)                                       | Specifies abstraction for SQL DATE data items. Also provides formatting and parsing operations to support the OCCI escape syntax for date values.                                                                                                                                               |
| [Environment Class](environment-class.md)                         | Provides an OCCI environment to manager memory and other resources of OCCI objects. An OCCI driver manager maps to an OCCI environment handle.                                                                                                                                                  |
| [IntervalDS Class](intervalds-class.md)                           | Represents a time period in terms of days, hours, minutes, and seconds.                                                                                                                                                                                                                         |
| [IntervalYM Class](intervalym-class.md)                           | Represents a time period in terms of year and months.                                                                                                                                                                                                                                           |
| [Listener Class](listener-class.md)                               | Listens on behalf of one or more agents on one or more queues.                                                                                                                                                                                                                                  |
| [Map Class](map-class.md)                                         | Used to store the mapping of the SQL structured type to C++ classes.                                                                                                                                                                                                                            |
| [Message Class](message-class.md)                                 | A unit that is enqueued or dequeued.                                                                                                                                                                                                                                                            |
| [MetaData Class](metadata-class.md)                               | Used to determine types and properties of columns in a `ResultSet`, that of existing schema objects in the database, or the database as a whole.                                                                                                                                                |
| [NotifyResult Class](notifyresult-class.md)                       | Used to hold notification information from the Database AQ callback function.                                                                                                                                                                                                                   |
| [Number Class](number-class.md)                                   | Models the numeric data type.                                                                                                                                                                                                                                                                   |
| [PObject Class](pobject-class.md)                                 | When defining types, enables specification of persistent or transient instances. Class instances derived from `PObject` can be either persistent or transient. If persistent, a class instance derived from `PObject` inherits from the `PObject` class; if transient, there is no inheritance. |
| [Producer Class](producer-class.md)                               | Supports enqueuing options and enqueues `Message`s.                                                                                                                                                                                                                                             |
| [Ref Class](ref-class.md)                                         | The mapping in C++ for the SQL REF value, which is a reference to a SQL structured type value in the database.                                                                                                                                                                                  |
| [RefAny Class](refany-class.md)                                   | The mapping in C++ for the SQL REF value, which is a reference to a SQL structured type value in the database.                                                                                                                                                                                  |
| [ResultSet Class](resultset-class.md)                             | Provides access to a table of data generated by executing an OCCI `Statement`.                                                                                                                                                                                                                  |
| [SQLException Class](sqlexecption-class.md)                       | Provides information on database access errors.                                                                                                                                                                                                                                                 |
| [StatelessConnectionPool Class](statelessconnectionpool-class.md) | Represents a pool of stateless, authenticated connections to the database.                                                                                                                                                                                                                      |
| [Statement Class](statement-class.md)                             | Used for executing SQL statements, including both query statements and insert / update / delete statements.                                                                                                                                                                                     |
| [Stream Class](stream-class.md)                                   | Used to provide streamed data (usually of the LONG data type) to a prepared DML statement or stored procedure call.                                                                                                                                                                             |
| [Subscription Class](subscription-class.md)                       | Encapsulates the information and operations necessary for registering a subscriber for notification.                                                                                                                                                                                            |
| [Timestamp Class](timestamp-class.md)                             | Specifies abstraction for SQL TIMESTAMP data items. Also provides formatting and parsing operations to support the OCCI escape syntax for time stamp values.                                                                                                                                    |

### 13.1.1 Using OCCI Classes

OCCI classes are defined in the `oracle::occi` namespace. An OCCI class name within the `oracle::occi` namespace can be referred to in one of three ways:

- Use the scope resolution operator (`::`) for each OCCI class name.

- Use the `using` declaration for each OCCI class name.

- Use the `using` directive for all OCCI class name.

#### Using Scope Resolution Operator for OCCI

The scope resolution operator (`::`) is used to explicitly specify the `oracle::occi` namespace and the OCCI class name. To declare `myConnection`, a `Connection` object, using the scope resolution operator, you would use the following syntax:

    oracle::occi::Connection myConnection;

#### Using Declaration in OCCI

The `using` declaration is used when the OCCI class name can be used in a compilation unit without conflict. To declare the OCCI class name in the `oracle::occi` namespace, you would use the following syntax:

    using oracle::occi::Connection;

`Connection` now refers to `oracle::occi::Connection`, and `myConnection` can be declared as `Connection myConnection;`.

#### Using Directive in OCCI

The `using` directive is used when all OCCI class names can be used in a compilation unit without conflict. To declare all OCCI class names in the `oracle::occi` namespace, you would use the following syntax:

    using oracle::occi;

Then, just as with the `using` declaration, the following declaration would now refer to the OCCI class `Connection` as `Connection myConnection;`.

#### Using Advanced Queuing in OCCI

The Advanced Queuing classes `Producer`, `Consumer`, `Message`, `Agent`, `Listener`, `Subscription` and `NotifyResult` are defined in `oracle::occi::aq` namespace.

### 13.1.2 OCCI Support for Windows NT and z/OS

When building OCCI application on Windows, a preprocessor definition for `WIN32COMMON` has to be added.

The following global methods are designed for accessing collections of `Ref`s in [ResultSet Class](resultset-class.md) and [Statement Class](statement-class.md) on Windows NT and z/OS. While method names changed, the number of parameters and their types remain the same.

- Use `getVectorOfRefs()` instead of `getVector()` on Windows NT and z/OS.

- Use `setVectorOfRefs()` instead of `setVector()` on Windows NT and z/OS.

Applications on Windows NT and z/OS should be calling these new methods only for retrieving and inserting collections of references. Applications not running on Windows NT or z/OS can use either set of accessors. However, Oracle recommends the use of the new methods for any vector operations with `Ref`s.

This section includes the following topic: Working with Collections of Refs.

#### 13.1.2.1 Working with Collections of Refs

Collections of Refs can be fetched and inserted using methods of the following classes:

##### 13.1.2.1.1 ResultSet Class

##### Fetching Collection of Refs

Use the following version of [getVectorOfRefs()](resultset-class.md) to return a column of references:

    void getVectorOfRefs(
       ResultSet  *rs,
       unsigned int index,
       vector<Ref<T> > &vect);

##### 13.1.2.1.2 Statement Class

##### Fetching Collection of Refs

Use [getVectorOfRefs()](statement-class.md) to return a collection of references from a column:

    void getVectorOfRefs(
       Statement  *stmt,
       unsigned int index,
       vector<Ref<T> > &vect);

##### Inserting a Collection of Refs

Use [setVectorOfRefs()](statement-class.md) to insert a collection of references into a column:

    template  <class T>
    void setVectorOfRefs(
       Statement *stmt,
       unsigned int paramIndex,
       const vector<Ref<T> > &vect,
       const string &sqltype);

##### Inserting a Collection of Refs: Multibyte Support

The following method is necessary for multibyte support:

    void setVectorOfRefs(
       Statement *stmt,
       unsigned int paramIndex,
       const vector<Ref<T> > &vect,
       const string &schemaName,
       const string &typeName);

##### Inserting a Collection of Refs: UString (UTF16) Support

The following method is necessary for `UString` support:

    template <class T>
    void setVectorOfRefs(
       Statement *stmt,
       unsigned int paramIndex,
       const vector<Ref<T> > &vect,
       const UString &schemaName,
       const UString &typeName);
