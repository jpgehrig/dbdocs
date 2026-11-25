## 1.160 INSTANCE_NAME

In an Oracle Real Application Clusters environment, multiple instances can be associated with a single database service. Clients can override Oracle's connection load balancing by specifying a particular instance by which to connect to the database. `INSTANCE_NAME` specifies the unique name of this instance.

| Property            | Description                                                                                                                                                 |
|:--------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Parameter type      | String                                                                                                                                                      |
| Syntax              | `INSTANCE_NAME = ``instance_id`                                                                                                                             |
| Default value       | The instance's SID<br>Note: The SID identifies the instance's shared memory on a host, but may not uniquely distinguish this instance from other instances. |
| Modifiable          | No                                                                                                                                                          |
| Modifiable in a PDB | No                                                                                                                                                          |
| Range of values     | Alphanumeric ASCII characters and the underscore (\_) character, up to a maximum of 255 characters                                                          |
| Basic               | No                                                                                                                                                          |

In a single-instance database system, the instance name is usually the same as the database name.

**See Also:**

[Oracle Real Application Clusters Administration and Deployment Guide](../racad/administering-database-instances-and-cluster-databases.md) and [Oracle Database Net Services Administrator's Guide](../netag/configuring-and-administering-oracle-net-listener.md) for more information
