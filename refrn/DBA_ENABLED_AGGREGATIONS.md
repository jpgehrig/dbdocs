## 4.277 DBA_ENABLED_AGGREGATIONS

`DBA_ENABLED_AGGREGATIONS` displays information about enabled on-demand statistic aggregation.

| Column             | Datatype       | NULL | Description                                                                                                 |
|:-------------------|:---------------|:-----|:------------------------------------------------------------------------------------------------------------|
| `AGGREGATION_TYPE` | `VARCHAR2(21)` |      | Type of the aggregation:<br>• `CLIENT_ID`<br>• `SERVICE`<br>• `SERVICE_MODULE`<br>• `SERVICE_MODULE_ACTION` |
| `PRIMARY_ID`       | `VARCHAR2(64)` |      | Primary qualifier (specific client identifier or service name)                                              |
| `QUALIFIER_ID1`    | `VARCHAR2(48)` |      | Secondary qualifier (specific module name)                                                                  |
| `QUALIFIER_ID2`    | `VARCHAR2(32)` |      | Additional qualifier (specific action name)                                                                 |
