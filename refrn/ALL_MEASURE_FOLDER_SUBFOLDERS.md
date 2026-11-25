## 2.259 ALL_MEASURE_FOLDER_SUBFOLDERS

`ALL_MEASURE_FOLDER_SUBFOLDERS` describes the OLAP measure folders contained within the OLAP measure folders accessible to the user.

### Related Views

- `DBA_MEASURE_FOLDER_SUBFOLDERS` describes the OLAP measure folders contained within the database OLAP measure folders.

- `USER_MEASURE_FOLDER_SUBFOLDERS` describes the OLAP measure folders contained within the OLAP measure folders owned by the current user. This view does not display the `OWNER` column.

| Column                    | Datatype        | NULL       | Description                                                |
|:--------------------------|:----------------|:-----------|:-----------------------------------------------------------|
| `OWNER`                   | `VARCHAR2(128)` | `NOT NULL` | Owner of the OLAP measure folder that contains a subfolder |
| `MEASURE_FOLDER_NAME`     | `VARCHAR2(128)` | `NOT NULL` | Name of the OLAP measure folder that contains a subfolder  |
| `MEASURE_SUBFOLDER_OWNER` | `VARCHAR2(128)` | `NOT NULL` | Owner of the OLAP measure folder subfolder                 |
| `MEASURE_SUBFOLDER_NAME`  | `VARCHAR2(128)` | `NOT NULL` | Name of the owning OLAP measure folder subfolder           |

**See Also:**

- "[DBA_MEASURE_FOLDER_SUBFOLDERS](DBA_MEASURE_FOLDER_SUBFOLDERS.md)"

- "[USER_MEASURE_FOLDER_SUBFOLDERS](USER_MEASURE_FOLDER_SUBFOLDERS.md)"
