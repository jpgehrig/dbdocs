## 6.74 DBA_UMF_LINK

`DBA_UMF_LINK` displays information about the registered database links in the Remote Management Framework (RMF).

This view returns no rows if you are querying on an RMF source node. It returns all the registered database links in the topology if you are querying on a target node.

| Column          | Datatype        | NULL       | Description                        |
|:----------------|:----------------|:-----------|:-----------------------------------|
| `TOPOLOGY_NAME` | `VARCHAR2(128)` | `NOT NULL` | Topology name for the link         |
| `FROM_NODE_ID`  | `NUMBER`        | `NOT NULL` | Node ID of the local node          |
| `TO_NODE_ID`    | `NUMBER`        | `NOT NULL` | Node ID of the remote node         |
| `LINK_NAME`     | `VARCHAR2(128)` | `NOT NULL` | Fully qualified database link name |

**See Also:**

[Oracle Database Performance Tuning Guide](../tgdba/gathering-database-statistics.md) for information about configuring the Remote Management Framework (RMF) architecture
