## 6.197 HS_FDS_CLASS

`HS_FDS_CLASS` contains information about legal non-Oracle (FDS) classes.

| Column                 | Datatype        | NULL        | Description                                                                      |
|:-----------------------|:----------------|:------------|:---------------------------------------------------------------------------------|
| `FDS_CLASS_NAME `      | `VARCHAR2(30) ` | `NOT NULL`  | Name of the FDS class (for example, ODBC, DB2)                                   |
| `FDS_CLASS _COMMENTS ` | `VARCHAR2(255)` |             | Text description of the non-Oracle class                                         |
| `FDS_CLASS_ID `        | `NUMBER`        | ` NOT NULL` | Sequence: a counter that is incremented for every row inserted (used internally) |
