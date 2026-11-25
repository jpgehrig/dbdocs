## 6.77 DBA_UMF_TOPOLOGY

`DBA_UMF_TOPOLOGY` displays information about the registered topologies in the Remote Management Framework (RMF).

This view returns no rows if you are querying on an RMF source node. It returns one row per registered topology if you are querying on a target node.

| Column             | Datatype        | NULL       | Description                                                                                                                         |
|:-------------------|:----------------|:-----------|:------------------------------------------------------------------------------------------------------------------------------------|
| `TOPOLOGY_NAME`    | `VARCHAR2(128)` | `NOT NULL` | Unique topology name                                                                                                                |
| `TARGET_ID`        | `NUMBER`        |            | Node ID of the target node                                                                                                          |
| `TOPOLOGY_VERSION` | `NUMBER`        | `NOT NULL` | Topology version number                                                                                                             |
| `TOPOLOGY_STATE`   | `VARCHAR2(8)`   |            | Possible values:<br>• `ACTIVE`: Topology can be used for RMF operations<br>• `INACTIVE`: Topology cannot be used for RMF operations |

**See Also:**

[Oracle Database Performance Tuning Guide](../tgdba/gathering-database-statistics.md) for information about configuring the Remote Management Framework (RMF) architecture
