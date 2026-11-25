## 2  Configuring Application Users and Application Roles

This chapter contains:

- About Configuring Application Users

- About Configuring Application Roles

- Effective Dates for Application Users and Application Roles

- About Granting Application Privileges to Principals

**See Also:**

"[XS_PRINCIPAL Package](XS_PRINCIPAL-package.md)"

### 2.1 About Configuring Application Users

This section contains the following topics:

- About Application User Accounts

- Creating a Simple Application User Account

- About Creating a Direct Login Application User Account

- Resetting the Application User's Password with the SQL\*Plus PASSWORD Command

- Configuring an Application User Switch

- Validating an Application User

#### 2.1.1 About Application User Accounts

Traditional database users own database schemas and can create traditional heavyweight database sessions to those schemas.

Application users do not own database schemas, but can create application sessions to the database through the middle tier provided they are granted the role or roles with the appropriate object privileges for accessing tables. Application users can also create heavyweight database sessions by connecting to the database directly through direct login application user accounts provided these accounts are associated with a schema and the `XSCONNECT` application role is granted to these application users. A profile can also be created and assigned to each of these application users.

This section contains: General Procedures for Creating Application User Accounts.

##### 2.1.1.1 General Procedures for Creating Application User Accounts

The general procedure for creating an application user account is as follows:

1.  Create a security manager user, `sec_mgr`, as follows and grant this user `create session` database privilege and Real Application Security `xs_session_admin` database role. Next, execute the `xs_admin_util.grant_system_privilege` call to grant the Real Application Security least system privilege `PROVISION` to `sec_mgr` as a database user. As the security manager, you can now create users and roles, set passwords, and so forth, and administer sessions using the Real Application Security least system privilege.
        sqlplus /nolog
        SQL> connect sys/password as sysdba
        SQL> grant create session, xs_session_admin to sec_mgr identified by password;
        SQL> exec sys.xs_admin_util.grant_system_privilege('provision', 'sec_mgr', sys.xs_admin_util.ptype_db);
2.  Log in to SQL\*Plus as a user who has either the Real Application Security `PROVISION` system privilege or the database `CREATE USER` system privilege.
        sqlplus sec_mgr
        Enter password: password
        Connected.

    See "[XS_PRINCIPAL Package](XS_PRINCIPAL-package.md)" for more information about the `XS_PRINCIPAL` package and specifically the "[CREATE_USER Procedure](XS_PRINCIPAL-package.md)".

    You must have the privileges required to create, modify, or drop application users and roles. These privileges are governed by the same system privileges required to create, modify, or drop database users and roles. For more information about these and other SQL statements, see [Oracle Database SQL Language Reference](../sqlrf/CREATE-USER.md).
3.  Create the application users with the `XS_PRINCIPAL.CREATE_USER` procedure.
    Select the appropriate type, and follow the instructions in these sections:

    - "Creating a Simple Application User Account"

    - "About Creating a Direct Login Application User Account"

###### 2.1.1.1.1 Other Tasks

After you create the application user account, you can grant the account a role, which provides privileges for the application users. For more information, see "Granting an Application Role to an Existing Application User".

#### 2.1.2 Creating a Simple Application User Account

**Note:**

In SQL\*Plus, case sensitivity is an issue for lower case characters and special characters, so keep these guidelines in mind.

- An application user whose name contains lower case or special characters must connect to SQL\*Plus with the account name in double quotation marks:

  For example:

      CONNECT "lwuser1"
      Enter password: password
      Connected.

- The name of an application role that contains lower case or special characters must be entered in SQL\*Plus enclosed in double quotation marks.

  For example:

      GRANT cust_role TO "app_regular_role";

When you create a simple application user account, the schema argument specifies the schema name to use to resolve unqualified names. This does not give you any privileges, and it is just used for name resolution purposes. If the schema name is not specified, `XS$NULL`, is used.

To create a simple application user account, do the following:

1.  Log in.
    For example, if `sec_mgr` has the `CREATE USER` privilege, log in as follows:

        sqlplus sec_mgr
        Enter password: password
        Connected.
2.  Create the application user account.
    For example:

        BEGIN
          SYS.XS_PRINCIPAL.CREATE_USER('lwuser1');
        END;
        /

    As a user with `DBA` role, you can check the user creation by querying the `DBA_XS_USERS` data dictionary view as follows. See "[DBA_XS_USERS](real-application-security-data-dictionary-views.md)" for more information.

        SELECT NAME FROM DBA_XS_USERS;

        NAME
        --------------------------
        XSGUEST
        LWUSER1

    This output displays the existing application user accounts. The `XSGUEST` user account is an already existing or predefined system created user account.

    For detailed information about the `XS_PRINCIPAL.CREATE_USER` procedure, see "[CREATE_USER Procedure](XS_PRINCIPAL-package.md)".

    You can delete an application user account using the `XS_PRINCIPAL.DELETE_PRINCIPAL` procedure, see "[DELETE_PRINCIPAL Procedure](XS_PRINCIPAL-package.md)".

#### 2.1.3 About Creating a Direct Login Application User Account

This section contains:

- Creating Direct Login Application User Accounts

- Procedure for Creating the Direct Login Application User Account

- Setting a Password Verifier for Direct Application User Accounts

- Oracle Label Security Context Is Established in Direct Logon Session

##### 2.1.3.1 Creating Direct Login Application User Accounts

You can use an application user account to directly log into the database. This is useful for users who need to perform functions such as logging directly into SQL\*Plus without logging in through SSO or a Web interface. The direct login user must have a password.

##### 2.1.3.2 Procedure for Creating the Direct Login Application User Account

To create a direct login application user account:

1.  Log in as described in "General Procedures for Creating Application User Accounts".
        sqlplus sec_mgr
        Enter password: password
        Connected.
2.  Create the application user account.
    For example, to create an application user account, `lwuser1`, whose default database schema is `HR`:

        BEGIN
          SYS.XS_PRINCIPAL.CREATE_USER
              (name       => 'lwuser1',
               schema     => 'HR');
        END;/

    **Note:**

    If the schema does not exist, the direct login fails.

    When this Real Application user directly connects to the database for name resolution of unqualified database objects in queries, `HR` schema is used as the default schema. For example:

        SELECT COUNT(*) FROM EMPLOYEES;
3.  Create a password for the application user account.
    For example:

        BEGIN
              SYS.XS_PRINCIPAL.SET_PASSWORD('lwuser1', 'password');
        END;
        /

    Set the password as described in "[SET_PASSWORD Procedure](XS_PRINCIPAL-package.md)". When you use the `SET_PASSWORD` procedure, it creates a verifier for you based on the password and the `type` parameter, and then inserts the verifier and the value of the `type` parameter into the dictionary table.

    **Note:**

    Replace `password` with a secure password. See [Oracle Database Security Guide](../dbseg/keeping-your-oracle-database-secure.md) for more information about password guidelines.
4.  Create a profile named `prof` and assign this profile to the application user account.
    For example:

        CREATE PROFILE prof LIMIT PASSWORD_REUSE_TIME 1/1440 PASSWORD_REUSE_MAX 3 PASSWORD_VERIFY_FUNCTION Verify_Pass;

        BEGIN
          SYS.XS_PRINCIPAL.SET_PROFILE('lwuser1','prof');
        END;

    The user assigning the profile must have `ALTER_USER` privilege. See the "[SET_PROFILE Procedure](XS_PRINCIPAL-package.md)" for more information.
5.  Grant the role `XSCONNECT` to the user to allow access to the database.
    For example:
        BEGIN
              SYS.XS_PRINCIPAL.GRANT_ROLES('lwuser1', 'XSCONNECT');
        END;
        /

Next, you are ready to assign privileges to the application user account. Go to "About Granting Application Privileges to Principals".

Afterward, the user can connect to the database as follows. For example:

    CONNECT lwuser1
    Password: password

##### 2.1.3.3 Setting a Password Verifier for Direct Application User Accounts

Optionally, you can set a [password verifier](glossary.md) for this password (a hash transformed password), enabling administrators to migrate users into Real Application Security with knowledge of the verifier and not the password. If you do not set a password verifier, the default hashing algorithm is `XS_SHA512`. For more information, see the [SET_PASSWORD Procedure](XS_PRINCIPAL-package.md) and the [SET_VERIFIER Procedure](XS_PRINCIPAL-package.md).

Example 2-1 shows how to use the `XS_PRINCIPAL.SET_VERIFIER` procedure to set the password verifier to the value as determined from a query of the `XS$VERIFIERS` dictionary table, using the hashing algorithm `XS_SHA512` for the application user account `LWUSER1` by following these steps:

1.  Query the view `DBA_XS_OBJECTS` to obtain the ID value for user `LWUSER1`.

2.  Query the `XS$VERIFIERS` dictionary table for user `LWUSER1` whose ID is 2147493730. The value of the verifier includes its type as value “T” followed by a colon (:) to denote that it is a verifier type of `XS_SHA512`, which is also indicated as being of type# 2.

3.  Using the entire verifier value including “`T:`”, set the verifier for user `LWUSER1`. The following example shows each of these steps.

Example 2-1 Setting the Password Verifier Using the Hash Algorithm XS_SHA512

    sqlplus sec_mgr
    Enter password: password
    Connected.

    SQL> column name format A10;
    SQL> column owner format A6;
    SQL> select NAME, OWNER, ID, TYPE, STATUS from  DBA_XS_OBJECTS where NAME = 'LWUSER1';

    NAME       OWNER          ID TYPE               STATUS
    ---------- ------ ---------- ------------------ --------
    LWUSER1    SYS    2147493730 PRINCIPAL          VALID

    SQL> column user# format 9999999999;
    SQL> column type# format 99;
    SQL> column verifier format A62;
    SQL> select USER#, VERIFIER, TYPE# from XS$VERIFIERS where USER# = '2147493730';

          USER# VERIFIER                                                       TYPE#
    ----------- -------------------------------------------------------------- -----
     2147493730 T:9BA95FEF2C2630A2BAACF2E7C5E41B0D50CDC7B0B60C88AD4FE81F8155D0     2
                02F99EEAF9D95477E4749870C67FDE870E154ED17809C359777F979E269010
                823FB981B2A998915EB1439FE3C6C1542A239C

    SQL> BEGIN
    SYS.XS_PRINCIPAL.SET_VERIFIER('lwuser1','T:9BA95FEF2C2630A2BAACF2E7C5E41B0D50CDC7B0B6
    0C88AD4FE81F8155D002F99EEAF9D95477E4749870C67FDE870E154ED17809C359777F979E269010823FB
    981B2A998915EB1439FE3C6C1542A239C', XS_PRINCIPAL.XS_SHA512);
    END;
    /  2    3    4    5

    PL/SQL procedure successfully completed.

For this procedure to complete successfully, both the verifier value and its type must match the information in the `VERIFIER` column of the `XS$VERIFIERS` dictionary table for the user whose verifier is being set. Note that when you change the password for an application user, it automatically changes its verifier value with the option of changing its verifier type.

This example set the verifier to its same exact value to show the steps involved. You have the option to set the verifier for a password to any verifier value that displays for an application user when you query the `XS$VERIFIERS` dictionary table as long as the verifier value matches the verifier type that you set. For example, if you wanted to change the verifier value and the verifier type to `XS_SALTED_SHA1`, do the following.

    SQL> BEGIN
    SYS.XS_PRINCIPAL.SET_VERIFIER('lwuser1','S:14DC0F5ABB72FC869549B1F845C548E0BEF7B863A116DB24DFAE22F0501E',
    XS_PRINCIPAL.XS_SALTED_SHA1);
    END;
    /  2    3    4

    PL/SQL procedure successfully completed.

Note that this is the same verifier value and verifier type that was set for application user `LWUSER3` as shown in the [SET_VERIFIER Procedure](XS_PRINCIPAL-package.md).

##### 2.1.3.4 Oracle Label Security Context Is Established in Direct Logon Session

Describes Oracle Label Security support for Real Application Security users.

Beginning with Oracle Database 12c Release 2 (12.2), Oracle Label Security supports Real Application Security users. This means that when a Real Application Security user attaches with Real Application Security user session through direct logon, the user can exercise its own Oracle Label Security authorization. Oracle Label Security context is established during the attach session.

**See Also:**

- [Attaching an Application Session to a Traditional Database Session](configuring-application-sessions.md) for more Information about how Oracle Label Security supports Real Application Security users

- [Oracle Label Security Administrator’s Guide](../olsag/oracle-label-security-pl-sql-packages.md) for more Information about Oracle Label Security

#### 2.1.4 Resetting the Application User's Password with the SQL\*Plus PASSWORD Command

As the security administrator, `sec_mgr`, you have the `create session` database privilege and Real Application Security`xs_session_admin` database role and in addition, `sec_mgr` is granted the Real Application Security `PROVISION` least system privilege as a database user. As the security manager, you can now create users and roles, set passwords, and so forth, and administer sessions using the Real Application Security least system privilege.Example 2-2 shows how the security administrator can reset the password for user `lwuser2` using the SQL\*Plus `PASSWORD` command.

However, if you as user `lwuser2`, perform a self password change using the SQL\*Plus `PASSWORD` command invoked from an explicitly attached session (a session attached using the `ATTACH_SESSION` procedure or the `attachSession()` method in Java), the session must have the `ALTER USER` privilege and the user name must be provided with the `PASSWORD` command.

Example 2-3 shows how the application user `lwuser2` explicitly attached to a session, performs a self password change that fails because the users session does not have the `ALTER USER` privilege.

Example 2-4 shows how an application user `lwuser2` explicitly attached to a session having the `ALTER USER` privilege can perform a self password change. The user's self password change is successful.

The `SET_PASSWORD` procedure does not prompt for old password, but requires either Real Application Security `PROVISION` privilege as the least privilege, or database `ALTER USER` privilege. (Note that `SET_PASSWORD` is the Real Application Security PL/SQL procedure, not the SQL\*Plus `PASSWORD` command.) If the user's session has the `PROVISION` least privilege or the `ALTER USER` privilege, you can reset the password for any application user from any application user's session (including an explicitly attached and a direct logon session) or the database user session if that session has the `PROVISION` least privilege or the `ALTER USER` privilege. The SQL\*Plus `PASSWORD` command never prompts for the old password if you are changing another application user's password.

Example 2-2 DBA Resets the Password with a Password Change Operation for User lwuser2 When Not Explicitly Attached to a Session

    sqlplus sec_mgr
    Enter password: password
    Connected.
    SQL> BEGIN
      2 SYS.XS_PRINCIPAL.CREATE_USER('lwuser2');
      3 END;
      4/

    PL/SQL orocedure successfully completed.

    SQL> PASSWORD lwuser2
    Changing password for lwuser2
    New password: password
    Retype new password: password
    Password changed

Example 2-3 User lwuser2 Performs a Self Password Change that Fails When Explicitly Attached to a Session Because the Session Lacks the ALTER USER Privilege

    sqlplus sec_mgr
    Enter password: password
    Connected.
    SQL> DECLARE
      2 SESSIONID RAW(16);
      3 BEGIN
      4 SYS.DBMS_XS_SESSIONS.CREATE_SESSION('lwuser2', sessionid);
      5 SYS.DBMS_XS_SESSIONS.ATTACH_SESSION(sessionid);
      6 END;
      7 /

    PL/SQL procedure successfully completed.

    SQL> CONNECT lwuser2
    Enter password: password
    Connected.
    SQL> SELECT SYS.XS_SYS_CONTEXT('XS$SESSION','USERNAME') FROM DUAL;

    XS_SYS_CONTEXT('XS$SESSION','USERNAME')
    --------------------------------------------------------------------------------
    LWUSER2

    SQL> PASSWORD lwuser2
    Changing password for lwuser2

    Old password: password
    New password: password
    Retype new password: password
    ERROR:
    ORA-01031: insufficient privileges

    Password unchanged

Example 2-4 A Self Password Change Succeeds When Explicitly Attached to a Session and User lwuser2's Session Has the ALTER USER Privilege

    sqlplus sec_mgr
    Enter password: password
    Connected.
    SQL> CREATE ROLE pwdchg;

    Role created.

    SQL> GRANT ALTER USER TO pwdchg;

    Grant succeeded.

    SQL> EXEC SYS.XS_PRINCIPAL.CREATE_ROLE(NAME => 'resetpwd_role', ENABLED => TRUE);

    PL/SQL procedure successfully completed.

    SQL> GRANT pwdchg TO resetpwd_role;

    Grant succeeded.

    SQL>  EXEC SYS.XS_PRINCIPAL.GRANT_ROLES('lwuser2','resetpwd_role');

    PL/SQL procedure successfully completed.

    SQL> CONNECT lwuser2
    Enter password: password
    Connected.

    SQL> SELECT SYS.XS_SYS_CONTEXT('XS$SESSION','USERNAME') FROM DUAL;

    SYS.XS_SYS_CONTEXT('XS$SESSION','USERNAME')
    --------------------------------------------------------------------------------
    LWUSER2

    SQL> PASSWORD lwuser2
    Changing password for lwuser2
    Old password: password
    New password: password
    Retype new password: password
    Password changed
    SQL>

#### 2.1.5 Configuring an Application User Switch

Using the `XS_PRINCIPAL.ADD_PROXY_USER` procedure, you can add an application user to proxy another application user and assume the application roles of that application user. You can use the `DBMS_XS_SESSIONS.SWITCH_USER` procedure to switch application users in a session if the user has been added as a proxy.

Assume `app_user1` has application roles `role1` and `role2`. Example 2-5 allows you to proxy the application roles `role1` and `role2` of `app_user1` to `app_user2`. The call `add_proxy_user('app_user1', 'app_user2', pxy_roles)` allows `app_user2` to switch to `app_user1` and assume `app_user1`'s roles, `role1` and `role2`. It does not grant the roles to `app_user2`.

The query of view `DBA_XS_ROLE_GRANTS` shows that roles, `roles1` and `roles2` are still only granted to `app_user1` and not to `app_user2`, and that `app_user2` only assumed these roles as a proxy user.

The query of view `DBA_XS_PROXY_ROLES` shows that `app_user2` is the proxy user, `app_user1` is the target user, and the target roles are `role1` and `role2`.

The query of view `DBA_XS_SESSIONS` also shows that `app_user2` is the proxy user in this session.

As the application user with DBA role, you can create a session for `app_user2` and switch application user to `app_user1`, as shown in Example 2-6.

This example first creates a session with `app_user2` and attaches to it. Then `app_user2` switches to `app_user1` and assumes `app_user1`'s roles, `role1` and `role2`.

The query of view `DBA_XS_ROLE_GRANTS` shows that roles, `roles1` and `roles2` are still only granted to `app_user1` and not to `app_user2`, and that `app_user2` only assumed these roles as a proxy user.

The query of view `DBA_XS_SESSION_ROLES` shows that roles `role1` and `role2` are associated with the same session ID in which `app_user1` was switched with `app_user2`.

The query of view `DBA_XS_SESSIONS` also shows that `app_user2` is the proxy user in this session.

Example 2-5 Configuring a Proxy Application User

    sqlplus sec_mgr
    Enter password: password
    Connected.

    SQL> EXEC SYS.XS_PRINCIPAL.CREATE_ROLE('role1',true);
    SQL> EXEC SYS.XS_PRINCIPAL.CREATE_ROLE('role2',true);

    SQL> EXEC SYS.XS_PRINCIPAL.CREATE_USER('app_user1','HR');
    SQL> EXEC SYS.XS_PRINCIPAL.SET_PASSWORD('app_user1', 'password');
    SQL> EXEC SYS.XS_PRINCIPAL.CREATE_USER('app_user2','HR');
    SQL> EXEC SYS.XS_PRINCIPAL.SET_PASSWORD('app_user2', 'password');

    SQL> EXEC SYS.XS_PRINCIPAL.GRANT_ROLES('app_user1', 'role1');
    SQL> EXEC SYS.XS_PRINCIPAL.GRANT_ROLES('app_user1', 'role2');

    DECLARE
      pxy_roles XS$NAME_LIST;
    begin
      pxy_roles := XS$NAME_LIST('role1','role2');
      sys.xs_principal.add_proxy_user(target_user => 'app_user1', proxy_user => 'app_user2', target_roles => pxy_roles);
    end;
    /

    SQL> SELECT grantee, granted_role FROM DBA_XS_ROLE_GRANTS;

    SQL> SELECT proxy_user, target_user, target_role FROM DBA_XS_PROXY_ROLES;

    SQL> SELECT user_name, sessionid, proxy_user FROM DBA_XS_SESSIONS;

Example 2-6 Creating a Session and Switching an Application User

    sqlplus sec_mgr
    Enter password: password
    Connected.
    SQL> EXEC SYS.XS_PRINCIPAL.CREATE_USER('app_user1','HR');
    SQL> EXEC SYS.XS_PRINCIPAL.SET_PASSWORD('app_user1', 'password');
    SQL> EXEC SYS.XS_PRINCIPAL.CREATE_USER('app_user2','HR');
    SQL> EXEC SYS.XS_PRINCIPAL.SET_PASSWORD('app_user2', 'password');

    SQL> EXEC SYS.XS_PRINCIPAL.CREATE_ROLE('role1',true);
    SQL> EXEC SYS.XS_PRINCIPAL.CREATE_ROLE('role2',true);

    SQL> EXEC SYS.XS_PRINCIPAL.CREATE_USER('app_user1','HR');
    SQL> EXEC SYS.XS_PRINCIPAL.SET_PASSWORD('app_user1', 'password');
    SQL> EXEC SYS.XS_PRINCIPAL.CREATE_USER('app_user2','HR');
    SQL> EXEC SYS.XS_PRINCIPAL.SET_PASSWORD('app_user2', 'password');

    SQL> EXEC SYS.XS_PRINCIPAL.GRANT_ROLES('app_user1', 'role1');
    SQL> EXEC SYS.XS_PRINCIPAL.GRANT_ROLES('app_user1', 'role2');

    declare
      sessionid raw(16);
    begin
      sys.dbms_xs_sessions.create_session('app_user2', sessionid);
      sys.dbms_xs_sessions.attach_session(sessionid);
      sys.dbms_xs_sessions.switch_user('app_user1');
    end;
    /

    SQL> SELECT grantee, granted_role FROM DBA_XS_ROLE_GRANTS;

    SQL> SELECT sessionid, role FROM DBA_XS_SESSION_ROLES;

    SQL> SELECT user_name, sessionid, proxy_user FROM DBA_XS_SESSIONS;

#### 2.1.6 Validating an Application User

Oracle recommends that you always validate the Real Application Security objects after administrative configuration changes. The `XS_DIAG` package provides a set of validation APIs to help ensure that these changes do not damage the complicated relationships among your Real Application Security objects. To validate an application user account, use the `XS_DIAG.VALIDATE_PRINCIPAL` function. The caller has invoker's rights on this package and must have `ADMIN_ANY_SEC_SECURITY` privilege to run the `XS_DIAG` package.

See the "[VALIDATE_PRINCIPAL Function](XS_DIAG-package.md)" for more information.

### 2.2 About Configuring Application Roles

This section contains the following topics:

- About Application Roles

- Regular and Dynamic Application Roles

- About Configuring an Application Role

- Predefined Regular Application Roles and Dynamic Application Roles

#### 2.2.1 About Application Roles

An application role is a role that can only be granted to an application user or to another application role. Application roles provide a way to group application users who must have a common application privilege, identified within an ACL, in order to access an application. The `XS_PRINCIPAL.CREATE_ROLE` procedure can create regular application roles. The `XS_PRINCIPAL.CREATE_DYNAMIC_ROLE` procedure can create dynamic application roles (one type of application role).

Application roles are conceptually similar to enterprise roles. An enterprise role can only be granted to an enterprise user and that grant occurs outside the database. Similarly, an application role can only be granted to an application user or application role, and that grant occurs outside of the standard database grant mechanisms. Dynamic roles cannot be granted to an application user or another application role, but can only be enabled in an application session as a parameter in an attach session call as described in "Dynamic Application Roles".

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-ROLE.md) for more information about SQL

- [Oracle Database PL/SQL Language Reference](../lnpls/plsql-language-elements.md) for more information about PL/SQL APIs

#### 2.2.2 Regular and Dynamic Application Roles

Real Application Security allows regular and dynamic application roles.

This section contains the following topics:

- Regular Application Roles

- Dynamic Application Roles

##### 2.2.2.1 Regular Application Roles

A regular application role is an application role that you can grant to an application user or another application role (regular or dynamic). You can specify if you want the regular application role to be enabled by default or not.

##### 2.2.2.2 Dynamic Application Roles

A dynamic application role is an application role that is enabled only under certain situations, for example, when a user has logged on using SSL, or during a specific period of time, and so on. Dynamic application roles might be used, for example, if there is some application privilege granted to all application users connecting during weekdays. If that criterion is met, then the application enables those application roles.

The application determines the criteria for enabling a dynamic application role, however the criteria can be evaluated by the application or by the database at the request of the application.

- When the Application Evaluates the Criteria

  If the application evaluates the criteria and the application role meets it, then the application, if it is attached to an application session, can enable dynamic application roles for application users. When the application detaches from the application session, the dynamic application role is automatically disabled.

  For security reasons, you cannot disable dynamic application roles during the session. This is especially important because they may infer negative application privileges.

- When the Database Evaluates the Criteria

  If the database evaluates the criteria and the application role meets it, then the database can enable application roles for the application user. The database can disable dynamic application roles based on two types of time-outs: one from the last time the session was accessed, and one from the last time the session was authenticated. Oracle Database checks these time-outs when the session is first attached.

You do not need to grant the dynamic application role formally to a user beforehand. There is no way to enable or disable a dynamic application role through the standard enable and disable APIs. You cannot grant dynamic application roles to other application roles, but you can grant other application roles to dynamic roles.

**See Also:**

"Predefined Regular Application Roles and Dynamic Application Roles"

#### 2.2.3 About Configuring an Application Role

This section contains the following topics:

- Creating a Regular Application Role

- Creating a Dynamic Application Role

- Validating an Application Role

##### 2.2.3.1 Creating a Regular Application Role

To create a regular application role, log into SQL\*Plus as user `sec_mgr` with the `CREATE ROLE` system privilege, and then use the `XS_PRINCIPAL.CREATE_ROLE` procedure.

Example 2-7 shows how to create a regular application role called `app_regular_role`. The `start_date` and `end_date` parameters specify the active start and end times for this application role. The `enable` parameter is set to `TRUE`.

After you create the regular application role, you are ready to grant it to one or more application users or application roles. See the following section:

"About Granting an Application Role to an Application User"

Example 2-7 Creating a Regular Application Role

    sqlplus sec_mgr
    Enter password: password
    Connected.

    DECLARE
      st_date TIMESTAMP WITH TIME ZONE;
      ed_date TIMESTAMP WITH TIME ZONE;
    BEGIN
      st_date := SYSTIMESTAMP;
      ed_date := TO_TIMESTAMP_TZ('2013-06-18 11:00:00 -5:00','YYYY-MM-DD HH:MI:SS');
      SYS.XS_PRINCIPAL.CREATE_ROLE
          (name        => 'app_regular_role',
          enabled      =>  TRUE,
          start_date   =>  st_date,
          end_date     =>  ed_date);
    END;
    /

##### 2.2.3.2 Creating a Dynamic Application Role

To create a dynamic application role, log into SQL\*Plus as user `sec_mgr` with the `CREATE ROLE` system privilege and then use the `XS_PRINCIPAL.CREATE_DYNAMIC_ROLE` procedure.

Example 2-8 shows how to create a dynamic application role called `app_dynamic_role`. The optional `duration` parameter specifies the period of time (in minutes) the application role is active. The `scope` parameter specifies the scope for this role, which can be either `SESSION_SCOPE` (the default value) or `REQUEST_SCOPE`. `SESSION_SCOPE` means the enabled dynamic role is still enabled when you detach the session and attach to the session again, unless you explicitly specify that it be disabled in the session reattach. `REQUEST_SCOPE` means that the role is disabled after the session is detached.

In this example, the dynamic application role is active for 40 minutes, and the scope is set to `SESSION_SCOPE` for the current application session. So the dynamic application role is active even when you detach the session and attach to the session again as long as the time limit has not exceeded 40 minutes after having created the dynamic application role.

Example 2-8 Creating a Dynamic Application Role

    sqlplus sec_mgr
    Enter password: password
    Connected.

    BEGIN
      SYS.XS_PRINCIPAL.CREATE_DYNAMIC_ROLE
          (name         => 'app_dynamic_role',
          duration      => 40,
          scope         => XS_PRINCIPAL.SESSION_SCOPE);
    END;
    /

##### 2.2.3.3 Validating an Application Role

Oracle recommends that you should always validate Real Application Security objects after administrative configuration changes. The `XS_DIAG` package provides a set of validation APIs to help ensure that these changes do not damage the complicated relationships among your Real Application Security objects. To validate an application role, use the `XS_DIAG.VALIDATE_PRINCIPAL` function. See the "[VALIDATE_PRINCIPAL Function](XS_DIAG-package.md)" for more information.

See [Troubleshooting Oracle Database Real Application Security](troubleshooting_real_application_security.md) for troubleshooting advice.

#### 2.2.4 Predefined Regular Application Roles and Dynamic Application Roles

Using predefined dynamic application roles in a Real Application Security session, application users can acquire application privileges based on their run-time states. These application roles cannot be acquired by grants.

As an example, an application role may be enabled for application users connecting from within the corporate firewall, which grants application users more application privileges than connecting from outside the firewall.

See "[Roles](predefined-objects-in-real-application-security.md)" for a description of Real Application Security predefined regular application roles, dynamic application roles, and database roles.

Regular application roles can be granted to an application user, but dynamic application roles cannot. Dynamic application roles are enabled based on user state.

See "Regular and Dynamic Application Roles" for descriptions.

### 2.3 Effective Dates for Application Users and Application Roles

You can specify effective dates for application users, application roles, and role grants. The application user or application role is available only within the period defined by the effective start and end date. Example 2-9 shows how effective dates are specified for an application user.

Sometimes the effective date restriction does not need to be an attribute of an application user or application role. Instead, it is only needed to restrict the effective dates on a per role grant basis. In this case, you can specify beginning and ending effective dates for an application role grant. This only constrains that particular application role grant and allows for implementing fine-grained access control policy. Example 2-10 shows how effective dates are specified for an application role.

These are the most direct consequences of effective date restrictions:

- If an application user is not currently effective (that is, within the period defined by its start and end date), the session for the particular application user cannot be created.

- If an application role is not currently effective, the application role (and any descendants) is not be available to the application user in the session.

- For application roles that are shared children of multiple application roles, the child application roles are available as long as there is at least one parent that is effective.

- If the application role grant of an application role is not currently effective, the application role (and any descendants) is not available to the application user or application role to which it is granted.

**Note:**

The effective dates should be used in the policy after a careful consideration of the nature of the restrictions that they impose on the use of application users and application roles.

Example 2-9 Setting Effective Dates for an Application User

    sqlplus sec_mgr
    Enter password: password
    Connected.

    DECLARE
     startDate TIMESTAMP := TO_TIMESTAMP (
          '2012-01-01 11:00:00','YYYY-MM-DD HH:MI:SS');
     endDate TIMESTAMP := TO_TIMESTAMP (
          '2013-01-01 11:00:00','YYYY-MM-DD HH:MI:SS');

    BEGIN
      SYS.XS_PRINCIPAL.CREATE_USER
          (name        => 'lwuser1',
          start_date   => startDate,
          end_date     => endDate);
    END;
    /

Example 2-10 Setting Effective Dates for an Application Role of an Application User

    sqlplus sec_mgr
    Enter password: password
    Connected.

    DECLARE
     startDate TIMESTAMP := TO_TIMESTAMP ('2012-01-01 11:00:00','YYYY-MM-DD
     HH:MI:SS');
     endDate TIMESTAMP := TO_TIMESTAMP ('2013-01-01 11:00:00','YYYY-MM-DD
     HH:MI:SS');
    BEGIN
      SYS.XS_PRINCIPAL.GRANT_ROLES
        (grantee      => 'lwuser1',
         role         => 'app_regular_role',
         start_date   => startDate,
         end_date     => endDate);
    END;
    /

### 2.4 About Granting Application Privileges to Principals

This section contains the following topics:

- About Granting an Application Role to an Application User

- Granting an Application Role to Another Application Role

- Granting a Database Role to an Application Role

#### 2.4.1 About Granting an Application Role to an Application User

This section contains the following topics:

##### 2.4.1.1 Creating a New Application User and Granting This User an Application Role

Example 2-11 shows how to grant an application role, `appl1_regular_role`, to an application user, `lwuser1`, when the application user account is created.

To find a listing of existing application roles, query the `DBA_XS_ROLES` data dictionary view.

Example 2-11 Creating a New Application User and Granting This User an Application Role

    sqlplus sec_mgr
    Enter password: password
    Connected.

    BEGIN
      SYS.XS_PRINCIPAL.CREATE_USER('lwuser1');
      SYS.XS_PRINCIPAL.GRANT_ROLES('lwuser1', 'appl1_regular_role');
    END;
    /

##### 2.4.1.2 Granting an Application Role to an Existing Application User

Example 2-12 shows how to grant an application role, `appl1_regular_role`, to an existing application user, `lwuser1`. You cannot grant dynamic application roles to an existing application user.

You can find a listing of existing application user accounts by querying the `DBA_XS_USERS` view.

Example 2-12 Granting an Application Role to an Existing Application User

    sqlplus sec_mgr
    Enter password: password
    Connected.

    BEGIN
      SYS.XS_PRINCIPAL.GRANT_ROLES('lwuser1', 'appl1_regular_role');
    END;
    /

#### 2.4.2 Granting an Application Role to Another Application Role

Example 2-13 shows how to grant a regular application role to another regular application role. You cannot grant dynamic application roles to other regular application roles, but you can grant other regular application roles to dynamic application roles. To find a listing of existing application roles, query the `DBA_XS_ROLES` view (see "[DBA_XS_ROLES](real-application-security-data-dictionary-views.md)").

Example 2-13 Granting a Regular Application Role to Another Regular Application Role

    sqlplus sec_mgr
    Enter password: password
    Connected.

    BEGIN
      SYS.XS_PRINCIPAL.GRANT_ROLES(grantee => 'app_regular_role', role => 'appl1_regular_role');
    END;
    /

#### 2.4.3 Granting a Database Role to an Application Role

To grant a database role to an application role, use the SQL `GRANT` statement. You can find a listing of existing database roles by querying the `DBA_ROLES` data dictionary view.

Example 2-14 shows how to grant the database role, `cust_role`, to the application role `app_regular_role`.

Example 2-14 Granting a Database Role to an Application Role

    sqlplus sec_mgr
    Enter password: password
    Connected.

    GRANT cust_role TO app_regular_role;
