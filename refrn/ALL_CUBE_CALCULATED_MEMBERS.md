## 2.138 ALL_CUBE_CALCULATED_MEMBERS

`ALL_CUBE_CALCULATED_MEMBERS` describes the calculated members for the OLAP cube dimensions accessible to the current user.

### Related Views

- `DBA_CUBE_CALCULATED_MEMBERS` describes the calculated members for all OLAP cube dimensions in the database.

- `USER_CUBE_CALCULATED_MEMBERS` describes the calculated members for the OLAP cube dimensions owned by the current user. This view does not display the `OWNER` column.

| Column                | Datatype        | NULL       | Description                                                                                                                                                                                    |
|:----------------------|:----------------|:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`               | `VARCHAR2(128)` | `NOT NULL` | Owner of the cube dimension                                                                                                                                                                    |
| `DIMENSION_NAME`      | `VARCHAR2(128)` | `NOT NULL` | Name of a cube dimension                                                                                                                                                                       |
| `MEMBER_NAME`         | `VARCHAR2(128)` | `NOT NULL` | Name of a calculated member in the cube dimension                                                                                                                                              |
| `IS_CUSTOM_AGGREGATE` | `VARCHAR2(3)`   |            | Indicates whether the calculated member is a custom aggregate (`YES`) or not (`NO`)                                                                                                            |
| `STORAGE_TYPE`        | `VARCHAR2(10)`  |            | Storage type of the calculated member:<br>• `DYNAMIC` - Value of the member is calculated for a query<br>• `PRECOMPUTE` - Value of the member is calculated and stored during data maintenance |
| `EXPRESSION`          | `CLOB`          |            | Expression used to generate the value of the calculated member                                                                                                                                 |

**See Also:**

- "[DBA_CUBE_CALCULATED_MEMBERS](DBA_CUBE_CALCULATED_MEMBERS.md)"

- "[USER_CUBE_CALCULATED_MEMBERS](USER_CUBE_CALCULATED_MEMBERS.md)"
