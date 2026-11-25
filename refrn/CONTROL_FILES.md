## 1.56 CONTROL_FILES

`CONTROL_FILES` specifies one or more names of control files, separated by commas.

| Property            | Description                                                                                                                                                                                                                    |
|:--------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Parameter type      | String                                                                                                                                                                                                                         |
| Syntax              | `CONTROL_FILES = ``filename`` [, ``filename`` ] ...`<br>Note: The control file name can be an OMF (Oracle Managed Files) name. This occurs when the control file is re-created using the `CREATE CONTROLFILE REUSE` statement. |
| Default value       | Operating system-dependent                                                                                                                                                                                                     |
| Modifiable          | No                                                                                                                                                                                                                             |
| Modifiable in a PDB | No                                                                                                                                                                                                                             |
| Range of values     | 1 to 8 filenames                                                                                                                                                                                                               |
| Basic               | Yes                                                                                                                                                                                                                            |
| Oracle RAC          | Multiple instances must have the same value.                                                                                                                                                                                   |

Every database has a control file, which contains entries that describe the structure of the database (such as its name, the timestamp of its creation, and the names and locations of its data files and redo files).

Oracle recommends that you multiplex multiple control files on different devices or mirror the file at the operating system level.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/using-oracle-managed-files.md) for information about specifying control files at database creation
