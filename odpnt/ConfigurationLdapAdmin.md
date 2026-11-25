This property specifies the `ldap.ora` directory location.

### Declaration

    // C#
    public static string LdapAdmin  { get; set; }

### Property Type

`System.String`

The `LdapAdmin` setting works in conjunction with the `TnsAdmin` setting to determine the `ldap.ora` search order.

### Example

    // C#
    OracleConfiguration.LdapAdmin=@"D:\user\ldap\";

### Remarks

ODP.NET will search for ldap.ora using the following location search order:

1.  `TnsAdmin` setting

2.  `LdapAdmin` setting

3.  Directory of the running ODP.NET Core assembly

4.  Current working directory

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
