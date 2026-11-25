## 4.253 DBA_DBFS_HS_FIXED_PROPERTIES

`DBA_DBFS_HS_FIXED_PROPERTIES` shows non-modifiable properties of all Database File System (DBFS) hierarchical stores.

### Related View

`USER_DBFS_HS_FIXED_PROPERTIES` shows non-modifiable properties of all DBFS hierarchical stores owned by current user. This view does not display the `STORE_OWNER` column.

| Column        | Datatype        | NULL       | Description    |
|:--------------|:----------------|:-----------|:---------------|
| `STORE_NAME`  | `VARCHAR2(128)` | `NOT NULL` | Name of store  |
| `STORE_OWNER` | `VARCHAR2(128)` | `NOT NULL` | Owner of store |
| `PROP_NAME`   | `VARCHAR2(256)` | `NOT NULL` | Property name  |
| `PROP_VALUE`  | `VARCHAR2(256)` | `NOT NULL` | Property value |

**See Also:**

"[USER_DBFS_HS_FIXED_PROPERTIES](USER_DBFS_HS_FIXED_PROPERTIES.md)"
