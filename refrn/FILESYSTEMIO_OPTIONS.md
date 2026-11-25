## 1.132 FILESYSTEMIO_OPTIONS

`FILESYSTEMIO_OPTIONS` specifies I/O operations for file system files. This parameter is platform-specific and has a default value that is suitable for a particular platform.

| Property            | Description                                                    |
|:--------------------|:---------------------------------------------------------------|
| Parameter type      | String                                                         |
| Syntax              | `FILESYSTEMIO_OPTIONS = { ASYNCH | DIRECTIO | SETALL | NONE }` |
| Default value       | Varies by database version and operating system.               |
| Modifiable          | No                                                             |
| Modifiable in a PDB | No                                                             |
| Basic               | No                                                             |

Values:

- `ASYNCH` - Enable asynchronous I/O on file system files, which has no timing requirement for transmission.

- `DIRECTIO` - Enable direct I/O on file system files, which bypasses the buffer cache.

- `SETALL` - Enable both asynchronous and direct I/O on file system files.

- `NONE` - Disable both asynchronous and direct I/O on file system files.

**See Also:**

- Your platform-specific documentation for more details

- [Oracle Database Performance Tuning Guide](../tgdba/IO-configuration-and-design.md) for information about setting this parameter before running I/O calibration
