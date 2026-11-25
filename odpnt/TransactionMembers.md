`OracleTransaction` members are listed in the following tables.

### OracleTransaction Static Methods

The `OracleTransaction` static method is listed in Table 6-166.

Table 6-166 OracleTransaction Static Method

| Method   | Description                                 |
|:---------|:--------------------------------------------|
| `Equals` | Inherited from `System.Object` (Overloaded) |

### OracleTransaction Properties

`OracleTransaction` properties are listed in Table 6-167.

Table 6-167 OracleTransaction Properties

| Property                                       | Description                                                      |
|:-----------------------------------------------|:-----------------------------------------------------------------|
| [IsolationLevel](TransactionIsolationlevel.md) | Specifies the isolation level for the transaction                |
| [Connection](TransactionConnection.md)         | Specifies the connection that is associated with the transaction |

### OracleTransaction Public Methods

`OracleTransaction` public methods are listed in Table 6-168.

Table 6-168 OracleTransaction Public Methods

| Public Method                               | Description                                                |
|:--------------------------------------------|:-----------------------------------------------------------|
| [Commit](TransactionCommit.md)              | Commits the database transaction                           |
| `CreateObjRef `                             | Inherited from `System.MarshalByRefObject`                 |
| [Dispose](TransactionDispose.md)            | Frees the resources used by the `OracleTransaction` object |
| `Equals`                                    | Inherited from `System.Object` (Overloaded)                |
| `GetHashCode`                               | Inherited from `System.Object`                             |
| `GetLifetimeService`                        | Inherited from `System.MarshalByRefObject`                 |
| `GetType`                                   | Inherited from `System.Object`                             |
| `InitializeLifetimeService`                 | Inherited from `System.MarshalByRefObject`                 |
| [Rollback](TransactionRollbackOverloads.md) | Rolls back a database transaction (Overloaded)             |
| [Save](TransactionSave.md)                  | Creates a savepoint within the current transaction         |
| `ToString`                                  | Inherited from `System.Object`                             |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleTransaction Class](OracleTransactionClass.md)
