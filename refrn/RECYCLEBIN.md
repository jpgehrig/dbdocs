## 1.301 RECYCLEBIN

`RECYCLEBIN` is used to control whether the Flashback Drop capability is turned on or off.

| Property            | Description                                  |
|:--------------------|:---------------------------------------------|
| Parameter type      | String                                       |
| Syntax              | `RECYCLEBIN = { on | off }`                  |
| Default value       | `on`                                         |
| Modifiable          | `ALTER SESSION`,` ALTER SYSTEM ... DEFERRED` |
| Modifiable in a PDB | Yes                                          |
| Basic               | No                                           |

If the parameter is set to `off`, then dropped tables do not go into the recycle bin. If this parameter is set to `on`, then dropped tables go into the recycle bin and can be recovered.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/managing-tables.md) for more information about using Flashback Drop and managing the recycle bin
