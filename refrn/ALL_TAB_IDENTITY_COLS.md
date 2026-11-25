## 3.109 ALL_TAB_IDENTITY_COLS

`ALL_TAB_IDENTITY_COLS` describes all table identity columns.

### Related Views

- `DBA_TAB_IDENTITY_COLS` describes all table identity columns.

- `USER_TAB_IDENTITY_COLS` describes all table identity columns. This view does not display the `OWNER` column.

| Column             | Datatype        | NULL       | Description                                                                           |
|:-------------------|:----------------|:-----------|:--------------------------------------------------------------------------------------|
| `OWNER`            | `VARCHAR2(128)` | `NOT NULL` | Owner of the table                                                                    |
| `TABLE_NAME`       | `VARCHAR2(128)` | `NOT NULL` | Name of the table                                                                     |
| `COLUMN_NAME`      | `VARCHAR2(128)` | `NOT NULL` | Name of the identity column                                                           |
| `GENERATION_TYPE`  | `VARCHAR2(10)`  |            | Generation type of the identity column. Possible values are `ALWAYS` or `BY DEFAULT`. |
| `SEQUENCE_NAME`    | `VARCHAR2(128)` | `NOT NULL` | Name of the sequence associated with the identity column                              |
| `IDENTITY_OPTIONS` | `VARCHAR2(298)` |            | Options for the identity column sequence generator                                    |

**See Also:**

- "[DBA_TAB_IDENTITY_COLS](DBA_TAB_IDENTITY_COLS.md)"

- "[USER_TAB_IDENTITY_COLS](USER_TAB_IDENTITY_COLS.md)"

**See Also:**

- The ALTER TABLE statement in [Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md) for more information about creating an identity column

- The CREATE TABLE statements in [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for more information about creating an identity column
