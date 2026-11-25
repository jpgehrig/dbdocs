`OracleDataAdapter` events are listed in Table 6-69.

Table 6-69 OracleDataAdapter Events

| Event Name                               | Description                                                                 |
|:-----------------------------------------|:----------------------------------------------------------------------------|
| `Disposed`                               | Inherited from `System.ComponentModel.Component`                            |
| `FillError`                              | Inherited from `System.Data.Common.DbDataAdapter`                           |
| [RowUpdated](DataAdapterRowUpdated.md)   | This event is raised when row(s) have been updated by the `Update()` method |
| [RowUpdating](DataAdapterRowUpdating.md) | This event is raised when row data are about to be updated to the database  |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataAdapter Class](OracleDataAdapterClass.md)

- [OracleDataAdapter Members](DataAdapterMembers.md)
