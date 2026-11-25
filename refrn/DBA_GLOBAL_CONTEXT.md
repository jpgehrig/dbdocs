## 4.318 DBA_GLOBAL_CONTEXT

`DBA_GLOBAL_CONTEXT` displays the definition (name, schema, and package) of all global contexts created in the database.

This view is a subset of `DBA_CONTEXT`, which describes all contexts, including global contexts.

| Column      | Datatype        | NULL       | Description                                                            |
|:------------|:----------------|:-----------|:-----------------------------------------------------------------------|
| `NAMESPACE` | `VARCHAR2(128)` | `NOT NULL` | Name of the context namespace                                          |
| `SCHEMA`    | `VARCHAR2(128)` | `NOT NULL` | Schema of the package that administers the globally accessible context |
| `PACKAGE`   | `VARCHAR2(128)` | `NOT NULL` | Package that administers the globally accessible context               |

**See Also:**

- "[DBA_CONTEXT](DBA_CONTEXT.md)"

- [Oracle Database Security Guide](../dbseg/using-application-contexts-to-retrieve-user-information.md) for more information about using global application contexts

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_SESSION.md) for more information about the `DBMS_SESSION.SET_CONTEXT` procedure
