## 1.183 LOG_ARCHIVE_DUPLEX_DEST

`LOG_ARCHIVE_DUPLEX_DEST` is similar to the initialization parameter `LOG_ARCHIVE_DEST`. This parameter specifies a second archive destination: the duplex archive destination. This duplex archive destination can be either a must-succeed or a best-effort archive destination, depending on how many archive destinations must succeed (as specified in the `LOG_ARCHIVE_MIN_SUCCEED_DEST` parameter).

| Property            | Description                                                                  |
|:--------------------|:-----------------------------------------------------------------------------|
| Parameter type      | String                                                                       |
| Syntax              | `LOG_ARCHIVE_DUPLEX_DEST = ``filespec`                                       |
| Default value       | There is no default value.                                                   |
| Modifiable          | `ALTER SYSTEM`                                                               |
| Modifiable in a PDB | No                                                                           |
| Range of values     | Either a null string or any valid path or device name, except raw partitions |
| Basic               | No                                                                           |

**Note:**

If you are using Oracle Enterprise Edition, this parameter is deprecated in favor of the `LOG_ARCHIVE_DEST_``n` parameters. If Oracle Enterprise Edition is not installed or it is installed but you have not specified any `LOG_ARCHIVE_DEST_``n` parameters, this parameter is valid.

The default setting of a null string ("") or (' ') indicates that a duplex archive destination does not exist.

**See Also:**

- "[LOG_ARCHIVE_DEST_n](LOG_ARCHIVE_DEST_n.md)"

- "[LOG_ARCHIVE_MIN_SUCCEED_DEST](LOG_ARCHIVE_MIN_SUCCEED_DEST.md)"

- "[V\$ARCHIVE_DEST](V-ARCHIVE_DEST.md)"

- [Oracle Database Administrator’s Guide](../admin/managing-archived-redo-log-files.md) for an example of using this parameter to specify an optional secondary archive destination
