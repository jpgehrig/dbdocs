## 6.240 SESSION_CONTEXT

`SESSION_CONTEXT` describes the context attributes and their values set for the current session.

| Column      | Datatype         | NULL | Description                               |
|:------------|:-----------------|:-----|:------------------------------------------|
| `NAMESPACE` | `VARCHAR2(128)`  |      | Namespace that the active attribute is in |
| `ATTRIBUTE` | `VARCHAR2(128)`  |      | Name of the active attribute              |
| `VALUE`     | `VARCHAR2(4000)` |      | Value of the active attribute             |
