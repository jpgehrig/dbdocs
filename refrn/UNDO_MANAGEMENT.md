## 1.369 UNDO_MANAGEMENT

`UNDO_MANAGEMENT` specifies which undo space management mode the system should use.

| Property            | Description                                  |
|:--------------------|:---------------------------------------------|
| Parameter type      | String                                       |
| Syntax              | `UNDO_MANAGEMENT = { MANUAL | AUTO }`        |
| Default value       | `AUTO`                                       |
| Modifiable          | No                                           |
| Modifiable in a PDB | Yes                                          |
| Basic               | No                                           |
| Oracle RAC          | Multiple instances must have the same value. |

When `UNDO_MANAGEMENT` is set to `AUTO`, the instance starts in automatic undo management mode. In manual undo management mode, undo space is allocated externally as rollback segments.

**Note:**

In a CDB, the `UNDO_MANAGEMENT` initialization parameter must be set to `AUTO`, and an undo tablespace is required to be created to manage the undo data.

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/creating-and-configuring-an-oracle-database.md) for more information about this parameter

- [Oracle Database Administrator’s Guide](../admin/managing-undo.md) for more information about managing undo data
