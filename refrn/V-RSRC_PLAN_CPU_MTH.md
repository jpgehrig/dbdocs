## 8.192 V\$RSRC_PLAN_CPU_MTH

`V$RSRC_PLAN_CPU_MTH` displays all available CPU resource allocation methods defined for resource plans.

| Column   | Datatype       | Description                                                                                                                                                                                                                                                                                                                                                                      |
|:---------|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NAME`   | `VARCHAR2(40)` | Name of the resource allocation method                                                                                                                                                                                                                                                                                                                                           |
| `CON_ID` | `NUMBER`       | The ID of the container to which the data pertains. Possible values include:<br>• `0`: This value is used for rows containing data that pertain to the entire CDB. This value is also used for rows in non-CDBs.<br>• `1`: This value is used for rows containing data that pertain to only the root<br>• n: Where n is the applicable container ID for the rows containing data |

**See Also:**

- "[V\$RSRC_CONSUMER_GROUP_CPU_MTH](V-RSRC_CONSUMER_GROUP_CPU_MTH.md)" for a listing of resource allocation methods defined for consumer groups

- [Oracle Database Administrator’s Guide](../admin/managing-resources-with-oracle-database-resource-manager.md) for information on resource plans

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_RESOURCE_MANAGER.md) for information on defining resource allocation methods for consumer plans with the `DBMS_RESOURCE_MANAGER` package
