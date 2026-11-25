## 6.202 IDEPTREE

This view, created by `utldtree.sql`, lists the indented dependency tree. It is a pre-sorted, pretty-print version of `DEPTREE`.

| Column         | Datatype         | NULL | Description                          |
|:---------------|:-----------------|:-----|:-------------------------------------|
| `NESTED_LEVEL` | `NUMBER`         |      | Nesting level in the dependency tree |
| `TYPE`         | `VARCHAR2(23)`   |      | Object type                          |
| `OWNER`        | `VARCHAR2(28)`   |      | Object schema                        |
| `NAME`         | `VARCHAR2(1002)` |      | Object name                          |
