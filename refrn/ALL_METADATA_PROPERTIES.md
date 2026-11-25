## 2.261 ALL_METADATA_PROPERTIES

`ALL_METADATA_PROPERTIES` describes OLAP metadata properties in the database that are accessible to the current user.

### Related Views

- `DBA_METADATA_PROPERTIES` describes OLAP metadata properties in the database.

- `USER_METADATA_PROPERTIES` describes OLAP metadata properties in the current user's schema. This view does not display the `OWNER` column.

| Column             | Datatype        | NULL | Description                                       |
|:-------------------|:----------------|:-----|:--------------------------------------------------|
| `OWNER`            | `VARCHAR2(128)` |      | Owner of the OLAP metadata property               |
| `OWNING_OBJECT_ID` | `NUMBER`        |      | Dictionary ID of the OLAP metadata property owner |
| `OWNING_TYPE`      | `VARCHAR2(23)`  |      | Owning type of the OLAP metadata property         |
| `PROPERTY_ID`      | `NUMBER`        |      | Dictionary Id of the OLAP metadata property       |
| `PROPERTY_KEY`     | `VARCHAR2(128)` |      | Key of the OLAP metadata property                 |
| `PROPERTY_VALUE`   | `CLOB`          |      | Value of the OLAP metadata property               |
| `PROPERTY_ORDER`   | `NUMBER`        |      | Order number of the OLAP metadata property        |

**See Also:**

- "[DBA_METADATA_PROPERTIES](DBA_METADATA_PROPERTIES.md)"

- "[USER_METADATA_PROPERTIES](USER_METADATA_PROPERTIES.md)"
