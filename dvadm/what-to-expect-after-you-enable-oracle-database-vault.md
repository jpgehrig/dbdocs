When you enable Oracle Database Vault, several Oracle Database security features, such as default user authorizations, are modified to provide stronger security restrictions.

- Initialization and Password Parameter Settings That Change
  The Oracle Database Vault configuration modifies several database initialization parameter settings to better secure your database configuration.
- How Oracle Database Vault Restricts User Authorizations
  Oracle Database Vault restricts user authorizations through the revocation of system and object privileges, the separation of responsibilities through new database roles, and the enforcement of new controls by Oracle Database Vault realms, command rules, and authorizations.
- Oracle Database Vault-Specific Database Roles to Enforce Separation of Duties
  The Oracle Database Vault configuration implements the concept of separation of duty so that you can improve security and meet regulatory, privacy, and other compliance requirements.
- Privileges That Are Revoked from Existing Users and Roles
  The Oracle Database Vault configuration revokes privileges from several Oracle Database-supplied users and roles, for better separation of duty.
- Privileges That Are Prevented for Existing Users and Roles
  The Oracle Database Vault configuration prevents several privileges for all users and roles who have been granted these privileges, including users `SYS` and `SYSTEM`.
- Modified AUDIT Statement Settings for a Non-Unified Audit Environment
  When you configure Oracle Database Vault and if you decide not to use unified auditing, then Database Vault configures several `AUDIT` statements.

### 2.1 Initialization and Password Parameter Settings That Change

The Oracle Database Vault configuration modifies several database initialization parameter settings to better secure your database configuration.

If these changes will affect your organizational processes or database maintenance procedures, then contact Oracle Support for help in resolving the issue.

Table 2-1 describes the initialization parameter settings that Oracle Database Vault modifies. Initialization parameters are stored in the `init.ora` initialization parameter file. See [Oracle Database Reference](../refrn/initialization-parameters-2.md) for more information about initialization parameters.

Table 2-1 Modified Database Initialization Parameter Settings

| Parameter                   | Default Value in Database | New Value Set by Database Vault | Impact of the Change                                                                                                                                                                                                                                                                                                                                                                                                                 |
|:----------------------------|:--------------------------|:--------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `AUDIT_SYS_OPERATIONS`      | `FALSE`                   | `TRUE`                          | Enables the auditing of top-level operations directly issued by user `SYS`, and users connecting with `SYSDBA` or `SYSOPER` privilege.                                                                                                                                                                                                                                                                                               |
| `OS_ROLES`                  | Not configured            | `FALSE`                         | Disables the operating system to completely manage the granting and revoking of roles to users. Any previous grants of roles to users using `GRANT` statements do not change, because they are still listed in the data dictionary. Only the role grants made at the operating system-level to users apply. Users can still grant privileges to roles and users.                                                                     |
| `REMOTE_LOGIN_PASSWORDFILE` | `EXCLUSIVE`               | `EXCLUSIVE`                     | Specifies whether Oracle Database checks for a password file. The `EXCLUSIVE` setting enforces the use of the password file, if you installed Oracle Database Vault into a database where `REMOTE_LOGIN_PASSWORDFILE` is not set to `EXCLUSIVE`.                                                                                                                                                                                     |
| `SQL92_SECURITY`            | `TRUE`                    | `TRUE`                          | Ensures that if a user has been granted the `UPDATE` or `DELETE` object privilege, then the user must also be granted the `SELECT` object privilege before being able to perform `UPDATE` or `DELETE` operations on tables that have `WHERE` or `SET` clauses.<br>Be aware that if the user is only granted the `READ` object privilege (instead of `SELECT`), then the user is not able to perform `UPDATE` or `DELETE` operations. |

**Parent topic:** What to Expect After You Enable Oracle Database Vault

### 2.2 How Oracle Database Vault Restricts User Authorizations

Oracle Database Vault restricts user authorizations through the revocation of system and object privileges, the separation of responsibilities through new database roles, and the enforcement of new controls by Oracle Database Vault realms, command rules, and authorizations.

In addition, several database roles are created. These roles are part of the separation of duties provided by Oracle Database Vault. One common audit problem that has affected several large organizations is the unauthorized creation of new database accounts by a database administrator within a production instance. Upon installation, Oracle Database Vault prevents anyone other than the Oracle Database Vault account manager or a user granted the Oracle Database Vault account manager role from creating users in the database.

**Related Topics**

- [Separation of Duty Guidelines](oracle-database-vault-security-guidelines.md)

**Parent topic:** What to Expect After You Enable Oracle Database Vault

### 2.3 Oracle Database Vault-Specific Database Roles to Enforce Separation of Duties

The Oracle Database Vault configuration implements the concept of separation of duty so that you can improve security and meet regulatory, privacy, and other compliance requirements.

Oracle Database Vault makes clear separation between the account management responsibility, data security responsibility, and database management responsibility inside the database. This means that the concept of a super-privileged role (for example, `DBA`) is divided among several new database roles to ensure no one user has full control over both the data and configuration of the system. Oracle Database Vault prevents privileged users (those with the `DBA` and other privileged roles and system privileges) from accessing designated protected areas of the database called realms. It also introduces new database roles called the Oracle Database Vault Owner (`DV_OWNER`) and the Oracle Database Vault Account Manager (`DV_ACCTMGR`). These new database roles separate the data security and the account management from the traditional `DBA` role. You should map these roles to distinct security professionals within your organization.

**Related Topics**

- [Separation of Duty Guidelines](oracle-database-vault-security-guidelines.md)
- [Oracle Database Vault Roles](oracle-database-vault-schemas-roles-and-accounts.md)

**Parent topic:** What to Expect After You Enable Oracle Database Vault

### 2.4 Privileges That Are Revoked from Existing Users and Roles

The Oracle Database Vault configuration revokes privileges from several Oracle Database-supplied users and roles, for better separation of duty.

Table 2-2 lists privileges that Oracle Database Vault revokes from the Oracle Database-supplied users and roles. Be aware that if you disable Oracle Database Vault, these privileges remain revoked. If your applications depend on these privileges, then grant them to application owner directly. In a multitenant environment, these privileges are revoked from the users and roles in the CDB root and its PDBs and from the application root and its PDBs.

Table 2-2 Privileges Oracle Database Vault Revokes

| User or Role                              | Privilege That Is Revoked                                                                                                                                                                                                                            |
|:------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DBA` role                                | • `BECOME USER`<br>• `SELECT ANY TRANSACTION`<br>• `CREATE ANY JOB`<br>• `CREATE EXTERNAL JOB`<br>• `EXECUTE ANY PROGRAM`<br>• `EXECUTE ANY CLASS`<br>• `MANAGE SCHEDULER`<br>• `DEQUEUE ANY QUEUE`<br>• `ENQUEUE ANY QUEUE`<br>• `MANAGE ANY QUEUE` |
| `IMP_FULL_DATABASE` role<sup>Foot 1</sup> | • `BECOME USER`<br>• `MANAGE ANY QUEUE`                                                                                                                                                                                                              |
| `EXECUTE_CATALOG_ROLE` role               | • `EXECUTE ON SYS.DBMS_LOGMNR_D`<br>• `EXECUTE ON SYS.DBMS_LOGMNR_LOGREP_DICT`<br>• `EXECUTE ON SYS.DBMS_FILE_TRANSFER`<br>• `EXECUTE ON SYS.DBMS_LOGMNR`                                                                                            |
| `PUBLIC` user                             | • `EXECUTE ON UTL_FILE` during the execution of the `CONFIGURE_DV` procedure, but before this revocation takes place, `CONFIGURE_DV` grants the object privilege directly to any schema that is dependent on this procedure                          |
| `SCHEDULER_ADMIN` role<sup>Foot 2</sup>   | • `CREATE ANY JOB`<br>• `CREATE EXTERNAL JOB`<br>• `EXECUTE ANY PROGRAM`<br>• `EXECUTE ANY CLASS`<br>• `MANAGE SCHEDULER`                                                                                                                            |

<sup>Footnote 1</sup>

To authorize users to export and import data using Oracle Data Pump, see [Using Oracle Data Pump with Oracle Database Vault](dba-operations-in-an-oracle-database-vault-environment.md).

<sup>Footnote 2</sup>

To authorize users to schedule database jobs, see [Using Oracle Scheduler with Oracle Database Vault](dba-operations-in-an-oracle-database-vault-environment.md).

**Note:**

Both the `SYS` and `SYSTEM` users retain the `SELECT` privilege for the `DBA_USERS_WITH_DEFPWD` data dictionary view, which lists user accounts that use default passwords. If you want other users to have access to this view, grant them the `SELECT` privilege on it.

**Related Topics**

- [Privileges of Oracle Database Vault Roles](oracle-database-vault-schemas-roles-and-accounts.md)
- [DV_ACCTMGR Database Vault Account Manager Role](oracle-database-vault-schemas-roles-and-accounts.md)

**Parent topic:** What to Expect After You Enable Oracle Database Vault

### 2.5 Privileges That Are Prevented for Existing Users and Roles

The Oracle Database Vault configuration prevents several privileges for all users and roles who have been granted these privileges, including users `SYS` and `SYSTEM`.

The `DV_ACCTMGR` role has these privileges for separation of duty:

- `ALTER PROFILE`

- `ALTER USER`

- `CREATE PROFILE`

- `CREATE USER`

- `DROP PROFILE`

- `DROP USER`

For better security and to maintain separation-of-duty standards, do not enable `SYS` or `SYSTEM` users the ability to create or manage user accounts.

Any role can be granted to user `SYS`, but `SYS` cannot use the role because no roles are enabled in the `SYS` session.

**Parent topic:** What to Expect After You Enable Oracle Database Vault

### 2.6 Modified AUDIT Statement Settings for a Non-Unified Audit Environment

When you configure Oracle Database Vault and if you decide not to use unified auditing, then Database Vault configures several `AUDIT` statements.

**Related Topics**

- [Oracle Database Audit Settings Created for Oracle Database Vault](auditing-oracle-database-vault.md)

**Parent topic:** What to Expect After You Enable Oracle Database Vault
