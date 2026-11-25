As with all Oracle Database products, you should follow security guidelines to better secure your Oracle Database Vault installation.

- Separation of Duty Guidelines
  Oracle Database Vault is designed to easily implement separation of duty guidelines.
- Managing Oracle Database Administrative Accounts
  Oracle provides guidelines for managing security for administrative accounts such as `SYSTEM` or users who have the `SYSDBA` administrative privilege.
- Accounts and Roles Trusted by Oracle Database Vault
  Oracle Database Vault restricts access to application data from many privileged users and roles in the database.
- Accounts and Roles That Should be Limited to Trusted Individuals
  You should limit powerful accounts and roles only to trusted individuals.
- Guidelines for Using Oracle Database Vault in a Production Environment
  You should follow special guidelines when you run Oracle Database Vault in a production environment.
- Secure Configuration Guidelines
  You should be aware of security considerations for special PL/SQL packages, privileges, and the recycle bin.

### D.1 Separation of Duty Guidelines

Oracle Database Vault is designed to easily implement separation of duty guidelines.

- How Oracle Database Vault Handles Separation of Duty
  Separation of duty is restricting each user's privileges only to the tasks he or she is responsible for, and no more.
- Separation of Tasks in an Oracle Database Vault Environment
  Oracle Database Vault defines the several main responsibilities.
- Separation of Duty Matrix for Oracle Database Vault
  Before applying separation of duty, you must understand who performs basic administration tasks in your environment and what these administration tasks are.
- Identification and Documentation of the Tasks of Database Users
  You should document the areas of the tasks that your organization needs.

**Parent topic:** Oracle Database Vault Security Guidelines

#### D.1.1 How Oracle Database Vault Handles Separation of Duty

Separation of duty is restricting each user's privileges only to the tasks he or she is responsible for, and no more.

You should assign specific categories of privileges to specific users, rather than granting many privileges to one user. Simply put, separation of duty creates accountability for each task that your organization requires.

Separation of duty has taken on increased importance over the past 10 years. For many organizations, separation of duty is a new concept that continues to evolve. Database consolidation, regulatory compliance, and outsourcing are just a few of the drivers for increased separation of duty. Oracle Database Vault separation of duty strengthens security by separating security-related administration from day-to-day DBA operations. You can tailor your Database Vault separation of duty implementation to easily adapt to current and future business requirements. Small organizations, in particular, need flexibility as they attempt to increase their security profile with limited resources.

**Parent topic:** Separation of Duty Guidelines

#### D.1.2 Separation of Tasks in an Oracle Database Vault Environment

Oracle Database Vault defines the several main responsibilities.

These responsibilities are as follows:

- Account management. Account management entails creating, modifying, and dropping user accounts. The `DV_ACCTMGR` role provides these privileges. A primary day-to-day `DV_ACCTMGR` user and a backup `DV_ACCTMGR` user are created during the Oracle Database Vault registration process. As a safety measure, you keep and maintain the backup account in case the primary `DV_ACCTMGR` account owner forgets his or her password or leaves the company.

- Security administration. Security administration covers basic security tasks such as creating realms and command rules, setting security policies for database users' access, and authorizing database users for jobs they are allowed to perform. Security administrators also run security audit reports. The `DV_OWNER` and `DV_ADMIN` roles provide these privileges. A primary day-to-day `DV_OWNER` user and a backup `DV_OWNER` user are created during the Oracle Database Vault registration process.

  **Important:**

  As a safety measure, you should keep and maintain the backup user account in case the primary `DV_OWNER` account owner forgets his or her password or leaves the company. It is also important that you do not lose access to all of the user accounts that have been granted the `DV_OWNER` role. There is no way to recover the `DV_OWNER` role if you lose access (such as with a lost password or a staff departure) to any account that has the `DV_OWNER` role. If you lose access to the `DV_OWNER` role, then you cannot modify any Database Vault controls or disable Database Vault. To remedy this problem, you can recover the database to the last known point where the database had possession of the Database Vault owner account.

  Optionally, you can consolidate the account management and security administrative responsibilities.

- Database management. Database management refers to managing the database system but not accessing business data. It includes the following operations:

  - Backup operations require a predefined time to perform the backup using predefined tools.

  - Tuning and monitoring operations require ongoing performance monitoring and analysis.

  - Patching operations require temporary access only during the time the patching takes place

  Oracle strongly recommends that you review database management accounts within the context of separation of duty. Different database administrators may have different responsibilities that require different privileges and roles. Similarly, more experienced database administrators may have more roles and privileges. Instead of granting users the default `DBA` role to users, consider tailoring database administrative roles for specific positions and for seniority in your organization. It is important to use only named accounts for day-to-day activities. Accounts such as `SYS` and accounts that use the `SYSDBA` administrative privilege should be managed with Privileged Account Management (PAM) systems and checked out (and audited) when they are used. You should also manage the backup Oracle Database Vault owner and account management accounts with a PAM system. Within the operating system, you should make the `root` and `oracle` accounts available only through a checkout system, because of the powerful privileges that these accounts have.

You should have separate accounts for database account management, database security administration, and additional named accounts for backup operations. Auditors check for separate database accounts for different responsibilities and being able to track the actions of each account. Less important is the number of users assigned to specific tasks. Remember that Oracle Database Vault audit events are protected and that the Database Vault reports show all attempted violations.

**See Also:**

- [Oracle Database Vault Roles](oracle-database-vault-schemas-roles-and-accounts.md) for an in-depth look at how the Oracle Database Vault roles provide for separation of duty

- [Oracle Database Vault Accounts Created During Registration](oracle-database-vault-schemas-roles-and-accounts.md) for a full list of the default Oracle Database Vault accounts

- [Backup Oracle Database Vault Accounts](oracle-database-vault-schemas-roles-and-accounts.md) for more information about the importance of backup accounts

**Parent topic:** Separation of Duty Guidelines

#### D.1.3 Separation of Duty Matrix for Oracle Database Vault

Before applying separation of duty, you must understand who performs basic administration tasks in your environment and what these administration tasks are.

Even if a single database administrator is responsible for managing both new database account provisioning and application patching, it is important to document and plan for each of these tasks. Using separate administration accounts for these types of tasks provides increased accountability and reduces associated risks if and when a single account is compromised by a malicious user. In midsize to large organizations, database administrators typically must perform common administration tasks but they do not need access to business data managed by the application. Creating a matrix for your separation of duty can help you plan your Database Vault deployment. As needed, you can include additional tasks and associated users to this list. This information should become part of the overall enterprise security documentation for your organization.

Table D-1 shows an example of a separation of duty matrix.

Table D-1 Example Separation of Duty Matrix

| User, Process or Application | Account Creation | Database Administration | Security Administrator |            |                       |     |     |
|:-----------------------------|:-----------------|:------------------------|:-----------------------|:-----------|:----------------------|:----|:----|
| SYSDBA                       | Backup           | Tuning                  | Patching               | Monitoring |                       |     |     |
| `JSMITH`                     | Yes              | No                      | No                     | No         | No                    | No  | No  |
| `SHARDY`                     | No               | No                      | No                     | No         | No                    | No  | Yes |
| `PKESTNER`                   | No               | No                      | Yes                    | No         | No                    | No  | No  |
| `RTYLER`                     | No               | No                      | No                     | No         | Yes                   | No  | No  |
| `SANDERSON`                  | No               | No                      | No                     | Yes        | No                    | Yes | No  |
| `SYSTEM`                     | No               | No                      | No                     | No         | Yes, for EBS patching | No  | No  |
| `RMAN`                       | No               | Yes                     | Yes                    | No         | No                    | No  | No  |

In some cases, system management tasks may require temporary access to data through specific tools and programs. When this happens, build provisions for this temporary or emergency access into the Oracle Database Vault rules and rule sets.

**Parent topic:** Separation of Duty Guidelines

#### D.1.4 Identification and Documentation of the Tasks of Database Users

You should document the areas of the tasks that your organization needs.

These areas are as follows:

- The responsibilities of each administrative user

- The kind of access users need. For example, application owners should have data access and developers need access to development instances only.

- Who must manage the system without accessing business data (for example, users who perform backup, patching, tuning, and monitoring operations)

- The duties of each category of tasks (for example, the files that must be backed up, the applications that require patching, what exactly is monitored). Include the alternate user accounts for each of these tasks.

- The databases and applications that must be protected. This includes Oracle applications, partner applications, and custom applications.

- Who must be authorized to access business data, including the following:

  - Application owners through middle tier processes

  - Business users through an application interface

- Emergency "what if" scenarios, such as how to handle a security breach

- Reporting in a production environment, which should include the following:

  - Who runs the reports

  - Which reports must be run

  - The frequency with which each report is run

  - The users who must receive a copy of each report

- In addition to a separation of duty matrix, the creation of the following matrices:

  - An Oracle Database Vault-specific matrix, which can cover the names and tasks of users who have been granted Database Vault roles

  - An application protection matrix, which can cover the applications to be protected and the types of protections you have put in place.

  Table D-2 shows an example of protections Oracle created for PeopleSoft Applications. `SYSADM`, `PSFTDBA`, `SYSTEM`, and `DBA` have all been authorized for the appropriate rule sets.

  Table D-2 Example Application Protection Maxtrix

  | Protection Type              | SYSADM                    | PSFTDBA               | SYSTEM            | DBA               |
  |:-----------------------------|:--------------------------|:----------------------|:------------------|:------------------|
  | PeopleSoft Realm             | Owner                     | Owner                 | No Access         | No Access         |
  | SELECT Command Rule          | Not Restricted            | Limit PSFTDB Rule Set | No Access         | No Access         |
  | CONNECT Command Rule         | PeopleSoftAccess Rule Set | Not Restricted        | Not Restricted    | Not Restricted    |
  | DROP TABLESPACE Command Rule | Disabled Rule Set         | Disabled Rule Set     | Disabled Rule Set | Disabled Rule Set |

**Parent topic:** Separation of Duty Guidelines

### D.2 Managing Oracle Database Administrative Accounts

Oracle provides guidelines for managing security for administrative accounts such as `SYSTEM` or users who have the `SYSDBA` administrative privilege.

- SYSTEM User Account for General Administrative Uses
  Ideally, the `SYSTEM` account should only be available as a backup that is checked out and audited while being used.
- SYSTEM Schema for Application Tables
  If you have application tables in the `SYSTEM` schema, then you should add the `SYSTEM` account to your realm authorizations for these tables.
- Limitation of the SYSDBA Administrative Privilege
  Limit the `SYSDBA` administrative privilege to users who must connect using this privilege when absolutely necessary and for applications that still require `SYSDBA` access.
- Root and Operating System Access to Oracle Database Vault
  For better security, you should carefully monitor root and operating system access to Oracle Database. Vault.

**Parent topic:** Oracle Database Vault Security Guidelines

#### D.2.1 SYSTEM User Account for General Administrative Uses

Ideally, the `SYSTEM` account should only be available as a backup that is checked out and audited while being used.

Only named accounts should be used for normal database administration tasks - not shared accounts. Doing so increases accountability for administrative actions in the database.

**Parent topic:** Managing Oracle Database Administrative Accounts

#### D.2.2 SYSTEM Schema for Application Tables

If you have application tables in the `SYSTEM` schema, then you should add the `SYSTEM` account to your realm authorizations for these tables.

This enables these applications to continue to work normally.

You can place restrictions on the `SYSTEM` account to increase or fine-tune security for these applications. For example, you can create a Database Vault rule set to restrict the `SYSTEM` user's access to specific IP addresses.

**Parent topic:** Managing Oracle Database Administrative Accounts

#### D.2.3 Limitation of the SYSDBA Administrative Privilege

Limit the `SYSDBA` administrative privilege to users who must connect using this privilege when absolutely necessary and for applications that still require `SYSDBA` access.

For example, mandatory patching processes require `SYSDBA` access.

For all other cases, create named database accounts to perform daily database administration. Members of the `OSDBA` user group are also given the `SYSDBA` administrative privilege. The database `SYS` account and accounts with `SYSDBA` privilege along with the operating system `root` and `oracle` accounts should be managed in a Privileged Account Management (PAM) system and checked out only when required.

**Related Topics**

- Management of SYSDBA Access

**Parent topic:** Managing Oracle Database Administrative Accounts

#### D.2.4 Root and Operating System Access to Oracle Database Vault

For better security, you should carefully monitor root and operating system access to Oracle Database. Vault.

Oracle Database Vault prevents highly privileged database users from accessing sensitive data. In addition, if you are using Oracle Database itself, then you can use Transparent Data Encryption to prevent the most highly privileged operating system users from accessing sensitive data. Transparent data encryption enables you to encrypt tablespaces and table columns. This prevents operating system users from browsing through the operating system database files and finding sensitive data. As a best practice, always carefully review and restrict direct access to the operating system.

You should have personalized accounts access the operating system. These personalized accounts should, in the Linux or UNIX environments, login using `sudo` to the `oracle` software owner when needed. With `sudo`, you can control which specific command each personalized user can execute. Be sure to prevent the use of the `make`, `relink`, `gdb`, or other commands that could potentially harm the database, for these users. However, if an administrative user must install a patch or perform some other emergency operation, you can enable the `make` and `relink` commands for a limited time, and audit their actions during this period.

**See Also:**

[Oracle Database Advanced Security Guide](../asoag/asopart1.md) for more information about Transparent Data Encryption

**Parent topic:** Managing Oracle Database Administrative Accounts

### D.3 Accounts and Roles Trusted by Oracle Database Vault

Oracle Database Vault restricts access to application data from many privileged users and roles in the database.

However, in some cases, Oracle Database Vaults trusts certain roles and privileges.

Table D-3 lists the trusted roles and privileges that are created when you install Oracle Database Vault.

Table D-3 Trusted Oracle Database Vault Roles and Privileges

| Role or Privilege        | Status         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:-------------------------|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DV_ACCTMGR` role        | Open           | Role created during registration and used for creating new database accounts. As a safety measure, maintain a backup user who has the `DV_ACCTMGR` role and manage this account using a Privileged Account Management (PAM) system.<br>Users who have the `DV_OWNER` role cannot alter this user.<br>Loss of all accounts with the `DV_ACCTMGR` role (such as due to lost passwords or people leaving the organization) is not recoverable. Ensure that a backup `DV_ACCTMGR` account is created for this purpose.                                                                     |
| `DV_OWNER` role          | Open           | Role created during registration and used for managing realms, factors and command rules. This user can add himself or herself to realm authorizations. As a safety measure, maintain a backup user who has the `DV_OWNER` role and manage this account using a Privileged Account Management (PAM) system.<br>Users who have the `DV_OWNER` role cannot alter this user.<br>Loss of all accounts with the `DV_OWNER` role (such as due to lost passwords or people leaving the organization) is not recoverable. Ensure that a backup `DV_OWNER` account is created for this purpose. |
| `SYSDBA` privilege       | Enabled        | Privilege created during Oracle Database installation. Required by some Oracle features.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `SYSOPER` privilege      | Enabled        | Privilege created during Oracle Database installation. Database startup and shutdown. Granted to `SYS` only by default.                                                                                                                                                                                                                                                                                                                                                                                                                                                                |

**Related Topics**

- [Backup Oracle Database Vault Accounts](oracle-database-vault-schemas-roles-and-accounts.md)
- Management of SYSDBA Access
- Management of SYSOPER Access

**Parent topic:** Oracle Database Vault Security Guidelines

### D.4 Accounts and Roles That Should be Limited to Trusted Individuals

You should limit powerful accounts and roles only to trusted individuals.

- Management of Users with Root Access to the Operating System
  Users who have root user access have full control over the system.
- Management of the Oracle Software Owner
  Users who have access to a system as the Oracle software owner have control over the Oracle software.
- Management of SYSDBA Access
  You should avoid using the `SYS` account and the `SYSDBA` privilege for normal database maintenance tasks.
- Management of SYSOPER Access
  By default, Oracle Database limits `SYSOPER` access to operating system users in the `OSOPER` group and to the user `SYS`.

**Parent topic:** Oracle Database Vault Security Guidelines

#### D.4.1 Management of Users with Root Access to the Operating System

Users who have root user access have full control over the system.

Activities that these users can perform include the following:

- Reading unencrypted files

- Moving and deleting any files

- Starting or stopping any program on the system

- Logging in as any user, including the user who owns the Oracle Database installation

Oracle Database Vault does not provide protection against the operating system root access. Manage the `root` and `oracle` accounts in a Privileged Account Management (PAM) system. Only check these accounts out when they are required for certain tasks. Enhance audit levels when highly privileged operating system accounts are being used, up to an including keystroke capture and video capture.

**Parent topic:** Accounts and Roles That Should be Limited to Trusted Individuals

#### D.4.2 Management of the Oracle Software Owner

Users who have access to a system as the Oracle software owner have control over the Oracle software.

Activities these users can perform include the following:

- Reading unencrypted database files

- Moving and deleting database files

- Starting or stopping Oracle programs in the system

Oracle Database Vault does not provide protection against the operating system access of the Oracle software owner. Manage the Oracle software owner account in a Privileged Account Management (PAM) system. Only check this account out when it is required for certain tasks. Enhance audit levels when highly privileged operating system accounts are being used, up to an including keystroke capture and video capture.

**Parent topic:** Accounts and Roles That Should be Limited to Trusted Individuals

#### D.4.3 Management of SYSDBA Access

You should avoid using the `SYS` account and the `SYSDBA` privilege for normal database maintenance tasks.

Instead, use named accounts that have the required system privileges or a specific administrative privilege such as `SYSBACKUP`, `SYSDG`, or `SYSKM`. However, there are cases where the `SYSDBA` privilege is required to perform a patch, upgrade of the database or troubleshoot issues (for example, connecting to a down database).

Because users with the `SYSDBA` privilege could have access to sensitive application data either directly or indirectly (for example, through diagnostics, database upgrades, and patching), use of the `SYSDBA` privilege and accounts must be highly restricted. The list of highly privileged accounts include `SYS` and user accounts with the `SYSDBA` privilege in the database, and the root and oracle accounts in the operating system. Access to highly privileged accounts in the database and the operating system should be on an exception basis and require the user to go through a process to unlock access to these accounts and privileges. Oracle recommends that you manage these accounts with a Privileged Account Management (PAM) system. Only check these accounts out when they are required for certain tasks. Enhance audit levels when highly privileged operating system accounts (`root` and `oracle`) and database accounts (`SYS` account and `SYSDBA` administrative privilege) are being used, up to an including keystroke capture and video capture. When these highly privileged accounts access the database, audit the `SYS` account to monitor their activities. Oracle recommends that you use the `ENABLE_DV_PATCH_ADMIN_AUDIT` procedure during patching operations when the `DV_PATCH_ADMIN` role is granted to `SYS` (or to users who have the with `SYSDBA` administrative privilege).

**Related Topics**

- [ENABLE_DV_PATCH_ADMIN_AUDIT Procedure](oracle-database-vault-general-administrative-apis.md)

**Parent topic:** Accounts and Roles That Should be Limited to Trusted Individuals

#### D.4.4 Management of SYSOPER Access

By default, Oracle Database limits `SYSOPER` access to operating system users in the `OSOPER` group and to the user `SYS`.

This prevents `SYSOPER` from modifying the Oracle data dictionary directly. The `SYSOPER` privilege has limited privileges within the database, but individuals with this role can start and shut down the Oracle database. Only grant the `SYSOPER` privilege to trusted individuals.

**Parent topic:** Accounts and Roles That Should be Limited to Trusted Individuals

### D.5 Guidelines for Using Oracle Database Vault in a Production Environment

You should follow special guidelines when you run Oracle Database Vault in a production environment.

These guidelines are as follows:

- Run a full test of your applications to ensure that the Database Vault policies you have created are working as expected

- Monitor the performance of your applications, and if necessary, tune your rule expressions

- Assign responsibilities to the appropriate production support and security groups, as follows:

  - Assign security responsibilities to the database security administrator.

  - Assign account management to the database account manager.

  - Assign resource management tasks to database administrators.

- Back up your Database Vault API scripts to a secure server.

**Parent topic:** Oracle Database Vault Security Guidelines

### D.6 Secure Configuration Guidelines

You should be aware of security considerations for special PL/SQL packages, privileges, and the recycle bin.

- General Secure Configuration Guidelines
  General secure configuration guidelines involved patches and revoke operations.
- UTL_FILE and DBMS_FILE_TRANSFER Package Security Considerations
  You should carefully restrict access to the `UTL_FILE` and `DBMS_FILE_TRANSFER` PL/SQL packages.
- CREATE ANY JOB Privilege Security Considerations
  The `CREATE ANY JOB` privilege has been revoked from the `DBA` and the `SCHEDULER_ADMIN` roles.
- CREATE EXTERNAL JOB Privilege Security Considerations
  The `CREATE EXTERNAL JOB` privilege was introduced in Oracle Database 10g release 2 (10.2).
- LogMiner Package Security Considerations
  The role `EXECUTE_CATALOG_ROLE` no longer has the `EXECUTE` privilege granted by default on the several LogMiner packages.
- ALTER SYSTEM and ALTER SESSION Privilege Security Considerations
  You should be aware of ways to secure the powerful `ALTER SYSTEM` and `ALTER SESSION` system privileges.

**Parent topic:** Oracle Database Vault Security Guidelines

#### D.6.1 General Secure Configuration Guidelines

General secure configuration guidelines involved patches and revoke operations.

- Installing patches and new applications might re-grant some of the privileges that Oracle recommends that you revoke in this section. Check these privileges after you install patches and new applications to verify that they are still revoked.

- When you revoke `EXECUTE` privileges on packages, ensure that you grant `EXECUTE` on the packages to the owner, check the package dependencies, and recompile any invalid packages after the revoke.

  To find users who have access to the package, log into the database instance as a named database administrator and issue the following query.

      SELECT * FROM DBA_TAB_PRIVS WHERE TABLE_NAME = package_name;

  `package_name` is the name of the package you are looking for.

  To find the users, packages, procedures, and functions that are dependent on the package, issue this query:

      SELECT OWNER, NAME, TYPE  FROM ALL_DEPENDENCIES
      WHERE REFERENCED_NAME = package_name;

  Note that these two queries do not identify references to packages made through dynamic SQL.

**Parent topic:** Secure Configuration Guidelines

#### D.6.2 UTL_FILE and DBMS_FILE_TRANSFER Package Security Considerations

You should carefully restrict access to the `UTL_FILE` and `DBMS_FILE_TRANSFER` PL/SQL packages.

- About Security Considerations for the UTL_FILE and DBMS_FILE_TRANSFER Packages
  The `UTL_FILE` package is owned by `SYS` and granted to `PUBLIC`.
- Securing Access to the DBMS_FILE_TRANSFER Package
  You can secure access to the `DBMS_FILE_TRANSFER` PL/SQLpackage in a variety of ways.
- Example: Creating a Command Rule to Deny Access to CREATE DATABASE LINK
  The `DBMS_MACADM.CREATE_COMMAND_RULE` enables you to create command rules to deny access to the `CREATE DATABASE LINK` SQL statement.
- Example: Creating a Command Rule to Enable Access to CREATE DATABASE LINK
  The `DBMS_MACADM.UPDATE_COMMAND_RULE` procedure can be used to modify an existing command rule.
- Example: Command Rules to Disable and Enable Access to CREATE DIRECTORY

**Parent topic:** Secure Configuration Guidelines

##### D.6.2.1 About Security Considerations for the UTL_FILE and DBMS_FILE_TRANSFER Packages

The `UTL_FILE` package is owned by `SYS` and granted to `PUBLIC`.

However, a user must have access to the directory object to manipulate the files in that operating system directory.

The `DBMS_FILE_TRANSFER` package is owned by `SYS` and granted to the `EXECUTE_CATALOG_ROLE`. Users with `EXECUTE` access on this package can move files from one location to another on the same file system. They also can move files between database instances, including databases on remote systems.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/UTL_FILE.md) for information about configuring the `UTL_FILE` package securely

**Parent topic:** UTL_FILE and DBMS_FILE_TRANSFER Package Security Considerations

##### D.6.2.2 Securing Access to the DBMS_FILE_TRANSFER Package

You can secure access to the `DBMS_FILE_TRANSFER` PL/SQLpackage in a variety of ways.

- Use any of the following methods to secure the `DBMS_FILE_TRANSFER` PL/SQLpackage:

  - Revoke the `EXECUTE` privilege from the `DBMS_FILE_TRANSFER` package and grant the `EXECUTE` privilege only to trusted users who need it.

  - Create command rules to control the `CREATE DATABASE LINK` and `CREATE DIRECTORY` SQL statements. See [Creating a Command Rule](configuring-command-rules.md) for information on creating command rules by using Oracle Database Vault Administrator.

  - Create Oracle Database Vault command rules to limit and enable access to the `CREATE DATABASE LINK` and `CREATE DIRECTORY` statements, which are used to establish connections to remote databases.

**See Also:**

The following sections for examples of command rules that you can create to protect use of the `CREATE DATABASE LINK` statement:

- Example: Creating a Command Rule to Deny Access to CREATE DATABASE LINK

- Example: Creating a Command Rule to Enable Access to CREATE DATABASE LINK

- Example: Command Rules to Disable and Enable Access to CREATE DIRECTORY

**Parent topic:** UTL_FILE and DBMS_FILE_TRANSFER Package Security Considerations

##### D.6.2.3 Example: Creating a Command Rule to Deny Access to CREATE DATABASE LINK

The `DBMS_MACADM.CREATE_COMMAND_RULE` enables you to create command rules to deny access to the `CREATE DATABASE LINK` SQL statement.

Example D-1 shows how to create a command rule to deny access to the `CREATE DATABASE LINK` privilege.

Example D-1 Creating a Command Rule to Deny Access to CREATE DATABASE LINK

    BEGIN
     DBMS_MACADM.CREATE_COMMAND_RULE (
      command       => 'CREATE DATABASE LINK',
      rule_set_name => 'Disabled',
      object_owner  => '%',
      object_name   => '%',
      enabled       => DBMS_MACUTL.G_YES);
      END;
      /
    COMMIT;

**Parent topic:** UTL_FILE and DBMS_FILE_TRANSFER Package Security Considerations

##### D.6.2.4 Example: Creating a Command Rule to Enable Access to CREATE DATABASE LINK

The `DBMS_MACADM.UPDATE_COMMAND_RULE` procedure can be used to modify an existing command rule.

Example D-2 shows how to create a command rule that enables access to the `CREATE DATABASE LINK` privilege.

When a valid user must use the `CREATE DATABASE LINK` statement, the Oracle Database Vault owner can reenable it from Oracle Database Vault Administrator or issue the following commands in SQL\*Plus.

Example D-2 Creating a Command Rule to Enable Access to CREATE DATABASE LINK

    BEGIN
     DBMS_MACADM.UPDATE_COMMAND_RULE (
      command       => 'CREATE DATABASE LINK',
      rule_set_name => 'Enabled',
      object_owner  => '%',
      object_name   => '%',
      enabled       => DBMS_MACUTL.G_YES);
     END;
     /
    COMMIT;

**Parent topic:** UTL_FILE and DBMS_FILE_TRANSFER Package Security Considerations

##### D.6.2.5 Example: Command Rules to Disable and Enable Access to CREATE DIRECTORY

Example D-3 shows command rules that disable and enable access to `CREATE DIRECTORY`.

Example D-3 Command Rules to Disable and Enable Access to CREATE DIRECTORY

    -- Disable access to CREATE DIRECTORY
    BEGIN
     DBMS_MACADM.CREATE_COMMAND_RULE (
      command       => 'CREATE DIRECTORY',
      rule_set_name => 'Disabled',
      object_owner  => '%',
      object_name   => '%',
      enabled       => dbms_macutl.g_yes);
     END;
      /
    COMMIT;

    -- Enable access to CREATE DIRECTORY
    BEGIN
     dbms_macadm.update_command_rule (
      command       => 'CREATE DIRECTORY',
      rule_set_name => 'Enabled',
      object_owner  => '%',
      object_name   => '%',
      enabled       => dbms_macutl.g_yes);
     END;
     /
    COMMIT;

**Parent topic:** UTL_FILE and DBMS_FILE_TRANSFER Package Security Considerations

#### D.6.3 CREATE ANY JOB Privilege Security Considerations

The `CREATE ANY JOB` privilege has been revoked from the `DBA` and the `SCHEDULER_ADMIN` roles.

Ensure that this change does not affect your applications.

**Related Topics**

- [Using Oracle Scheduler with Oracle Database Vault](dba-operations-in-an-oracle-database-vault-environment.md)

**Parent topic:** Secure Configuration Guidelines

#### D.6.4 CREATE EXTERNAL JOB Privilege Security Considerations

The `CREATE EXTERNAL JOB` privilege was introduced in Oracle Database 10g release 2 (10.2).

This privilege is required for database users who want to execute jobs that run on the operating system outside the database. By default, the `CREATE EXTERNAL JOB` privilege is granted to all users who have been granted the `CREATE JOB` privilege. For greater security, revoke this privilege from users who do not need it and then grant it only to those users who do need it.

**Parent topic:** Secure Configuration Guidelines

#### D.6.5 LogMiner Package Security Considerations

The role `EXECUTE_CATALOG_ROLE` no longer has the `EXECUTE` privilege granted by default on the several LogMiner packages.

These packages are as follows:

- `SYS.DBMS_LOGMNR_D`

- `SYS.DBMS_LOGMNR_LOGREP_DICT`

- `SYS.DBMS_LOGMNR_FILE_TRANSFER`

- `SYS.DBMS_LOGMNR`

You should ensure that this change does not affect your applications.

**Parent topic:** Secure Configuration Guidelines

#### D.6.6 ALTER SYSTEM and ALTER SESSION Privilege Security Considerations

You should be aware of ways to secure the powerful `ALTER SYSTEM` and `ALTER SESSION` system privileges.

- About ALTER SYSTEM and ALTER SESSION Privilege Security Considerations
  Be aware that trace and debug commands have the potential to show Oracle database memory information.
- Example: Adding Rules to the Existing ALTER SYSTEM Command Rule
  You can create a rule that prevents users with the `ALTER SYSTEM` privilege from issuing `ALTER SYSTEM` statements.

**Parent topic:** Secure Configuration Guidelines

##### D.6.6.1 About ALTER SYSTEM and ALTER SESSION Privilege Security Considerations

Be aware that trace and debug commands have the potential to show Oracle database memory information.

Oracle Database Vault does not protect against these commands. To help secure the Oracle database memory information, Oracle recommends that you strictly control access to the `ALTER SYSTEM` and `ALTER SESSION` privileges. These privileges can be granted by the user `SYS` when connected as `SYSDBA` and by any user granted the `DBA` role.

Oracle also recommends that you add rules to the existing command rule for `ALTER SYSTEM` statement. You can use Oracle Database Vault Administrator to create a rule and add it to a rule set. You should grant the `ALTER SESSION` privilege only to trusted users. (For example, the `ALTER SESSION` statement can enable tracing.)

**Parent topic:** ALTER SYSTEM and ALTER SESSION Privilege Security Considerations

##### D.6.6.2 Example: Adding Rules to the Existing ALTER SYSTEM Command Rule

You can create a rule that prevents users with the `ALTER SYSTEM` privilege from issuing `ALTER SYSTEM` statements.

Example D-4 shows how to create a rule that prevents users with `ALTER SYSTEM` privilege from issuing the `ALTER SYSTEM DUMP` statement. Log into the database instance as the Oracle Database Vault Owner when you create this command rule.

Alternatively, you can use Oracle Database Vault Administrator to create and add this rule to the rule set. See [Creating a Rule to Add to a Rule Set](configuring-rule-sets.md) for more information.

Example D-4 Adding Rules to the Existing ALTER SYSTEM Command Rule

    CONNECT accts_admin_ace
    Enter password: password

    BEGIN
     DBMS_MACADM.CREATE_RULE('NO_SYSTEM_DUMP',
     '(INSTR(UPPER(DV_SQL_TEXT),''DUMP'') = 0)');
     END;
    /
    EXEC DBMS_MACADM.ADD_RULE_TO_RULE_SET
      ('Allow Fine Grained Control of System Parameters','NO_SYSTEM_DUMP');

    COMMIT;

**Parent topic:** ALTER SYSTEM and ALTER SESSION Privilege Security Considerations
