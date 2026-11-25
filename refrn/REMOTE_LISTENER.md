## 1.304 REMOTE_LISTENER

`REMOTE_LISTENER` specifies a network name that resolves to an address or address list of Oracle Net remote listeners (that is, listeners that are not running on the same system as this instance). The address or address list is specified in the `TNSNAMES.ORA` file or other address repository as configured for your system.

| Property            | Description                        |
|:--------------------|:-----------------------------------|
| Parameter type      | String                             |
| Syntax              | `REMOTE_LISTENER = ``network_name` |
| Default value       | There is no default value.         |
| Modifiable          | `ALTER SYSTEM`                     |
| Modifiable in a PDB | Yes                                |
| Basic               | Yes                                |

**See Also:**

- [Oracle Database Concepts](../cncpt/application-and-networking-architecture.md) for more information about listener processes and dispatcher processes

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-and-administering-oracle-net-listener.md) and your operating system-specific Oracle documentation for more information about specifying network addresses for the protocols on your system

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-clusterware-administration.md) for information about SCAN addresses
