## 4.251 DBA_DBFS_HS

`DBA_DBFS_HS` shows all Database File System (DBFS) hierarchical stores.

### Related View

`USER_DBFS_HS` shows all Database File System hierarchical stores owned by the current user. This view does not display the `STOREOWNER` column.

| Column       | Datatype        | NULL | Description    |
|:-------------|:----------------|:-----|:---------------|
| `STORENAME`  | `VARCHAR2(256)` |      | Name of store  |
| `STOREOWNER` | `VARCHAR2(64)`  |      | Owner of store |

**See Also:**

"[USER_DBFS_HS](USER_DBFS_HS.md)"
