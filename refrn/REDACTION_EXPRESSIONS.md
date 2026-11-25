## 6.225 REDACTION_EXPRESSIONS

`REDACTION_EXPRESSIONS` shows all the Data Redaction named Policy Expressions in the database.

| Column                          | Datatype         | NULL | Description                                                                      |
|:--------------------------------|:-----------------|:-----|:---------------------------------------------------------------------------------|
| `POLICY_EXPRESSION_NAME`        | `VARCHAR2(256)`  |      | Customer-specified name of the named Policy Expression                           |
| `EXPRESSION`                    | `VARCHAR2(4000)` |      | The SQL expression defined for this Data Redaction named Policy Expression       |
| `OBJECT_OWNER`                  | `VARCHAR2(128)`  |      | Owner of the table or view which this named Policy Expression is associated with |
| `OBJECT_NAME`                   | `VARCHAR2(128)`  |      | Name of the table or view which this named Policy Expression is associated with  |
| `COLUMN_NAME`                   | `VARCHAR2(128)`  |      | Name of the column which this named Policy Expression is associated with         |
| `POLICY_EXPRESSION_DESCRIPTION` | `VARCHAR2(4000)` |      | Description of this named Policy Expression                                      |

**See Also:**

[Oracle Database Advanced Security Guide](../asoag/asopart2.md) for more information about Oracle Data Redaction
