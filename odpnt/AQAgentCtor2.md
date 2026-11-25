This constructor instantiates the `OracleAQAgent` class using the specified name and address.

### Declaration

    // C#
    public OracleAQAgent(string name, string address);

### Parameters

- `name`

  The name of the agent.

- `address`

  The address is of the form \[`schema.`\]`queue`\[`@``dblink`\].

### Exceptions

`ArgumentNullException` - The `address` parameter is `null.`

`ArgumentException` - The `address` parameter is empty.

### Remarks

The agent name signifies the name of a producer or consumer of a message. In the context of functionality exposed by `Listen`, an agent name corresponds to the name of a consumer for which a message is expected on a multiconsumer queue.

The `name` parameter can be specified as `null` in this constructor. In such a scenario, the agent only has an `address`.

The `address` parameter signifies the name of the queue against which this agent listens for new messages. The `address` represents a queue at a local or remote database.The validity of the `address` is not checked implicitly. The exceptions due to wrong `address` are thrown only during database operations such as `Listen`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleAQAgent Class](OracleAQAgentClass.md)

- [OracleAQAgent Members](AQAgentMembers.md)
