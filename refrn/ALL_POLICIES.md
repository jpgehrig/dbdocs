## 3.13 ALL_POLICIES

`ALL_POLICIES` describes all Oracle Virtual Private Database (VPD) security policies for objects accessible to the current user. A security policy is a list of security requirements and rules that regulate row level access to those database objects.

### Related Views

- `DBA_POLICIES` describes all Oracle Virtual Private Database (VPD) security policies in the database.

- `USER_POLICIES` describes all Oracle Virtual Private Database (VPD) security policies associated with objects owned by the current user. This view does not display the `OBJECT_OWNER` column.

| Column           | Datatype        | NULL | Description                                                                                                                                                           |
|:-----------------|:----------------|:-----|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OBJECT_OWNER`   | `VARCHAR2(128)` |      | Owner of the synonym, table, or view                                                                                                                                  |
| `OBJECT_NAME`    | `VARCHAR2(128)` |      | Name of the synonym, table, or view                                                                                                                                   |
| `POLICY_GROUP`   | `VARCHAR2(128)` |      | Name of the policy group                                                                                                                                              |
| `POLICY_NAME`    | `VARCHAR2(128)` |      | Name of the policy                                                                                                                                                    |
| `PF_OWNER`       | `VARCHAR2(128)` |      | Owner of the policy function                                                                                                                                          |
| `PACKAGE`        | `VARCHAR2(128)` |      | Name of the package containing the policy function                                                                                                                    |
| `FUNCTION`       | `VARCHAR2(128)` |      | Name of the policy function                                                                                                                                           |
| `SEL`            | `VARCHAR2(3)`   |      | Indicates whether the policy is applied to queries on the object (`YES`) or not (`NO`)                                                                                |
| `INS`            | `VARCHAR2(3)`   |      | Indicates whether the policy is applied to `INSERT` statements on the object (`YES`) or not (`NO`)                                                                    |
| `UPD`            | `VARCHAR2(3)`   |      | Indicates whether the policy is applied to `UPDATE` statements on the object (`YES`) or not (`NO`)                                                                    |
| `DEL`            | `VARCHAR2(3)`   |      | Indicates whether the policy is applied to `DELETE` statements on the object (`YES`) or not (`NO`)                                                                    |
| `IDX`            | `VARCHAR2(3)`   |      | Indicates whether the policy is enforced for index maintenance on the object (`YES`) or not (`NO`)                                                                    |
| `CHK_OPTION`     | `VARCHAR2(3)`   |      | Indicates whether the check option is enforced for the policy (`YES`) or not (`NO`)                                                                                   |
| `ENABLE`         | `VARCHAR2(3)`   |      | Indicates whether the policy is enabled (`YES`) or disabled (`NO`)                                                                                                    |
| `STATIC_POLICY`  | `VARCHAR2(3)`   |      | Indicates whether the policy is static (`YES`) or not (`NO`). This column is obsolete because information about static policies is shown in the `POLICY_TYPE` column. |
| `POLICY_TYPE`    | `VARCHAR2(24)`  |      | Policy type:<br>• `STATIC`<br>• `SHARED_STATIC`<br>• `CONTEXT_SENSITIVE`<br>• `SHARED_CONTEXT_SENSITIVE`<br>• `DYNAMIC`                                               |
| `LONG_PREDICATE` | `VARCHAR2(3)`   |      | Indicates whether the policy function can return a maximum of 32 KB of predicate (`YES`) or not (`NO`). If `NO`, the default maximum predicate size is `4000` bytes.  |
| `COMMON`         | `VARCHAR2(3)`   |      | Indicates whether the policy is applied and enforced in all application PDBs (`YES`) or only in the local PDB (`NO`)                                                  |
| `INHERITED`      | `VARCHAR2(3)`   |      | Indicates whether the policy is inherited from the root (`YES`) or not (`NO`)                                                                                         |

**See Also:**

- "[DBA_POLICIES](DBA_POLICIES.md)"

- "[USER_POLICIES](USER_POLICIES.md)"

- [Oracle Database Concepts](../cncpt/topics-for-database-administrators-and-developers.md) for an overview of security policies and fine-grained access control

- [Oracle Database Security Guide](../dbseg/introduction-to-oracle-database-security.md) for more information about security policies

- The `DBMS_RLS` package in [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_RLS.md) for information on administering security policies
