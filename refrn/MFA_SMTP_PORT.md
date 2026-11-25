## 1.215 MFA_SMTP_PORT

`MFA_SMTP_PORT` specifies the SMTP port for emails sent to users when configuring multi-factor authentication using Oracle Mobile Authenticator (OMA) or Cicco Duo push notifications.

| Property            | Description                                   |
|:--------------------|:----------------------------------------------|
| Parameter type      | Integer                                       |
| Default value       | 587                                           |
| Modifiable          | `ALTER SYSTEM`                                |
| Modifiable in a PDB | Yes                                           |
| Range of values     | 25 to 587                                     |
| Basic               | No                                            |
| Oracle RAC          | Multiple instances can have different values. |

This parameter is configured at the PDB level. When adding OMA or Duo as an additional authentication method for a user in a PDB, the user is sent an email with instructions on how to register a device. This parameter specifies the SMTP port for those emails.

Set this parameter to to a valid SMTP port. For example:

    ALTER SYSTEM SET MFA_SMTP_PORT = 587;

**Note:**

This parameter is available starting with Oracle Database 19c, Release Update 19.28.

**See Also:**

[Oracle Database Security Guide](../dbseg/configuring-authentication.md) for more information about this parameter
