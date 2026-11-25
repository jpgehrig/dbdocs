## 6.62 DBA_TSDP_POLICY_PARAMETER

`DBA_TSDP_POLICY_PARAMETER` shows the parameter-value pairs for the condition of the Transparent Sensitive Data Protection policy.

| Column           | Datatype         | NULL       | Description                                                                                                                                                                     |
|:-----------------|:-----------------|:-----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `POLICY_NAME`    | `VARCHAR2(128)`  |            | The name of the Transparent Sensitive Data Protection policy                                                                                                                    |
| `SUB_POLICY`     | `NUMBER`         | `NOT NULL` | The sub policy of the Transparent Sensitive Data Protection policy                                                                                                              |
| `PARAMETER`      | `VARCHAR2(128)`  |            | The parameter for the Transparent Sensitive Data Protection sub policy                                                                                                          |
| `VALUE`          | `VARCHAR2(4000)` |            | The value of the parameter                                                                                                                                                      |
| `DEFAULT_OPTION` | `VARCHAR2(5)`    |            | Indicates whether this is the default option for the policy:<br>• `TRUE`: This is the default option for the policy<br>• `FALSE`: This is not the default option for the policy |

**See Also:**

[Oracle Database Security Guide](../dbseg/using-transparent-sensitive-data-protection.md) for more information about using Transparent Sensitive Data Protection
