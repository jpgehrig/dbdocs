## 2.194 ALL_GOLDENGATE_PRIVILEGES

`ALL_GOLDENGATE_PRIVILEGES` displays details about Oracle GoldenGate privileges for the user. Oracle GoldenGate privileges are granted using the `DBMS_GOLDENGATE_AUTH` package.

### Related Views

- `DBA_GOLDENGATE_PRIVILEGES` displays details about Oracle GoldenGate privileges for all users who have been granted Oracle GoldenGate privileges.

- `USER_GOLDENGATE_PRIVILEGES` displays details about Oracle GoldenGate privileges. This view does not display the `USERNAME` column.

| Column                    | Datatype        | NULL       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:--------------------------|:----------------|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `USERNAME`                | `VARCHAR2(128)` | `NOT NULL` | Name of the user that is granted the privilege                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `PRIVILEGE_TYPE`          | `VARCHAR2(7)`   |            | Type of privilege granted:<br>• `APPLY`<br>• `CAPTURE`<br>• \*: Both `APPLY` and `CAPTURE`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `GRANT_SELECT_PRIVILEGES` | `VARCHAR2(3)`   |            | Shows whether the set of privileges granted to the administrator make the administrator a full privilege administrator or a minimum privilege administrator:<br>• `YES`: The administrator has the `SELECT_CATALOG_ROLE` role and other privileges, is considered a full privilege administrator, and can manage any Oracle GoldenGate configuration.<br>• `NO`: The administrator is considered a minimum privilege administrator, and can only manage Oracle GoldenGate configurations where the apply_user or capture_user (based on the `PRIVILEGE_TYPE` column) matches the username. |
| `CREATE_TIME`             | `TIMESTAMP(6)`  |            | Time at which the privilege was granted                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |

**See Also:**

- "[DBA_GOLDENGATE_PRIVILEGES](DBA_GOLDENGATE_PRIVILEGES.md)"

- "[USER_GOLDENGATE_PRIVILEGES](USER_GOLDENGATE_PRIVILEGES.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_GOLDENGATE_AUTH.md) for more information about the DBMS_GOLDENGATE_AUTH package
