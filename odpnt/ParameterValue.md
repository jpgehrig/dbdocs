This property specifies the value of the `Parameter`.

### Declaration

    // C#
    public override object Value { get; set; }

### Property Value

An `object`.

### Implements

`IDataParameter`

### Exceptions

`ArgumentException` - The `Value` property specified is invalid.

`InvalidArgumentException`- The `Value` property specified is invalid.

### Remarks

Default = `null`

If the `OracleParameter` object is used for Array Bind or PL/SQL Associative Array, `Value` is an array of parameter values.

The `Value` property can be overwritten by `OracleDataAdapter.Update()`.

The provider attempts to convert any type of value if it supports the `IConvertible` interface. Conversion errors occur if the specified type is not compatible with the value.

When sending a `null` parameter value to the database, the user must specify `DBNull`, not `null`. The `null` value in the system is an empty object that has no value. `DBNull` is used to represent `null` values. The user can also specify a `null` value by setting `Status` to `OracleParameterStatus.NullValue`. In this case, the provider sends a `null` value to the database.

If neither `OracleDbType` nor `DbType` are set, their values can be inferred by `Value`. Please see the following for related information:

- Tables in section "[Inference of DbType and OracleDbType from Value](featOraCommand.md)"

- "[ArrayBindCount](CommandArrayBindCount.md)"

- "[ArrayBindSize](ParameterArrayBindSize.md)"

- "[ArrayBindStatus](ParameterArrayBindStatus.md)"

- "[OracleDbType Enumeration](OracleDbTypeEnumerationType.md)"

For input parameters the value is:

- Bound to the `OracleCommand` that is sent to the database.

- Converted to the data type specified in `OracleDbType` or `DbType` when the provider sends the data to the database.

For output parameters the value is:

- Set on completion of the `OracleCommand` (true for return value parameters also).

- Set to the data from the database, to the data type specified in `OracleDbType` or `DbType`.

When array binding is used with:

- Input parameter - `Value` should be set to an array of values. `OracleCommand.ArrayBindCount` should be set to a value that is greater than zero to indicate the number of elements to be bound.

  The number of elements in the array should be equal to the `OracleCommand.ArrayBindCount` property; otherwise, their minimum value is used to bind the elements in the array.

- Output parameter - `OracleCommand.ArrayBindCount` should be set to a value that is greater than zero to indicate the number of elements to be retrieved (for `SELECT` statements).

When PL/SQL Associative Array binding is used with:

- Input parameter – Value should be set to an array of values. `CollectionType` should be set to `OracleCollection.PLSQLAssociativeArray.Size` should be set to specify the possible maximum number of array elements in the PL/SQL Associative Array. If `Size` is smaller than the number of elements in `Value`, then `Size` specifies the number of elements in the Value property to be bound.

- Output parameter - `CollectionType` should be set to `OracleCollection.PLSQLAssociativeArray`. `Size` should be set to specify the maximum number of array elements in PL/SQL Associative Array.

Each parameter should have a value. To bind a parameter with a `null` value, set `Value` to `DBNull.Value`, or set `Status` to `OracleParameterStatus.` `NullInsert`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameter Members](ParameterMembers.md)

- "[ArrayBindCount](CommandArrayBindCount.md)"

- "[OracleParameterStatus Enumeration](OracleParameterStatusEnumeration.md)"
