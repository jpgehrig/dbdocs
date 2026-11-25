## 6.187 GLOBAL_CONTEXT

`GLOBAL_CONTEXT` displays the values of global context attributes, which are accessible for the current session, based on the `CLIENT_IDENTIFIER` value.

`GLOBAL_CONTEXT` is similar to `SESSION_CONTEXT`, which lists the values of session (or local) context attributes set under the current session.

| Column              | Datatype         | NULL | Description                                                        |
|:--------------------|:-----------------|:-----|:-------------------------------------------------------------------|
| `NAMESPACE`         | `VARCHAR2(31)`   |      | Namespace of the globally accessible context                       |
| `ATTRIBUTE`         | `VARCHAR2(31)`   |      | Attribute of the globally accessible context                       |
| `VALUE`             | `VARCHAR2(4000)` |      | Value of the attribute of the globally accessible context          |
| `USERNAME`          | `VARCHAR2(31)`   |      | Username for which globally accessible context value is applicable |
| `CLIENT_IDENTIFIER` | `VARCHAR2(65)`   |      | Client identifier of the globally accessible context               |

**See Also:**

- "[SESSION_CONTEXT](SESSION_CONTEXT.md)"

- [Oracle Database Security Guide](../dbseg/using-application-contexts-to-retrieve-user-information.md) for more information about using global application contexts
