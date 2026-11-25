`OracleCommandBuilder` public methods are listed in Table 6-22.

Table 6-22 OracleCommandBuilder Public Methods

| Public Method                                                  | Description                                                                                                                                        |
|:---------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|
| `CreateObjRef`                                                 | Inherited from `System.``MarshalByRefObject`                                                                                                       |
| `Dispose`                                                      | Inherited from `System.ComponentModel.Component`                                                                                                   |
| `Equals`                                                       | Inherited from `System.``Object` (Overloaded)                                                                                                      |
| [GetDeleteCommand](CommandBuilderGetDeleteCommandOverloads.md) | Gets the automatically generated `OracleCommand` object that has the SQL statement (`CommandText`) perform deletions on the database (Overloaded)  |
| `GetHashCode`                                                  | Inherited from `System.``Object`                                                                                                                   |
| [GetInsertCommand](CommandBuilderGetInsertCommandOverloads.md) | Gets the automatically generated `OracleCommand` object that has the SQL statement (`CommandText`) perform insertions on the database (Overloaded) |
| `GetLifetimeService`                                           | Inherited from `System.MarshalByRefObject`                                                                                                         |
| `GetType`                                                      | Inherited from `System.``Object`                                                                                                                   |
| [GetUpdateCommand](CommandBuilderGetUpdateCommandOverloads.md) | Gets the automatically generated `OracleCommand` object that has the SQL statement (`CommandText`) perform updates on the database (Overloaded)    |
| `InitializeLifetimeService`                                    | Inherited from `System.MarshalByRefObject`                                                                                                         |
| [QuoteIdentifier](CommandBuilderQuoteIdentifier.md)            | Returns the correct quoted form of the provided unquoted identifier, with any embedded quotes in the identifier properly escaped                   |
| [RefreshSchema](CommandBuilderRefreshSchema.md)                | Refreshes the database schema information used to generate `INSERT`, `UPDATE`, or `DELETE` statements                                              |
| [UnquoteIdentifier](CommandBuilderUnquoteIdentifier.md)        | Returns the correct unquoted form of the provided quoted identifier, removing any escape notation for quotes embedded in the identifier            |
| `ToString`                                                     | Inherited from `System.Object`                                                                                                                     |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommandBuilder Class](OracleCommandBuilderClass.md)

- [OracleCommandBuilder Members](CommandBuilderMembers.md)
