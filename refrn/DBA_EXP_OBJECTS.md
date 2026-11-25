## 4.288 DBA_EXP_OBJECTS

`DBA_EXP_OBJECTS` describes objects that have been incrementally exported.

| Column           | Datatype        | NULL       | Description                          |
|:-----------------|:----------------|:-----------|:-------------------------------------|
| `OWNER`          | `VARCHAR2(128)` | `NOT NULL` | Owner of exported object             |
| `OBJECT_NAME`    | `VARCHAR2(128)` | `NOT NULL` | Name of exported object              |
| `OBJECT_TYPE`    | `VARCHAR2(13)`  |            | Type of exported object              |
| `CUMULATIVE`     | `DATE`          |            | Timestamp of last cumulative export  |
| `INCREMENTAL`    | `DATE`          | `NOT NULL` | Timestamp of last incremental export |
| `EXPORT_VERSION` | `NUMBER(3)`     | `NOT NULL` | The ID of the export session         |
