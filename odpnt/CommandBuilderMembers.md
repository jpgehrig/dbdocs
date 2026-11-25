`OracleCommandBuilder` members are listed in the following tables.

### OracleCommandBuilder Constructors

`OracleCommandBuilder` constructors are listed in Table 6-15.

Table 6-15 OracleCommandBuilder Constructors

| Constructor                                                 | Description                                                              |
|:------------------------------------------------------------|:-------------------------------------------------------------------------|
| [OracleCommandBuilder Constructors](CommandBuilderCtors.md) | Instantiates a new instance of `OracleCommandBuilder` class (Overloaded) |

### OracleCommandBuilder Static Methods

`OracleCommandBuilder` static methods are listed in Table 6-16.

Table 6-16 OracleCommandBuilder Static Methods

| Method                                                | Description                                                                                                                                                                                   |
|:------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [DeriveParameters](CommandBuilderDeriveParameters.md) | Queries for the parameters of a stored procedure or function, represented by a specified `OracleCommand`, and populates the `OracleParameterCollection` of the command with the return values |
| `Equals`                                              | Inherited from `System.Object` (Overloaded)                                                                                                                                                   |

### OracleCommandBuilder Properties

`OracleCommandBuilder` properties are listed in Table 6-17.

Table 6-17 OracleCommandBuilder Properties

| Property                                              | Description                                                                                                                                              |
|:------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Container`                                           | Inherited from `System.ComponentModel.Component`                                                                                                         |
| [CaseSensitive](CommandBuilderCaseSensitive.md)       | Indicates whether or not double quotes are used around Oracle object names when generating SQL statements                                                |
| [CatalogLocation](CommandBuilderCatalogLocation.md)   | Not Supported                                                                                                                                            |
| [CatalogSeparator](CommandBuilderCatalogSeparator.md) | Not Supported                                                                                                                                            |
| [ConflictOption](CommandBuilderConflictOption.md)     | Not Supported                                                                                                                                            |
| [DataAdapter](CommandBuilderDataAdapter.md)           | Indicates the `OracleDataAdapter` for which the SQL statements are generated                                                                             |
| [QuotePrefix](CommandbuilderQuotePrefix.md)           | Specifies the beginning character or characters used to specify database objects whose names contain special characters such as spaces or reserved words |
| [QuoteSuffix](CommandbuilderQuoteSuffix.md)           | Specifies the ending character or characters used to specify database objects whose names contain special characters such as spaces or reserved words    |
| [SchemaSeparator](CommandBuilderSchemaSeparator.md)   | Specifies the character to be used for the separator between the schema identifier and other identifiers                                                 |
| `Site`                                                | Inherited from `System.ComponentModel.Component`                                                                                                         |

### OracleCommandBuilder Public Methods

`OracleCommandBuilder` public methods are listed in Table 6-18.

Table 6-18 OracleCommandBuilder Public Methods

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

### OracleCommandBuilder Events

The `OracleCommandBuilder` event is listed in Table 6-19.

Table 6-19 OracleCommandBuilder Events

| Event Name | Description                                      |
|:-----------|:-------------------------------------------------|
| `Disposed` | Inherited from `System.ComponentModel.Component` |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommandBuilder Class](OracleCommandBuilderClass.md)
