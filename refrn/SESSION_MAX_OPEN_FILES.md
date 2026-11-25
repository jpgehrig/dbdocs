## 1.329 SESSION_MAX_OPEN_FILES

`SESSION_MAX_OPEN_FILES` specifies the maximum number of BFILEs that can be opened in any session. Once this number is reached, subsequent attempts to open more files in the session by using `DBMS_LOB.FILEOPEN()` or `OCILobFileOpen()` will fail. The maximum value for this parameter depends on the equivalent parameter defined for the underlying operating system.

| Property            | Description                                                                                              |
|:--------------------|:---------------------------------------------------------------------------------------------------------|
| Parameter type      | Integer                                                                                                  |
| Default value       | `10`                                                                                                     |
| Modifiable          | No                                                                                                       |
| Modifiable in a PDB | No                                                                                                       |
| Range of values     | 1 to either 50 or the value of `MAX_OPEN_FILES` defined at the operating system level, whichever is less |
| Basic               | No                                                                                                       |

**See Also:**

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/introduction-to-large-objects.md) for information on LOBs in general

- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/introduction-to-large-objects.md) for information on BFILEs

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_LOB.md) for information on the `DBMS_LOB.FILEOPEN()` procedure

- [Oracle Call Interface Programmer's Guide](../lnoci/lob-functions.md) for information on the `OCILobFileOpen()` procedure
