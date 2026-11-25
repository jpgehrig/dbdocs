## 1.143 IDENTITY_PROVIDER_TYPE

`IDENTITY_PROVIDER_TYPE` specifies an external identity provider for the database.

| Property            | Description                                              |
|:--------------------|:---------------------------------------------------------|
| Parameter type      | String                                                   |
| Syntax              | `IDENTITY_PROVIDER_TYPE = { AZURE_AD | OCI_IAM | NONE }` |
| Default value       | `NONE`                                                   |
| Modifiable          | `ALTER SYSTEM`                                           |
| Modifiable in a PDB | Yes                                                      |
| Basic               | No                                                       |
| Oracle RAC          | The same value must be used on all instances.            |

Values:

- `AZURE_AD` - Enables the database to use Microsoft Azure Active Directory (Azure AD) as an external identity provider.

  When you specify this value, you must also specify configuration settings for Azure AD by setting the `IDENTITY_PROVIDER_CONFIG` initialization parameter.

- `OCI_IAM` - Enables the database to use Oracle Cloud Infrastructure Identity and Access Management (OCI IAM) as an external identity provider.

  When you specify this value, there is no need to specify configuration settings with the `IDENTITY_PROVIDER_CONFIG` initialization parameter.

- `NONE` - The database will not use Azure AD or OCI IAM as an external identity provider.

**Note:**

Setting the value of this parameter is only one step in a series of steps for configuring an external identity provider for the database. Refer to Oracle Database Security Guide for the complete set of steps for configuring [Azure AD](../dbseg/authenticating-and-authorizing-microsoft-entra-id-ms-ei-users-oracle-databases-oracle-exadata.md) or [OCI IAM](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md) before you set this parameter value.

**Note:**

This parameter is available starting with Oracle Database 19c, Release Update 19.16.

**Note:**

This parameter is not available to update directly for Oracle Autonomous Database Serverless.

**See Also:**

"[IDENTITY_PROVIDER_CONFIG](IDENTITY_PROVIDER_CONFIG.md)"
