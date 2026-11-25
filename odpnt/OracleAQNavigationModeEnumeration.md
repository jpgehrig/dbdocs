Table 12-35 lists all the `OracleAQNavigationMode` enumeration values with a description of each enumerated value.

Table 12-35 OracleAQNavigationMode Members

| Member Name              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:-------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `FirstMessage`           | Retrieves the first message that is available and matches the search criteria. This resets the position to the beginning of the queue.                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `FirstMessageMultiGroup` | Indicates that a call to `DequeueArray` resets the position to the beginning of the queue, and dequeues messages that are available and match the search criteria. Messages are dequeued till the `dequeueCount` limit is reached. The dequeued messages can belong to different transaction groups.<br>You can use the `OracleAQMessage.TransactionGroup` property to distinguish between messages from different transaction groups. All messages from the same transaction group have the same value for the `OracleAQMessage.TransactionGroup` property. |
| `NextMessage`            | Retrieves the next message that is available and matches the search criteria. If the previous message belongs to a message group, AQ retrieves the next available message that matches the search criteria and belongs to the message group.                                                                                                                                                                                                                                                                                                                 |
| `NextMessageMultiGroup`  | Indicates that a call to `DequeueArray` dequeues the next set of messages that are available and match the search criteria. Messages are dequeued till the `dequeueCount` limit is reached. The dequeued messages can belong to different transaction groups.<br>You can use the `OracleAQMessage.TransactionGroup` property to distinguish between messages from different transaction groups. All messages from the same transaction group have the same value for the `OracleAQMessage.TransactionGroup` property.                                        |
| `NextTransaction`        | Skips the remainder of the current transaction group (if any) and retrieves the first message of the next transaction group.                                                                                                                                                                                                                                                                                                                                                                                                                                 |

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  |
|:---------------|:---------------------------|
| Assembly       | `Oracle.DataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- "[OracleAQDequeueOptions Class](OracleAQDequeueOptionsClass.md)"

- "[NavigationMode](AQDequeueOptionsNavigationMode.md)"
