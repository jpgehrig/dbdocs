## 5.307 DBA_RSRC_MAPPING_PRIORITY

`DBA_RSRC_MAPPING_PRIORITY` displays information about all consumer group mapping attribute priorities.

| Column      | Datatype        | NULL | Description                                                                                |
|:------------|:----------------|:-----|:-------------------------------------------------------------------------------------------|
| `ATTRIBUTE` | `VARCHAR2(128)` |      | Session attribute                                                                          |
| `PRIORITY`  | `NUMBER`        |      | Priority (`1` is the highest)                                                              |
| `STATUS`    | `VARCHAR2(128)` |      | Indicates whether the consumer group is part of the pending area (`PENDING`) or not (NULL) |
