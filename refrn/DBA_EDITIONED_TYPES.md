## 4.271 DBA_EDITIONED_TYPES

`DBA_EDITIONED_TYPES` lists all types that are editioned by default for every user in the database.

### Related View

`USER_EDITIONED_TYPES` lists the types that are editioned by default for the current user. This view does not display the `SCHEMA` column.

| Column        | Datatype        | NULL       | Description                                     |
|:--------------|:----------------|:-----------|:------------------------------------------------|
| `SCHEMA`      | `VARCHAR2(128)` | `NOT NULL` | Schema in which the object types is editionable |
| `OBJECT_TYPE` | `VARCHAR2(23)`  |            | Object type that is editionable                 |

**See Also:**

"[USER_EDITIONED_TYPES](USER_EDITIONED_TYPES.md)"
