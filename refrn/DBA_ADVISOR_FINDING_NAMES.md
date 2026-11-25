## 4.25 DBA_ADVISOR_FINDING_NAMES

`DBA_ADVISOR_FINDING_NAMES` provides a list of all finding names registered with the Advisor Framework.

| Column         | Datatype         | NULL       | Description            |
|:---------------|:-----------------|:-----------|:-----------------------|
| `ID`           | `NUMBER`         |            | ID of the finding name |
| `ADVISOR_NAME` | `VARCHAR2(128)`  | `NOT NULL` | Advisor name           |
| `FINDING_NAME` | `VARCHAR2(4000)` |            | Finding name           |
