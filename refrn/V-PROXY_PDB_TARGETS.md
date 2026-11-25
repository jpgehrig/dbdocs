## 8.139 V\$PROXY_PDB_TARGETS

`V$PROXY_PDB_TARGETS` provides information about the target of a proxy PDB.

| Column           | Datatype        | Description                                                                                                                                      |
|:-----------------|:----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------|
| `CON_ID`         | `NUMBER`        | The ID of the container to which the data pertains. Possible values include:<br>n: Where n is the container ID of a proxy PDB                    |
| `TARGET_PORT`    | `NUMBER`        | Port number that the target of the proxy PDB has registered with the listener, and which will be used by the proxy PDB to connect to the target  |
| `TARGET_HOST`    | `VARCHAR2(128)` | Host name where the target of the proxy PDB is running, and which will be used by the proxy PDB to connect to the target                         |
| `TARGET_SERVICE` | `VARCHAR2(128)` | Service name that the target of the proxy PDB has registered with the listener, and which will be used by the proxy PDB to connect to the target |
| `TARGET_USER`    | `VARCHAR2(128)` | User name used by the proxy PDB to connect to the target of the proxy PDB. If null, the name of the connected user will be used.                 |

**See Also:**

[Oracle Multitenant Administrator's Guide](../multi/creating-a-proxy-pdb.md) for information about creating proxy PDBs
