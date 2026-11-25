You can use dynamic performance views to access information in the Oracle database server.

The Oracle database server stores information about agents, sessions, and parameters. You can use the following dynamic performance views to access this information:

- Determining Which Agents Are Running on a Host: V\$HS_AGENT View
  The `V$HS_AGENT` view identifies the set of Heterogeneous Services agents currently operating on a specified host.
- Determining the Open Heterogeneous Services Sessions: V\$HS_SESSION View
  The `V$HS_SESSION` view shows the sessions for each agent and specifies the database link that is used.
- Determining the Heterogeneous Services Parameters: V\$HS_PARAMETER View
  The `V$HS_PARAMETER` view lists the Heterogeneous Services parameters and their values that are registered in the Oracle database server.

**Parent topic:** [Using Heterogeneous Services Agents](using-heterogeneous-services-agents.md)

### Determining Which Agents Are Running on a Host: V\$HS_AGENT View

The `V$HS_AGENT` view identifies the set of Heterogeneous Services agents currently operating on a specified host.

Table 4-5 shows the most relevant columns.

Table 4-5 Important Columns in the V\$HS_AGENT View

| Column         | Description                                                                      |
|:---------------|:---------------------------------------------------------------------------------|
| `AGENT_ID`     | Oracle Net session identifier used for connections to agent (`listener.ora SID`) |
| `MACHINE`      | Operating system machine name                                                    |
| `PROGRAM`      | Program name of agent                                                            |
| `AGENT_TYPE`   | Type of agent                                                                    |
| `FDS_CLASS_ID` | The ID of the foreign data store class                                           |
| `FDS_INST_ID`  | The instance name of the foreign data store                                      |

**See Also:**

[Oracle Database Reference](../refrn/V-HS_AGENT.md) for a description of all the columns in the view.

**Parent topic:** Heterogeneous Services Dynamic Performance Views

### Determining the Open Heterogeneous Services Sessions: V\$HS_SESSION View

The `V$HS_SESSION` view shows the sessions for each agent and specifies the database link that is used.

Table 4-6 shows the most relevant columns.

Table 4-6 Important Columns in the V\$HS_SESSION View

| Column          | Description                                                                                                                                 |
|:----------------|:--------------------------------------------------------------------------------------------------------------------------------------------|
| `HS_SESSION_ID` | Unique Heterogeneous Services session identifier                                                                                            |
| `AGENT_ID`      | Oracle Net session identifier used for connections to agent (`listener.ora SID`)                                                            |
| `DB_LINK`       | Server database link name used to access the agent `NULL` means that no database link is used (for example, when using external procedures) |
| `DB_LINK_OWNER` | Owner of the database link in `DB_LINK`                                                                                                     |

**See Also:**

[Oracle Database Reference](../refrn/V-HS_SESSION.md) for a description of all the columns in the view.

**Parent topic:** Heterogeneous Services Dynamic Performance Views

### Determining the Heterogeneous Services Parameters: V\$HS_PARAMETER View

The `V$HS_PARAMETER` view lists the Heterogeneous Services parameters and their values that are registered in the Oracle database server.

Table 4-7 shows the most relevant columns.

Table 4-7 Important Columns in the V\$HS_PARAMETER View

| Column          | Description                                       |
|:----------------|:--------------------------------------------------|
| `HS_SESSION_ID` | Unique Heterogeneous Services session identifier  |
| `PARAMETER`     | The name of the Heterogeneous Services parameter  |
| `VALUE`         | The value of the Heterogeneous Services parameter |

Information about the database link that was used for establishing the distributed connection, the startup time, and the set of initialization parameters used for the session is also available. All of the runtime information is derived from dynamically updated tables.

**See Also:**

[Oracle Database Reference](../refrn/V-HS_PARAMETER.md) for a description of all the columns in the view.

**Parent topic:** Heterogeneous Services Dynamic Performance Views
