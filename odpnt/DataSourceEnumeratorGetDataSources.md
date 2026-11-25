This method returns a `DataTable` object with information on all the TNS alias entries in the `tnsnames.ora `file and entries retrieved from the LDAP servers configured in `ldap.ora` if LDAP naming is enabled.

### Declaration

    // C#
    public override DataTable GetDataSources();


### Return Value

A `DataTable` object.

### Remarks

This method returns a `DataTable` object for each TNS alias entry that exists in the `tnsnames.ora` file and each entry retrieved from the LDAP servers. If a `tnsnames.ora` file is not found and LDAP Naming is not configured, then the returned `DataTable` object will be empty.

This method in ODP.NET, Managed Driver can fetch all the data source aliases from an LDAP server, such as Oracle Internet Directory or Microsoft Active Directory. This method in ODP.NET, Unmanaged Driver does not support retrieving data source aliases from an LDAP server.

When Oracle Internet Directory (OID) is used for the TNS naming repository, there is a limit of 1000 TNS entries retrieved.

The following columns are returned for each row, but only the `InstanceName` column is populated.

- `InstanceName` (type: `System.String`)

- `ServerName` (type: `System.String`)

- `ServiceName` (type: `System.String`)

- `Protocol` (type: `System.String`)

- `Port` (type: `System.String`)

If the TNS and/or LDAP information changes for existing pooled connections, then calling `GetDataSources` will not return these changes unless the pools have been cleared.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataSourceEnumerator Class](OracleDataSourceEnumeratorClass.md)

- [OracleDataSourceEnumerator Members](OracleDataSourceEnumeratorMembers.md)
