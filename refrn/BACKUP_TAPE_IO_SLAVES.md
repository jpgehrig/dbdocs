## 1.33 BACKUP_TAPE_IO_SLAVES

`BACKUP_TAPE_IO_SLAVES` specifies whether I/O server processes are used by Recovery Manager to back up, copy, or restore data to tape.

| Property            | Description                 |
|:--------------------|:----------------------------|
| Parameter type      | Boolean                     |
| Default value       | `false`                     |
| Modifiable          | `ALTER SYSTEM ... DEFERRED` |
| Modifiable in a PDB | No                          |
| Range of values     | `true | false`              |
| Basic               | No                          |

When the value is set to `true`, Oracle uses an I/O server process to write to or read from a tape device. When the value is set to `false` (the default), Oracle does not use I/O server process for backups. Instead, the shadow process engaged in the backup accesses the tape device.

**Note:**

You cannot perform duplexed backups unless you enable this parameter. Otherwise, Oracle returns an error. When this parameter is enabled, Recovery Manager will configure as many server processes as needed for the number of backup copies requested.

**See Also:**

- [Oracle Database Backup and Recovery User’s Guide](../bradv/configuring-rman-client-advanced.md) for more information on duplexed backups

- "[DBWR_IO_SLAVES](DBWR_IO_SLAVES.md)"
