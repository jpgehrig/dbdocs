This property is used to get or set an `OracleCredential` object on the connection.

### Declaration

    // C#
    public OracleCredential Credential { get; set; }

### Property Value

An `OracleCredential` object to be used for opening connection.

### Remarks

To obtain the `OracleCredential` object through the property getter, “persist security info” must be set to true in the connection string.

If “Persist security info” is set to false in the Connection String, then the `OracleCredential` object is not returned through the property getter after the password has been validated.

The application can set this property with an `OracleCredential` object. An `InvalidOperationException` will be raised in following scenarios:

- If connection is already open.

- If connection string has already been set on this connection and it contains any of `user id`, `password`, `DBA Privilege`, `proxy user id`or `proxy password`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConnection Class](OracleConnectionClass.md)

- [OracleConnection Members](ConnectionMembers.md)

- [OracleConnectionType Enumeration](OracleConnectionTypeEnumeration.md)
