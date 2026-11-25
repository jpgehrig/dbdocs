## 1.212 MFA_SENDER_EMAIL_DISPLAYNAME

`MFA_SENDER_EMAIL_DISPLAYNAME` specifies the `From:` display name for emails sent to users when configuring multi-factor authentication using Oracle Mobile Authenticator (OMA) or Cisco Duo push notifications.

| Property            | Description                                   |
|:--------------------|:----------------------------------------------|
| Parameter type      | String                                        |
| Syntax              | `MFA_SENDER_EMAIL_DISPLAYNAME =` `string`     |
| Default value       | None                                          |
| Modifiable          | `ALTER SYSTEM`                                |
| Modifiable in a PDB | Yes                                           |
| Basic               | No                                            |
| Oracle RAC          | Multiple instances can have different values. |

This parameter is configured at the PDB level. When adding OMA or Duo as an additional authentication method for a user in a PDB, the user is sent an email with instructions on how to register a device. This parameter specifies the display name used in those emails.

Set this parameter to the desired email display name. For example:

    ALTER SYSTEM SET MFA_SENDER_EMAIL_DISPLAYNAME = "Database MFA Registration";

**Note:**

This parameter is available starting with Oracle Database 19c, Release Update 19.28.

**See Also:**

[Oracle Database Security Guide](../dbseg/configuring-authentication.md) for more information about this parameter
