This instance property specifies the name of the agent.

### Declaration

    // C#
    public string Name {get; }

### Property Value

A `string`.

### Remarks

The default is `null`. The string length can be up to 30 characters. A non-`null` value implies that this agent name either corresponds to a consumer name in a multiconsumer queue, or a recipient as specified in message properties.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQAgent Class](OracleAQAgentClass.md)

- [OracleAQAgent Members](AQAgentMembers.md)
