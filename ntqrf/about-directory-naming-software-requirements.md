Directory naming method maps connect identifiers to connect descriptors contained in Microsoft Active Directory server.

A directory server provides central administration of database services and net service names, making it easier to add or relocate services.

Use Oracle Enterprise Manager or Oracle Net Manager to create net service names. To use Microsoft Active Directory naming method, the Oracle Database Client must run on supported Windows operating systems. You must have Oracle Database that is required for registering the database service as an object in Active Directory. The database server can run on any of the supported operating system, not necessarily Windows operating system.

By default, directory naming adaptor connects anonymously to active directory. Authenticated naming method requires client computer to be a part of the active directory domain to resolve a database service or net service name to a connect descriptor stored in a central directory server of its domain.

`NAMES.LDAP_AUTHENTICATE_BIND=``true` parameter in `sqlnet.ora` file enables authenticated naming method.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-naming-methods.md)

**Parent topic:** [Overview of Requirements for Using Oracle Database with Active Directory](overview-of-requirements-for-using-oracle-database-with-active-directory.md)
