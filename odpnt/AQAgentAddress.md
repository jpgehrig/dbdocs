This instance property specifies the address of the agent.

### Declaration

    // C#
    public string Address {get; }

### Property Value

A `string` that specifies the agent address.

### Remarks

The address represents a queue at a local or remote database. The default value is `null`. The address of the agent is of the form \[`schema.`\]`queue`\[`@``dblink`\]. The string length can be up to 128 characters.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQAgent Class](OracleAQAgentClass.md)

- [OracleAQAgent Members](AQAgentMembers.md)
