## 6.220 PUBLIC_DEPENDENCY

`PUBLIC_DEPENDENCY` lists dependencies to and from objects, by object number.

| Column                 | Datatype | NULL       | Description                           |
|:-----------------------|:---------|:-----------|:--------------------------------------|
| `OBJECT_ID`            | `NUMBER` | `NOT NULL` | Object number                         |
| `REFERENCED_OBJECT_ID` | `NUMBER` | `NOT NULL` | Referenced object (the parent object) |
