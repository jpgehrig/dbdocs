## 6.229 REPORT_FILES

`REPORT_FILES` displays data for all of the XML schema and XSLT files associated with reports for a given component.

| Column     | Datatype        | NULL       | Description                      |
|:-----------|:----------------|:-----------|:---------------------------------|
| `FILENAME` | `VARCHAR2(500)` | `NOT NULL` | Name of the XSLT/XML schema file |
| `DATA`     | `XMLTYPE`       |            | XSLT/XML schema data             |
