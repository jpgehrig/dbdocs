## 2.248 ALL_JSON_COLUMNS

`ALL_JSON_COLUMNS` provides information on the JavaScript Object Notation (JSON) columns accessible to the current user. Each column that has an IS JSON check constraint in an AND condition and is accessible to the user appears in this view. This view enables a user to find all the JSON columns that are accessible to him or her.

For example, if a check constraint combines the IS JSON condition with another condition using logical condition OR, then the column is not listed in this view. In this case, it is not certain that the data in the column is JSON data. For example, the following constraint does not ensure that the data in column jcol is JSON data:

    jcol is json OR length(jcol) < 1000

### Related Views

- `DBA_JSON_COLUMNS` provides information on all JSON columns.

- `USER_JSON_COLUMNS` provides information on the JSON columns for which the user is the owner. This view does not display the `OWNER` column.

| Column        | Datatype        | NULL | Description                             |
|:--------------|:----------------|:-----|:----------------------------------------|
| `OWNER`       | `VARCHAR2(128)` |      | Owner of the table with the JSON column |
| `TABLE_NAME`  | `VARCHAR2(128)` |      | Name of the table with the JSON column  |
| `OBJECT_TYPE` | `VARCHAR2(5)`   |      | Object type:<br>• `TABLE`<br>• `VIEW`   |
| `COLUMN_NAME` | `VARCHAR2(128)` |      | Name of the JSON column                 |
| `FORMAT`      | `VARCHAR2(9)`   |      | Format of the JSON data                 |
| `DATA_TYPE`   | `VARCHAR2(13)`  |      | Data type of the JSON column            |

**See Also:**

- "[DBA_JSON_COLUMNS](DBA_JSON_COLUMNS.md)"

- "[USER_JSON_COLUMNS](USER_JSON_COLUMNS.md)"

- [Oracle Database JSON Developer’s Guide](../adjsn/json-in-oracle-database.md) for more information about using JSON with Oracle Database
