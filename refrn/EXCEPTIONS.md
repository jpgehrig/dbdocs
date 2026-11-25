## 6.185 EXCEPTIONS

`EXCEPTIONS` contains information on violations of integrity constraints. This table is created by the `utlexcpt.sql` script.

| Column       | Datatype        | NULL | Description                            |
|:-------------|:----------------|:-----|:---------------------------------------|
| `ROW_ID`     | `ROWID`         |      | Row that caused the violation          |
| `OWNER`      | `VARCHAR2(128)` |      | Owner of the table                     |
| `TABLE_NAME` | `VARCHAR2(128)` |      | Name of the table                      |
| `CONSTRAINT` | `VARCHAR2(128)` |      | Integrity constraint that was violated |
