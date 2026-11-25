`OracleRef` members are listed in the following tables.

### OracleRef Constructors

`OracleRef` constructors are listed in Table 16-30.

Table 16-30 OracleRef Constructors

| Constructor                                  | Description                                                   |
|:---------------------------------------------|:--------------------------------------------------------------|
| [OracleRef Constructors](RefConstructors.md) | Instantiates a new instance of `OracleRef` class (Overloaded) |

### OracleRef Static Fields

OracleRef static methods are listed in Table 16-31

Table 16-31 OracleRef Static Fields

| Static Field       | Description                                                             |
|:-------------------|:------------------------------------------------------------------------|
| [Null](RefNull.md) | Represents a null value that can be assigned to an `OracleRef` instance |

### OracleRef Static Methods

`OracleRef` static methods are listed in Table 16-32.

Table 16-32 OracleRef Static Methods

| Method   | Description                                 |
|:---------|:--------------------------------------------|
| `Equals` | Inherited from `System.Object` (Overloaded) |

### OracleRef Instance Properties

`OracleRef` instance properties are listed in Table 16-33.

Table 16-33 OracleRef Instance Properties

| Property                                 | Description                                                                     |
|:-----------------------------------------|:--------------------------------------------------------------------------------|
| [Connection](RefConnection.md)           | References the connection used by the `OracleRef`                               |
| [HasChanges](RefHasChanges.md)           | References the connection used by the `OracleRef`                               |
| [IsLocked](RefIsLocked.md)               | Indicates whether or not the `REF` is locked                                    |
| [IsNull](RefIsNull.md)                   | Indicates whether or not the Oracle `REF` is `NULL`                             |
| [ObjectTableName](RefObjectTableName.md) | Returns the fully qualified object table name that is associated with the `REF` |
| [Value](RefValue.md)                     | Returns a .NET representation of this Oracle `REF`                              |

### OracleRef Instance Methods

`OracleRef` instance methods are listed in Table 16-34.

Table 16-34 OracleRef Instance Methods

| Method                                                              | Description                                                                                            |
|:--------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------|
| [Clone](RefClone.md)                                                | Clones the `REF`                                                                                       |
| [Delete](RefDelete.md)                                              | Deletes the referenced object from the database                                                        |
| [Dispose](RefDispose.md)                                            | Releases resources allocated for the `OracleRef` instance                                              |
| `Equals`                                                            | Inherited from `System.Object`                                                                         |
| [Flush](RefFlush.md)                                                | Flushes changes made on the `REF` object to the database                                               |
| [GetCustomObject](RefGetCustomObjectOverloads.md)                   | Returns the object that the specified REF references as a custom type (Overloaded)                     |
| [GetCustomObjectForUpdate](RefGetCustomObjectForUpdateOverloads.md) | Returns the object that the specified REF references as a custom type (Overloaded)                     |
| `GetHashCode`                                                       | Inherited from `System.Object`                                                                         |
| `GetType`                                                           | Inherited from `System.Object`                                                                         |
| [IsEqual](RefIsEqual.md)                                            | Compares two `OracleREF` objects                                                                       |
| [Lock](RefLock.md)                                                  | Locks the `REF` in the database                                                                        |
| `ToString`                                                          | Inherited from `System.Object`                                                                         |
| [Update](RefUpdate.md)                                              | Updates the object referenced by the specified `REF` in the database using the specified custom object |

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleRef Class](OracleRefClass.md)
