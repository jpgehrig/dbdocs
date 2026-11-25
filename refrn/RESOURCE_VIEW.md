## 6.233 RESOURCE_VIEW

`RESOURCE_VIEW` contains one row for each resource in the Oracle XML DB repository.

| Column     | Datatype                                                                            | NULL | Description                                            |
|:-----------|:------------------------------------------------------------------------------------|:-----|:-------------------------------------------------------|
| `RES`      | XMLTYPE(XMLSchema "http://xmlns.oracle.com/xdb/XDBResource.xsd" Element "Resource") |      | A resource in the repository                           |
| `ANY_PATH` | `VARCHAR2(4000)`                                                                    |      | An (absolute) path to the resource                     |
| `RESID`    | `RAW(16)`                                                                           |      | Resource OID, which is a unique handle to the resource |

**See Also:**

[Oracle XML DB Developer’s Guide](../adxdb/repository-access-using-RESOURCE_VIEW-and-PATH_VIEW.md) for information about using this view
