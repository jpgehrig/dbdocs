## 1.381 XML_DB_EVENTS

`XML_DB_EVENTS` enables or disables XML DB events.

| Property            | Description                            |
|:--------------------|:---------------------------------------|
| Parameter type      | String                                 |
| Syntax              | `XML_DB_EVENTS = { enable | disable }` |
| Default value       | `enable`                               |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`        |
| Modifiable in a PDB | Yes                                    |
| Basic               | No                                     |

Changing this parameter through an `ALTER SESSION` statement affects only the current session. Only users with the `XDBADMIN` role are allowed to change this parameter in a session.

Changing this parameter through an `ALTER SYSTEM` statement will make a systemwide change of this parameter; however, the change is only registered by new sessions started after the change. Currently running sessions need to be restarted to pick up the new change. Users must have the `ALTER SYSTEM` privilege to make a systemwide change.

**See Also:**

[Oracle XML DB Developer’s Guide](../adxdb/XML-DB-repository-events.md) for more information about this parameter
