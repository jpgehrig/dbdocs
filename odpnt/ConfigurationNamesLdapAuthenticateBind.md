This property specifies whether the LDAP naming adapter should attempt to authenticate using a specified wallet when it connects to the LDAP directory to resolve the name in the connect string.

### Declaration

    // C#
    public static bool NamesLdapAuthenticateBind   { get; set; }

### Property Type

`System.Boolean`

If the parameter is set to `true`, then the LDAP connection is authenticated using a wallet whose location must be specified in the `OracleConfiguration.WalletLocation` property.

If the parameter is set to `false`, then the LDAP connection is established using an anonymous bind.

Default value is `false`.

### Example

    // C#
    OracleConfiguration.NamesLdapAuthenticateBind = true;

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
