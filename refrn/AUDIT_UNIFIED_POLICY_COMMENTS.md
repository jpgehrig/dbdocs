## 3.175 AUDIT_UNIFIED_POLICY_COMMENTS

`AUDIT_UNIFIED_POLICY_COMMENTS` shows the description of each unified audit policy, if a description was entered for the unified audit policy using the `COMMENT `SQL statement.

**Note:**

This view is populated only in an Oracle Database where unified auditing is enabled.

- See [Oracle Database Security Guide](../dbseg/part_6.md) for more information about unified auditing.

- See [Oracle Database Upgrade Guide](../spucs/recommended-and-best-practices-complete-upgrading-oracle-database.md) for more information about migrating to unified auditing.

| Column        | Datatype         | NULL       | Description                                                                                   |
|:--------------|:-----------------|:-----------|:----------------------------------------------------------------------------------------------|
| `POLICY_NAME` | `VARCHAR2(128)`  | `NOT NULL` | Name of the unified audit policy                                                              |
| `COMMENTS`    | `VARCHAR2(4000)` |            | Description of the unified audit policy, if one was entered using the `COMMENT` SQL statement |
