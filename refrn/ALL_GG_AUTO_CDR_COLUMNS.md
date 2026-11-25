## 2.190 ALL_GG_AUTO_CDR_COLUMNS

`ALL_GG_AUTO_CDR_COLUMNS` provides details about Oracle GoldenGate automatic conflict detection and resolution (CDR) columns owned by the current user.

### Related View

`DBA_GG_AUTO_CDR_COLUMNS` provides details about all of the Oracle GoldenGate automatic CDR columns in the database.

| Column              | Datatype        | NULL | Description                 |
|:--------------------|:----------------|:-----|:----------------------------|
| `TABLE_OWNER`       | `VARCHAR2(128)` |      | Owner of the table          |
| `TABLE_NAME`        | `VARCHAR2(128)` |      | Table name                  |
| `COLUMN_GROUP_NAME` | `VARCHAR2(128)` |      | Column group name           |
| `COLUMN_NAME`       | `VARCHAR2(128)` |      | Column name                 |
| `RESOLUTION_COLUMN` | `VARCHAR2(128)` |      | Timestamp resolution column |

**See Also:**

"[DBA_GG_AUTO_CDR_COLUMNS](DBA_GG_AUTO_CDR_COLUMNS.md)"
