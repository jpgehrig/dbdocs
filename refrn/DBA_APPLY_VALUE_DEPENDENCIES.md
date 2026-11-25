## 4.120 DBA_APPLY_VALUE_DEPENDENCIES

`DBA_APPLY_VALUE_DEPENDENCIES` displays information about the value dependencies for all apply processes in the database.

| Column            | Datatype        | NULL       | Description            |
|:------------------|:----------------|:-----------|:-----------------------|
| `DEPENDENCY_NAME` | `VARCHAR2(128)` | `NOT NULL` | Name of the dependency |
| `OBJECT_OWNER`    | `VARCHAR2(128)` | `NOT NULL` | Owner of the object    |
| `OBJECT_NAME`     | `VARCHAR2(128)` | `NOT NULL` | Name of the object     |
| `COLUMN_NAME`     | `VARCHAR2(128)` | `NOT NULL` | Name of the column     |
| `COLUMN_POSITION` | `NUMBER`        |            | Position of the column |
