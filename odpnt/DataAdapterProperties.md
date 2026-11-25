`OracleDataAdapter` properties are listed in Table 6-67.

Table 6-67 OracleDataAdapter Properties

| Property                                                                 | Description                                                                                                                                                                                         |
|:-------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `AcceptChangesDuringFill`                                                | Inherited from `System.Data.Common.DataAdapter`                                                                                                                                                     |
| `Container`                                                              | Inherited from `System.ComponentModel.Component`                                                                                                                                                    |
| `ContinueUpdateOnError`                                                  | Inherited from `System.Data.Common.DataAdapter`                                                                                                                                                     |
| [DeleteCommand](DataAdapterDeleteCommand.md)                             | A SQL statement or stored procedure to delete rows from an Oracle database                                                                                                                          |
| [IdentityInsert](DataAdapterIdentityInsert.md)                           | Determines whether or not to insert identity column values in the `DataSet` into the database when the `Update` method is invoked.<br>Not Available in the ODP.NET, Managed Driver and ODP.NET Core |
| [IdentityUpdate](DataAdapterIdentityUpdate.md)                           | Determines whether or not to update identity column values in the `DataSet` into the database when the `Update` method is invoked.<br>Not Available in the ODP.NET, Managed Driver and ODP.NET Core |
| [InsertCommand](DataAdapterInsertCommand.md)                             | A SQL statement or stored procedure to insert new rows into an Oracle database                                                                                                                      |
| `MissingMappingAction`                                                   | Inherited from `System.Data.Common.DataAdapter`                                                                                                                                                     |
| `MissingSchemaAction`                                                    | Inherited from `System.Data.Common.DataAdapter`                                                                                                                                                     |
| [Requery](DataAdapterRequery.md)                                         | Determines whether or not the `SelectCommand` is reexecuted on the next call to `Fill`                                                                                                              |
| [ReturnProviderSpecificTypes](DataAdapterReturnProviderSpecificTypes.md) | Determines if the `Fill` method returns ODP.NET-specific values or .NET common language specification values                                                                                        |
| [SafeMapping](DataAdapterSafeMapping.md)                                 | Creates a mapping between column names in the result set to .NET types, to preserve the data<br>Not Available in ODP.NET, Managed Driver and ODP.NET Core                                           |
| [SelectCommand](DataAdapterSelectCommand.md)                             | A SQL statement or stored procedure that returns a single or multiple result set                                                                                                                    |
| `Site`                                                                   | Inherited from `System.ComponentModel.Component`                                                                                                                                                    |
| `TableMappings`                                                          | Inherited from `System.Data.Common.DataAdapter`                                                                                                                                                     |
| [UpdateBatchSize](DataAdapterUpdateBatchSize.md)                         | Specifies a value that enables or disables batch processing support, and specifies the number of SQL statements that can be executed in a single round-trip to the database                         |
| [UpdateCommand](DataAdapterUpdateCommand.md)                             | A SQL statement or stored procedure to update rows from the `DataSet` to an Oracle database                                                                                                         |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataAdapter Class](OracleDataAdapterClass.md)

- [OracleDataAdapter Members](DataAdapterMembers.md)
