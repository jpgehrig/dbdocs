The `OracleAQMessageState` enumeration type identifies the state of the message at the time of dequeue.

Table 12-33 lists all the `OracleAQMessageState` enumeration values with a description of each enumerated value.

Table 12-33 OracleAQMessageState Members

| Member Name | Description                                                       |
|:------------|:------------------------------------------------------------------|
| `Expired`   | Indicates that the message has been moved to the exception queue. |
| `Processed` | Indicates that the message has been processed and retained.       |
| `Ready`     | Indicates that the message is ready to be processed.              |
| `Waiting`   | Indicates that the message delay has not been reached.            |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- "[OracleAQMessage Class](OracleAQMessageClass.md)"

- "[State](AQMessageState.md)"
