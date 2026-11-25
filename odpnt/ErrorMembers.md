`OracleError` members are listed in the following tables.

### OracleError Static Methods

The `OracleError` static method is listed in Table 6-89.

Table 6-89 OracleError Static Method

| Method   | Description                                 |
|:---------|:--------------------------------------------|
| `Equals` | Inherited from `System.Object` (Overloaded) |

### OracleError Properties

`OracleError` properties are listed in Table 6-90.

Table 6-90 OracleError Properties

| Property                            | Description                                                                      |
|:------------------------------------|:---------------------------------------------------------------------------------|
| [ArrayBindIndex](ArrayBindIndex.md) | Specifies the row number of errors that occurred during the Array Bind execution |
| [DataSource](ErrorDataSource.md)    | Specifies the Oracle service name (TNS name) that identifies the Oracle database |
| [Message](ErrorMessage.md)          | Specifies the `message` describing the `error`                                   |
| [Number](ErrorNumber.md)            | Specifies the Oracle `error` number                                              |
| [Procedure](ErrorProcedure.md)      | Specifies the stored procedure that causes the `error`                           |
| [Source](ErrorSource.md)            | Specifies the name of the data provider that generates the `error`               |

### OracleError Methods

`OracleError` methods are listed in Table 6-91.

Table 6-91 OracleError Methods

| Method                       | Description                                          |
|:-----------------------------|:-----------------------------------------------------|
| `Equals`                     | Inherited from `System.Object` (Overloaded)          |
| `GetHashCode`                | Inherited from `System.Object`                       |
| `GetType`                    | Inherited from `System.Object`                       |
| [ToString](ErrorToString.md) | Returns a string representation of the `OracleError` |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleError Class](OracleErrorClass.md)
