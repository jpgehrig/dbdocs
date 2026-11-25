`OracleDataAdapter` members are listed in the following tables.

### OracleDataAdapter Constructors

`OracleDataAdapter` constructors are listed in Table 6-61.

Table 6-61 OracleDataAdapter Constructors

| Constructor                                           | Description                                                           |
|:------------------------------------------------------|:----------------------------------------------------------------------|
| [OracleDataAdapter Constructors](DataAdapterCtors.md) | Instantiates a new instance of `OracleDataAdapter` class (Overloaded) |

### OracleDataAdapter Static Methods

The `OracleDataAdapter` static method is listed in Table 6-62.

Table 6-62 OracleDataAdapter Static Method

| Method   | Description                                 |
|:---------|:--------------------------------------------|
| `Equals` | Inherited from `System.Object` (Overloaded) |

### OracleDataAdapter Properties

`OracleDataAdapter` properties are listed in Table 6-63.

Table 6-63 OracleDataAdapter Properties

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
| [SafeMapping](DataAdapterSafeMapping.md)                                 | Creates a mapping between column names in the result set to .NET types, to preserve the data<br>Not Available in the ODP.NET, Managed Driver and ODP.NET Core                                       |
| [SelectCommand](DataAdapterSelectCommand.md)                             | A SQL statement or stored procedure that returns a single or multiple result set                                                                                                                    |
| `Site`                                                                   | Inherited from `System.ComponentModel.Component`                                                                                                                                                    |
| `TableMappings`                                                          | Inherited from `System.Data.Common.DataAdapter`                                                                                                                                                     |
| [UpdateBatchSize](DataAdapterUpdateBatchSize.md)                         | Specifies a value that enables or disables batch processing support, and specifies the number of SQL statements that can be executed in a single round-trip to the database                         |
| [UpdateCommand](DataAdapterUpdateCommand.md)                             | A SQL statement or stored procedure to update rows from the `DataSet` to an Oracle database                                                                                                         |

### OracleDataAdapter Public Methods

`OracleDataAdapter` public methods are listed in Table 6-64.

Table 6-64 OracleDataAdapter Public Methods

| Public Method                       | Description                                                                                   |
|:------------------------------------|:----------------------------------------------------------------------------------------------|
| `CreateObjRef`                      | Inherited from `System.MarshalByRefObject`                                                    |
| `Dispose`                           | Inherited from `System.ComponentModel.Component`                                              |
| `Equals`                            | Inherited from `System.Object` (Overloaded)                                                   |
| [Fill](DataAdapterFillOverloads.md) | Adds or refreshes rows in the `DataSet` to match the data in the Oracle database (Overloaded) |
| `FillSchema`                        | Inherited from `System.Data.Common.DbDataAdapter`                                             |
| `GetFillParameters`                 | Inherited from `System.Data.Common.DbDataAdapter`                                             |
| `GetHashCode`                       | Inherited from `System.Object`                                                                |
| `GetLifetimeService`                | Inherited from `System.MarshalByRefObject`                                                    |
| `GetType`                           | Inherited from `System.Object`                                                                |
| `InitializeLifetimeService`         | Inherited from `System.MarshalByRefObject`                                                    |
| `ToString`                          | Inherited from `System.Object`                                                                |
| `Update`                            | Inherited from `System.Data.Common.DbDataAdapter`                                             |

### OracleDataAdapter Events

`OracleDataAdapter` events are listed in Table 6-65.

Table 6-65 OracleDataAdapter Events

| Event Name                               | Description                                                                 |
|:-----------------------------------------|:----------------------------------------------------------------------------|
| `Disposed`                               | Inherited from `System.ComponentModel.Component`                            |
| `FillError`                              | Inherited from `System.Data.Common.DbDataAdapter`                           |
| [RowUpdated](DataAdapterRowUpdated.md)   | This event is raised when row(s) have been updated by the `Update()` method |
| [RowUpdating](DataAdapterRowUpdating.md) | This event is raised when row data are about to be updated to the database  |
