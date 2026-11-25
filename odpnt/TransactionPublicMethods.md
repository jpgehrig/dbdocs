`OracleTransaction` public methods are listed in Table 6-171.

Table 6-171 OracleTransaction Public Methods

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

- [OracleTransaction Members](TransactionMembers.md)
