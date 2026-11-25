This method removes the entry corresponding to the specified attribute from the connection string.

### Declaration

    // C#
    public override bool Remove(string keyword);

### Parameters

- `keyword`

  The attribute that specifies the entry to be removed.

### Return Value

Returns `true` if the attribute existed in the connection string and the corresponding entry was removed; otherwise, returns `false`.

### Exceptions

`ArgumentNullException` - The specified attribute is null.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnectionStringBuilder Class](OracleConnectionStringBuilderClass.md)

- [OracleConnectionStringBuilder Members](OracleConnectionStringBuilderMembers.md)
