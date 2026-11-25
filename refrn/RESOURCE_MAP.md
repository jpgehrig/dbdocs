## 6.232 RESOURCE_MAP

`RESOURCE_MAP` describes resources. This table can be used to map resource names to resource numbers.

| Column      | Datatype       | NULL       | Description           |
|:------------|:---------------|:-----------|:----------------------|
| `RESOURCE#` | `NUMBER`       | `NOT NULL` | Numeric resource code |
| `TYPE#`     | `NUMBER`       | `NOT NULL` | Numeric type code     |
| `NAME `     | `VARCHAR2(32)` | `NOT NULL` | Name of the resource  |
