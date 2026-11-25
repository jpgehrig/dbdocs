## 6.60 DBA_TSDP_POLICY_CONDITION

`DBA_TSDP_POLICY_CONDITION` describes the Transparent Sensitive Data Protection policy and condition mapping. It also lists the property-value pairs for the condition.

| Column        | Datatype        | NULL       | Description                                                                                                 |
|:--------------|:----------------|:-----------|:------------------------------------------------------------------------------------------------------------|
| `POLICY_NAME` | `VARCHAR2(128)` |            | The name of the Transparent Sensitive Data Protection policy                                                |
| `SUB_POLICY`  | `NUMBER`        | `NOT NULL` | The sub policy of the Transparent Sensitive Data Protection policy                                          |
| `PROPERTY`    | `VARCHAR2(11)`  |            | The condition property. Possible values:<br>• `DATATYPE`<br>• `LENGTH`<br>• `SCHEMA_NAME`<br>• `TABLE_NAME` |
| `VALUE`       | `VARCHAR2(128)` |            | The value of the condition property                                                                         |

**See Also:**

[Oracle Database Security Guide](../dbseg/using-transparent-sensitive-data-protection.md) for more information about using Transparent Sensitive Data Protection
