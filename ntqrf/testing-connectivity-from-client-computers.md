When using Oracle Net directory naming, client computers connect to a database by specifying the database or net service name entry that appears in the Oracle Context.

For example, if the database entry under the Oracle Context in Active Directory is `orcl`, and the client and the database are in the same domain, then a user connects to the database through SQL\*Plus by entering the following connect string:

    SQL> CONNECT username@orcl
    Enter password: password

If the client and the database are in different domains, then a user connects to the database through SQL\*Plus by entering:

    SQL> CONNECT username@orcl.domain
    Enter password: password

where `domain` is the domain in which the Oracle Database server is located.

The LDAP naming adapter has an internal function called simplified naming, which attempts to translate a DNS-style name into an x500 (LDAP) style name (DN) based on the naming convention used in `ldap.ora:DEFAULT_ADMIN_CONTEXT.`

It relies on `ldap.ora:default_admin_context` using either an org form or a domain component (dc) form. This cues the mechanism to use either of the following conventions to convert the domain name to an x500 DN:

- 'dc=, dc='

- 'ou=, o='

- 'ou=, o=, c='

For example,

    SQL> CONNECT SMITH@hr.example.com
    Enter password: password

The following values for default_admin_context results in the associated DN:

    DEFAULT_ADMIN_CONTEXT="o=stdev"

The resulting DN is

    cn=HR,cn=OracleContext,ou=EXAMPLE,o=COM

    DEFAULT_ADMIN_CONTEXT="dc=oracle, dc=com"

The resulting DN is

    cn=HR,cn=OracleContext,dc=EXAMPLE,dc=COM

    DEFAULT_ADMIN_CONTEXT="o=oracle,c=us"

The resulting DN is

    cn=HR,cn=OracleContext,o=EXAMPLE,c=COM

**Note:**

The value of the `default_admin_context` is not used literally, since the queried-name is given in a fully qualified form. The `default_admin_context` determines which style DN is produced, or which side to use when converting each domain in the given DN component.

DNS-style conventions enable client users to access an Oracle Database server through a directory server by entering minimal connection information, even when the client computer and Oracle Database server are in separate domains. Names following the X.500 convention are longer, especially when the client and Oracle Database server are located in different domains (also known as administrative contexts).

**See Also:**

- [Oracle Database Net Services Administrator's Guide](../netag/part-II-config-and-admin-of-oracle-net-services.md) for more information about Configuration Management Concepts

- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/unlocking-and-resetting-user-passwords.md) for more information about Minimum Requirements for Passwords

**Parent topic:** [About Testing Connectivity](about-testing-connectivity.md)
