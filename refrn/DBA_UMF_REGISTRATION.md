## 6.75 DBA_UMF_REGISTRATION

`DBA_UMF_REGISTRATION` displays information about the registered nodes in the Remote Management Framework (RMF).

This view returns no rows if you are querying on an RMF source node. It returns all the registered nodes in the topology if you are querying on a target node.

| Column                | Datatype        | NULL       | Description                                                                                                                                                                                                                           |
|:----------------------|:----------------|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `TOPOLOGY_NAME`       | `VARCHAR2(128)` | `NOT NULL` | Topology name for the node                                                                                                                                                                                                            |
| `NODE_NAME`           | `VARCHAR2(128)` | `NOT NULL` | Unique node name in the topology                                                                                                                                                                                                      |
| `NODE_ID`             | `NUMBER`        | `NOT NULL` | Unique node ID in the topology                                                                                                                                                                                                        |
| `NODE_TYPE`           | `NUMBER`        | `NOT NULL` | Node type. Possible value:<br>• `0`: RDBMS node                                                                                                                                                                                       |
| `AS_SOURCE`           | `VARCHAR2(5)`   |            | Indicates whether the node is a source node. Possible values:<br>• `TRUE`: The node is a source node, and it can provide remote services<br>• `FALSE`: The node is not a source node, and it cannot provide remote services           |
| `AS_CANDIDATE_TARGET` | `VARCHAR2(5)`   |            | Node is a candidate target. Possible values:<br>• `TRUE`: Node can be promoted to target role<br>• `FALSE`: Node cannot be promoted to target role                                                                                    |
| `STATE`               | `VARCHAR2(20)`  |            | Current state of the node. Possible values:<br>• `OK`: Node is registered<br>• `REGISTRATION_PENDING`: Node registration has started, but has not been completed<br>• `SYNC_FAILED`: Unable to synchronize the topology with the node |

**See Also:**

[Oracle Database Performance Tuning Guide](../tgdba/gathering-database-statistics.md) for information about configuring the Remote Management Framework (RMF) architecture
