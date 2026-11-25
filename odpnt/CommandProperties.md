`OracleCommand` properties are listed in Table 6-13.

Table 6-13 OracleCommand Properties

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
| Container                                                  | Inherited from `System.ComponentModel.Component`                                                                                                                            |
| [DesignTimeVisible](CommandDesignTimeVisible.md)           | Specifies whether or not the `OracleCommand` object is visible on designer controls.                                                                                        |
| [FetchSize](CommandFetchSize.md)                           | Specifies the size of `OracleDataReader`'s internal cache to store result set data                                                                                          |
| [ImplicitRefCursors](CommandImplicitRefCursors.md)         | Specifies an array of `OracleRefCursors` mapped to an implicit resultset returned by the stored procedure.<br>Not Available in the ODP.NET, Managed Driver and ODP.NET Core |
| [InitialLOBFetchSize](CommandInitialLOBFetchSize.md)       | Specifies the amount of data that the `OracleDataReader` initially fetches for LOB columns                                                                                  |
| [InitialLONGFetchSize](CommandInitialLONGFetchSize.md)     | Specifies the amount that of data the `OracleDataReader` initially fetches for `LONG` and `LONG` `RAW` columns                                                              |
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

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)
