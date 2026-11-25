## 5.101 DBA_ILMPARAMETERS

`DBA_ILMPARAMETERS` can be queried to provide information on the Automatic Data Optimization parameters in the database and their values.

**Note:**

Automatic Data Optimization is supported in Oracle Database 12c Release 2 multitenant environments.

| Column  | Datatype        | NULL | Description                                                                                                                               |
|:--------|:----------------|:-----|:------------------------------------------------------------------------------------------------------------------------------------------|
| `NAME`  | `VARCHAR2(128)` |      | Name of the Automatic Data Optimization environment parameter. The value is one of the constants defined in the `DBMS_ILM_ADMIN` package. |
| `VALUE` | `NUMBER`        |      | Value of the parameter                                                                                                                    |

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_ILM.md) for more information about the API interface for implementing Automatic Data Optimization strategies

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_ILM_ADMIN.md) for more information about the `DBMS_ILM_ADMIN` package
