This property returns or sets the an entry for a unique logical server name, which is to be associated with a list of nodes.

### Declaration

    // C#
    public string this[string serverName] { get; set; }

### Parameters

- `serverName`

  - Type: `System.String`

  - Unique logical server name to be added or updated

- `Value`

  - Type: `System.String`

  - Node names and remote ports for the list of nodes that ODP.NET shares ONS communication with using the following example format: `nodeList=racnode1:4200, racnode2:4200`

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleOnsServerCollection Class](OracleOnsServerCollectionClass.md)

- [OracleOnsServerCollection Members](OracleOnsServerCollectionMembers.md)
