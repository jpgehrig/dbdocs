This section lists the names of the scripts that create the Information Exchange (`IX`) schema group and describes the objects in the schemas. Table 4-22 lists the `IX` scripts in alphabetical order, while Table 4-23 lists its objects.

Table 4-22 IX Sample Schema Scripts

| Script Name   | Description                                      |
|:--------------|:-------------------------------------------------|
| `cix_v3.sql`  | Creates the `IX` schema objects                  |
| `dix_v3.sql`  | Drops schema `IX` objects                        |
| `ix_main.sql` | Main script for schema `IX`; calls other scripts |
| `vix_v3.sql`  | Enables, disables, and verifies `IX` objects     |

Table 4-23 IX Sample Schema Objects

| Object Type        | Objects                                                                                                                                                                                                                            |
|:-------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Evaluation Context | `AQ$_ORDERS_QUEUETABLE_V`, `AQ$_STREAMS_QUEUE_TABLE_V`                                                                                                                                                                             |
| Index              | `SYS_C003540`, `SYS_C003543`, `SYS_C003548`, `SYS_C003551`, `SYS_IOT_TOP_45932`, `SYS_IOT_TOP_45934`, `SYS_IOT_TOP_45936`, `SYS_IOT_TOP_45939`, `SYS_IOT_TOP_45949`, `SYS_IOT_TOP_45951`, `SYS_IOT_TOP_45953`, `SYS_IOT_TOP_45956` |
| Lob                | `SYS_LOB0000045926C00036$$`, `SYS_LOB0000045941C00028$$`, `SYS_LOB0000045941C00029$$`                                                                                                                                              |
| Queue              | `AQ$_ORDERS_QUEUETABLE_E`, `AQ$_STREAMS_QUEUE_TABLE_E`, `ORDERS_QUEUE`, `STREAMS_QUEUE`                                                                                                                                            |
| Rule Set           | `ORDERS_QUEUE_N`, `ORDERS_QUEUE_R`, `STREAMS_QUEUE_N`, `STREAMS_QUEUE_R`                                                                                                                                                           |
| Sequence           | `AQ$_ORDERS_QUEUETABLE_N`, `AQ$_STREAMS_QUEUE_TABLE_N`                                                                                                                                                                             |
| Table              | `ORDERS_QUEUETABLE`, `STREAMS_QUEUE_TABLE`                                                                                                                                                                                         |
| Type               | `ORDER_EVENT_TYP`                                                                                                                                                                                                                  |
| View               | `AQ$ORDERS_QUEUETABLE`, `AQ$ORDERS_QUEUETABLE_R`, `AQ$ORDERS_QUEUETABLE_S`, `AQ$STREAMS_QUEUE_TABLE`, `AQ$STREAMS_QUEUE_TABLE_R`, `AQ$STREAMS_QUEUE_TABLE_S`                                                                       |
