## 2.119 ALL_CLUSTERING_JOINS

`ALL_CLUSTERING_JOINS` describes joins to the dimension tables associated with tables with an attribute clustering clause the user owns or has system privileges for.

### Related Views

- `DBA_CLUSTERING_JOINS` describes joins to the dimension tables associated with all tables with an attribute clustering clause in the database.

- `USER_CLUSTERING_JOINS` describes joins to the dimension tables associated with tables with an attribute clustering clause owned by the user. This view does not display the `OWNER` column.

| Column        | Datatype        | NULL       | Description                             |
|:--------------|:----------------|:-----------|:----------------------------------------|
| `OWNER`       | `VARCHAR2(128)` | `NOT NULL` | Owner of the attribute clustering table |
| `TABLE_NAME`  | `VARCHAR2(128)` | `NOT NULL` | Name of the attribute clustering table  |
| `TAB1_OWNER`  | `VARCHAR2(128)` | `NOT NULL` | Table 1 owner of the join               |
| `TAB1_NAME`   | `VARCHAR2(128)` | `NOT NULL` | Table 1 name of the join                |
| `TAB1_COLUMN` | `VARCHAR2(128)` | `NOT NULL` | Table 1 column name of the join         |
| `TAB2_OWNER`  | `VARCHAR2(128)` | `NOT NULL` | Table 2 owner of the join               |
| `TAB2_NAME`   | `VARCHAR2(128)` | `NOT NULL` | Table 2 name of the join                |
| `TAB2_COLUMN` | `VARCHAR2(128)` | `NOT NULL` | Table 2 column name of the join         |

**See Also:**

- "[DBA_CLUSTERING_JOINS](DBA_CLUSTERING_JOINS.md)"

- "[USER_CLUSTERING_JOINS](USER_CLUSTERING_JOINS.md)"

- The `ALTER TABLE` section in [Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md) for information about using the `CLUSTERING` clause to create an attribute clustering table

- The `CREATE TABLE` section in [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for information about using the `CLUSTERING` clause to create an attribute clustering table

- [Oracle Database Data Warehousing Guide](../dwhsg/basic-materialized-views.md) for information about dimension tables

- [Oracle Database Data Warehousing Guide](../dwhsg/using-zone-maps.md) for information about attribute clustering with zone maps
