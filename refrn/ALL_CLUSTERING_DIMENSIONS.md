## 2.118 ALL_CLUSTERING_DIMENSIONS

`ALL_CLUSTERING_DIMENSIONS` describes dimension tables associated with tables with an attribute clustering clause that the user owns or has system privileges for.

### Related Views

- `DBA_CLUSTERING_DIMENSIONS` describes dimension tables associated with all tables with an attribute clustering clause in the database.

- `USER_CLUSTERING_DIMENSIONS` describes dimension tables associated with tables with an attribute clustering clause owned by the user. This view does not display the `OWNER` column.

| Column            | Datatype        | NULL       | Description                             |
|:------------------|:----------------|:-----------|:----------------------------------------|
| `OWNER`           | `VARCHAR2(128)` | `NOT NULL` | Owner of the attribute clustering table |
| `TABLE_NAME`      | `VARCHAR2(128)` | `NOT NULL` | Name of the attribute clustering table  |
| `DIMENSION_OWNER` | `VARCHAR2(128)` | `NOT NULL` | Owner of the dimension table            |
| `DIMENSION_NAME`  | `VARCHAR2(128)` | `NOT NULL` | Name of the dimension table             |

**See Also:**

- "[DBA_CLUSTERING_DIMENSIONS](DBA_CLUSTERING_DIMENSIONS.md)"

- "[USER_CLUSTERING_DIMENSIONS](USER_CLUSTERING_DIMENSIONS.md)"

- The `ALTER TABLE` section in [Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md) for information about using the `CLUSTERING` clause to create an attribute clustering table

- The `CREATE TABLE` section in [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for information about using the `CLUSTERING` clause to create an attribute clustering table

- [Oracle Database Data Warehousing Guide](../dwhsg/basic-materialized-views.md) for information about dimension tables

- [Oracle Database Data Warehousing Guide](../dwhsg/using-zone-maps.md) for information about attribute clustering with zone maps
