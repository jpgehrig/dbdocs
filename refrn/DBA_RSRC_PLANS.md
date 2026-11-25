## 5.309 DBA_RSRC_PLANS

`DBA_RSRC_PLANS` displays information about all resource plans in the database.

For a list of currently active plans, see "[V\$RSRC_PLAN](V-RSRC_PLAN.md)".

| Column                      | Datatype         | NULL       | Description                                                                                       |
|:----------------------------|:-----------------|:-----------|:--------------------------------------------------------------------------------------------------|
| `PLAN_ID`                   | `NUMBER`         | `NOT NULL` | ID number of the resource plan                                                                    |
| `PLAN`                      | `VARCHAR2(128)`  |            | Name of the resource plan                                                                         |
| `NUM_PLAN_DIRECTIVES`       | `NUMBER`         |            | Number of plan directives for the plan                                                            |
| `CPU_METHOD`                | `VARCHAR2(128)`  |            | CPU resource allocation method for the plan                                                       |
| `MGMT_METHOD`               | `VARCHAR2(128)`  |            | Resource allocation method for the plan                                                           |
| `ACTIVE_SESS_POOL_MTH`      | `VARCHAR2(128)`  |            | Active session pool resource allocation method for the plan                                       |
| `PARALLEL_DEGREE_LIMIT_MTH` | `VARCHAR2(128)`  |            | Parallel degree limit resource allocation method for the plan                                     |
| `QUEUING_MTH`               | `VARCHAR2(128)`  |            | Queuing resource allocation method for the plan                                                   |
| `SUB_PLAN`                  | `VARCHAR2(3)`    |            | Indicates whether the plan is a subplan (`YES`) or not (`NO`)                                     |
| `COMMENTS`                  | `VARCHAR2(2000)` |            | Text comment on the plan                                                                          |
| `STATUS`                    | `VARCHAR2(128)`  |            | Indicates whether the plan is part of the pending area (`PENDING`) or not (NULL)                  |
| `MANDATORY`                 | `VARCHAR2(3)`    |            | Indicates whether the plan is mandatory (`YES`) or not (`NO`). Mandatory plans cannot be deleted. |

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/managing-resources-with-oracle-database-resource-manager.md) for information on resource plans in general

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_RESOURCE_MANAGER.md) for more information on creating resource plans with the `DBMS_RESOURCE_MANAGER` package
