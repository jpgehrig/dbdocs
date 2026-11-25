The `DBMS_MACADM` PL/SQL package enables you to configure Oracle Database Vault realms.

Only users who have been granted the `DV_OWNER` or `DV_ADMIN` role can use these procedures. For constants that you can use with these procedures, see [Table 20-1](oracle-database-vault-utility-apis.md) for more information.

- ADD_AUTH_TO_REALM Procedure
  The `ADD_AUTH_TO_REALM` procedure authorizes a user or role to access a realm as an owner or a participant. In a multitenant environment, you can authenticate both common and local realms.
- ADD_OBJECT_TO_REALM Procedure
  The `ADD_OBJECT_TO_REALM` procedure registers a set of objects for realm protection.
- CREATE_REALM Procedure
  The `CREATE_REALM` procedure creates a realm. In a multitenant environment, you can create both common and local realms.
- DELETE_AUTH_FROM_REALM Procedure
  The `DELETE_AUTH_FROM_REALM` procedure removes the authorization of a user or role to access a realm.
- DELETE_OBJECT_FROM_REALM Procedure
  The `DELETE_OBJECT_FROM_REALM` procedure removes a set of objects from realm protection.
- DELETE_REALM Procedure
  The `DELETE_REALM` procedure deletes a realm, including its related configuration information that specifies who is authorized and what objects are protected.
- DELETE_REALM_CASCADE Procedure
  The `DELETE_REALM_CASCADE` procedure deletes a realm, including its related Database Vault configuration information that specifies who is authorized and the objects that are protected.
- RENAME_REALM Procedure
  The `RENAME_REALM` procedure renames a realm; the name change takes effect everywhere the realm is used.
- UPDATE_REALM Procedure
  The `UPDATE_REALM` procedure updates a realm.
- UPDATE_REALM_AUTH Procedure
  The `UPDATE_REALM_AUTH` procedure updates the authorization of a user or role to access a realm.

### 14.1 ADD_AUTH_TO_REALM Procedure

The `ADD_AUTH_TO_REALM` procedure authorizes a user or role to access a realm as an owner or a participant. In a multitenant environment, you can authenticate both common and local realms.

For detailed information about realm authorization, see [About Realm Authorization](configuring-realms.md).

Optionally, you can specify a rule set that must be checked before allowing the authorization to be enabled.

#### Syntax

    DBMS_MACADM.ADD_AUTH_TO_REALM(
     realm_name    IN VARCHAR2,
     grantee       IN VARCHAR2,
     rule_set_name IN VARCHAR2,
     auth_options  IN NUMBER
     auth_scope    IN NUMBER DEFAULT);

#### Parameters

Table 14-1 ADD_AUTH_TO_REALM Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:----------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `realm_name`    | Realm name.<br>To find the existing realms in the current database instance, query the `DBA_DV_REALM` view, described in [DBA_DV_REALM View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `grantee`       | User or role name to authorize as an owner or a participant.<br>To find the existing users and roles in the current database instance, query the [`DBA_USERS`](../refrn/DBA_USERS.md) and [`DBA_ROLES`](../refrn/DBA_ROLES.md) views, described in Oracle Database Reference.<br>To find the authorization of a particular user or role, query the `DVA_DV_REALM_AUTH` view, described in [DBA_DV_REALM_AUTH View](oracle-database-vault-data-dictionary-views.md).<br>To find existing secure application roles used in privilege management, query the `DBA_DV_ROLE` view. Both are described in [Oracle Database Vault Data Dictionary Views](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                      |
| `rule_set_name` | Optional. The rule set to check during runtime. The realm authorization is enabled only if the rule set evaluates to `TRUE`.<br>To find the available rule sets, query the `DBA_DV_RULE_SET` view, described in [DBA_DV_RULE_SET_RULE View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `auth_options`  | Optional. Specify one of the following options to authorize the realm:<br>• `DBMS_MACUTL.G_REALM_AUTH_PARTICIPANT`: Participant. This account or role allows system or direct privileges to access, manipulate, and create objects protected by the realm, provided these rights have been granted using the standard Oracle Database privilege grant process. (Default)<br>• `DBMS_MACUTL.G_REALM_AUTH_OWNER`: Owner. This account or role has the same authorization as the realm participant, plus the authorization to grant or revoke realm-secured roles and privileges on realm-protected objects.<br>The `audit_options` parameter applies to traditional auditing only. If you have enabled unified auditing, then create a unified audit policy instead of using `audit_options`.<br>See [About Realm Authorization](configuring-realms.md) for more information on participants and owners. |
| `auth_scope`    | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) to authorize the realm locally in the current PDB<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2`) to authorize the realm in the application root                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

#### Examples

The following example authorizes user `SYSADM` as a participant in the Performance Statistics Realm. Because the default is to authorize the user as a participant, the `auth_options` parameter can be omitted.

    BEGIN
     DBMS_MACADM.ADD_AUTH_TO_REALM(
      realm_name  => 'Performance Statistics Realm',
      grantee     => 'SYSADM');
    END;
    /

This example sets user `SYSADM` as the owner of the Performance Statistics Realm.

    BEGIN
     DBMS_MACADM.ADD_AUTH_TO_REALM(
      realm_name   => 'Performance Statistics Realm',
      grantee      => 'SYSADM',
      auth_options => DBMS_MACUTL.G_REALM_AUTH_OWNER);
    END;
    /

The next example triggers the Check Conf Access rule set before allowing user `SYSADM` to act as the owner of the Performance Statistics Realm.

    BEGIN
     DBMS_MACADM.ADD_AUTH_TO_REALM(
      realm_name    => 'Performance Statistics Realm',
      grantee       => 'SYSADM',
      rule_set_name => 'Check Conf Access',
      auth_options  => DBMS_MACUTL.G_REALM_AUTH_OWNER);
    END;
    /

This example shows how to commonly grant the common user `C##HR_ADMIN` access to the common realm HR Statistics Realm. The user running this procedure must be in the CDB root, and the rule set must be a common rule set residing in the application root.

    BEGIN
     DBMS_MACADM.ADD_AUTH_TO_REALM(
      realm_name    => 'HR Statistics Realm',
      grantee       => 'C##HR_ADMIN',
      rule_set_name => 'Check Access',
      auth_options  => DBMS_MACUTL.G_REALM_AUTH_OWNER,
     auth_scope    => DBMS_MACUTL.G_SCOPE_COMMON);
    END;
    /

This example shows how to locally grant the common user `C##HR_CLERK` access to the common realm HR Statistics Realm. The user running this procedure must be in the same PDB in which the authorization applies. To find the existing PDBs query the `DBA_PDBS` data dictionary view. The rule set must be a local rule set.

    BEGIN
     DBMS_MACADM.ADD_AUTH_TO_REALM(
      realm_name    => 'HR Statistics Realm',
      grantee       => 'C##HR_CLERK',
      rule_set_name => 'Check Access',
      auth_options  => DBMS_MACUTL.G_REALM_AUTH_OWNER,
      auth_scope    => DBMS_MACUTL.G_SCOPE_LOCAL);
    END;
    /

**Parent topic:** Oracle Database Vault Realm APIs

### 14.2 ADD_OBJECT_TO_REALM Procedure

The `ADD_OBJECT_TO_REALM` procedure registers a set of objects for realm protection.

#### Syntax

    DBMS_MACADM.ADD_OBJECT_TO_REALM(
      realm_name   IN VARCHAR2,
      object_owner IN VARCHAR2,
      object_name  IN VARCHAR2,
      object_type  IN VARCHAR2);

#### Parameters

Table 14-2 ADD_OBJECT_TO_REALM Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                  |
|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `realm_name`   | Realm name.<br>To find the existing realms in the current database instance, query the `DBA_DV_REALM` view.                                                                                                                                                                                                                                  |
| `object_owner` | The owner of the object that is being added to the realm. If you add a role to a realm, the object owner of the role is shown as `%` (for all), because roles do not have owners.<br>To find the available users, query the `DBA_USERS` view.<br>To find the authorization of a particular user or role, query the `DVA_DV_REALM_AUTH` view. |
| `object_name`  | Object name. (The wildcard % is allowed.) You can also use the `DBMS_MACUTL.``G_ALL_OBJECT` constant.<br>To find the available objects, query the `ALL_OBJECTS` view.<br>To find objects that are secured by existing realms, query the `DBA_DV_REALM_OBJECT` view.                                                                          |
| `object_type`  | Object type, such as `TABLE`, `INDEX`, or `ROLE`. (The wildcard % is allowed.)<br>You can also use the `DBMS_MACUTL.``G_ALL_OBJECT` constant.                                                                                                                                                                                                |

#### Example

    BEGIN
     DBMS_MACADM.ADD_OBJECT_TO_REALM(
      realm_name    => 'HR Apps',
      object_owner  => '%',
      object_name   => 'HR_SELECT_ROLE',
      object_type   => 'ROLE');
    END;
    /

**Related Topics**

- [About Realm-Secured Objects](configuring-realms.md)

**Parent topic:** Oracle Database Vault Realm APIs

### 14.3 CREATE_REALM Procedure

The `CREATE_REALM` procedure creates a realm. In a multitenant environment, you can create both common and local realms.

After you create the realm, use the following procedures to complete the realm definition:

- `ADD_OBJECT_TO_REALM` procedure registers one or more objects for the realm.

- `ADD_AUTH_TO_REALM` procedure authorizes users or roles for the realm.

#### Syntax

    DBMS_MACADM.CREATE_REALM(
     realm_name    IN VARCHAR2,
     description   IN VARCHAR2,
     enabled       IN VARCHAR2,
     audit_options IN NUMBER,
     realm_type    IN NUMBER DEFAULT,
     realm_scope   IN NUMBER DEFAULT
     pl_sql_stack  IN BOOLEAN DEFAULT);

#### Parameters

Table 14-3 CREATE_REALM Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `realm_name`    | Realm name, up to 128 characters in mixed-case.<br>To find the existing realms in the current database instance, query the `DBA_DV_REALM` view, described in [DBA_DV_REALM View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `description`   | Description of the purpose of the realm, up to 1024 characters in mixed-case.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `enabled`       | Specify one of the following options to set the status of the realm:<br>• `DBMS_MACUTL.G_YES` or `‘y’` to enable realm checking (default)<br>• `DBMS_MACUTL.G_NO` or `‘n’` to disable all realm checking, including the capture of violations in the simulation log<br>• `DBMS_MACUTL.G_SIMULATION` or `‘s’` to enable SQL statements to execute but capture violations in the simulation log                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `audit_options` | Specify one of the following options to audit the realm:<br>• `DBMS_MACUTL.G_REALM_AUDIT_OFF`: Disables auditing for the realm (default)<br>• `DBMS_MACUTL.G_REALM_AUDIT_FAIL`: Creates an audit record when a realm violation occurs (for example, when an unauthorized user tries to modify an object that is protected by the realm)<br>• `DBMS_MACUTL.G_REALM_AUDIT_SUCCESS`: Creates an audit record for authorized activities on objects protected by the realm<br>• `DBMS_MACUTL.G_REALM_AUDIT_FAIL + DBMS_MACUTL.G_REALM_AUDIT_SUCCESS`: Creates an audit record for both authorized and unauthorized activities on objects protected by the realm<br>The `audit_options` parameter applies to traditional auditing only. If you have enabled unified auditing, then create a unified audit policy instead of using `audit_options`. |
| `realm_type`    | Specify one of the following options:<br>• `0`: Disables mandatory realm checking.<br>• `1`: Enables mandatory realm checking for realm objects. Only realm owners or realm participants will have access to objects in a realm. Object owners and object-privileged users who are not realm owners or participants will have no access.<br>See also [Mandatory Realms to Restrict User Access to Objects within a Realm](configuring-realms.md) for more information about mandatory realms.                                                                                                                                                                                                                                                                                                                                                |
| `realm_scope`   | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) if the realm must be local in the current PDB.<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2`) if the realm must be in the application root. This setting duplicates the realm in all of the associated PDBs.<br>If you create the common realm in an application root and want it visible to the associated PDBs, then you must synchronize the application. For example:<br>`ALTER PLUGGABLE DATABASE APPLICATION saas_sales_app SYNC;`                                                                                                                                                                                                                                        |
| `pl_sql_stack`  | When simulation mode is enabled, specifies whether to record the PL/SQL stack for failed operations. Enter `TRUE` to record the PL/SQL stack, `FALSE` to not record. The default is `FALSE`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

#### Examples

The following example shows how to create a realm that is enabled, has auditing set to track both failed and successful access, uses mandatory realm checking, and records the PL/SQL stack.

    BEGIN
     DBMS_MACADM.CREATE_REALM(
      realm_name     => 'HR Apps',
      description    => 'Realm to protect the HR schema',
      enabled        => DBMS_MACUTL.G_YES,
      audit_options  => DBMS_MACUTL.G_REALM_AUDIT_OFF,
      realm_type     => 1,
      pl_sql_stack   => TRUE);
    END;
    /

This example shows how to create a variation of the preceding example, but as a common realm located in the application root. The user who creates this realm must be a common user and must execute the procedure in the application root.

    BEGIN
     DBMS_MACADM.CREATE_REALM(
      realm_name     => 'HR Apps',
      description    => 'Realm to protect the HR schema',
      enabled        => DBMS_MACUTL.G_YES,
      audit_options  => DBMS_MACUTL.G_REALM_AUDIT_OFF,
      realm_type     => 1,
      realm_scope    => DBMS_MACUTL.G_SCOPE_COMMON);
    END;
    /

This example shows how to create a local version of the preceding example. The user who creates this realm must be in the PDB in which the realm will reside. To find existing PDBs, query the `DBA_PDBS` data dictionary view.

    BEGIN
     DBMS_MACADM.CREATE_REALM(
      realm_name     => 'HR Apps',
      description    => 'Realm to protect the HR schema',
      enabled        => DBMS_MACUTL.G_YES,
      audit_options  => DBMS_MACUTL.G_REALM_AUDIT_OFF,
      realm_type     => 1,
      realm_scope    => DBMS_MACUTL.G_SCOPE_LOCAL);
    END;
    /

**See Also:**

[Example 20-1](oracle-database-vault-utility-apis.md)

**Parent topic:** Oracle Database Vault Realm APIs

### 14.4 DELETE_AUTH_FROM_REALM Procedure

The `DELETE_AUTH_FROM_REALM` procedure removes the authorization of a user or role to access a realm.

#### Syntax

    DBMS_MACADM.DELETE_AUTH_FROM_REALM(
     realm_name    IN VARCHAR2,
     grantee       IN VARCHAR2,
     auth_scope    IN NUMBER DEFAULT);

#### Parameters

Table 14-4 DELETE_AUTH_FROM_REALM Parameters

| Parameter    | Description                                                                                                                                                                                                                                                                                                           |
|:-------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `realm_name` | Realm name.<br>To find the existing realms in the current database instance, query the `DBA_DV_REALM` view, described in [DBA_DV_REALM View](oracle-database-vault-data-dictionary-views.md)                                                                                                                          |
| `grantee`    | User or role name.<br>To find the authorization of a particular user or role, query the `DVA_DV_REALM_AUTH` view, described in [DBA_DV_REALM_AUTH View](oracle-database-vault-data-dictionary-views.md).                                                                                                              |
| `auth_scope` | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) if the realm was authorized locally in the current PDB<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2` if the realm was authorized in the application root |

#### Example

    BEGIN
    DBMS_MACADM.DELETE_AUTH_FROM_REALM(
     realm_name     => 'HR Apps',
     grantee        => 'PSMITH',
     auth_scope     => DBMS_MACUTL.G_SCOPE_LOCAL);
    END;
    /

**Parent topic:** Oracle Database Vault Realm APIs

### 14.5 DELETE_OBJECT_FROM_REALM Procedure

The `DELETE_OBJECT_FROM_REALM` procedure removes a set of objects from realm protection.

#### Syntax

    DBMS_MACADM.DELETE_OBJECT_FROM_REALM(
      realm_name   IN VARCHAR2,
      object_owner IN VARCHAR2,
      object_name  IN VARCHAR2,
      object_type  IN VARCHAR2);

#### Parameters

Table 14-5 DELETE_OBJECT_FROM_REALM Parameters

| Parameter      | Description                                                                                                                                                                                                                                                                                                                                                                                                 |
|:---------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `realm_name`   | Realm name.<br>To find the existing realms in the current database instance, query the `DBA_DV_REALM` view, described in [DBA_DV_REALM View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                               |
| `object_owner` | The owner of the object that was added to the realm.<br>To find the available users, query the `DBA_USERS` view, described in [Oracle Database Reference](../refrn/DBA_USERS.md).                                                                                                                                                                                                                           |
| `object_name`  | Object name. (The wildcard % is allowed. See "Object Name" under [About Realm-Secured Objects](configuring-realms.md) for exceptions to the wildcard %.) You can also use the `DBMS_MACUTL.``G_ALL_OBJECT` constant.<br>To find objects that are secured by existing realms, query the `DBA_DV_REALM_OBJECT` view, described in [DBA_DV_REALM_OBJECT View](oracle-database-vault-data-dictionary-views.md). |
| `object_type`  | Object type, such as `TABLE`, `INDEX`, or `ROLE`. (The wildcard % is allowed. See "Object Types" under [About Realm-Secured Objects](configuring-realms.md) for exceptions to the wildcard %.)<br>You can also use the `DBMS_MACUTL.``G_ALL_OBJECT` constant.                                                                                                                                               |

#### Example

    BEGIN
     DBMS_MACADM.DELETE_OBJECT_FROM_REALM(
      realm_name   => 'Performance Statistics Realm',
      object_owner => 'SYS',
      object_name  => 'GATHER_SYSTEM_STATISTICS',
      object_type  => 'ROLE');
    END;
    /

**Parent topic:** Oracle Database Vault Realm APIs

### 14.6 DELETE_REALM Procedure

The `DELETE_REALM` procedure deletes a realm, including its related configuration information that specifies who is authorized and what objects are protected.

This procedure does not delete the actual database objects or users.

To find users who are authorized for the realm, query the `DBA_DV_REALM_AUTH` view. To find the objects that are protected by the realm, query the `DBA_DV_REALM_OBJECT` view. These views are described in [Oracle Database Vault Data Dictionary Views](oracle-database-vault-data-dictionary-views.md).

#### Syntax

    DBMS_MACADM.DELETE_REALM(
      realm_name IN VARCHAR2);

#### Parameters

Table 14-6 DELETE_REALM Parameter

| Parameter    | Description                                                                                                                                                                                   |
|:-------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `realm_name` | Realm name.<br>To find the existing realms in the current database instance, query the `DBA_DV_REALM` view, described in [DBA_DV_REALM View](oracle-database-vault-data-dictionary-views.md). |

#### Example

    EXEC DBMS_MACADM.DELETE_REALM('Performance Statistics Realm');

**Parent topic:** Oracle Database Vault Realm APIs

### 14.7 DELETE_REALM_CASCADE Procedure

The `DELETE_REALM_CASCADE` procedure deletes a realm, including its related Database Vault configuration information that specifies who is authorized and the objects that are protected.

The `DBA_DV_REALM_AUTH` view lists who is authorized in the realm and the `DBA_DV_REALM_OBJECT` view lists the protected objects.

It does not delete the actual database objects or users. This procedure works the same as the `DELETE_REALM` procedure. (In previous releases, these procedures were different, but now they are the same. Both are retained for earlier compatibility.) To find a listing of the realm-related objects, query the `DBA_DV_REALM` view. To find its authorizations, query `DBA_DV_REALM_AUTH`. Both are described under [Oracle Database Vault Data Dictionary Views](oracle-database-vault-data-dictionary-views.md).

#### Syntax

    DBMS_MACADM.DELETE_REALM_CASCADE(
      realm_name IN VARCHAR2);

#### Parameters

Table 14-7 DELETE_REALM_CASCADE Parameter

| Parameter    | Description                                                                                                                                                                                   |
|:-------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `realm_name` | Realm name.<br>To find the existing realms in the current database instance, query the `DBA_DV_REALM` view, described in [DBA_DV_REALM View](oracle-database-vault-data-dictionary-views.md). |

#### Example

    EXEC DBMS_MACADM.DELETE_REALM_CASCADE('Performance Statistics Realm');

**Parent topic:** Oracle Database Vault Realm APIs

### 14.8 RENAME_REALM Procedure

The `RENAME_REALM` procedure renames a realm; the name change takes effect everywhere the realm is used.

#### Syntax

    DBMS_MACADM.RENAME_REALM(
     realm_name  IN VARCHAR2,
     new_name    IN VARCHAR2);

#### Parameters

Table 14-8 RENAME_REALM Parameters

| Parameter    | Description                                                                                                                                                                                           |
|:-------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `realm_name` | Current realm name.<br>To find the existing realms in the current database instance, query the `DBA_DV_REALM` view, described in [DBA_DV_REALM View](oracle-database-vault-data-dictionary-views.md). |
| `new_name`   | New realm name, up to 128 characters in mixed-case.                                                                                                                                                   |

#### Example

    BEGIN
     DBMS_MACADM.RENAME_REALM(
      realm_name => 'Performance Statistics Realm',
      new_name   => 'Sector 2 Performance Statistics Realm');
    END;
    /

**Parent topic:** Oracle Database Vault Realm APIs

### 14.9 UPDATE_REALM Procedure

The `UPDATE_REALM` procedure updates a realm.

To find information about the current settings for a realm, query the `DVSYS.DV$REALM` view, described in [DVSYS.DV\$REALM View](oracle-database-vault-data-dictionary-views.md).

#### Syntax

    DBMS_MACADM.UPDATE_REALM(
     realm_name    IN VARCHAR2,
     description   IN VARCHAR2,
     enabled       IN VARCHAR2,
     audit_options IN NUMBER DEFAULT NULL,
     realm_type    IN NUMBER DEFAULT NULL
     pl_sql_stack  IN BOOLEAN DEFAULT NULL);

#### Parameters

Table 14-9 UPDATE_REALM Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `realm_name`    | Realm name.<br>To find the existing realms in the current database instance, query the `DBA_DV_REALM` view, described in [DBA_DV_REALM View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `description`   | Description of the purpose of the realm, up to 1024 characters in mixed-case.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `enabled`       | Specify one of the following options to set the status of the realm:<br>• `DBMS_MACUTL.G_YES` or `‘y’` to enable realm checking<br>• `DBMS_MACUTL.G_NO` or `‘n’` to disable all realm checking, including the capture of violations in the simulation log<br>• `DBMS_MACUTL.G_SIMULATION` or `‘s’` to enable SQL statements to execute but capture violations in the simulation log<br>The default for `enabled` is the previously set value, which you can find by querying the `DBA_DV_REALM` data dictionary view.                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `audit_options` | Specify one of the following options to audit the realm:<br>• `DBMS_MACUTL.G_REALM_AUDIT_OFF`: Disables auditing for the realm<br>• `DBMS_MACUTL.G_REALM_AUDIT_FAIL`: Creates an audit record when a realm violation occurs (for example, when an unauthorized user tries to modify an object that is protected by the realm<br>• `DBMS_MACUTL.G_REALM_AUDIT_SUCCESS`: Creates an audit record for authorized activities on objects protected by the realm.<br>• `DBMS_MACUTL.G_REALM_AUDIT_FAIL + DBMS_MACUTL.G_REALM_AUDIT_SUCCESS`: Creates an audit record for both authorized and unauthorized activities on objects protected by the realm<br>The default for `audit_options` is the previously set value, which you can find by querying the `DBA_DV_REALM` data dictionary view.<br>The `audit_options` parameter applies to traditional auditing only. If you have enabled unified auditing, then create a unified audit policy instead of using `audit_options`. |
| `realm_type`    | If you do not specify the `realm_type` parameter, then Oracle Database Vault does not update the current `realm_type` setting.<br>Specify one of the following options:<br>• `0`: Sets the realm to be a regular realm, which does not have mandatory realm checking.<br>• `1`: Enables mandatory realm checking for realm objects. Only realm owners or realm participants will have access to objects in a realm. Object owners and object-privileged users who are not realm owners or participants will have no access.<br>See also [Mandatory Realms to Restrict User Access to Objects within a Realm](configuring-realms.md) for more information about mandatory realms.                                                                                                                                                                                                                                                                                           |
| `pl_sql_stack`  | When simulation mode is enabled, indicates whether the PL/SQL stack has been recorded for failed operations. `TRUE` indicates that the PL/SQL stack has been recorded; `FALSE` indicates that the PL/SQL stack has not been recorded.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

#### Example

    BEGIN
     DBMS_MACADM.UPDATE_REALM(
      realm_name    => 'Sector 2 Performance Statistics Realm',
      description   => 'Realm to measure performance for Sector 2 applications',
      enabled       => DBMS_MACUTL.G_YES,
      audit_options => DBMS_MACUTL.G_REALM_AUDIT_FAIL + DBMS_MACUTL.G_REALM_AUDIT_SUCCESS),
      realm_type    => 1);
    END;
    /

**Parent topic:** Oracle Database Vault Realm APIs

### 14.10 UPDATE_REALM_AUTH Procedure

The `UPDATE_REALM_AUTH` procedure updates the authorization of a user or role to access a realm.

#### Syntax

    DBMS_MACADM.UPDATE_REALM_AUTH(
     realm_name    IN VARCHAR2,
     grantee       IN VARCHAR2,
     rule_set_name IN VARCHAR2,
     auth_options  IN NUMBER,
     auth_scope    IN NUMBER DEFAULT);

#### Parameters

Table 14-10 UPDATE_REALM_AUTH Parameters

| Parameter       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `realm_name`    | Realm name.<br>To find the existing realms in the current database instance, query the `DBA_DV_REALM` view, described in [DBA_DV_REALM View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `grantee`       | User or role name.<br>To find the available users and roles in the current database instance, query the [`DBA_USERS`](../refrn/DBA_USERS.md) and [`DBA_ROLES`](../refrn/DBA_ROLES.md) views, described in Oracle Database Reference.<br>To find the authorization of a particular user or role, query the `DVA_DV_REALM_AUTH` view, described in [DBA_DV_REALM_AUTH View](oracle-database-vault-data-dictionary-views.md).<br>To find existing secure application roles used in privilege management, query the `DBA_DV_ROLE` view, described in [DBA_DV_ROLE View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                                                                                                    |
| `rule_set_name` | Optional. A rule set to check during runtime. The realm authorization is enabled only if the rule set evaluates to `TRUE`.<br>To find the available rule sets, query the `DBA_DV_RULE_SET` view. To find rules that are associated with the rule sets, query the `DBA_DB_RULE_SET_RULE` view. Both are described in [Oracle Database Vault Data Dictionary Views](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `auth_options`  | Optional. Specify one of the following options to authorize the realm:<br>• `DBMS_MACUTL.G_REALM_AUTH_PARTICIPANT`: Participant. This account or role provides system or direct privileges to access, manipulate, and create objects protected by the realm, provided these rights have been granted using the standard Oracle Database privilege grant process.<br>• `DBMS_MACUTL.G_REALM_AUTH_OWNER`: Owner. This account or role has the same authorization as the realm participant, plus the authorization to grant or revoke realm-secured roles and privileges on realm-protected objects. A realm can have multiple owners.<br>The default for `auth_options` value is the previously set value, which you can find by querying the `DBA_DV_REALM_AUTH` data dictionary view.<br>The `audit_options` parameter applies to traditional auditing only. If you have enabled unified auditing, then create a unified audit policy instead of using `audit_options`. |
| `realm_auth`    | For a multitenant environment, determines how to execute this procedure. The default is local. Options are as follows:<br>• `DBMS_MACUTL.G_SCOPE_LOCAL` (or `1`) if the realm is authorized locally in the current PDB<br>• `DBMS_MACUTL.G_SCOPE_COMMON` (or `2`) if the realm is authorized in the application root                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |

#### Example

    BEGIN
     DBMS_MACADM.UPDATE_REALM_AUTH(
      realm_name    => 'Sector 2 Performance Statistics Realm',
      grantee       => 'SYSADM',
      rule_set_name => 'Check Conf Access',
      auth_options  => DBMS_MACUTL.G_REALM_AUTH_OWNER);
    END;
    /

**Parent topic:** Oracle Database Vault Realm APIs
