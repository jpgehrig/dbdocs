## 6.193 HS_BASE_DD

`HS_BASE_DD` displays information from the base data dictionary translation table.

| Column          | Datatype         | NULL       | Description                                                                      |
|:----------------|:-----------------|:-----------|:---------------------------------------------------------------------------------|
| `DD_TABLE_NAME` | `VARCHAR2(128) ` | `NOT NULL` | Name of the Oracle data dictionary table                                         |
| `DD_TABLE_DESC` | `VARCHAR2(255)`  |            | Description of the Oracle data dictionary table                                  |
| `DD_TABLE_ID`   | `NUMBER `        | `NOT NULL` | Sequence: a counter that is incremented for every row inserted (used internally) |
