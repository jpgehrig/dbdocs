## 4.121 DBA_AQ_AGENT_PRIVS

`DBA_AQ_AGENT_PRIVS` displays information about the registered AQ agents that are mapped to all users in the database.

### Related View

`USER_AQ_AGENT_PRIVS` displays information about the registered AQ agents that are mapped to the current user. This view does not display the `DB_USERNAME` column.

| Column         | Datatype        | NULL       | Description                                                                            |
|:---------------|:----------------|:-----------|:---------------------------------------------------------------------------------------|
| `AGENT_NAME`   | `VARCHAR2(128)` | `NOT NULL` | Name of the AQ agent                                                                   |
| `DB_USERNAME`  | `VARCHAR2(128)` |            | Name of the database user that the agent maps to                                       |
| `HTTP_ENABLED` | `VARCHAR2(4)`   |            | Indicates whether the agent is allowed to access AQ through HTTP (`YES`) or not (`NO`) |
| `SMTP_ENABLED` | `VARCHAR2(4)`   |            | Indicates whether the agent is allowed to access AQ through SMTP (`YES`) or not (`NO`) |

**See Also:**

"[USER_AQ_AGENT_PRIVS](USER_AQ_AGENT_PRIVS.md)"
