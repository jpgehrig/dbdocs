## 5.256 DBA_PROXIES

`DBA_PROXIES` displays information about all proxy connections in the database.

### Related View

`USER_PROXIES` displays information about connections the current user is allowed to proxy. This view does not display the `PROXY` or `PROXY_AUTHORITY` columns.

| Column                     | Datatype        | NULL       | Description                                                                                                                                                                                                                    |
|:---------------------------|:----------------|:-----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `PROXY`                    | `VARCHAR2(128)` |            | Name of the proxy user                                                                                                                                                                                                         |
| `CLIENT`                   | `VARCHAR2(128)` | `NOT NULL` | Name of the client user who the proxy user can act on behalf of                                                                                                                                                                |
| `AUTHENTICATION`           | `VARCHAR2(3)`   |            | Indicates whether the proxy is required to supply the client's authentication credentials (`YES`) or not (`NO`)                                                                                                                |
| `AUTHORIZATION_CONSTRAINT` | `VARCHAR2(35)`  |            | Indicates the proxy's authority to exercise roles on the client's behalf:<br>• `NO CLIENT ROLES MAY BE ACTIVATED`<br>• `PROXY MAY ACTIVATE ROLE`<br>• `PROXY MAY ACTIVATE ALL CLIENT ROLES`<br>• `PROXY MAY NOT ACTIVATE ROLE` |
| `ROLE`                     | `VARCHAR2(128)` |            | Name of the role referenced in `AUTHORIZATION_CONSTRAINT`                                                                                                                                                                      |
| `PROXY_AUTHORITY`          | `VARCHAR2(9)`   |            | Value is either:<br>• `DIRECTORY` if an EUS proxy is enabled for the database user<br>• `DATABASE` if this row describes a local proxy permission                                                                              |

**See Also:**

- "[USER_PROXIES](USER_PROXIES.md)"

- "[PROXY_USERS](PROXY_USERS.md)" for a list of proxy users and the clients on whose behalf they can act
