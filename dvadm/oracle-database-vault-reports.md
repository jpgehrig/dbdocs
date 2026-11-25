Oracle Database Vault provides reports that track activities, such as the Database Vault configuration settings.

- About the Oracle Database Vault Reports
  Oracle Database Vault provides reports that display security-related information from the database.
- Who Can Run the Oracle Database Vault Reports?
  Users must have the `DV_OWNER`, `DV_ADMIN`, or `DV_SECANALYST` role before they can run the Oracle Database Vault reports.
- Running the Oracle Database Vault Reports
  A user who has been granted the appropriate roles can run the Oracle Database Vault reports from Database Vault Administrator.
- Oracle Database Vault Configuration Issues Reports
  The configuration issues reports track the settings for command rules, rule sets, realms, and other Oracle Database Vault configurations.
- Oracle Database Vault Auditing Reports
  If you have unified auditing enabled, then the Oracle Database Vault audit reports capture the results of unified audit policies.
- Oracle Database Vault General Security Reports
  The general security reports track information such as object privileges related to `PUBLIC` or privileges granted to a database account or role.

### 26.1 About the Oracle Database Vault Reports

Oracle Database Vault provides reports that display security-related information from the database.

These reports also show custom Oracle Database Vault audit event information. If you have unified auditing enabled, then the reports capture the results of your unified audit policies.

The reports are in two categories:

- Database Vault Reports. These reports allow you to check configuration issues with realms, command rules, factors, factor identities, rule sets, and secure application roles. These reports also reveal realm violations, auditing results, and so on.

- General Security Reports. These reports allow you to check the status of object privileges, database account system privileges, sensitive objects, privilege management, powerful database accounts and roles, initialization parameters, profiles, account passwords, security audits, and other security vulnerability reports.

**Related Topics**

- [Oracle Database Vault-Specific Reports in Enterprise Manager Cloud Control](dba-operations-in-an-oracle-database-vault-environment.md)
- [Oracle Database Vault Data Dictionary Views](oracle-database-vault-data-dictionary-views.md)

**Parent topic:** Oracle Database Vault Reports

### 26.2 Who Can Run the Oracle Database Vault Reports?

Users must have the `DV_OWNER`, `DV_ADMIN`, or `DV_SECANALYST` role before they can run the Oracle Database Vault reports.

**Related Topics**

- [DV_OWNER Database Vault Owner Role](oracle-database-vault-schemas-roles-and-accounts.md)
- [DV_ADMIN Database Vault Configuration Administrator Role](oracle-database-vault-schemas-roles-and-accounts.md)
- [DV_SECANALYST Database Vault Security Analyst Role](oracle-database-vault-schemas-roles-and-accounts.md)

**Parent topic:** Oracle Database Vault Reports

### 26.3 Running the Oracle Database Vault Reports

A user who has been granted the appropriate roles can run the Oracle Database Vault reports from Database Vault Administrator.

1.  Log in to Oracle Database Vault Administrator from Cloud Control as a user who has been granted the `DV_OWNER`, `DV_ADMIN`, or `DV_SECANALYST` role and the `SELECT ANY DICTIONARY` privilege. [Logging in to Oracle Database Vault from Oracle Enterprise Cloud Control](getting-started-with-oracle-database-vault.md) explains how to log in.
2.  In the Home page, under Reports, select Database Vault Reports.
3.  On the left side, select the category of reports that you want.
    - Database Vault Configuration Issues

    - Database Vault Enforcement Audit Reports

    - Database Vault Configuration Changes
4.  In the Reports page, expand the category that contains the report.
    For example, to find the Rule Set Configurations Issues report, you must expand Database Vault Configuration Issues.
5.  Select the report (for example, Rule Set Configuration Issues).
    The report appears in the right pane.
6.  Optionally, use the Search field to filter the report.
    For example, you can search for reported incidents that involve a specific rule set. The Search field contents vary depending on the report.
7.  When you finished viewing the report, click the OK button.

**Parent topic:** Oracle Database Vault Reports

### 26.4 Oracle Database Vault Configuration Issues Reports

The configuration issues reports track the settings for command rules, rule sets, realms, and other Oracle Database Vault configurations.

- Command Rule Configuration Issues Report
  The Command Rule Configuration Issues Report displays command rules that have configuration issues.
- Rule Set Configuration Issues Report
  The Rule Set Configuration Issues Report displays Oracle Database Vault rule set configuration issues.
- Realm Authorization Configuration Issues Report
  The Realm Authorization Configuration Issues Report displays Oracle Database Vault realm configuration issues.
- Factor Configuration Issues Report
  The Factor Configuration Issues Report displays Oracle Database Vault factors configuration issues.
- Factor Without Identities Report
  The Factor Without Identities Report displays Oracle Database Vault factors that have no identities configured.
- Identity Configuration Issues Report
  The Identity Configuration Issues Report displays Oracle Database Vault factor identity configuration issues.
- Secure Application Configuration Issues Report
  The Secure Application Configuration Issues Report displays Database Vault secure application role configuration issues.

**Parent topic:** Oracle Database Vault Reports

#### 26.4.1 Command Rule Configuration Issues Report

The Command Rule Configuration Issues Report displays command rules that have configuration issues.

These issues are as follows:

- Rule set for the command rule is disabled.

- Rule set for the command rule is incomplete.

- Object owner for the command rule does not exist. This can happen when the user account for the object has been dropped.

**Parent topic:** Oracle Database Vault Configuration Issues Reports

#### 26.4.2 Rule Set Configuration Issues Report

The Rule Set Configuration Issues Report displays Oracle Database Vault rule set configuration issues.

This report tracks when no rules are defined or enabled for a rule set.

**Parent topic:** Oracle Database Vault Configuration Issues Reports

#### 26.4.3 Realm Authorization Configuration Issues Report

The Realm Authorization Configuration Issues Report displays Oracle Database Vault realm configuration issues.

These issues are as follows:

- Rule set for a realm authorization is disabled.

- Grantee does not exist for a realm authorization.

- Owner does not exist for a realm-secured object. This can happen when the user account has been dropped.

In most cases, however, these types of issues are caught when you configure the realm and during validation.

**Parent topic:** Oracle Database Vault Configuration Issues Reports

#### 26.4.4 Factor Configuration Issues Report

The Factor Configuration Issues Report displays Oracle Database Vault factors configuration issues.

These issues are as follows:

- Rule set for factor assignment is disabled.

- Rule set for factor assignment is incomplete.

- Audit options for the factor are invalid.

- No factor retrieval method or constant exists.

- No subfactors (that is, child factors) are linked to a factor identity.

- No subfactors (child factors) are linked to a label factor.

- Oracle Label Security policy does not exist for the factor.

**Parent topic:** Oracle Database Vault Configuration Issues Reports

#### 26.4.5 Factor Without Identities Report

The Factor Without Identities Report displays Oracle Database Vault factors that have no identities configured.

For some factors such as `Background_Job_Id`, this may not be a real problem, but the report can help you determine whether your access control configuration is complete and whether you have accounted for all factor configuration.

**Parent topic:** Oracle Database Vault Configuration Issues Reports

#### 26.4.6 Identity Configuration Issues Report

The Identity Configuration Issues Report displays Oracle Database Vault factor identity configuration issues.

These issues are as follows:

- Label identity for the Oracle Label Security label for this identity has been removed and no longer exists.

- No map exists for the identity.

**Parent topic:** Oracle Database Vault Configuration Issues Reports

#### 26.4.7 Secure Application Configuration Issues Report

The Secure Application Configuration Issues Report displays Database Vault secure application role configuration issues.

These issues are as follows:

- The database role does not exist. This can happen when the database role has been dropped.

- The rule set for role is disabled.

- The rule set for role is incomplete.

**Parent topic:** Oracle Database Vault Configuration Issues Reports

### 26.5 Oracle Database Vault Auditing Reports

If you have unified auditing enabled, then the Oracle Database Vault audit reports capture the results of unified audit policies.

- Realm Audit Report
  The Realm Audit Report shows audit records generated by the realm protection and realm authorization operations.
- Command Rule Audit Report
  The Command Rule Audit Report shows audit records generated by command rule processing operations.
- Factor Audit Report
  The Factor Audit Report shows factors that failed to evaluate or were set to create audit records under various conditions.
- Label Security Integration Audit Report
  The Label Security Integration Audit Report shows audit records the session initialization operation generates and the session label assignment operation of label security.
- Core Database Vault Audit Trail Report
  The Core Database Vault Audit Trail Report shows audit records that the core access security session initialization operation generates.
- Secure Application Role Audit Report
  The Secure Application Role Audit Report shows the audit records that the Oracle Database Vault secure application role-enabling operation generates.

**Parent topic:** Oracle Database Vault Reports

#### 26.5.1 Realm Audit Report

The Realm Audit Report shows audit records generated by the realm protection and realm authorization operations.

You can manage realm authorizations by using rule sets, and then audit the rule set processing results. A realm violation occurs when the database account, performing an action on a realm-protected object, is not authorized to perform that action. Oracle Database Vault audits the violation even if you do not specify any rule sets attached to the realm. When you configure a realm, you can set it to audit instances of realm violations. You can use this information to investigate attempts to break security.

**Parent topic:** Oracle Database Vault Auditing Reports

#### 26.5.2 Command Rule Audit Report

The Command Rule Audit Report shows audit records generated by command rule processing operations.

When you configure a command rule, you can set it to audit the rule set processing results.

**Parent topic:** Oracle Database Vault Auditing Reports

#### 26.5.3 Factor Audit Report

The Factor Audit Report shows factors that failed to evaluate or were set to create audit records under various conditions.

This report also shows failed attempts to set factors.

You can audit instances where a factor identity cannot be resolved and assigned (such as No data found or Too many rows). A factor can have an associated rule set that assigns an identity to the factor at run time. When you configure a factor, you can set it to audit the rule set processing results.

**Parent topic:** Oracle Database Vault Auditing Reports

#### 26.5.4 Label Security Integration Audit Report

The Label Security Integration Audit Report shows audit records the session initialization operation generates and the session label assignment operation of label security.

You can audit instances where the label security session fails to initialize, and where the label security component prevents a session from setting a label that exceeds the maximum session label.

**Parent topic:** Oracle Database Vault Auditing Reports

#### 26.5.5 Core Database Vault Audit Trail Report

The Core Database Vault Audit Trail Report shows audit records that the core access security session initialization operation generates.

You can audit instances where the access security session fails to initialize. It displays the following data:

| Data A-R        | Data R-U  |
|:----------------|:----------|
| Account         | Rule Set  |
| Command         | Timestamp |
| Instance Number | Rule Set  |
| Object Name     | User Host |
| Return Code     | \-        |

**Parent topic:** Oracle Database Vault Auditing Reports

#### 26.5.6 Secure Application Role Audit Report

The Secure Application Role Audit Report shows the audit records that the Oracle Database Vault secure application role-enabling operation generates.

**Related Topics**

- [Configuring Secure Application Roles for Oracle Database Vault](configuring-secure-application-roles-for-oracle-database-vault.md)

**Parent topic:** Oracle Database Vault Auditing Reports

### 26.6 Oracle Database Vault General Security Reports

The general security reports track information such as object privileges related to `PUBLIC` or privileges granted to a database account or role.

- Object Privilege Reports
  The object privilege reports track privileges affected by `PUBLIC`, direct object privileges, and object dependencies.
- Database Account System Privileges Reports
  The database account system privileges reports track activities such as direct, indirect, hierarchical, and `ANY` system privileges.
- Sensitive Objects Reports
  The sensitive objects reports track activities such as grants on the `EXECUTE` privilege on `SYS` schema objects and access to sensitive objects.
- Privilege Management - Summary Reports
  The privilege management summary reports track privilege distribution by grantees, owners, and privileges.
- Powerful Database Accounts and Roles Reports
  The powerful database accounts and roles reports track information about users who have been granted power privileges, such as the `WITH ADMIN` privilege.
- Initialization Parameters and Profiles Reports
  The initialization parameters and profiles reports track database parameters, resource profiles, and system limits.
- Database Account Password Reports
  The database account password reports track default passwords and account statuses of database accounts.
- Security Audit Report: Core Database Audit Report
  The Core Database Audit Report lists database audit trail records..
- Other Security Vulnerability Reports
  Other security vulnerability reports track vulnerabilities that arise with activities such as Java policy grants ir operating system directory objects.

**Parent topic:** Oracle Database Vault Reports

#### 26.6.1 Object Privilege Reports

The object privilege reports track privileges affected by `PUBLIC`, direct object privileges, and object dependencies.

- Object Access By PUBLIC Report
  The Object Access By PUBLIC Report lists all objects whose access has been granted to `PUBLIC`.
- Object Access Not By PUBLIC Report
  The Object Access Not By PUBLIC Report describes the object access used by the database accounts on the Report Parameters page.
- Direct Object Privileges Report
  The Direct Object Privileges Report shows the direct object privileges granted to nonsystem database accounts.
- Object Dependencies Report
  The Object Dependencies Report describes dependencies in the database between procedures, packages, functions, package bodies, and triggers.

**Parent topic:** Oracle Database Vault General Security Reports

##### 26.6.1.1 Object Access By PUBLIC Report

The Object Access By PUBLIC Report lists all objects whose access has been granted to `PUBLIC`.

This report details all the object access the database accounts that you specify on the Report Parameters page, through object grants to `PUBLIC`. On the Reports Parameters page, you can filter the results based on the privilege, the object owner, or the object name.

**Note:**

This report can be quite large if you choose the defaults.

**Parent topic:** Object Privilege Reports

##### 26.6.1.2 Object Access Not By PUBLIC Report

The Object Access Not By PUBLIC Report describes the object access used by the database accounts on the Report Parameters page.

It checks the grants to the account directly or through a role, but excluding the grants to `PUBLIC`.

On the Reports Parameters page, you can filter the results based on the privilege, the object owner or the object name.

**Note:**

This report can be quite large if you choose the defaults.

**Parent topic:** Object Privilege Reports

##### 26.6.1.3 Direct Object Privileges Report

The Direct Object Privileges Report shows the direct object privileges granted to nonsystem database accounts.

The following database accounts are excluded from the report:

| Accounts C-O | Accounts P-W |
|:-------------|:-------------|
| `CTXSYS`     | `PUBLIC`     |
| `DMSYS`      | `SYS`        |
| `DVSYS`      | `SYSMAN`     |
| `LBACSYS`    | `SYSTEM`     |
| `MDSYS`      | `WKSYS`      |
| `ORDSYS`     | `WMSYS`      |

**Parent topic:** Object Privilege Reports

##### 26.6.1.4 Object Dependencies Report

The Object Dependencies Report describes dependencies in the database between procedures, packages, functions, package bodies, and triggers.

The report includes dependencies on views created without any database links.

This report can help you develop a security policy using the principle of least privilege for existing applications. If a database object, such as a `UTL_FILE` package, has privileges granted to `PUBLIC` or some other global role, then you can use the Object Dependencies Report to determine an account that may depend on the object and to determine how the account uses the object. To run the report, enter the database account you are inspecting for dependency and the object it may be dependent on, in the Report Parameters page.

The Report Results page shows the dependent object and object type and the source object name and type. This report shows where the potentially sensitive object is being used. By looking at several accounts, you might be able to see patterns that can help you develop restricted roles. These restricted roles can replace `PUBLIC` grants on widely used sensitive objects.

**Parent topic:** Object Privilege Reports

#### 26.6.2 Database Account System Privileges Reports

The database account system privileges reports track activities such as direct, indirect, hierarchical, and `ANY` system privileges.

- Direct System Privileges By Database Account Report
  The Direct System Privileges By Database Account Report lists system privileges directly granted to the database account selected on the Report Parameters page.
- Direct and Indirect System Privileges By Database Account Report
  The Direct and Indirect System Privileges By Database Account Report displays system privileges for the database account selected on the Report Parameters page.
- Hierarchical System Privileges by Database Account Report
  The Hierarchical System Privileges by Database Account Report shows a hierarchical breakdown of role-based system privileges and direct system privileges.
- ANY System Privileges for Database Accounts Report
  The ANY System Privileges for Database Accounts Report shows `ANY` system privileges granted to the specified database account or role.
- System Privileges By Privilege Report
  The System Privileges By Privilege Report lists database accounts and roles that have the system privilege selected on the Report Parameters page.

**Parent topic:** Oracle Database Vault General Security Reports

##### 26.6.2.1 Direct System Privileges By Database Account Report

The Direct System Privileges By Database Account Report lists system privileges directly granted to the database account selected on the Report Parameters page.

This report also shows whether a privilege has been granted the `WITH ADMIN` option.

**Parent topic:** Database Account System Privileges Reports

##### 26.6.2.2 Direct and Indirect System Privileges By Database Account Report

The Direct and Indirect System Privileges By Database Account Report displays system privileges for the database account selected on the Report Parameters page.

The system privileges may have been granted directly or granted through a database role that has the `WITH ADMIN` status.

**Parent topic:** Database Account System Privileges Reports

##### 26.6.2.3 Hierarchical System Privileges by Database Account Report

The Hierarchical System Privileges by Database Account Report shows a hierarchical breakdown of role-based system privileges and direct system privileges.

These privileges are granted to the database account specified on the Report Parameters page.

**Parent topic:** Database Account System Privileges Reports

##### 26.6.2.4 ANY System Privileges for Database Accounts Report

The ANY System Privileges for Database Accounts Report shows `ANY` system privileges granted to the specified database account or role.

`ANY` system privileges are very powerful and should be judiciously assigned to accounts and roles.

**Parent topic:** Database Account System Privileges Reports

##### 26.6.2.5 System Privileges By Privilege Report

The System Privileges By Privilege Report lists database accounts and roles that have the system privilege selected on the Report Parameters page.

Another way to control privileges is to create privilege analysis policies to analyze privilege use.

**Parent topic:** Database Account System Privileges Reports

#### 26.6.3 Sensitive Objects Reports

The sensitive objects reports track activities such as grants on the `EXECUTE` privilege on `SYS` schema objects and access to sensitive objects.

- Execute Privileges to Strong SYS Packages Report
  The Execute Privileges to Strong SYS Packages Report shows database accounts and roles with the `EXECUTE` privilege on powerful system packages.
- Access to Sensitive Objects Report
  The Access to Sensitive Objects Report shows database accounts and roles that have object privileges on system tables or views that have sensitive information.
- Public Execute Privilege To SYS PL/SQL Procedures Report
  The Public Execute Privilege to SYS PL/SQL Procedures Report shows database accounts and roles that have `EXECUTE` privileges on that `SYS` owns.
- Accounts with SYSDBA/SYSOPER Privilege Report
  The Accounts with SYSDBA/SYSOPER Privilege Report displays database accounts that have `SYS`-privileged connection privileges.

**Parent topic:** Oracle Database Vault General Security Reports

##### 26.6.3.1 Execute Privileges to Strong SYS Packages Report

The Execute Privileges to Strong SYS Packages Report shows database accounts and roles with the `EXECUTE` privilege on powerful system packages.

For example, these types of packages can be used to access operating system resources.

The following system PL/SQL packages are included:

| Packages D-D                   | Packages D-U                  |
|:-------------------------------|:------------------------------|
| `DBMS_ALERT`                   | `DBMS_RANDOM`                 |
| `DBMS_BACKUP_RESTORE`          | `DBMS_REPAIR`                 |
| `DBMS_CAPTURE_ADM`             | `DBMS_REPCAT`                 |
| `DBMS_DDL`                     | `DBMS_REPCAT_ADMIN`           |
| `DBMS_DISTRIBUTED_TRUST_ADMIN` | `DBMS_RESOURCE_MANAGER`       |
| `DBMS_FGA`                     | `DBMS_RESOURCE_MANAGER_PRIVS` |
| `DBMS_JOB`                     | `DBMS_RLS`                    |
| `DBMS_LDAP`                    | `DBMS_SESSION`                |
| `DBMS_LOB`                     | `DEBUG_EXTPROC`               |
| `DBMS_LOGMNR`                  | `UTL_FILE`                    |
| `DBMS_LOGMNR_D`                | `UTL_HTTP`                    |
| `DBMS_OBFUSCATION_TOOLKIT`     | `UTL_SMTP`                    |
| `DBMS_ORACLE_TRACE_AGENT`      | `UTL_TCP`                     |
| `DBMS_PIPE`                    | \-                            |

**Parent topic:** Sensitive Objects Reports

##### 26.6.3.2 Access to Sensitive Objects Report

The Access to Sensitive Objects Report shows database accounts and roles that have object privileges on system tables or views that have sensitive information.

This report includes the following system tables and views:

| Tables/Views A-O      | Tables/Views P-S        |
|:----------------------|:------------------------|
| `ALL_SOURCE`          | `PROFILE$`              |
| `ALL_USERS`           | `PROXY_ROLE_DATA$`      |
| `APPROLE$`            | `PROXY_ROLE_INFO$`      |
| `AUD$`                | `ROLE_ROLE_PRIVS `      |
| `AUDIT_TRAIL$`        | `SOURCE$`               |
| `DBA_ROLE_PRIVS`      | `STATS$SQLTEXT`         |
| `DBA_ROLES`           | `STATS$SQL_SUMMARY`     |
| `DBA_TAB_PRIVS`       | `SYSTEM_PRIVILEGE_MAP ` |
| `DBMS_BACKUP_RESTORE` | `TABLE_PRIVILEGE_MAP`   |
| `DEFROLE$`            | `TRIGGER$`              |
| `FGA_LOG$`            | `USER$`                 |
| `LINK$`               | `USER_HISTORY$`         |
| `OBJ$`                | `USER_TAB_PRIVS`        |
| `OBJAUTH$`            | `SYSTEM_PRIVILEGE_MAP ` |
| `OBJPRIV$`            | \-                      |

**Parent topic:** Sensitive Objects Reports

##### 26.6.3.3 Public Execute Privilege To SYS PL/SQL Procedures Report

The Public Execute Privilege to SYS PL/SQL Procedures Report shows database accounts and roles that have `EXECUTE` privileges on that `SYS` owns.

This report can be used to determine which privileges can be revoked from `PUBLIC`, or from other accounts and roles. This reduces vulnerabilities as part of an overall security policy implementation using the principle of least privilege.

**Parent topic:** Sensitive Objects Reports

##### 26.6.3.4 Accounts with SYSDBA/SYSOPER Privilege Report

The Accounts with SYSDBA/SYSOPER Privilege Report displays database accounts that have `SYS`-privileged connection privileges.

This report also shows whether the accounts use an external password. However, note that this report does not include operating system users who can become `SYSDBA`.

**Parent topic:** Sensitive Objects Reports

#### 26.6.4 Privilege Management - Summary Reports

The privilege management summary reports track privilege distribution by grantees, owners, and privileges.

- Privileges Distribution By Grantee Report
  The Privileges Distribution By Grantee Report displays the count of privileges granted to a database account or role.
- Privileges Distribution By Grantee, Owner Report
  The Privileges Distribution By Grantee, Owner Report displays a count of privileges based on the grantee and the owner of the object.
- Privileges Distribution By Grantee, Owner, Privilege Report
  The Privileges Distribution By Grantee, Owner, Privilege Report displays a count of privileges based on the privilege, the grantee, and the object owner.

**See Also:**

[DBA_DV_PUB_PRIVS View](oracle-database-vault-data-dictionary-views.md) to find the values on which the counts listed in these reports are based

**Parent topic:** Oracle Database Vault General Security Reports

##### 26.6.4.1 Privileges Distribution By Grantee Report

The Privileges Distribution By Grantee Report displays the count of privileges granted to a database account or role.

This report provides insight into accounts and roles that may have powerful privileges.

**Parent topic:** Privilege Management - Summary Reports

##### 26.6.4.2 Privileges Distribution By Grantee, Owner Report

The Privileges Distribution By Grantee, Owner Report displays a count of privileges based on the grantee and the owner of the object.

This report provides insight into accounts or roles that may have powerful privileges. You can use this report if you suspect potential intruders or insider threats are looking for accounts that have powerful privileges as accounts to attack or compromise. If intruders can compromise the account (for example, by guessing the password), they can get more privileges than they already have.

**Parent topic:** Privilege Management - Summary Reports

##### 26.6.4.3 Privileges Distribution By Grantee, Owner, Privilege Report

The Privileges Distribution By Grantee, Owner, Privilege Report displays a count of privileges based on the privilege, the grantee, and the object owner.

This report provides insight into the accounts or roles that may have powerful privileges.

**Parent topic:** Privilege Management - Summary Reports

#### 26.6.5 Powerful Database Accounts and Roles Reports

The powerful database accounts and roles reports track information about users who have been granted power privileges, such as the `WITH ADMIN` privilege.

- WITH ADMIN Privilege Grants Report
  The WITH ADMIN Privileges Grants Report shows all database accounts and roles that have been granted privileges with the `WITH ADMIN` clause.
- Accounts With DBA Roles Report
  The Accounts With DBA Roles Report shows all database accounts that have the `DBA` role granted to them.
- Security Policy Exemption Report
  The Security Policy Exemption Report shows database (but not Oracle Database Vault) accounts and roles that have the `EXEMPT ACCESS POLICY` system privilege.
- BECOME USER Report
  The BECOME USER Report shows database accounts roles that have the `BECOME USER` system privilege.
- ALTER SYSTEM or ALTER SESSION Report
  The ALTER SYSTEM or ALTER SESSION Report shows database accounts and roles that have the `ALTER SYSTEM` or `ALTER SESSION` privilege.
- Password History Access Report
  The Password History Access Report shows database accounts that have access to the `USER_HISTORY$` table.
- WITH GRANT Privileges Report
  The WITH GRANT Privileges Report shows database accounts that are granted privileges with the `WITH GRANT` clause.
- Roles/Accounts That Have a Given Role Report
  This report displays the database accounts and roles to which a role has been granted.
- Database Accounts With Catalog Roles Report
  The Database Accounts With Catalog Roles Report displays all database accounts and roles that have the catalog-related roles granted to them.
- AUDIT Privileges Report
  The AUDIT Privileges Report displays all database accounts and roles that have the `AUDIT ANY` or `AUDIT SYSTEM` privilege.
- OS Security Vulnerability Privileges Report
  The OS Security Vulnerability Privileges Report lists database accounts and roles that have privileges to export sensitive information to the operating system.

**Parent topic:** Oracle Database Vault General Security Reports

##### 26.6.5.1 WITH ADMIN Privilege Grants Report

The WITH ADMIN Privileges Grants Report shows all database accounts and roles that have been granted privileges with the `WITH ADMIN` clause.

This privilege can be misused to give another account more system privileges than required.

**Parent topic:** Powerful Database Accounts and Roles Reports

##### 26.6.5.2 Accounts With DBA Roles Report

The Accounts With DBA Roles Report shows all database accounts that have the `DBA` role granted to them.

The `DBA` role is a privileged role that can be misused. It is often granted to a database account to save time and to avoid having to determine the least number of privileges an account really needs. This report can help you to start applying a policy using the principle of least privilege to an existing database.

**See Also:**

[Oracle Database Vault Security Guidelines](oracle-database-vault-security-guidelines.md) for guidelines on deciding who should have privileged roles

**Parent topic:** Powerful Database Accounts and Roles Reports

##### 26.6.5.3 Security Policy Exemption Report

The Security Policy Exemption Report shows database (but not Oracle Database Vault) accounts and roles that have the `EXEMPT ACCESS POLICY` system privilege.

Accounts that have this privilege can bypass all Virtual Private Database (VPD) policy filters and any Oracle Label Security policies that use Oracle Virtual Private Database indirectly. This is a powerful system privilege that should be granted only if absolutely necessary, as it presents a target to gain access to sensitive information in tables that are protected by Oracle Virtual Private Database or Oracle Label Security. You can use the auditing policies described in [Auditing Oracle Database Vault](auditing-oracle-database-vault.md), to audit the use of this privilege.

**Parent topic:** Powerful Database Accounts and Roles Reports

##### 26.6.5.4 BECOME USER Report

The BECOME USER Report shows database accounts roles that have the `BECOME USER` system privilege.

The `BECOME USER` privilege is a very powerful system privilege: it enables the `IMP_FULL_DATABASE` and `EXP_FULL_DATABASE` roles for use with Oracle Data Pump. Accounts that possess this privilege can be misused to get sensitive information or to compromise an application.

**Parent topic:** Powerful Database Accounts and Roles Reports

##### 26.6.5.5 ALTER SYSTEM or ALTER SESSION Report

The ALTER SYSTEM or ALTER SESSION Report shows database accounts and roles that have the `ALTER SYSTEM` or `ALTER SESSION` privilege.

Oracle recommends that you restrict these privileges only to those accounts and roles that truly need them (for example, the `SYS` account and the `DV_ADMIN` role). The `ALTER SYSTEM` statement can be used to change the security-related database initialization parameters that are set to recommended values as part of the Oracle Database Vault security strengthening service. Both the `ALTER SYSTEM` and `ALTER SESSION` statements can be used to dump database trace files, potentially containing sensitive configuration information, to the operating system.

**See Also:**

[ALTER SYSTEM and ALTER SESSION Privilege Security Considerations](oracle-database-vault-security-guidelines.md) for guidelines on using the `ALTER SYSTEM` and `ALTER SESSION` privileges

**Parent topic:** Powerful Database Accounts and Roles Reports

##### 26.6.5.6 Password History Access Report

The Password History Access Report shows database accounts that have access to the `USER_HISTORY$` table.

This table stores hashed passwords that were previously used by each account.

Access to this table can make guessing the existing password for an account easier for someone hacking the database.

**Parent topic:** Powerful Database Accounts and Roles Reports

##### 26.6.5.7 WITH GRANT Privileges Report

The WITH GRANT Privileges Report shows database accounts that are granted privileges with the `WITH GRANT` clause.

Remember that `WITH GRANT` is used for object-level privileges: An account that has been granted privileges using the `WITH GRANT` option can be misused to grant object privileges to another account.

**Parent topic:** Powerful Database Accounts and Roles Reports

##### 26.6.5.8 Roles/Accounts That Have a Given Role Report

This report displays the database accounts and roles to which a role has been granted.

This report is provided for dependency analysis.

**Parent topic:** Powerful Database Accounts and Roles Reports

##### 26.6.5.9 Database Accounts With Catalog Roles Report

The Database Accounts With Catalog Roles Report displays all database accounts and roles that have the catalog-related roles granted to them.

These roles are as follows:

- `DELETE_CATALOG_ROLE`

- `EXECUTE_CATALOG_ROLE`

- `RECOVERY_CATALOG_OWNER`

- `SELECT_CATALOG_ROLE`

These catalog-based roles have a very large number of powerful privileges. They should be granted with caution, much like the `DBA` role, which uses them.

**Parent topic:** Powerful Database Accounts and Roles Reports

##### 26.6.5.10 AUDIT Privileges Report

The AUDIT Privileges Report displays all database accounts and roles that have the `AUDIT ANY` or `AUDIT SYSTEM` privilege.

This privilege can be used to disable auditing, which could be used to eliminate the audit trail record of a intruder who has compromised the system. The accounts that have this privilege could be targets for intruders.

**Parent topic:** Powerful Database Accounts and Roles Reports

##### 26.6.5.11 OS Security Vulnerability Privileges Report

The OS Security Vulnerability Privileges Report lists database accounts and roles that have privileges to export sensitive information to the operating system.

This report can reveal important vulnerabilities related to the operating system.

**Parent topic:** Powerful Database Accounts and Roles Reports

#### 26.6.6 Initialization Parameters and Profiles Reports

The initialization parameters and profiles reports track database parameters, resource profiles, and system limits.

- Security Related Database Parameters Report
  The Security Related Database Parameters Report lists database parameters that can cause security vulnerabilities if they not set correctly.
- Resource Profiles Report
  The Resource Profiles Report lists resource profiles that may be allowing unlimited resource consumption.
- System Resource Limits Report
  The System Resource Limits Report provides insight into the current system resource usage by the database.

**Parent topic:** Oracle Database Vault General Security Reports

##### 26.6.6.1 Security Related Database Parameters Report

The Security Related Database Parameters Report lists database parameters that can cause security vulnerabilities if they not set correctly.

This report can be used to compare the recommended settings with the current state of the database parameter values.

**Parent topic:** Initialization Parameters and Profiles Reports

##### 26.6.6.2 Resource Profiles Report

The Resource Profiles Report lists resource profiles that may be allowing unlimited resource consumption.

Examples of resource profiles are `CPU_PER_SESSION` and `IDLE_TIME`. You should review the profiles that might need a cap on the potential resource usage.

**Parent topic:** Initialization Parameters and Profiles Reports

##### 26.6.6.3 System Resource Limits Report

The System Resource Limits Report provides insight into the current system resource usage by the database.

This report helps determine whether any of these resources are approaching their limits under the existing application load. Resources that show large increases over a short period may point to a denial-of-service (DoS) attack. You might want to reduce the upper limit for the resource to prevent the condition in the future.

**Parent topic:** Initialization Parameters and Profiles Reports

#### 26.6.7 Database Account Password Reports

The database account password reports track default passwords and account statuses of database accounts.

- Database Account Default Password Report
  The Database Account Default Password Report lists the database accounts that have default passwords.
- Database Account Status Report
  The Database Account Status Report lists existing database accounts.

**Parent topic:** Oracle Database Vault General Security Reports

##### 26.6.7.1 Database Account Default Password Report

The Database Account Default Password Report lists the database accounts that have default passwords.

Default passwords are provided during the Oracle Database installation.

You should change the passwords for accounts included in this report to nondefault, complex passwords to help secure the database.

**Parent topic:** Database Account Password Reports

##### 26.6.7.2 Database Account Status Report

The Database Account Status Report lists existing database accounts.

This report shows the account status for each account, which helps you identify accounts that must be locked. Lock and expiry dates provide information that helps determine whether the account was locked as a result of password aging. If a special password and resource secure profile is used, then you can identify accounts that are not using them. Accounts not using organizationally defined default tablespaces also can be identified, and the temporary tablespace for accounts can be determined. This report also identifies accounts that use external passwords.

**Parent topic:** Database Account Password Reports

#### 26.6.8 Security Audit Report: Core Database Audit Report

The Core Database Audit Report lists database audit trail records..

This report applies to a non-unified auditing environment.

The Core Database Audit Report returns audit records for the audit policy defined in [Auditing Oracle Database Vault](auditing-oracle-database-vault.md), and any auditing records that are generated for audit statements you have defined.

This report only displays audit records that are captured if the database initialization parameter `AUDIT_TRAIL` has been set to `DB` (with unified auditing disabled).

**See Also:**

[Oracle Database Reference](../refrn/AUDIT_TRAIL.md) for more information about the `AUDIT_TRAIL` parameter

**Parent topic:** Oracle Database Vault General Security Reports

#### 26.6.9 Other Security Vulnerability Reports

Other security vulnerability reports track vulnerabilities that arise with activities such as Java policy grants ir operating system directory objects.

- Java Policy Grants Report
  The Java Policy Grants Report shows the Java policy permissions stored in the database.
- OS Directory Objects Report
  The OS Directory Objects Report shows directory objects in the database, their privileges, and whether they are available to `PUBLIC`.
- Objects Dependent on Dynamic SQL Report
  The Objects Dependent on Dynamic SQL Report lists objects that use dynamic SQL.
- Unwrapped PL/SQL Package Bodies Report
  The Unwrapped PL/SQL Package Bodies Report lists PL/SQL package procedures that are not wrapped.
- Username/Password Tables Report
  The Username/Password Tables Report identifies application tables in the database that store user names and password strings.
- Tablespace Quotas Report
  The Tablespace Quotas Report lists database accounts that have quotas on one or more tablespaces.
- Non-Owner Object Trigger Report
  The Non-Owner Object Trigger Report lists non-owner triggers.

**Parent topic:** Oracle Database Vault General Security Reports

##### 26.6.9.1 Java Policy Grants Report

The Java Policy Grants Report shows the Java policy permissions stored in the database.

This report helps reveal violations to the principle of least privilege. Look for `GRANT`, `READ`, or `WRITE` privileges to `PUBLIC` or other accounts and roles that do not necessarily need the privilege. It is advisable to disable Java loading privileges from `PUBLIC`, if Java is not required in the database.

**Note:**

Oracle JVM, the Java virtual machine option provided with Oracle Database Vault, must be installed before you can run the Java Policy Grants Report.

**Parent topic:** Other Security Vulnerability Reports

##### 26.6.9.2 OS Directory Objects Report

The OS Directory Objects Report shows directory objects in the database, their privileges, and whether they are available to `PUBLIC`.

Directory objects should exist only for secured operating system (OS) directories, and access to them within the database should be protected. You should never use the root operating system directory on any storage device (for example, `/`), because it allows remote database sessions to look at all files on the device.

**Parent topic:** Other Security Vulnerability Reports

##### 26.6.9.3 Objects Dependent on Dynamic SQL Report

The Objects Dependent on Dynamic SQL Report lists objects that use dynamic SQL.

Potential intruders have a greater chance of using this channel if parameter checking or bind variables are not used. The report helps by narrowing the scope of where to look for problems by pointing out who is using dynamic SQL. Such objects can be a target for a SQL injection attack and must be secured to avoid this type of attack. After determining the objects that use dynamic SQL, do the following:

- Check the privileges that client applications (for example, a Web application) have over the object.

- Check the access granted for the object to `PUBLIC` or a wider account base.

- Validate parameters.

- Use bind variables where possible.

**Parent topic:** Other Security Vulnerability Reports

##### 26.6.9.4 Unwrapped PL/SQL Package Bodies Report

The Unwrapped PL/SQL Package Bodies Report lists PL/SQL package procedures that are not wrapped.

Oracle provides a wrap utility that obfuscates code to the point where it cannot be read in the data dictionary or from the data dictionary views. This helps reduce the ability of an intruder to circumvent data protection by eliminating the ability to read source code that manipulates data.

**Parent topic:** Other Security Vulnerability Reports

##### 26.6.9.5 Username/Password Tables Report

The Username/Password Tables Report identifies application tables in the database that store user names and password strings.

You should examine these tables to determine if the information is encrypted. (Search for column names such as `%USER%NAME%` or `%PASSWORD%`.) If it is not, modify the code and applications using these tables to protect them from being visible to database sessions.

**Parent topic:** Other Security Vulnerability Reports

##### 26.6.9.6 Tablespace Quotas Report

The Tablespace Quotas Report lists database accounts that have quotas on one or more tablespaces.

These tablespaces can become potential targets for denial-of-service (DoS) attacks.

**Parent topic:** Other Security Vulnerability Reports

##### 26.6.9.7 Non-Owner Object Trigger Report

The Non-Owner Object Trigger Report lists non-owner triggers.

These are triggers that are owned by a database account that is different from the account that owns the database object on which the trigger acts.

If the trigger is not part of a trusted database application, then it can steal sensitive data, possibly from tables protected through Oracle Label Security or Virtual Private Database (VPD), and place it into an unprotected table for subsequent viewing or export.

**Parent topic:** Other Security Vulnerability Reports
