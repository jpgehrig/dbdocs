## 1.210 MFA_DUO_API_HOST

`MFA_DUO_API_HOST` specifies the host name of the Cisco Duo security API to be used for multi-factor authentication using Cisco Duo push notifications.

| Property            | Description                                   |
|:--------------------|:----------------------------------------------|
| Parameter type      | String                                        |
| Syntax              | `MFA_DUO_API_HOST =` `string`                 |
| Default value       | None                                          |
| Modifiable          | `ALTER SYSTEM`                                |
| Modifiable in a PDB | Yes                                           |
| Basic               | No                                            |
| Oracle RAC          | Multiple instances can have different values. |

This parameter is configured at the PDB level. Setting this parameter allows users in a PDB to be registered for multi-factor authentication using Cisco Duo push notifications.

Set this parameter to a valid Duo API host. For example:

    ALTER SYSTEM SET MFA_DUO_API_HOST = "api-855fd6a0.duosecurity.com";

**Note:**

This parameter is available starting with Oracle Database 19c, Release Update 19.28.

**See Also:**

[Oracle Database Security Guide](../dbseg/configuring-authentication.md) for more information about this parameter
