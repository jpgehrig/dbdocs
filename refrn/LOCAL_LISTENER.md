## 1.176 LOCAL_LISTENER

`LOCAL_LISTENER` specifies a network name that resolves to an address or address list of Oracle Net local listeners (that is, listeners that run on the same system as this instance). The address or address list is specified in the `TNSNAMES.ORA` file or other address repository as configured for your system.

| Property            | Description                                                                                                        |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------|
| Parameter type      | String                                                                                                             |
| Syntax              | `LOCAL_LISTENER = ``network_name`                                                                                  |
| Default value       | `(ADDRESS = (PROTOCOL=TCP)(HOST=``hostname``)(PORT=1521))` where `hostname` is the network name of the local host. |
| Modifiable          | `ALTER SYSTEM`                                                                                                     |
| Modifiable in a PDB | Yes                                                                                                                |
| Basic               | No                                                                                                                 |

**See Also:**

- [Oracle Database Concepts](../cncpt/application-and-networking-architecture.md) for more information about listener processes and dispatcher processes

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-and-administering-oracle-net-listener.md) and your operating system-specific Oracle documentation for more information about specifying network addresses for the protocols on your system
