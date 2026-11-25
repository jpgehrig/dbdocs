`OracleCommand` members are listed in the following tables.

### OracleCommand Constructors

`OracleCommand` constructors are listed in Table 6-8.

Table 6-8 OracleCommand Constructors

| Constructor                                         | Description                                                       |
|:----------------------------------------------------|:------------------------------------------------------------------|
| [OracleCommand Constructors](OracleCommandCtors.md) | Instantiates a new instance of `OracleCommand` class (Overloaded) |

### OracleCommand Static Methods

The `OracleCommand` static method is listed in Table 6-9.

Table 6-9 OracleCommand Static Method

| Method   | Description                                 |
|:---------|:--------------------------------------------|
| `Equals` | Inherited from `System.Object` (Overloaded) |

### OracleCommand Properties

`OracleCommand` properties are listed in Table 6-10.

Table 6-10 OracleCommand Properties

| Property                                                   | Description                                                                                                                                                                 |
|:-----------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [AddRowid](CommandAddRowid.md)                             | Adds the `ROWID` as part of the select list                                                                                                                                 |
| [AddToStatementCache](CommandAddToStatementCache.md)       | Causes executed statements to be cached, when the property is set to `true` and statement caching is enabled                                                                |
| [ArrayBindCount](CommandArrayBindCount.md)                 | Specifies if the array binding feature is to be used and also specifies the maximum number of array elements to be bound in the `Value` property                            |
| [ArrayBindRowsAffected](CommandArrayBindRowsAffected.md)   | Returns the number of affected rows for each iteration while executing a DML using array binding                                                                            |
| [BindByName](CommandBindByName.md)                         | Specifies the binding method in the collection                                                                                                                              |
| [CommandText](CommandCommandText.md)                       | Specifies the SQL statement or stored procedure to run against the Oracle database or the XML data used to store changes to the Oracle database                             |
| [CommandTimeout](CommandCommandTimeout.md)                 | Specifies the number of seconds the command is allowed to execute before terminating the execution with an exception                                                        |
| [CommandType](CommandCommandType.md)                       | Specifies the command type that indicates how the `CommandText` property is to be interpreted                                                                               |
| [Connection](CommandConnection.md)                         | Specifies the `OracleConnection` object that is used to identify the connection to execute a command                                                                        |
| `Container`                                                | Inherited from `System.ComponentModel.Component`                                                                                                                            |
| [DesignTimeVisible](CommandDesignTimeVisible.md)           | Specifies whether or not the `OracleCommand` object is visible on designer controls.                                                                                        |
| [FetchSize](CommandFetchSize.md)                           | Specifies the size of `OracleDataReader`'s internal cache to store result set data                                                                                          |
| [ImplicitRefCursors](CommandImplicitRefCursors.md)         | Specifies an array of `OracleRefCursors` mapped to an implicit resultset returned by the stored procedure.<br>Not Available in the ODP.NET, Managed Driver and ODP.NET Core |
| [InitialLOBFetchSize](CommandInitialLOBFetchSize.md)       | Specifies the amount of data that the `OracleDataReader` initially fetches for LOB columns                                                                                  |
| [InitialLONGFetchSize](CommandInitialLONGFetchSize.md)     | Specifies the amount of data that the `OracleDataReader` initially fetches for `LONG` and `LONG` `RAW` columns                                                              |
| [Notification](CommandNotification.md)                     | Indicates that there is a notification request for the command                                                                                                              |
| [NotificationAutoEnlist](CommandNotificationAutoEnlist.md) | Indicates whether or not to register for a continuous query notification with the database automatically when the command is executed                                       |
| [Parameters](CommandParameters.md)                         | Specifies the parameters for the SQL statement or stored procedure                                                                                                          |
| [RowSize](CommandRowSize.md)                               | Specifies the amount of memory needed by the `OracleDataReader` internal cache to store one row of data                                                                     |
| Site                                                       | Inherited from `System.ComponentModel.Component`                                                                                                                            |
| [Transaction](CommandTransaction.md)                       | Specifies the `OracleTransaction` object in which the `OracleCommand` executes<br>Not supported in a .NET stored procedure                                                  |
| [UpdatedRowSource](CommandUpdatedRowSource.md)             | Specifies how query command results are applied to the row being updated<br>Not supported in a .NET stored procedure                                                        |
| [UseEdmMapping](CommandUseEdmMapping.md)                   | Indicates whether or not the command object utilizes the Entity Data Model mapping configuration values                                                                     |
| [XmlCommandType](CommandXmlCommandType.md)                 | Specifies the type of XML operation on the `OracleCommand`                                                                                                                  |
| [XmlQueryProperties](CommandXmlQueryProperties.md)         | Specifies the properties that are used when an XML document is created from the result set of a SQL query statement                                                         |
| [XmlSaveProperties](CommandXmlSaveProperties.md)           | Specifies the properties that are used when an XML document is used to save changes to the database                                                                         |

### OracleCommand Public Methods

`OracleCommand` public methods are listed in Table 6-11.

Table 6-11 OracleCommand Public Methods

| Public Method                                     | Description                                                                                                                                           |
|:--------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Cancel](CommandCancel.md)                        | Attempts to cancels a command that is currently executing on a particular connection                                                                  |
| [Clone](CommandClone.md)                          | Creates a copy of `OracleCommand` object                                                                                                              |
| `CreateObjRef`                                    | Inherited from `System.MarshalByRefObject`                                                                                                            |
| [CreateParameter](CommandCreateParameter.md)      | Creates a new instance of `OracleParameter` class                                                                                                     |
| [Dispose](CommandDispose.md)                      | Releases any resources or memory allocated by the object                                                                                              |
| `Equals`                                          | Inherited from `System.Object` (Overloaded)                                                                                                           |
| [ExecuteNonQuery](CommandExecuteNonQuery.md)      | Executes a SQL statement or a command using the `XmlCommandType` and `CommandText` properties and returns the number of rows affected                 |
| [ExecuteReader](CommandExecuteReaderOverloads.md) | Executes a command (Overloaded)                                                                                                                       |
| [ExecuteScalar](CommandExecuteScalar.md)          | Returns the first column of the first row in the result set returned by the query                                                                     |
| [ExecuteStream](CommandExecuteStream.md)          | Executes a command using the `XmlCommandType` and `CommandText` properties and returns the results in a new `Stream` object                           |
| [ExecuteToStream](CommandExecuteToStream.md)      | Executes a command using the `XmlCommandType` and `CommandText` properties and appends the results as an XML document to the existing `Stream`        |
| [ExecuteXmlReader](CommandExecuteXmlReader.md)    | Executes a command using the `XmlCommandType` and `CommandText` properties and returns the result as an XML document in a .NET `XmlTextReader` object |
| `GetHashCode`                                     | Inherited from `System.Object`                                                                                                                        |
| `GetLifetimeService`                              | Inherited from `System.MarshalByRefObject`                                                                                                            |
| `GetType`                                         | Inherited from `System.Object`                                                                                                                        |
| `InitializeLifetimeService`                       | Inherited from `System.MarshalByRefObject`                                                                                                            |
| [Prepare](CommandPrepare.md)                      | This method is a no-op                                                                                                                                |
| `ToString`                                        | Inherited from `System.Object`                                                                                                                        |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)
