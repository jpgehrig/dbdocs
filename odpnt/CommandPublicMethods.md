`OracleCommand` public methods are listed in Table 6-14.

Table 6-14 OracleCommand Public Methods

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
| `GetLifetimeService`                              | Inherited from System.`MarshalByRefObject`                                                                                                            |
| `GetType`                                         | Inherited from `System.Object`                                                                                                                        |
| `InitializeLifetimeService`                       | Inherited from `System.MarshalByRefObject`                                                                                                            |
| [Prepare](CommandPrepare.md)                      | This method is a no-op                                                                                                                                |
| `ToString`                                        | Inherited from `System.Object`                                                                                                                        |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)
