## 5.262 DBA_RCHILD

`DBA_RCHILD` displays all the children in any refresh group.

| Column     | Datatype        | NULL       | Description                              |
|:-----------|:----------------|:-----------|:-----------------------------------------|
| `REFGROUP` | `NUMBER`        |            | Internal identifier of the refresh group |
| `OWNER`    | `VARCHAR2(128)` | `NOT NULL` | Owner of the object in the refresh group |
| `NAME `    | `VARCHAR2(128)` | `NOT NULL` | Name of the object in the refresh group  |
| `TYPE#`    | `VARCHAR2(128)` |            | Type of the object in the refresh group  |
