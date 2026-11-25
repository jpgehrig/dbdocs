This constructor instantiates the `OracleAQAgent` class using the specified name.

### Declaration

    // C#
    public OracleAQAgent(string name);

### Parameters

- `name`

  The name of the agent.

### Exceptions

`ArgumentNullException` - The `name` parameter is `null`.

`ArgumentException` - The `name` parameter is empty.

### Remarks

The agent name signifies the name of a producer or consumer of a message. In the context of functionality exposed by `Listen`, an agent name corresponds to the name of a consumer for which a message is expected on a multiconsumer queue. It may also be set on a message to signify sender identification or intended recipients of the message.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQAgent Class](OracleAQAgentClass.md)

- [OracleAQAgent Members](AQAgentMembers.md)
