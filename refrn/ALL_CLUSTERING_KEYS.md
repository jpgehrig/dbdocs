## 2.120 ALL_CLUSTERING_KEYS

`ALL_CLUSTERING_KEYS` describes clustering keys for tables with an attribute clustering clause accessible to the user.

### Related Views

- `DBA_CLUSTERING_KEYS` describes clustering keys for all tables with an attribute clustering clause.

- `USER_CLUSTERING_KEYS` describes clustering keys for tables with an attribute clustering clause owned by the user.

| Column          | Datatype        | NULL       | Description                                                     |
|:----------------|:----------------|:-----------|:----------------------------------------------------------------|
| `OWNER`         | `VARCHAR2(128)` | `NOT NULL` | Owner of the table on which the clustering clause is defined    |
| `TABLE_NAME`    | `VARCHAR2(128)` | `NOT NULL` | Name of the table on which the clustering clause is defined     |
| `DETAIL_OWNER`  | `VARCHAR2(128)` | `NOT NULL` | Owner of the detailed table contributing to the clustering keys |
| `DETAIL_NAME`   | `VARCHAR2(128)` | `NOT NULL` | Name of the detailed table contributing to the clustering keys  |
| `DETAIL_COLUMN` | `VARCHAR2(128)` | `NOT NULL` | Name of the detail column                                       |
| `POSITION`      | `NUMBER`        | `NOT NULL` | Position of the column in the clustering clause                 |
| `GROUPID`       | `NUMBER`        | `NOT NULL` | Group ID of the column in the clustering clause                 |

**See Also:**

- "[DBA_CLUSTERING_KEYS](DBA_CLUSTERING_KEYS.md)"

- "[USER_CLUSTERING_KEYS](USER_CLUSTERING_KEYS.md)"

- The `ALTER TABLE` section in [Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md) for information about using the `CLUSTERING` clause to create an attribute clustering table

- The `CREATE TABLE` section in [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for information about using the `CLUSTERING` clause to create an attribute clustering table

- [Oracle Database Data Warehousing Guide](../dwhsg/basic-materialized-views.md) for information about dimension tables

- [Oracle Database Data Warehousing Guide](../dwhsg/using-zone-maps.md) for information about attribute clustering with zone maps
