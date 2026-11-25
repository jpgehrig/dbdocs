Overrides `Exception`

This property specifies the error messages that occur in the exception.

### Declaration

    // C#
    public override string Message {get;}

### Property Value

A `string`.

### Remarks

`Message` is a concatenation of all errors in the `Errors` collection. Each error message is concatenated and is followed by a carriage return, except the last one.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleException Class](OracleExceptionClass.md)

- [OracleException Members](ExceptionMembers.md)
