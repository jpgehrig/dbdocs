This method returns the value corresponding to the supplied attribute, as an output parameter.

### Declaration

    // C#
    public override bool TryGetValue(string keyword, out object value);

### Parameters

- `keyword`

  The attribute for which the value is being retrieved.

- `value`

  The value of the supplied attribute.

  Sets `value` to the default value if the attribute is not present in the connection string.

### Return Value

Returns `true` if the value that corresponds to the attribute has been successfully retrieved; otherwise, returns `false`. If the attribute is not present in the connection string, returns `false` and sets the `value` to null.

### Exceptions

`ArgumentNullException` - The specified attribute is null.

### Remarks

If the function returns `false`, sets `value` to `null`.

If the attribute is not present in the connection string, sets `value` to the default value.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnectionStringBuilder Class](OracleConnectionStringBuilderClass.md)

- [OracleConnectionStringBuilder Members](OracleConnectionStringBuilderMembers.md)
