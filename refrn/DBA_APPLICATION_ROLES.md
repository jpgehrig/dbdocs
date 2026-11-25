## 4.98 DBA_APPLICATION_ROLES

`DBA_APPLICATION_ROLES` describes all the roles that have authentication policy functions defined.

| Column    | Datatype        | NULL       | Description                      |
|:----------|:----------------|:-----------|:---------------------------------|
| `ROLE`    | `VARCHAR2(128)` | `NOT NULL` | Name of the application role     |
| `SCHEMA`  | `VARCHAR2(128)` | `NOT NULL` | Schema of the authorized package |
| `PACKAGE` | `VARCHAR2(128)` | `NOT NULL` | Name of the authorized package   |
