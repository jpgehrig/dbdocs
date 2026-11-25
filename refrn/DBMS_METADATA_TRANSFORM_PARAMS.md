## 6.175 DBMS_METADATA_TRANSFORM_PARAMS

`DBMS_METADATA_TRANSFORM_PARAMS` documents the valid transform parameters for each transform.

| Column        | Datatype         | NULL       | Description                                  |
|:--------------|:-----------------|:-----------|:---------------------------------------------|
| `OBJECT_TYPE` | `VARCHAR2(128)`  | `NOT NULL` | Object type name                             |
| `TRANSFORM`   | `VARCHAR2(128)`  | `NOT NULL` | Transform name                               |
| `PARAM`       | `VARCHAR2(128)`  | `NOT NULL` | Parameter name                               |
| `DATATYPE`    | `VARCHAR2(11)`   |            | `BOOLEAN`, `TEXT`, `NUMBER` or `UNSPECIFIED` |
| `DEFAULT_VAL` | `VARCHAR2(2000)` |            | Default value of transform parameter         |
| `DESCRIPTION` | `VARCHAR2(4000)` |            | Description of the transform parameter       |

**See Also:**

- "[DBMS_METADATA_PARSE_ITEMS](DBMS_METADATA_PARSE_ITEMS.md)"

- "[DBMS_METADATA_TRANSFORMS](DBMS_METADATA_TRANSFORMS.md)"
