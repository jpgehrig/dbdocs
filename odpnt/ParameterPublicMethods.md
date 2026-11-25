`OracleParameter` public methods are listed in Table 6-128.

Table 6-128 OracleParameter Public Methods

| Public Method                                      | Description                                                                                                        |
|:---------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------|
| [Clone](ParameterClone.md)                         | Creates a shallow copy of an `OracleParameter` object                                                              |
| `CreateObjRef`                                     | Inherited from `System.MarshalByRefObject`                                                                         |
| [Dispose](ParameterDispose.md)                     | Releases allocated resources                                                                                       |
| `Equals`                                           | Inherited from `System.Object` (Overloaded)                                                                        |
| `GetHashCode`                                      | Inherited from `System.Object`                                                                                     |
| `GetLifetimeService`                               | Inherited from `System.MarshalByRefObject`                                                                         |
| `GetType`                                          | Inherited from `System.Object`                                                                                     |
| `InitializeLifetimeService`                        | Inherited from `System.MarshalByRefObject`                                                                         |
| [ResetDbType](ParameterResetDbType.md)             | Resets the type associated with the parameter so that it can infer its type from the value passed in the parameter |
| [ResetOracleDbType](ParameterResetOracleDbType.md) | Resets the type associated with the parameter so that it can infer its type from the value passed in the parameter |
| [ToString](ParameterToString.md)                   | Returns the string representation of the current instance                                                          |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameter Members](ParameterMembers.md)
