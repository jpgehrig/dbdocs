## 2.189 ALL_GG_AUTO_CDR_COLUMN_GROUPS

`ALL_GG_AUTO_CDR_COLUMN_GROUPS` provides details about Oracle GoldenGate automatic conflict detection and resolution (CDR) column groups owned by the current user.

### Related View

`DBA_GG_AUTO_CDR_COLUMN_GROUPS` provides details about all of the Oracle GoldenGate automatic CDR column groups in the database.

| Column              | Datatype        | NULL       | Description                 |
|:--------------------|:----------------|:-----------|:----------------------------|
| `TABLE_OWNER`       | `VARCHAR2(128)` | `NOT NULL` | Owner of the table          |
| `TABLE_NAME`        | `VARCHAR2(128)` | `NOT NULL` | Table name                  |
| `COLUMN_GROUP_NAME` | `VARCHAR2(128)` | `NOT NULL` | Column group name           |
| `RESOLUTION_COLUMN` | `VARCHAR2(128)` | `NOT NULL` | Timestamp resolution column |

**See Also:**

"[DBA_GG_AUTO_CDR_COLUMN_GROUPS](DBA_GG_AUTO_CDR_COLUMN_GROUPS.md)"
