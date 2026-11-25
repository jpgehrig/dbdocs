## 1.324 SEC_RETURN_SERVER_RELEASE_BANNER

`SEC_RETURN_SERVER_RELEASE_BANNER` specifies whether the server returns complete database software information to unauthenticated clients.

| Property            | Description    |
|:--------------------|:---------------|
| Parameter type      | Boolean        |
| Default value       | `false`        |
| Modifiable          | No             |
| Modifiable in a PDB | No             |
| Range of values     | `true | false` |
| Basic               | No             |

### Values

- `true`

  Returns complete database version information to the client.

- `false`

  Returns a generic version string to the client.

**See Also:**

[Oracle Call Interface Programmer's Guide](../lnoci/managing-scalable-platforms.md) and [Oracle Database Security Guide](../dbseg/managing-security-for-application-developers.md) for more information on controlling the display of the database version banner.
