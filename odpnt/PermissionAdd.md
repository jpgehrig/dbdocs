This method adds a new connection string fragment and a list of restricted keywords to the `OraclePermission` object.

### Declaration

    // C#
    public void Add(string connStr, string keyRestrict,
       KeyRestrictionBehavior behavior);

### Parameters

- `connStr`

  The connection string fragment.

- `keyRestrict`

  The key restrictions.

- `behavior`

  One of the following `KeyRestrictionBehavior` enumerations:

  - `AllowOnly`

  - PreventUsage

### Exceptions

`ArgumentException` - The `KeyRestrictionBehavior` value or the format of the `connStr` or `keyRestict` string is invalid.

### Remarks

The `Add` method configures the connection strings allowed or disallowed by the permission object.

Opening an `OracleConnection` is allowed or denied based upon the connection string fragment, key restrictions combination, and the key restriction behavior.

In the following example, `KeyRestrictionBehavior.AllowOnly` allows connection strings that use `orcl` as the `Data Source` with any `User Id` and `Password` combination but no other connection string keywords. Connection string keywords other than `User Id` and `Password` cause security exceptions.

    orclPermission.Add("Data Source=orcl;","User Id=;Password=;",
       KeyRestrictionBehavior.AllowOnly);

In the next example, `KeyRestrictionBehavior.PreventUsage` restricts connection strings that use the keyword `Pooling`. Use of the `Pooling` keyword causes an exception.

    orclPermission.Add("Data Source=orcl;","Pooling=;",
       KeyRestrictionBehavior.PreventUsage)

As a general rule, in an unrestricted environment, any connection string that is not allowed is restricted and throws a security exception.

If a connection string fragment contains key-value pairs for the `password` and `proxy password` attributes, then values for these attributes are ignored. However, the presence of the attributes themselves is still checked. This means that the connection is allowed only if the `password` and `proxy attributes` keywords are allowed in the connection string.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OraclePermission Class](OraclePermissionClass.md)

- [OraclePermission Members](PermissionMembers.md)
