## 7.173 V\$DB_TRANSPORTABLE_PLATFORM

`V$DB_TRANSPORTABLE_PLATFORM` displays all platforms to which the database can be transported using the RMAN `CONVERT DATABASE` command.

The transportable database feature only supports transports of the same endian platform. Therefore, `V$DB_TRANSPORTABLE_PLATFORM` displays fewer rows than `V$TRANSPORTABLE_PLATFORM`.

| Column          | Datatype        | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:----------------|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `PLATFORM_ID`   | `NUMBER`        | Platform identification number                                                                                                                                                                                                                                                                                                                                                   |
| `PLATFORM_NAME` | `VARCHAR2(101)` | Platform name                                                                                                                                                                                                                                                                                                                                                                    |
| `ENDIAN_FORMAT` | `VARCHAR2(14)`  | Platform endian format:<br>• `Big`<br>• `Little`<br>• `UNKNOWN FORMAT`                                                                                                                                                                                                                                                                                                           |
| `CON_ID`        | `NUMBER`        | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

"[V\$TRANSPORTABLE_PLATFORM](V-TRANSPORTABLE_PLATFORM.md)"
