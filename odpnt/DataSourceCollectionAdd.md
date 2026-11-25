This method adds unique network service name (TNS) entries in the OracleDataSourceCollection using net service names and complete connect descriptors.

### Declaration

    // C#
    public void Add(string tnsName, string tnsDescriptor)

### Parameters

- `tnsName`

  - Type: `System.String`

  - Network service name used as the ODP.NET connection string Data Source name.

- `tnsDescriptor`

  - Type: `System.String`

  - The complete connect descriptor information for this specific net service name.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleDataSourceCollection Class](OracleDataSourceCollectionClass.md)

- [OracleDataSourceCollection Members](OracleDataSourceCollectionMembers.md)
