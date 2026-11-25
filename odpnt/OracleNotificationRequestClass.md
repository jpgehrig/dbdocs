An `OracleNotificationRequest` class represents a notification request to be subscribed in the database. It contains information about the request and the characteristics of the notification. Using the `OracleNotificationRequest` class, Oracle Data Provider for .NET can create the notification registration in the database.

### Class Inheritance

`System.Object`

`  Oracle.DataAccess.Client.OracleNotificationRequest`

### Declaration

    // C#
    public sealed class OracleNotificationRequest

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

Not supported in a .NET stored procedure

### Thread Safety

All public static methods are thread-safe, although methods do not guarantee thread safety.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleNotificationRequest Members](NotificationRequestMembers.md)

- [OracleNotificationRequest Static Methods](NotificationRequestStaticMethod.md)

- [OracleNotificationRequest Properties](NotificationRequestInstanceProperties.md)

- [OracleNotificationRequest Methods](NotificationRequestInstanceMethods.md)
