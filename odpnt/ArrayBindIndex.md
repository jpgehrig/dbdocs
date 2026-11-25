This property specifies the row number of errors that occurred during the Array Bind execution.

### Declaration

    // C#
    public int ArrayBindIndex {get;}

### Property Value

An `int` value that specifies the row number for errors that occurred during the Array Bind execution.

### Remarks

Default = 0.

This property is used for Array Bind operations only.

`ArrayBindIndex` represents the zero-based row number at which the error occurred during an Array Bind operation. For example, if an array bind execution causes two errors on the 2nd and 4th operations, two `OracleError` objects appear in the `OracleErrorCollection` with the `ArrayBindIndex` property values 2 and 4 respectively.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleError Class](OracleErrorClass.md)

- [OracleError Members](ErrorMembers.md)

- "[Array Binding](featOraCommand.md)"
