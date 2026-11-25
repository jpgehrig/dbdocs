## 1.211 MFA_OMA_IAM_DOMAIN_URL

`MFA_OMA_IAM_DOMAIN_URL` specifies the OCI IAM domain URL for multi-factor authentication using Oracle Mobile Authenticator (OMA) push notifications.

| Property            | Description                                   |
|:--------------------|:----------------------------------------------|
| Parameter type      | String                                        |
| Syntax              | `MFA_OMA_IAM_DOMAIN_URL =` `string`           |
| Default value       | None                                          |
| Modifiable          | `ALTER SYSTEM`                                |
| Modifiable in a PDB | Yes                                           |
| Basic               | No                                            |
| Oracle RAC          | Multiple instances can have different values. |

This parameter is configured at the PDB level. Setting this parameter allows users in a PDB to be registered for multi-factor authentication using OMA push notifications.

Set this parameter to a valid OCI IAM domain URL. For example:

    ALTER SYSTEM SET MFA_OMA_IAM_DOMAIN_URL =
       "https://idcs-cbcb9aaca84945e78466ab5b2e576360.identity.oraclecloud.com";

**Note:**

This parameter is available starting with Oracle Database 19c, Release Update 19.28.

**See Also:**

[Oracle Database Security Guide](../dbseg/configuring-authentication.md) for more information about this parameter
