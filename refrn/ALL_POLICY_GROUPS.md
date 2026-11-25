## 3.16 ALL_POLICY_GROUPS

`ALL_POLICY_GROUPS` describes the policy groups defined for the synonyms, tables, and views accessible to the current user.

### Related Views

- `DBA_POLICY_GROUPS` describes all policy groups in the database.

- `USER_POLICY_GROUPS` describes the policy groups defined for the synonyms, tables, and views owned by the current user. This view does not display the `OBJECT_OWNER` column.

| Column         | Datatype        | NULL | Description                                                                                                                |
|:---------------|:----------------|:-----|:---------------------------------------------------------------------------------------------------------------------------|
| `OBJECT_OWNER` | `VARCHAR2(128)` |      | Owner of the synonym, table, or view                                                                                       |
| `OBJECT_NAME`  | `VARCHAR2(128)` |      | Name of the synonym, table, or view                                                                                        |
| `POLICY_GROUP` | `VARCHAR2(128)` |      | Name of the policy group                                                                                                   |
| `COMMON`       | `VARCHAR2(3)`   |      | Indicates whether the policy group is applied and enforced in all application PDBs (`YES`) or only in the local PDB (`NO`) |
| `INHERITED`    | `VARCHAR2(3)`   |      | Indicates whether the policy group is inherited from the root (`YES`) or not (`NO`)                                        |

**See Also:**

- "[DBA_POLICY_GROUPS](DBA_POLICY_GROUPS.md)"

- "[USER_POLICY_GROUPS](USER_POLICY_GROUPS.md)"
