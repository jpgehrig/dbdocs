## 5.282 DBA_REGISTRY_SCHEMAS

`DBA_REGISTRY_SCHEMAS` lists the primary and ancillary schemas included in the component registry. The ancillary schemas that are listed in this view are the same schemas that would be included in the `OTHER_SCHEMAS` column of the `DBA_REGISTRY` view.

| Column      | Datatype        | NULL | Description                                      |
|:------------|:----------------|:-----|:-------------------------------------------------|
| `NAMESPACE` | `VARCHAR2(30)`  |      | Component namespace                              |
| `COMP_ID`   | `VARCHAR2(30)`  |      | Component identifier                             |
| `SCHEMA`    | `VARCHAR2(128)` |      | User that contains the objects for the component |

**See Also:**

- "[DBA_REGISTRY](DBA_REGISTRY.md)"

- "[USER_REGISTRY](USER_REGISTRY.md)"
