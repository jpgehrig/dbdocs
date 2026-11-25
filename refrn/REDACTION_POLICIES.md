## 6.226 REDACTION_POLICIES

`REDACTION_POLICIES` displays all redaction policies in the database.

| Column               | Datatype         | NULL       | Description                                                   |
|:---------------------|:-----------------|:-----------|:--------------------------------------------------------------|
| `OBJECT_OWNER`       | `VARCHAR2(128)`  | `NOT NULL` | Owner of the object with the policy                           |
| `OBJECT_NAME`        | `VARCHAR2(128)`  | `NOT NULL` | Name of the object with the policy                            |
| `POLICY_NAME`        | `VARCHAR2(128)`  | `NOT NULL` | Name of the policy                                            |
| `EXPRESSION`         | `VARCHAR2(4000)` | `NOT NULL` | Expression for this policy                                    |
| `ENABLE`             | `VARCHAR2(7)`    |            | Indicates whether the policy is enabled (`YES`) or not (`NO`) |
| `POLICY_DESCRIPTION` | `VARCHAR2(4000)` |            | Description of the policy                                     |

**See Also:**

[Oracle Database Advanced Security Guide](../asoag/asopart2.md) for more information about Oracle Data Redaction
