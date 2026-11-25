## 1.334 SHADOW_CORE_DUMP

`SHADOW_CORE_DUMP` specifies whether Oracle includes the SGA in the core file for foreground (client) processes.

| Property            | Description                                         |
|:--------------------|:----------------------------------------------------|
| Parameter type      | String                                              |
| Syntax              | `SHADOW_CORE_DUMP = { partial | full | none }`      |
| Default value       | `partial`. On Windows, the default value is `none`. |
| Modifiable          | `ALTER SYSTEM`                                      |
| Modifiable in a PDB | Yes                                                 |
| Basic               | No                                                  |

### Values

- `partial`

  Oracle does not include the SGA in the core dump.

- `full`

  Oracle includes the SGA in the core dump.

- `none`

  No core files will be generated for foreground processes.

**See Also:**

"[BACKGROUND_CORE_DUMP](BACKGROUND_CORE_DUMP.md)"
