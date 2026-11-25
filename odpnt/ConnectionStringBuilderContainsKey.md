This method indicates whether or not a specific attribute in the connection string is supported by ODP.NET.

### Declaration

    // C#
    public override bool ContainsKey(string keyword);

### Parameters

- `keyword`

  The attribute being verified.

### Return Value

Returns `true` if the specified attribute exists; otherwise, returns `false`.

### Exceptions

`ArgumentNullException` - The specified attribute is null.

### Remarks

This method indicates if the attribute is part of the provider-supported attributes. It does not indicate if the user added the attribute to the connection string.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnectionStringBuilder Class](OracleConnectionStringBuilderClass.md)

- [OracleConnectionStringBuilder Members](OracleConnectionStringBuilderMembers.md)
