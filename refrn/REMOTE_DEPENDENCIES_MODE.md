## 1.303 REMOTE_DEPENDENCIES_MODE

`REMOTE_DEPENDENCIES_MODE` specifies how Oracle should handle dependencies upon remote PL/SQL stored procedures.

| Property            | Description                                            |
|:--------------------|:-------------------------------------------------------|
| Parameter type      | String                                                 |
| Syntax              | `REMOTE_DEPENDENCIES_MODE = { TIMESTAMP | SIGNATURE }` |
| Default value       | `TIMESTAMP`                                            |
| Modifiable          | `ALTER SESSION`, `ALTER SYSTEM`                        |
| Modifiable in a PDB | Yes                                                    |
| Basic               | No                                                     |

### Values

- `TIMESTAMP`

  The client running the procedure compares the timestamp recorded on the server-side procedure with the current timestamp of the local procedure and executes the procedure only if the timestamps match.

- `SIGNATURE`

  Oracle allows the procedure to execute as long as the signatures are considered safe. This setting allows client PL/SQL applications to be run without recompilation.

**See Also:**

[Oracle Database Development Guide](../adfns/schema-object-dependency.md) for suggestions for managing dependencies
