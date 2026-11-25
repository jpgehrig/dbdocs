## role Commands

Use commands with the `role` keyword to add, delete, and manage roles.

- rhpctl add role
  Creates roles and adds them to the list of existing roles on the Fleet Patching and Provisioning Server configuration.
- rhpctl delete role
  Deletes a role from the list of existing roles on the Fleet Patching and Provisioning Server configuration.
- rhpctl grant role
  Grants a role to a client user or to another role.
- rhpctl query role
  Displays the configuration information of a specific role.
- rhpctl revoke role
  Revokes a role from a client user.

**Parent topic:** [RHPCTL Command Reference](rhpctl-command-reference.md)

### rhpctl add role

Creates roles and adds them to the list of existing roles on the Fleet Patching and Provisioning Server configuration.

**See Also:**

[Fleet Patching and Provisioning Roles](oracle-fpp-roles.md)

#### Syntax

    rhpctl add role –role role_name -hasRoles roles

#### Parameters

Table A-48 rhpctl add role Command Parameters

| Parameter           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:--------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `–role ``role_name` | Specify a name for the role that you want to create.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `-hasRoles ``roles` | Specify a comma-delimited list of roles to include with the new role.<br>• GH_ROLE_ADMIN<br>• GH_AUDIT_ADMIN<br>• GH_USER_ADMIN<br>• GH_SITE_ADMIN<br>• GH_WC_ADMIN<br>• GH_WC_OPER<br>• GH_WC_USER<br>• GH_IMG_ADMIN<br>• GH_IMG_USER<br>• GH_SUBSCRIBE_USER<br>• GH_SUBSCRIBE_ADMIN<br>• GH_IMGTYPE_ADMIN<br>• GH_IMGTYPE_ALLOW<br>• GH_IMGTYPE_OPER<br>• GH_SERIES_ADMIN<br>• GH_SERIES_CONTRIB<br>• GH_IMG_TESTABLE<br>• GH_IMG_RESTRICT<br>• GH_IMG_PUBLISH<br>• GH_IMG_VISIBILITY<br>• GH_JOB_USER<br>• GH_JOB_ADMIN<br>• GH_AUTHENTICATED_USER<br>• GH_CLIENT_ACCESS<br>• GH_ROOT_UA_CREATE<br>• GH_ROOT_UA_ASSOCIATE<br>• GH_ROOT_UA_USE<br>• GH_OPER<br>• GH_CA<br>• GH_SA<br>• OTHER |

#### Usage Notes

- You can only run this command on the Fleet Patching and Provisioning Server.

- You must be assigned the GH_ROLE_ADMIN role to run this command.

#### Example

To add a role on the Fleet Patching and Provisioning Server:

    $ rhpctl add role -role hr_admin -hasRoles GH_WC_USER,GH_IMG_USER

**Parent topic:** role Commands

### rhpctl delete role

Deletes a role from the list of existing roles on the Fleet Patching and Provisioning Server configuration.

#### Syntax

    rhpctl delete role –role role_name

#### Usage Notes

- Specify the name of the role that you want to delete

- You cannot delete any built-in roles

- You can only run this command on the Fleet Patching and Provisioning Server

#### Example

To delete a role from the Fleet Patching and Provisioning Server:

    $ rhpctl delete role -role hr_admin

**Parent topic:** role Commands

### rhpctl grant role

Grants a role to a client user or to another role.

#### Syntax

    rhpctl grant role {–role role_name {-user user_name [-client cluster_name]
      | -grantee role_name}} | {[-client cluster_name]
      [-maproles role=user_name[+user_name...][,role=user_name[+user_name...][,...]}

#### Parameters

Table A-49 rhpctl grant role Command Parameters

| Parameter                                                                                                                           | Description                                                                                                                                                                                                                                                                                         |
|:------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-role ``role_name`                                                                                                                 | Specify the name of the role that you want to grant clients or users.                                                                                                                                                                                                                               |
| `-user ``user_name`` [-client ``cluster_name``]`                                                                                    | Specify the name of a user. The user name that you specify must be in the form of `user``@``rhpclient`, where `rhpclient` is the name of the Fleet Patching and Provisioning Client.<br>Optionally, you can specify the name of the client cluster to which the user belongs.                       |
| `-grantee ``role_name`                                                                                                              | Use this parameter to specify a role to which you want to grant another role.                                                                                                                                                                                                                       |
| `[``-client ``cluster_name``] -maproles ``role``=``user_name``[+``user_name``...][,``role``=``user_name``[+``user_name``...][,...]` | You can map either built-in roles or roles that you have defined to either users on a specific client cluster or to specific users.<br>When you use the `-maproles` parameter, use a plus sign (`+`) to map more than one user to a specific role. Separate additional role/user pairs with commas. |

#### Example

The following example grants a role, ABC, to four specific users.

    $ rhpctl grant role -role ABC -maproles ABC=mjk@rhpc1+dc@rhpc1+aj@rhpc1+jc@rhpc1

**Parent topic:** role Commands

### rhpctl query role

Displays the configuration information of a specific role.

#### Syntax

    rhpctl query role [–role role_name]

#### Usage Notes

- Specify the name of the role for which you want to display the configuration information

- You can only run this command on the Fleet Patching and Provisioning Server

#### Example

This command returns output similar to the following:

    $ rhpctl query role -role GH_CA

    Role name: GH_CA
    Associated roles: GH_IMGTYPE_ADMIN, GH_IMGTYPE_ALLOW, GH_IMGTYPE_OPER, GH_IMG_ADMIN,
    GH_IMG_PUBLISH, GH_IMG_RESTRICT, GH_IMG_TESTABLE, GH_IMG_VISIBILITY, GH_SERIES_ADMIN,
    GH_SERIES_CONTRIB, GH_SUBSCRIBE_ADMIN, GH_WC_ADMIN
    Users with this role: rhpusr@rwsdcVM13

**Parent topic:** role Commands

### rhpctl revoke role

Revokes a role from a client user.

#### Syntax

    rhpctl revoke role {–role role_name {-user user_name
      [-client cluster_name] | -grantee role_name}}
      | {[-client cluster_name] -maproles role=user_name[+user_name...]
      [,role=user_name[+user_name...]...]}

#### Parameters

Table A-50 rhpctl revoke role Command Parameters

| Parameter                                                                       | Description                                                                                                                                                                                                                                                 |
|:--------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `–role ``role_name`                                                             | Specify the name of the role from which you want to revoke clients or users.                                                                                                                                                                                |
| `-user ``user_name`` [-client ``cluster_name``]`                                | Specify the name of a user and, optionally, a client cluster from which you want to revoke a role. The user name that you specify must be in the form of `user``@``rhpclient`, where `rhpclient` is the name of the Fleet Patching and Provisioning Client. |
| `-grantee ``role_name`                                                          | Specify the grantee role name.                                                                                                                                                                                                                              |
| `[-client ``client_name``] -maproles ``role``=``user_name``[+``user_name``...]` | You can map either built-in roles or roles that you have defined to specific users. Use a plus sign (`+`) to map more than one user to a specific role. Separate additional role/user pairs with commas. Optionally, you can also specify a client cluster. |

**Parent topic:** role Commands
