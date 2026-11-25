This property contains detailed information about the current notification.

### Declaration

    // C#
    Public DataTable Details{get;}

### Property Value

A `DataTable` instance that contains detailed information about the current notification.

### Remarks

The returned `DataTable` object contains column data about the current notification in order as shown in Table 9-25.

Table 9-25 DataTable Object Column Data

| Name           | Type                     | Description                                                                                   |
|:---------------|:-------------------------|:----------------------------------------------------------------------------------------------|
| `ResourceName` | `System.String`          | The resource name of the invalidated object in the format \<`Schema_name`\>.\<`object_name`\> |
| `Info`         | `OracleNotificationInfo` | The information about the database event that occurs on a resource                            |
| `Rowid`        | `System.String`          | The rowid for the invalidated table row                                                       |
| `QueryId`      | `Int32`                  | The `CHANGE_NOTIFICATION_QUERY_ID`                                                            |

The `QueryId` column contains the `CHANGE_NOTIFICATION_QUERY_ID` that corresponds to the pseudo-column that may have been retrieved by a SELECT statement at the time of the query-based notification. Also, the `OracleDependency` object maintains all the `CHANGE_NOTIFICATION_QUERY_ID`s that are registered with it.

For Continuous Query Notification:

- The `Details` property indicates changes for each invalidated object in the notification in the data table.

- If `ROWID` information is requested, then the `ROWID` information is populated into the `Rowid` column. However, if many rows are modified in a table, then the whole table is invalidated, and `ROWID` information is not provided. Therefore, the `Rowid` column contains all `Null` values.

- If the database event is related to a DDL change of the table or a table drop, then the `Rowid` column is set to `Null`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleNotificationEventArgs Class](OracleNotificationEventArgsClass.md)

- [OracleNotificationEventArgs Members](NotificationEventArgsMembers.md)
