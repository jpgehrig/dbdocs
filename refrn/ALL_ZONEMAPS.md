## 3.170 ALL_ZONEMAPS

`ALL_ZONEMAPS` describes all the zone maps accessible to the user.

### Related Views

- `DBA_ZONEMAPS` describes all the zone maps in the database.

- `USER_ZONEMAPS` describes all the zone maps owned by the user.

| Column                | Datatype        | NULL | Description                                                                                                                                                                                   |
|:----------------------|:----------------|:-----|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OWNER`               | `VARCHAR2(128)` |      | Owner of the zone map                                                                                                                                                                         |
| `ZONEMAP_NAME`        | `VARCHAR2(128)` |      | Name of the zone map                                                                                                                                                                          |
| `FACT_OWNER`          | `VARCHAR2(128)` |      | Owner of the fact table of the zone map                                                                                                                                                       |
| `FACT_TABLE`          | `VARCHAR2(128)` |      | Name of the fact table on which the zone map is defined                                                                                                                                       |
| `SCALE`               | `NUMBER`        |      | Scale factor of the zone map                                                                                                                                                                  |
| `HIERARCHICAL`        | `VARCHAR2(12)`  |      | Indicates whether the zone map is hierarchical (`YES`) or not (`NO`)                                                                                                                          |
| `WITH_CLUSTERING`     | `VARCHAR2(15)`  |      | Indicates whether the zone map is created with the `CLUSTERING` clause (`YES`) or not (`NO`)                                                                                                  |
| `QUERY`               | `LONG`          |      | Zone map defining query                                                                                                                                                                       |
| `QUERY_LEN`           | `NUMBER(38)`    |      | Length of defining query in bytes                                                                                                                                                             |
| `PRUNING`             | `VARCHAR2(8)`   |      | Indicates whether the zone map is enabled for pruning (`ENABLED`) or not (`DISABLED`)                                                                                                         |
| `REFRESH_MODE`        | `VARCHAR2(17)`  |      | Refresh mode for the zone map:<br>• COMMIT<br>• DEMAND<br>• DATAMOVEMENT<br>• LOAD<br>• LOAD DATAMOVEMENT                                                                                     |
| `REFRESH_METHOD`      | `VARCHAR2(14)`  |      | Refresh method for the zone map<br>• `COMPLETE`<br>• `FORCE`<br>• `FAST`                                                                                                                      |
| `LAST_REFRESH_METHOD` | `VARCHAR2(19)`  |      | The last refresh method used for the zone map:<br>• `NA`<br>• `COMPLETE`<br>• `FAST`<br>• `ERROR-UNKNOWN`                                                                                     |
| `LAST_REFRESH_TIME`   | `TIMESTAMP(9)`  |      | Time of the last refresh                                                                                                                                                                      |
| `INVALID`             | `VARCHAR2(7)`   |      | Indicates whether the zone map is invalid due to some DDL (`YES`) or not (`NO`)                                                                                                               |
| `STALE`               | `VARCHAR2(7)`   |      | Indicates whether the zone map is stale because of DML operations and cannot be used for pruning (`YES`) or not (`NO`) or whether this cannot be determined (`UNKNOWN`)                       |
| `UNUSABLE`            | `VARCHAR2(8)`   |      | Indicates whether the zone map has been marked unusable by the owner (`YES`) or not (`NO`)                                                                                                    |
| `COMPILE_STATE`       | `VARCHAR2(19)`  |      | Current compile state of the zone map:<br>• `VALID`<br>• `AUTHORIZATION_ERROR`<br>• `COMPILATION_ERROR`<br>• `NEEDS_COMPILE`<br>• `ERROR_UNKNOWN`<br>Similar to `ALL_MVIEWS`.`COMPILE_STATE`. |

**Note:**

This view is intended for use with Oracle Exadata release 12.1.2.1.1 or later.

**See Also:**

- "[DBA_ZONEMAPS](DBA_ZONEMAPS.md)"

- "[USER_ZONEMAPS](USER_ZONEMAPS.md)"

- [Oracle Database Data Warehousing Guide](../dwhsg/using-zone-maps.md) for more information about zone maps
