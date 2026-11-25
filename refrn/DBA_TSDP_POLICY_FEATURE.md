## 6.61 DBA_TSDP_POLICY_FEATURE

`DBA_TSDP_POLICY_FEATURE` shows the Transparent Sensitive Data Protection policy security feature mapping for all the TSDP policies in the database.

At this time, only Oracle Data Redaction is supported.

| Column             | Datatype        | NULL | Description                                                                                           |
|:-------------------|:----------------|:-----|:------------------------------------------------------------------------------------------------------|
| `POLICY_NAME`      | `VARCHAR2(128)` |      | The name of the Transparent Sensitive Data Protection policy                                          |
| `SECURITY_FEATURE` | `VARCHAR2(12)`  |      | The Oracle security feature with which the Transparent Sensitive Data Protection policy is associated |

**See Also:**

[Oracle Database Security Guide](../dbseg/using-transparent-sensitive-data-protection.md) for more information about using Transparent Sensitive Data Protection
