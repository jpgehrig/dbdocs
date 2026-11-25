`OracleConfiguration` Directories properties are listed in Table 6-34 .

Table 6-34 OracleConfiguration Directories Properties

| Property                                                               | Description                                                                                                                                                                        |
|:-----------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [DefaultAdminContext](ConfigurationDefaultAdminContext.md)             | Specifies the default directory entry that contains a LDAP Oracle Context from which connect identifiers can be created, modified, or looked up                                    |
| [DirectoryServers](ConfigurationDirectoryServers.md)                   | Lists the host names and port numbers of the primary and alternate LDAP directory servers                                                                                          |
| [DirectoryType](ConfigurationDirectoryType.md)                         | Specifies the directory server type used, such as Oracle Internet Directory or Microsoft Active Directory                                                                          |
| [LdapAdmin](ConfigurationLdapAdmin.md)                                 | Specifies the `ldap.ora` directory location                                                                                                                                        |
| [NamesLdapAuthenticateBind](ConfigurationNamesLdapAuthenticateBind.md) | Specifies whether the LDAP naming adapter should attempt to authenticate using a specified wallet when it connects to the LDAP directory to resolve the name in the connect string |
| [NamesLdapConnTimeout](ConfigurationNamesLdapConnTimeout.md)           | specifies the non-blocking connection timeout to the LDAP server                                                                                                                   |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleConfiguration Class](OracleConfigurationClass.md)

- [OracleConfiguration Members](OracleConfigurationMembers.md)
