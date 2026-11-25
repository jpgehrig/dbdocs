## 1.174 LISTENER_NETWORKS

`LISTENER_NETWORKS` specifies one or more sets of local, forward, and remote listeners for cross-registration. All listeners within the same network_name will cross-register.

| Property            | Description                                                                                                                                                                                                                          |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Parameter type      | String                                                                                                                                                                                                                               |
| Syntax              | `LISTENER_NETWORKS =`<br>` '((NAME=network_name)`<br>`  (LOCAL_LISTENER=["]listener_address[,...]["])`<br>`  (FORWARD_LISTENER=["]listener_address[,...]["])`<br>`  [(REMOTE_LISTENER=["]listener_address[,...]["])])'`<br>` [,...]` |
| Default value       | There is no default value.                                                                                                                                                                                                           |
| Modifiable          | `ALTER SYSTEM`                                                                                                                                                                                                                       |
| Modifiable in a PDB | Yes                                                                                                                                                                                                                                  |
| Basic               | No                                                                                                                                                                                                                                   |

If a network_name is specified multiple times, then the resulting listener set is the union of each specification. This can be used to specify sets that require more than 255 characters, which is the per element limit.

The listener_address specifies a string that is an address, address list, or an alias that resolves to an address or address list of Oracle Net listeners. If an alias, the address or address list is specified in the TNSNAMES.ORA file or another address repository as configured for your system.

If a comma is used to specify a listener_address list, then the set of addresses must be surrounded by double quotes.

**See Also:**

- "[LOCAL_LISTENER](LOCAL_LISTENER.md)"

- "[FORWARD_LISTENER](FORWARD_LISTENER.md)"

- "[REMOTE_LISTENER](REMOTE_LISTENER.md)"

- [Oracle Database Net Services Administrator's Guide](../netag/configuring-and-administering-oracle-net-listener.md) for more information on setting this parameter
