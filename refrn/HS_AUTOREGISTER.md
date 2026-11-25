## 1.141 HS_AUTOREGISTER

`HS_AUTOREGISTER` enables or disables automatic self-registration of Heterogeneous Services (HS) agents.

| Property            | Description    |
|:--------------------|:---------------|
| Parameter type      | Boolean        |
| Default value       | `true`         |
| Modifiable          | `ALTER SYSTEM` |
| Modifiable in a PDB | No             |
| Range of values     | `true | false` |
| Basic               | No             |

When enabled, information is uploaded into the server's data dictionary to describe a previously unknown agent class or a new agent version.

Oracle recommends that you set this parameter to `true`. Oracle incurs less overhead when establishing subsequent connections through the same agent if self-registered information is available in the server's data dictionary.

**See Also:**

[Oracle Database Heterogeneous Connectivity User's Guide](../heter/using-heterogeneous-services-agents.md) for more information about using HS agents
