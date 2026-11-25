This method adds unique entries in the `OracleOnsServerCollection` using logical server names and it's corresponding list of nodes.

### Declaration

    // C#
    public void Add(string serverName, string nodeList)

### Parameters

- `serverName`

  - Type: `System.String`

  - A unique logical name for a list of nodes to be added

- `nodeList`

  - Type: `System.String`

  - Node names and remote ports for the list of nodes that ODP.NET shares ONS communication with using the following example format: `nodeList=racnode1:4200, racnode2:4200`

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleOnsServerCollection Class](OracleOnsServerCollectionClass.md)

- [OracleOnsServerCollection Members](OracleOnsServerCollectionMembers.md)
