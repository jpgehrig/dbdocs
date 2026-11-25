Table 12-31 lists all the `OracleAQDequeueMode` enumeration values with a description of each enumerated value.

Table 12-31 OracleAQDequeueMode Members

| Member Name    | Description                                                                                                                                               |
|:---------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Browse`       | Reads the message without acquiring any lock on the message. This is equivalent to a `SELECT` statement.                                                  |
| `Locked`       | Reads and obtains a write lock on the message. The lock lasts for the duration of the transaction. This is equivalent to a `SELECT FOR UPDATE` statement. |
| `Remove`       | Reads the message and updates or deletes it. This is the default.<br>The message can be retained in the queue table based on the retention properties     |
| `RemoveNoData` | Confirms receipt of the message but does not deliver the actual message content.                                                                          |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- "[OracleAQDequeueOptions Class](OracleAQDequeueOptionsClass.md)"

- "[DequeueMode](AQDequeueOptionsDequeueMode.md)"
