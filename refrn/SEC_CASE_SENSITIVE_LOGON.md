## 1.320 SEC_CASE_SENSITIVE_LOGON

`SEC_CASE_SENSITIVE_LOGON` enables or disables password case sensitivity in the database.

| Property            | Description    |
|:--------------------|:---------------|
| Parameter type      | Boolean        |
| Default value       | `true`         |
| Modifiable          | `ALTER SYSTEM` |
| Modifiable in a PDB | No             |
| Range of values     | `true | false` |
| Basic               | No             |

**Note:**

The `SEC_CASE_SENSITIVE_LOGON` parameter is deprecated. It is retained for backward compatibility only. For more information about the deprecation of this parameter, see [Oracle Database Security Guide](../dbseg/configuring-authentication.md).

### Values

- `true`

  Database logon passwords are case sensitive.

- `false`

  Database logon passwords are not case sensitive.

**See Also:**

[Oracle Database Security Guide](../dbseg/configuring-authentication.md) for more details about the SEC_CASE_SENSITIVE_LOGON parameter
