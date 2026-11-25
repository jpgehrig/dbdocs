## 6.173 DBMS_LOCK_ALLOCATED

`DBMS_LOCK_ALLOCATED` describes user-allocated locks.

| Column       | Datatype        | NULL       | Description                                                                     |
|:-------------|:----------------|:-----------|:--------------------------------------------------------------------------------|
| `NAME`       | `VARCHAR2(128)` | `NOT NULL` | Name of the lock                                                                |
| `LOCKID`     | `NUMBER(38)`    |            | Lock identifier number                                                          |
| `EXPIRATION` | `DATE`          |            | Planned lock expiration date (updates whenever the allocation procedure is run) |
