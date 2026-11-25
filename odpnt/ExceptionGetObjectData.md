Overrides `Exception`

This method sets the serializable `info` object with information about the exception.

### Declaration

    // C#
    public override void GetObjectData(SerializationInfo info, StreamingContext
        context);

### Parameters

- `info`

  A `SerializationInfo` object.

- `context`

  A `StreamingContext` object.

### Remarks

The information includes `DataSource`, `Message`, `Number`, `Procedure`, `Source`, and `StackTrace`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleException Class](OracleExceptionClass.md)

- [OracleException Members](ExceptionMembers.md)
