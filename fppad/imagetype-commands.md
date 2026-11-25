## imagetype Commands

Use commands with the `imagetype` keyword to add, delete, modify, and manage an image type.

- rhpctl add imagetype
  Configures a new image type and its associated user actions.
- rhpctl allow imagetype
  Grants access to an image type to a user or a role.
- rhpctl delete imagetype
  Deletes an existing image type.
- rhpctl disallow imagetype
  Revokes access to an image type from a user or a role.
- rhpctl modify imagetype
  Modifies the configuration of an image type.
- rhpctl query imagetype
  Displays the configuration of an image type.

**Parent topic:** [RHPCTL Command Reference](rhpctl-command-reference.md)

### rhpctl add imagetype

Configures a new image type and its associated user actions.

#### Syntax

    rhpctl add imagetype -imagetype image_type -basetype {SOFTWARE |
      ORACLEGISOFTWARE | ORACLEDBSOFTWARE | ORACLEGGSOFTWARE}
      [-useractions user_action_list]

#### Parameters

Table A-36 rhpctl add imagetype Command Parameters

| Parameter                                                                       | Description                                                                                                                                                                                                                                                                                       |
|:--------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-imagetype ``image_type`                                                       | Specify the name of the image type you are creating.                                                                                                                                                                                                                                              |
| `-basetype {SOFTWARE | ORACLEGISOFTWARE | ORACLEDBSOFTWARE | ORACLEGGSOFTWARE}` | Specify a base image type on which the image type you are creating is based. Use `ORACLEDBSOFTWARE` (default) for Oracle Database software, `ORACLEGISOFTWARE` for Oracle Grid Infrastructure software, `ORACLEGGSOFTWARE` for Oracle GoldenGate software, and `SOFTWARE` for all other software. |
| `-useractions ``user_action_list`                                               | Specify a comma-delimited list of names of user actions                                                                                                                                                                                                                                           |

#### Example

To add a new image type:

    rhpctl add imagetype -imagetype DB122_PATCH_TYPE -basetype ORACLEDBSOFTWARE

**Parent topic:** imagetype Commands

### rhpctl allow imagetype

Grants access to an image type to a user or a role.

#### Syntax

    rhpctl allow imagetype -imagetype image_type {-user user_name [-client cluster_name] | -role role_name}

#### Parameters

Table A-37 rhpctl allow imagetype Command Parameters

| Parameter                 | Description                                                                                                                                                                                                                                                                                                                                                                                                         |
|:--------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-imagetype ``image_type` | Specify the software type. Use `ORACLEDBSOFTWARE` (default) for Oracle database software, `ORACLEGISOFTWARE` for Oracle Grid Infrastructure software, `ORACLEGGSOFTWARE` for Oracle GoldenGate software, `ODAPATCHSOFTWARE` for engineered systems (Oracle Data Appliance), `EXAPATCHSOFTWARE` for Oracle Exadata software, or `SOFTWARE` for all other software. For a custom image type, use the image type name. |
| `-user ``user_name`       | Specify an operating system user to whom you are granting access to the image type. Either this parameter or the `-role` parameter is required.                                                                                                                                                                                                                                                                     |
| `-client ``cluster_name`  | Optionally, you can specify the name of the client cluster to which the operating system user belongs, if you choose to use the `-user` parameter.                                                                                                                                                                                                                                                                  |
| `-role ``role_name`       | Alternative to the `-user` parameter, you can specify a particular role to which to grant access to the image.                                                                                                                                                                                                                                                                                                      |

**Parent topic:** imagetype Commands

### rhpctl delete imagetype

Deletes an existing image type.

#### Syntax

    rhpctl delete imagetype -imagetype image_type

#### Usage Notes

Specify an image type to delete. You cannot delete any of the built-in image types.

**Parent topic:** imagetype Commands

### rhpctl disallow imagetype

Revokes access to an image type from a user or a role.

#### Syntax

    rhpctl disallow imagetype -imagetype image_type {-user user_name [-client cluster_name] | -role role_name}

#### Parameters

Table A-38 rhpctl disallow imagetype Command Parameters

| Parameter                 | Description                                                                                                                                                                                                                                                                                                                                                                                                         |
|:--------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-imagetype ``image_type` | Specify the software type. Use `ORACLEDBSOFTWARE` (default) for Oracle database software, `ORACLEGISOFTWARE` for Oracle Grid Infrastructure software, `ORACLEGGSOFTWARE` for Oracle GoldenGate software, `ODAPATCHSOFTWARE` for engineered systems (Oracle Data Appliance), `EXAPATCHSOFTWARE` for Oracle Exadata software, or `SOFTWARE` for all other software. For a custom image type, use the image type name. |
| `-user ``user_name`       | Specify an operating system user from whom you are revoking access to the image type. Either this parameter or the `-role` parameter is required.                                                                                                                                                                                                                                                                   |
| `-client ``cluster_name`  | Optionally, you can specify the name of the client cluster to which the operating system user belongs, if you choose to use the `-user` parameter.                                                                                                                                                                                                                                                                  |
| `-role ``role_name`       | Alternative to the `-user` parameter, you can specify a particular role from which to revoke access to the image.                                                                                                                                                                                                                                                                                                   |

**Parent topic:** imagetype Commands

### rhpctl modify imagetype

Modifies the configuration of an image type.

#### Syntax

    rhpctl modify imagetype -imagetype image_type -useractions user_action_list

#### Parameters

Table A-39 rhpctl modify imagetype Command Parameters

| Parameter                         | Description                                                                                                                                                                                                                                                                                                                  |
|:----------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-imagetype ``image_type`         | Specify the name of the image type you want to modify. Use `ORACLEDBSOFTWARE` (default) for Oracle database software, `ORACLEGISOFTWARE` for Oracle Grid Infrastructure software, `ORACLEGGSOFTWARE` for Oracle GoldenGate software, or `SOFTWARE` for all other software. For a custom image type, use the image type name. |
| `-useractions ``user_action_list` | Specify a comma-delimited list of names of user actions                                                                                                                                                                                                                                                                      |

**Parent topic:** imagetype Commands

### rhpctl query imagetype

Displays the configuration of an image type.

#### Syntax

    rhpctl query imagetype -imagetype image_type

#### Usage Notes

Specify the name of the image type you want to query. Use ORACLEDBSOFTWARE (default) for Oracle database software, ORACLEGISOFTWARE for Oracle Grid Infrastructure software, or SOFTWARE for all other software. For a custom image type, use the image type name.

**Parent topic:** imagetype Commands
