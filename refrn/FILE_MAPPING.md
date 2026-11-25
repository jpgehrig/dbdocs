## 1.130 FILE_MAPPING

`FILE_MAPPING` specifies whether file mapping is enabled.

| Property            | Description    |
|:--------------------|:---------------|
| Parameter type      | Boolean        |
| Default value       | `false`        |
| Modifiable          | `ALTER SYSTEM` |
| Modifiable in a PDB | No             |
| Range of values     | `true | false` |
| Basic               | No             |

**Note:**

The `FILE_MAPPING` initialization parameter is deprecated. It is still supported for backward compatibility.

The FMON background process is started to manage the mapping information when file mapping is enabled.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/managing-data-files-and-temp-files.md) for more information about the file mapping feature
