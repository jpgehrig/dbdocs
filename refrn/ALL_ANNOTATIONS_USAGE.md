## 2.53 ALL_ANNOTATIONS_USAGE

`ALL_ANNOTATIONS_USAGE` provides usage information about schema annotations accessible to the current user.

### Related Views

- `DBA_ANNOTATIONS_USAGE` provides usage information about all schema annotations in the database.

- `USER_ANNOTATIONS_USAGE` provides usage information about schema annotations owned by the current user. This view does not display the `ANNOTATION_OWNER` column.

| Column             | Datatype         | NULL | Description                                                                                                                                                                                  |
|:-------------------|:-----------------|:-----|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `OBJECT_NAME`      | `VARCHAR2(128)`  |      | Object name                                                                                                                                                                                  |
| `OBJECT_TYPE`      | `VARCHAR2(9)`    |      | Object type                                                                                                                                                                                  |
| `COLUMN_NAME`      | `VARCHAR2(128)`  |      | If the annotation is specified for a table column, view column, or domain column, the name of the column; otherwise NULL                                                                     |
| `DOMAIN_NAME`      | `VARCHAR2(128)`  |      | If the annotation is carried over from a domain or a domain column, the name of the domain; otherwise NULL<br>Note that domains carry over their annotations to objects that reference them. |
| `DOMAIN_OWNER`     | `VARCHAR2(128)`  |      | If the annotation is carried over from a domain or domain column, the owner of the domain; otherwise NULL<br>Note that domains carry over their annotations to objects that reference them.  |
| `ANNOTATION_OWNER` | `VARCHAR2(128)`  |      | Annotation owner                                                                                                                                                                             |
| `ANNOTATION_NAME`  | `VARCHAR2(1024)` |      | Annotation name                                                                                                                                                                              |
| `ANNOTATION_VALUE` | `VARCHAR2(4000)` |      | Optional annotation value<br>A NULL value is possible when the annotation does not require a value, that is, when the annotation is defined solely by its name.                              |

**Note:**

This view is available starting with Oracle Database 19c, Release Update 19.28.

**See Also:**

- "[DBA_ANNOTATIONS_USAGE](DBA_ANNOTATIONS_USAGE.md)"

- "[USER_ANNOTATIONS_USAGE](USER_ANNOTATIONS_USAGE.md)"
