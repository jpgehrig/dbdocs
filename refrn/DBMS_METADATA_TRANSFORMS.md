## 6.176 DBMS_METADATA_TRANSFORMS

`DBMS_METADATA_TRANSFORMS` documents the valid Oracle-supplied transforms.

| Column        | Datatype        | NULL       | Description                  |
|:--------------|:----------------|:-----------|:-----------------------------|
| `OBJECT_TYPE` | `VARCHAR2(128)` | `NOT NULL` | Object type name             |
| `TRANSFORM`   | `VARCHAR2(128)` | `NOT NULL` | Transform name               |
| `INPUT_TYPE`  | `VARCHAR2(24)`  |            | Type of input document       |
| `OUTPUT_TYPE` | `VARCHAR2(24)`  |            | Type of output document      |
| `DESCRIPTION` | `VARCHAR2(71)`  |            | Description of the transform |

**See Also:**

- "[DBMS_METADATA_PARSE_ITEMS](DBMS_METADATA_PARSE_ITEMS.md)"

- "[DBMS_METADATA_TRANSFORM_PARAMS](DBMS_METADATA_TRANSFORM_PARAMS.md)"
