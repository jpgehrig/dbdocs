The `OracleHAEventArgs` properties are listed in Table 8-2.

Table 8-2 OracleHAEventArgs Properties

| Name                                                   | Description                                                                                           |
|:-------------------------------------------------------|:------------------------------------------------------------------------------------------------------|
| [DatabaseDomainName](HAEventArgsDatabaseDomainName.md) | Specifies the domain name of the database affected by the `HAevent`                                   |
| [DatabaseName](HAEventArgsDatabaseName.md)             | Specifies the database affected by the HAevent                                                        |
| [DrainTimeout](HAEventArgsDrainTimeout.md)             | Indicates the number of seconds allowed for resource draining to be completed during a planned outage |
| [HostName](HAEventArgsHostName.md)                     | Specifies the host that triggered the event                                                           |
| [InstanceName](HAEventArgsInstanceName.md)             | Specifies the instance that triggered the event                                                       |
| [Reason](HAEventArgsReason.md)                         | Specifies the reason for which the HA event was sent by the server                                    |
| [ServiceName](HAEventArgsServiceName.md)               | Specifies the service that triggered the event                                                        |
| [Source](HAEventArgsSource.md)                         | Specifies the source that triggered the event                                                         |
| [Status](HAEventArgsStatus.md)                         | Specifies the status of the source that triggered the event                                           |
| [Time](HAEventArgsTime.md)                             | Specifies the time when the event was triggered on the server                                         |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleHAEventArgs Class](OracleHAEventArgsClass.md)

- [OracleHAEventArgs Members](HAEventArgsMembers.md)
