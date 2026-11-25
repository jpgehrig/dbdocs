## 1.31 BACKGROUND_CORE_DUMP

`BACKGROUND_CORE_DUMP` specifies whether Oracle includes the SGA in the core file for Oracle background processes.

| Property            | Description                                 |
|:--------------------|:--------------------------------------------|
| Parameter type      | String                                      |
| Syntax              | `BACKGROUND_CORE_DUMP = { partial | full }` |
| Default value       | `partial`                                   |
| Modifiable          | `ALTER SYSTEM`                              |
| Modifiable in a PDB | No                                          |
| Basic               | No                                          |

### Values

- `partial`

  Oracle does not include the SGA in the core dump.

- `full`

  Oracle includes the SGA in the core dump.

**See Also:**

"[SHADOW_CORE_DUMP](SHADOW_CORE_DUMP.md)"
