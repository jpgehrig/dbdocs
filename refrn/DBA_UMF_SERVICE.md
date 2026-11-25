## 6.76 DBA_UMF_SERVICE

`DBA_UMF_SERVICE` displays information about the registered services in the Remote Management Framework (RMF).

This view returns no rows if you are querying on an RMF source node. It returns all the registered services in the topology if you are querying on a target node

| Column          | Datatype        | NULL       | Description                                                                                       |
|:----------------|:----------------|:-----------|:--------------------------------------------------------------------------------------------------|
| `TOPOLOGY_NAME` | `VARCHAR2(128)` | `NOT NULL` | Topology name for the service                                                                     |
| `NODE_ID`       | `NUMBER`        | `NOT NULL` | Node ID of the node providing the service                                                         |
| `SERVICE_ID`    | `VARCHAR2(7)`   |            | Service Identifier. Possible values:<br>• `1`: Automatic Workload Repository<br>• `2`: SQL Tuning |

**See Also:**

[Oracle Database Performance Tuning Guide](../tgdba/gathering-database-statistics.md) for information about configuring the Remote Management Framework (RMF) architecture
