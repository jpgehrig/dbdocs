## 6.212 PATH_VIEW

`PATH_VIEW` contains one row for each unique path to access a resource in the Oracle XML DB repository.

| Column  | Datatype                                                                            | NULL | Description                                     |
|:--------|:------------------------------------------------------------------------------------|:-----|:------------------------------------------------|
| `PATH`  | `VARCHAR2(1024)`                                                                    |      | An (absolute) path to repository resource `RES` |
| `RES`   | XMLTYPE(XMLSchema "http://xmlns.oracle.com/xdb/XDBResource.xsd" Element "Resource") |      | The resource referred to by the `PATH` column   |
| `LINK`  | `XMLTYPE`                                                                           |      | Link property                                   |
| `RESID` | `RAW(16)`                                                                           |      | Resource OID                                    |

**See Also:**

[Oracle XML DB Developer’s Guide](../adxdb/repository-access-using-RESOURCE_VIEW-and-PATH_VIEW.md) for information about using this view
