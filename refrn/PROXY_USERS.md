## 6.218 PROXY_USERS

`PROXY_USERS` describes the list of proxy users and the clients on whose behalf they can act.

| Column           | Datatype        | NULL       | Description                                                                                                                                                                                                                                  |
|:-----------------|:----------------|:-----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `PROXY`          | `VARCHAR2(128)` | `NOT NULL` | Name of a proxy user                                                                                                                                                                                                                         |
| `CLIENT`         | `VARCHAR2(128)` | `NOT NULL` | Name of the client user who the proxy user can act as                                                                                                                                                                                        |
| `AUTHENTICATION` | `VARCHAR2(3)`   |            | Indicates whether the proxy is required to supply the client's authentication credentials (`YES`) or not (`NO`)                                                                                                                              |
| `FLAGS`          | `VARCHAR2(35)`  |            | Flags associated with the proxy/client pair:<br>• `PROXY MAY ACTIVATE ALL CLIENT ROLES`<br>• `NO CLIENT ROLES MAY BE ACTIVATED`<br>• `PROXY MAY ACTIVATE ROLE`<br>• `PROXY MAY ACTIVATE ALL CLIENT ROLES`<br>• `PROXY MAY NOT ACTIVATE ROLE` |

**See Also:**

"[DBA_PROXIES](DBA_PROXIES.md)" for information about all proxy connections in the database
