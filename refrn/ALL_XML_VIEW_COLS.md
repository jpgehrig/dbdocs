## 3.154 ALL_XML_VIEW_COLS

`ALL_XML_VIEW_COLS` describes the columns of the XML views accessible to the current user.

### Related Views

- `DBA_XML_VIEW_COLS` describes the columns of all XML views in the database.

- `USER_XML_VIEW_COLS` describes the columns of the XML views owned by the current user. This view does not display the `OWNER` column.

| Column         | Datatype         | NULL | Description                                                  |
|:---------------|:-----------------|:-----|:-------------------------------------------------------------|
| `OWNER`        | `VARCHAR2(128)`  |      | Owner of the XML view                                        |
| `VIEW_NAME`    | `VARCHAR2(128)`  |      | Name of the XML view                                         |
| `COLUMN_NAME`  | `VARCHAR2(4000)` |      | Name of the XML view column                                  |
| `XMLSCHEMA`    | `VARCHAR2(700)`  |      | Name of the XML Schema that is used for the view definition  |
| `SCHEMA_OWNER` | `VARCHAR2(128)`  |      | Owner of the XML Schema that is used for the view definition |
| `ELEMENT_NAME` | `VARCHAR2(2000)` |      | Name of the XML SChema element that is used for the view     |

**See Also:**

- "[DBA_XML_VIEW_COLS](DBA_XML_VIEW_COLS.md)"

- "[USER_XML_VIEW_COLS](USER_XML_VIEW_COLS.md)"
