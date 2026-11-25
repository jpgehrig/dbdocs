`OracleRefCursor` members are listed in the following tables.

### OracleRefCursor Static Methods

`OracleRefCursor` static methods are listed in Table 13-28.

Table 13-28 OracleRefCursor Static Methods

| Methods  | Description                                 |
|:---------|:--------------------------------------------|
| `Equals` | Inherited from `System.Object` (Overloaded) |

### OracleRefCursor Static Fields

`OracleRefCursor` static field is listed in Table 13-29.

Table 13-29 OracleRefCursor Static Field

| Methods                             | Description                                                                   |
|:------------------------------------|:------------------------------------------------------------------------------|
| [Null](RefcursorStaticFieldNull.md) | Represents a null value that can be assigned to an `OracleRefCursor` instance |

### OracleRefCursor Properties

`OracleRefCursor` properties are listed in Table 13-30.

Table 13-30 OracleRefCursor Properties

| Properties                           | Description                                                                                        |
|:-------------------------------------|:---------------------------------------------------------------------------------------------------|
| [Connection](RefcursorConnection.md) | A reference to the `OracleConnection` used to fetch the `REF` `CURSOR` data                        |
| [FetchSize](RefcursorFetchSize.md)   | Specifies the size that the `OracleDataReader` internal cache needs to store result set data       |
| [IsNull](RefcursorIsNull.md)         | Indicates whether or not the `OracleRefCursor` is null                                             |
| [RowSize](RefcursorRowSize.md)       | Specifies the amount of memory the `OracleRefcursor` internal cache needs to store one row of data |

### OracleRefCursor Instance Methods

`OracleRefCursor` instance methods are listed in Table 13-31.

Table 13-31 OracleRefCursor Instance Methods

| Methods                                    | Description                                                      |
|:-------------------------------------------|:-----------------------------------------------------------------|
| [Dispose](RefcursorDispose.md)             | Disposes the resources allocated by the `OracleRefCursor` object |
| `Equals`                                   | Inherited from `System.Object` (Overloaded)                      |
| [GetDataReader](RefcursorGetDataReader.md) | Returns an `OracleDataReader` object for the `REF` `CURSOR`      |
| `GetHashCode`                              | Inherited from `System.Object`                                   |
| `GetType`                                  | Inherited from `System.Object`                                   |
| `ToString`                                 | Inherited from `System.Object`                                   |

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleRefCursor Class](OracleRefCursorClass.md)
