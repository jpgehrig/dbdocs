## 6.227 REDACTION_VALUES_FOR_TYPE_FULL

`REDACTION_VALUES_FOR_TYPE_FULL` shows all of the current values for full redaction.

For example, if a redaction policy is applied to a column of type `BINARY_DOUBLE` and the redaction type is full redaction, that column will be redacted with the value shown in the `BINARY_DOUBLE_VALUE` column of this view.

| Column                           | Datatype                      | NULL       | Description                                                             |
|:---------------------------------|:------------------------------|:-----------|:------------------------------------------------------------------------|
| `NUMBER_VALUE`                   | `NUMBER`                      | `NOT NULL` | Redaction result for full redaction on NUMBER columns                   |
| `BINARY_FLOAT_VALUE`             | `BINARY_FLOAT`                | `NOT NULL` | Redaction result for full redaction on BINARY_FLOAT columns             |
| `BINARY_DOUBLE_VALUE`            | `BINARY_DOUBLE`               | `NOT NULL` | Redaction result for full redaction on BINARY_DOUBLE columns            |
| `CHAR_VALUE`                     | `VARCHAR2(1)`                 |            | Redaction result for full redaction on CHAR columns                     |
| `VARCHAR_VALUE`                  | `VARCHAR2(1)`                 |            | Redaction result for full redaction on VARCHAR2 columns                 |
| `NCHAR_VALUE`                    | `NCHAR(1)`                    |            | Redaction result for full redaction on NCHAR columns                    |
| `NVARCHAR_VALUE`                 | `NVARCHAR2(1)`                |            | Redaction result for full redaction on NVARCHAR2 columns                |
| `DATE_VALUE`                     | `DATE`                        | `NOT NULL` | Redaction result for full redaction on DATE columns                     |
| `TIMESTAMP_VALUE`                | `TIMESTAMP(6)`                | `NOT NULL` | Redaction result for full redaction on TIMESTAMP columns                |
| `TIMESTAMP_WITH_TIME_ZONE_VALUE` | `TIMESTAMP(6) WITH TIME ZONE` | `NOT NULL` | Redaction result for full redaction on TIMESTAMP WITH TIME ZONE columns |
| `BLOB_VALUE`                     | `BLOB`                        |            | Redaction result for full redaction on BLOB columns                     |
| `CLOB_VALUE`                     | `CLOB`                        |            | Redaction result for full redaction on CLOB columns                     |
| `NCLOB_VALUE`                    | `NCLOB`                       |            | Redaction result for full redaction on NCLOB columns                    |

**See Also:**

[Oracle Database Advanced Security Guide](../asoag/asopart2.md) for more information about Oracle Data Redaction
