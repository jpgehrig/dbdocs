Simulation mode writes violations to the simulation log instead of preventing SQL execution to quickly test new and modified Oracle Database Vault controls.

- About Simulation Mode
  Simulation mode enables you to capture violations in a simulation log instead of blocking SQL execution by Oracle Database Vault realms and command rules.
- Simulation Mode Use Cases
  Simulation mode is useful for testing a development configuration of new realms and command rules.
- Logging Realms in Simulation Mode
  You can set both regular and mandatory realms in simulation mode.
- Tutorial: Tracking Violations to a Realm Using Simulation Mode
  This tutorial shows how to create a realm that uses simulation mode and then test violations to the realm.

### 10.1 About Simulation Mode

Simulation mode enables you to capture violations in a simulation log instead of blocking SQL execution by Oracle Database Vault realms and command rules.

Simulation mode stores the errors that are captured in one location for easy analysis. To use simulation mode, when you create or update a realm or command rule, instead of enabling or disabling the realm or command rule, you can set it to simulation mode. The realm or command rule is still enabled, but because violations are not blocked and are instead recorded to the simulation log file, you can test it for any potential errors before you enable it for a production environment. When simulation mode is enabled, the report may include violations for multiple realms or command rules. For more detailed reports that can help you better identify the source of user SQL statements, you can configure simulation mode to include the PL/SQL call stack. The call stack captures the calling procedures and functions recursively to better troubleshoot the Database Vault audit records. Call stack information is stored in the `PL_SQL_STACK` column in the `DVSYS.DBA_DV_SIMULATION_LOG` data dictionary view.

For example, the following creation statement for a realm enables simulation mode and generates the PL/SQL call stack:

    BEGIN
     DBMS_MACADM.CREATE_REALM(
     realm_name    => 'HR Apps',
     description   => 'Realm to protect the HR realm',
     enabled       => DBMS_MACUTL.G_SIMULATION,
     audit_options => DBMS_MACUTL.G_REALM_AUDIT_FAIL,
     realm_type    => 1,
     realm_scope   => DBMS_MACUTL.G_SCOPE_LOCAL,
     pl_sql_stack  => TRUE);
    END;
    /

At this stage, SQL statements that violate realms or command rules are still able to execute, but these activities are recorded to the `DBA_DV_SIMULATION_LOG` data dictionary view. For example, the following query finds violations against the HR Apps realm and any other realms or command rules that have been configured for simulation mode:

    SELECT USERNAME, COMMAND, SQLTEXT, VIOLATION_TYPE
    FROM DBA_DV_SIMULATION_LOG, TABLE(DBA_DV_SIMULATION_LOG.REALM_NAME) RN
    WHERE RN.COLUMN_VALUE = "HR APPS";

    USERNAME  COMMAND    SQLTEXT                          VIOLATION_TYPE

    --------  ---------- -------------------------------  --------------
    DGRANT    SELECT     SELECT SALARY FROM HR.EMPLOYEES; Realm Violation

After you have completed testing the realm or command rule, a user who has been granted the `DV_ADMIN` or `DV_OWNER` role can clear the `DBA_DV_SIMULATION_LOG` data dictionary view by deleting the contents of the underlying table of this view, `DVSYS.SIMULATION_LOG$`.

For example:

    DELETE FROM DVSYS.SIMULATION_LOG$;

Or:

    DELETE FROM DVSYS.SIMULATION_LOG$ WHERE COMMAND = 'SELECT';

**Parent topic:** Using Simulation Mode for Logging Realm and Command Rule Activities

### 10.2 Simulation Mode Use Cases

Simulation mode is useful for testing a development configuration of new realms and command rules.

Use cases are as follows:

- Application certification

  When you are certifying applications, you can use simulation mode as follows in an application test environment:

  1.  Put all schemas for the application into mandatory realms with simulation mode enabled.

  2.  Run a full regression test.

  3.  Analyze the simulation mode log by querying the `DBA_DV_SIMULATION_LOG` data dictionary view to find who can access these schemas.

  4.  Update the realms with new authorizations, and the enable the realms (that is, not using simulation mode).

  5.  Re-run the regression test.

- Introduction of a new command rule

  You can use simulation mode on a production database that has Oracle Database Vault enabled.

  1.  Put the new command rule into production in simulation mode for however many weeks that are necessary.

  2.  Analyze the simulation mode log by querying `DBA_DV_SIMULATION_LOG` to determine if the command rule is working correctly.

  3.  Make changes to the command rule as necessary.

  4.  Enable the command rule.

- Putting a new realm into a production database in simulation mode.

  This method can help to find the system context information needed to set the trusted path rules in rule sets and find authorized users for realms.

  1.  Create the new realm in mandatory mode and add the protected objects

  2.  Do not add any authorized users.

  3.  Run applications and development operations from the normal IP addresses that will be used.

  4.  Check the simulation log file for both authorized users and system context information that you can use to create trusted paths.

  5.  Create the trusted paths, and then add the authorized users.

  6.  Clear the simulation log and run the application and development operation tasks again.

  7.  After a period of time, review the simulation log. If all the controls were updated correctly, then the simulation log is empty. Log entries in the simulation mode indicate additional changes that you need to make to the realm and rule sets or the log entries may indicate a malicious use.

**Parent topic:** Using Simulation Mode for Logging Realm and Command Rule Activities

### 10.3 Logging Realms in Simulation Mode

You can set both regular and mandatory realms in simulation mode.

- Considerations When Logging Realms in Simulation Mode
  There are several use cases to consider if you want to use realms in simulation mode.
- Use Case: All New Realms in Simulation Mode
  In this use case, all realms are either mandatory or regular and all user-created realms are in simulation mode.
- Use Case: New Realms Introduced to Existing Realms
  In this use case, you add a set of new realms to a database that has an existing set of realms.
- Use Case: Testing the Addition of New Objects in a Realm
  In this use case, you add new objects to an existing realm and then test it using simulation mode without removing the current realm protections.
- Use Case: Testing the Removal of Objects from a Realm
  In this use case, you test the removal of objects to an existing realm.
- Use Case: Testing the Addition of an Authorized User to a Realm
  In this use case, you loosen security controls by adding more users. You do not need to simulate anything if you are simply adding more authorized users.
- Use Case: Testing the Removal of an Authorized User from a Realm
  In this use case, you want to drop an authorized user and use simulation mode to check if the user still needs to access the realm.
- Use Case: Testing New Factors with Realms
  In this use case, you want to test changes to factors.
- Use Case: Testing Changes to an Existing Command Rule
  In this use case, you test changes to an existing command rule while keeping the original command rule enabled.

**Parent topic:** Using Simulation Mode for Logging Realm and Command Rule Activities

#### 10.3.1 Considerations When Logging Realms in Simulation Mode

There are several use cases to consider if you want to use realms in simulation mode.

- Testing an application with all new Database Vault controls: all realms are in simulation mode

- Adding a realm to existing working Database Vault controls: only a subset of realms are in simulation mode

- Adding new objects to an existing enabled realm and then testing the difference with simulation mode and not disabling existing controls

- Dropping one or more existing objects from an existing enabled realm and then testing the difference with simulation mode and not disabling existing controls

- Adding new authorized users to an existing enabled realm and then testing the difference with simulation mode and not disabling existing controls

- Dropping one or more existing authorized users from an existing enabled realm and then testing the difference with simulation mode and not disabling existing controls

- Adding or changing factors in an existing enabled realm and then testing the difference with simulation mode and not disabling existing controls

- Testing changes to a command rule in production while keeping the original command rule enabled

When a user executes a SQL statement and it fails, it may fail for realms that are enabled, fail for realms that are simulated, or it could fail for both of these reasons. There could be mandatory realms, regular realms, or both. These conditions determine the data that is captured in the simulation log.

After you create the use cases that are described in the next sections, regular realms are completely overpowered by mandatory realms when an object has both types of realms protecting it. In all cases where mandatory and regular realms protect the same object, regular realms can be ignored with regard to simulation logs. Only mandatory realm failures are captured in the simulation logs. The only time regular realm failures are entered into the simulation log is when all realms for an object are regular realms. And then, the following must happen for regular realms to be written to the simulation log:

- All regular realms in simulation mode fails and

- All regular realms that are enabled also fail

If at least one enabled or simulation regular realm succeeds, then no simulation regular realms are logged.

**Parent topic:** Logging Realms in Simulation Mode

#### 10.3.2 Use Case: All New Realms in Simulation Mode

In this use case, all realms are either mandatory or regular and all user-created realms are in simulation mode.

Examples are as follows:

- Mandatory realms only, which are all in simulation mode

  - The user is authorized to execute the SQL statement in all mandatory realms. Nothing is captured in the simulation log table.

  - The user fails one or more mandatory realm checks. All realm check failures are logged to the simulation log. Mandatory realm checks where the user’s SQL statement succeeded is not logged.

    In this example, there are three mandatory realms. The user SQL statement succeeds with one realm and fails with the other two. Only the two failed realm checks are recorded in the simulation log.

- Regular realms only, which are all in simulation mode

  - The user is authorized to execute the SQL statement in at least one regular realm. The user should have access to the data so nothing is logged to the simulation log.

  - The user is not authorized to execute the SQL statement in all regular realms. The simulation log captures all the failed realm authorization failures. This enables the user to select which realm to which the user should be authorized. The SQL only needs to be authorized in one regular realm to work and not all regular realms need to be updated to authorize the SQL.

- Mix of mandatory and regular realms, which are all in simulation mode

  - In this case, you capture the key realms when a user is rejected. In the case with mandatory and regular realms, the mandatory realms are the key realms. All mandatory realms must pass the authorization check for the user to gain access. In fact, regular realms could be considered superfluous when mandatory realms are protecting an object. So in cases where there are both mandatory and regular realms protecting the same object, it is only the mandatory realms that control if the SQL statement is blocked or allowed to execute. It does not matter whether the user was authorized to the regular realm or not. This example follows the rules for the first scenario, for mandatory realms in simulation mode.

  - The user is authorized to execute the SQL statement in all mandatory realms. Nothing is captured in the simulation log table. Even though the user may succeed or fail in one or more regular realms, nothing about regular realm failure is captured.

  - The user fails one or more mandatory realm checks. All realm check failures are logged to the simulation log. Mandatory realm checks where the user SQL statement succeeded are not be logged.

    For example, there are three mandatory realms. The user SQL statement succeeds with one realm and fails with the other two. Only the two failed realm checks are recorded in the simulation log.

    No regular realms need to be captured, because only the mandatory realms need to be captured in the simulation log.

**Parent topic:** Logging Realms in Simulation Mode

#### 10.3.3 Use Case: New Realms Introduced to Existing Realms

In this use case, you add a set of new realms to a database that has an existing set of realms.

The existing realms are enabled and working. The new realms are in simulation mode. This use case applies only if both simulation and enabled realms are protecting the same object.

Examples:

- New mandatory realms in simulation mode with existing enabled mandatory realms. This use case shows some additional mandatory realms for an object: adding more security to an existing object.

  - Enabled mandatory realms and mandatory realms in simulation mode all successful with user SQL statement: in this case, the SQL executes normally and nothing is captured

  - Enabled mandatory realms (at least one) fails and mandatory realms in simulation mode all successful: SQL is blocked and nothing is written to the simulation log

  - Enabled mandatory realms (at least one) fails and mandatory realms in simulation mode has one or more failures: SQL is blocked and all failing mandatory realms in simulation mode are entered into simulation log

  - Enabled mandatory realms all successful and mandatory realms in simulation mode have at least one failure: SQL is not blocked, all failed mandatory realms in simulation mode entered into simulation log

- New regular realms in simulation mode with existing enabled regular realms: More regular realms are added to a security object, providing new ways for users to access sensitive data

  - Enabled regular realms (at least one) and regular realms in simulation mode (at least one) successful: the user SQL executes normally with nothing written to simulation log

  - Enabled regular realms (at least one) is successful, and regular realms in simulation mode all fail: user SQL executes normally, nothing is entered into the simulation log

  - Enabled regular realms all fail and regular realms in simulation mode all fail: the user SQL is blocked and all regular realms in simulation mode are entered into simulation log. The user must evaluate which regular realm to authorize to if needed. The current implementation blocks the SQL and does not add the regular realms in simulation mode into the simulation log because the enabled regular realm would have blocked it anyway. This must change because the user may have added a new realm to authorize the SQL in this use case. There is no way to tell what happened if the new SQL should have worked, but is blocked by all regular realms in simulation mode as well (when one of the regular realms in simulation mode was designed to allow it to work). This would simulate an entry into the audit log for this situation.

  - Enabled regular realms all fail and regular realms in simulation mode (at least one) successful: the user SQL is blocked and nothing is written to the simulation log.

- New regular realms with existing enabled mandatory realms: You do not need to do anything in this situation. The enabled mandatory realms will continue to control the objects and the new regular realms in simulation mode will have no impact if they are enabled or not. No simulation logs should be generated in this case.

- New mandatory realms in simulation mode with existing enabled regular realm: While the enabled regular realm controls the objects for now, when the new mandatory realms in simulation mode are enabled, then they will have full control over the objects with no control by the older enabled regular realms. So, simulation logs will be created for all mandatory realms. This is the same as the scenario for new mandatory realms with existing enabled mandatory realms.

- New regular realms in simulation mode with existing enabled mandatory and regular realms: The enabled mandatory realms will be the deciding realms whether the new regular realms in simulation mode are added to the existing enabled regular realms in the system. This is the same as the scenario as a mix of mandatory and regular realms, all in simulation mode. Nothing is written to the simulation logs.

- New mandatory realms in simulation mode with enabled mandatory and regular realms: The enabled regular realms can be ignored. This is the same as the scenario for new mandatory realms with existing enabled mandatory realms.

- Mix of new mandatory and regular realms in simulation mode with existing enabled mandatory and regular realms: Ignore all enabled and mandatory regular realms. This is simply adding more mandatory realms to an existing object. This is the same scenario as new mandatory realms with existing enabled mandatory realms.

**Parent topic:** Logging Realms in Simulation Mode

#### 10.3.4 Use Case: Testing the Addition of New Objects in a Realm

In this use case, you add new objects to an existing realm and then test it using simulation mode without removing the current realm protections.

Oracle recommends that you create a duplicate realm in simulation mode for the new objects with the same authorized users and rule sets. This way, the existing realm can continue to provide protection to the existing objects while testing the new object.

**Parent topic:** Logging Realms in Simulation Mode

#### 10.3.5 Use Case: Testing the Removal of Objects from a Realm

In this use case, you test the removal of objects to an existing realm.

Because you are removing security controls for an existing object, there is no need to use simulation mode. Simply remove the object from the realm.

**Parent topic:** Logging Realms in Simulation Mode

#### 10.3.6 Use Case: Testing the Addition of an Authorized User to a Realm

In this use case, you loosen security controls by adding more users. You do not need to simulate anything if you are simply adding more authorized users.

If you are adding new functionality that is accessing data in a realm, but are not sure which new database users to authorize to the realm, then simply run the new functionality as a test (which will be blocked if not already authorized). Review the Database Vault audit logs to see the user name that attempted to access the realm data and add any new database users that are now authorized.

**Parent topic:** Logging Realms in Simulation Mode

#### 10.3.7 Use Case: Testing the Removal of an Authorized User from a Realm

In this use case, you want to drop an authorized user and use simulation mode to check if the user still needs to access the realm.

You may not be sure about dropping this user because you must check if the authorized user is accessing the realm for authorized activities.

If the data is only protected by a regular realm, then you can clone the realm with authorized users as the only difference. Remove the user to be dropped from the original realm and then add this user to the cloned realm. Then the cloned realm’s audit setting is changed to capture `audit on success`. This enables the dropped user to be visible in the audit records if they accessed the realm over a period of time. Audit policies can also be used in this case. For data that is protected by a mandatory realm, the best solution is to create an audit policy.

**Parent topic:** Logging Realms in Simulation Mode

#### 10.3.8 Use Case: Testing New Factors with Realms

In this use case, you want to test changes to factors.

There are two scenarios where the factors can change:

- Changes to an application or the infrastructure that force a change to the factors

  In this case, you do not need to keep the original factors in place. However, objects and authorized users should be able to remain enabled during the testing of the new factors. With an enabled realm, you can remove the factors from the authorized users. At the same time, create a mandatory realm for the same protected objects in simulation mode with no authorized users. The regular realm will protect the objects from unauthorized users while the simulation realm will capture all access along with the factor information. The simulation log can then be mined for each user to come up with the new factors which can then be added to the mandatory realm in simulation mode to make sure it’s clean before being migrated to the original regular realm.

- No changes to the application or the infrastructure but changes such as new factors being added or factors being removed take place

  When factors are being added, you must clone a second simulation realm from the original, but with the new factors added in. If the simulation logs shows that the usage is clean, then you can safely introduce the new factors into the original realm.

  Dropping factors lowers the security profile, so you can simply drop the factor from the rule set. No testing needs to be done.

**Parent topic:** Logging Realms in Simulation Mode

#### 10.3.9 Use Case: Testing Changes to an Existing Command Rule

In this use case, you test changes to an existing command rule while keeping the original command rule enabled.

Command rules may need to be updated and ideally tested before the changes are enabled in production. For a new command rule that will be added to a set of already existing command rules, put the new command rule into simulation mode when you create it. The other pre-existing command rules are already enabled and offer protection.

If you want to modify an existing command rule, there is no way to maintain the existing protection and test the new modification. Oracle recommends that you create an audit policy to capture what the original command rule was doing and then set an alert for it. The audit will not prevent the SQL as a command rule would do, but at least you can be alerted about the action. Then you can put the new updated command rule into simulation mode and test it.

**Parent topic:** Logging Realms in Simulation Mode

### 10.4 Tutorial: Tracking Violations to a Realm Using Simulation Mode

This tutorial shows how to create a realm that uses simulation mode and then test violations to the realm.

- About This Tutorial
  In this tutorial, you will create a realm around the `HR.EMPLOYEES` table and test violations against it.
- Step 1: Create Users for This Tutorial
  You must create three users for this tutorial.
- Step 2: Create a Realm and an Oracle Database Vault Policy
  Next, you create a realm around the `HR.EMPLOYEES` table, and then add this realm to an Oracle Database Vault policy.
- Step 3: Test the Realm and Policy
  User `tjones_dba` will commit a violation on the realm to test the realm and policy.
- Step 4: Query the DBA_DV_SIMULATION_LOG View for Violations
  Now you can check the simulation mode log for the violations that user `tjones_dba` committed.
- Step 5: Enable and Re-test the Realm
  Now that you have captured the violations, user `psmith` can update the `HR.EMPLOYEES_pol` policy.
- Step 6: Remove the Components for This Tutorial
  You can remove the components that you created for this tutorial if you no longer need them.

**Parent topic:** Using Simulation Mode for Logging Realm and Command Rule Activities

#### 10.4.1 About This Tutorial

In this tutorial, you will create a realm around the `HR.EMPLOYEES` table and test violations against it.

The `HR.EMPLOYEES` table contains confidential data such employee salaries. To test the realm, an administrator, `tjones_dba`, will look up and modify the salary of another employee, `smavris`. The Database Vault administrator, `sec_admin_owen`, will use simulation mode to track the violations to the `HR.EMPLOYEES` table. To accomplish this, user `sec_admin_owen` will create a Database Vault policy, which a delegated administrator, user `psmith`, will own. User `psmith` will then be able to make limited changes to the policy without needing the `DV_OWNER` or `DV_ADMIN` role.

**Parent topic:** Tutorial: Tracking Violations to a Realm Using Simulation Mode

#### 10.4.2 Step 1: Create Users for This Tutorial

You must create three users for this tutorial.

The users are: `psmith`, who is the Database Vault policy owner; `tjones_dba`, who commits violations on the `HR.EMPLOYEES` table; and `smavris`, whose salary is the recipient of `tjones_dba`’s violations.

1.  Log into the database instance as a user who has been granted the `DV_ACCTMGR` role.
    For example:

        sqlplus accts_admin_ace
        Enter password: password

    In a multitenant environment, you must log in to the appropriate pluggable database (PDB). For example:

        CONNECT accts_admin_ace@hrpdb
        Enter password: password

    To find the available PDBs, run the `show pdbs` command. To check the current PDB, run the `show con_name` command.
2.  Create the following users and grant them the `CREATE SESSION` privilege.
        GRANT CREATE SESSION TO psmith IDENTIFIED BY password;
        GRANT CREATE SESSION TO tjones_dba IDENTIFIED BY password;
        GRANT CREATE SESSION TO smavris IDENTIFIED BY password;

    Follow the guidelines in [Oracle Database Security Guide](../dbseg/configuring-authentication.md) to replace `password` with a password that is secure.
3.  Connect as a user who has been granted the `DV_OWNER` role.
    For example:
        CONNECT sec_admin_owen -- Or, sec_admin_owen@hrpdb
        Enter password: password
4.  Grant user `psmith` the `DV_POLICY_OWNER` role, which enables `psmith` to manage Database Vault policies.
        GRANT DV_POLICY_OWNER TO psmith;
5.  Connect as user `SYS` with the `SYSDBA` administrative privilege.
        CONNECT SYS AS SYSDBA -- Or, CONNECT SYS@hrpdb AS SYSDBA
        Enter password: password
6.  Grant the `DBA` role to user `tjones_dba`
        GRANT DBA TO tjones_dba;
7.  Connect as the `HR` schema owner.
        CONNECT HR -- Or, HR@hrpdb
        Enter password: password
8.  Grant the `SELECT` privilege on the `HR.EMPLOYEES` table to user `smavris`
        GRANT SELECT ON HR.EMPLOYEES TO smavris;

At this stage, the users have all been created and granted the appropriate privileges.

**Parent topic:** Tutorial: Tracking Violations to a Realm Using Simulation Mode

#### 10.4.3 Step 2: Create a Realm and an Oracle Database Vault Policy

Next, you create a realm around the `HR.EMPLOYEES` table, and then add this realm to an Oracle Database Vault policy.

1.  Connect as a user who has been granted the `DV_OWNER` role.
    For example:

        CONNECT sec_admin_owen -- Or, sec_admin_owen@hrpdb
        Enter password: password
2.  Create the realm around `HR.EMPLOYEES` table as follows.
    These procedures create the `HR.EMPLOYEES_realm` realm, add the `HR.EMPLOYEES` table to this realm, authenticate `HR` as an owner, authenticate user `psmith` as an participant, and set the realm in simulation mode.

        BEGIN
         DBMS_MACADM.CREATE_REALM(
          realm_name    => 'HR.EMPLOYEES_realm',
          description   => 'Realm to protect HR.EMPLOYEES',
          enabled       => DBMS_MACUTL.G_SIMULATION,
          audit_options => DBMS_MACUTL.G_REALM_AUDIT_FAIL,
          realm_type    => 0);
        END;
        /

        BEGIN
         DBMS_MACADM.ADD_OBJECT_TO_REALM(
          realm_name   => 'HR.EMPLOYEES_realm',
          object_owner => 'HR',
          object_name  => 'EMPLOYEES',
          object_type  => 'TABLE');
        END;
        /
3.  Create the `HR.EMPLOYEES_pol` Database Vault policy and set it to be in simulation mode.
    These procedures create the `HR.EMPLOYEES_pol` policy, add the realm that was just created to the policy, and then add user `psmith` as the owner of the policy.

        BEGIN
         DBMS_MACADM.CREATE_POLICY(
          policy_name  => 'HR.EMPLOYEES_pol',
          description  => 'Policy to protect HR.EMPLOYEES',
          policy_state => DBMS_MACADM.G_SIMULATION);
        END;
        /

        BEGIN
         DBMS_MACADM.ADD_REALM_TO_POLICY(
          policy_name  => 'HR.EMPLOYEES_pol',
          realm_name   => 'HR.EMPLOYEES_realm');
        END;
        /

        BEGIN
         DBMS_MACADM.ADD_OWNER_TO_POLICY(
          policy_name  => 'HR.EMPLOYEES_pol',
          owner_name   => 'PSMITH');
        END;
        /

At this point, the realm and policy are ready to be tested.

**Parent topic:** Tutorial: Tracking Violations to a Realm Using Simulation Mode

#### 10.4.4 Step 3: Test the Realm and Policy

User `tjones_dba` will commit a violation on the realm to test the realm and policy.

1.  Connect as user `tjones_dba`.
        CONNECT tjones_dba -- Or, tjones_dba@hrpdb
        Enter password: password
2.  Query the `HR.EMPLOYEES` table for the salary of `smavris`.
        SELECT SALARY FROM HR.EMPLOYEES WHERE EMAIL = 'SMAVRIS';

    Output similar to the following should appear:

            SALARY
        ----------
              6500
3.  Cut `smavris`’s salary in half.
        UPDATE HR.EMPLOYEES
        SET SALARY = SALARY / 2
        WHERE EMAIL = 'SMAVRIS';

        1 row updated.
4.  Connect as user `smavris`.
        CONNECT smavris -- Or, smavris@hrpdb
5.  Query the salary of `smavris`.
        SELECT SALARY FROM HR.EMPLOYEES WHERE EMAIL = 'SMAVRIS';

    Output similar to the following should appear:

            SALARY
        ----------
              3250

At this point, `tjones_dba`’s violations have been recorded in the `DBA_DV_SIMULATION_LOG` data dictionary view.

**Parent topic:** Tutorial: Tracking Violations to a Realm Using Simulation Mode

#### 10.4.5 Step 4: Query the DBA_DV_SIMULATION_LOG View for Violations

Now you can check the simulation mode log for the violations that user `tjones_dba` committed.

1.  Connect as a user who has been granted the `DV_OWNER` role.
    For example:
        CONNECT sec_admin_owen -- Or, leo_dvowner@hrpdb
        Enter password: password
2.  Query the `DBA_DV_SIMULATION_LOG` data dictionary view.
        SELECT USERNAME, COMMAND, SQLTEXT, VIOLATION_TYPE
        FROM DBA_DV_SIMULATION_LOG, TABLE(DBA_DV_SIMULATION_LOG.REALM_NAME) RN
        WHERE RN.COLUMN_VALUE = 'HR.EMPLOYEES_realm';

    Output similar to the following should appear:

        USERNAME
        --------------------------------------------------------------------------------
        COMMAND
        --------------------------------------------------------------------------------
        SQLTEXT
        --------------------------------------------------------------------------------
        VIOLATION_TYPE
        --------------------------------------------------------------------------------
        TJONES_DBA
        UPDATE
        UPDATE HR.EMPLOYEES SET SALARY = SALARY / 2 WHERE EMAIL = 'SMAVRIS'
        Realm Violation

        USERNAME
        --------------------------------------------------------------------------------
        COMMAND
        --------------------------------------------------------------------------------
        SQLTEXT
        --------------------------------------------------------------------------------
        VIOLATION_TYPE
        --------------------------------------------------------------------------------
        TJONES_DBA
        SELECT
        SELECT SALARY FROM HR.EMPLOYEES WHERE EMAIL = 'SMAVRIS'
        Realm Violation

The output indicates that user `tjones_dba` has committed two offences: first, he looked at another employee’s salary, and not only that, he cut it in half. The violation type is a realm violation. The query by `smavris` was not captured because she legitimately can look at her salary.

**Parent topic:** Tutorial: Tracking Violations to a Realm Using Simulation Mode

#### 10.4.6 Step 5: Enable and Re-test the Realm

Now that you have captured the violations, user `psmith` can update the `HR.EMPLOYEES_pol` policy.

This is so that the `HR.EMPLOYEES_realm` realm can be enabled. Then you can test the violations again.

1.  Connect as user `psmith`.
        CONNECT psmith -- Or, psmith@hrpdb
        Enter password: password
2.  Update the policy so that it is enabled.
        BEGIN
         DBMS_MACADM.UPDATE_POLICY_STATE(
          policy_name   => 'HR.EMPLOYEES_pol',
          policy_state  => 1);
        END;
        /
3.  Connect as user `tjones_dba`.
        CONNECT tjones_dba --Or, tjones_dba@hrpdb
4.  Try lowering `smavris`’s salary to new depths.
        UPDATE HR.EMPLOYEES
        SET SALARY = SALARY / 2
        WHERE EMAIL = 'SMAVRIS';

    Output similar to the following should appear:

        ERROR at line 1:
        ORA-01031: insufficient privileges

    The policy, now enabled, enables the realm to protect the `HR.EMPLOYEES` table. `smavris`’s salary can shrink no more.

**Parent topic:** Tutorial: Tracking Violations to a Realm Using Simulation Mode

#### 10.4.7 Step 6: Remove the Components for This Tutorial

You can remove the components that you created for this tutorial if you no longer need them.

1.  Connect as a user who has been granted the `DV_OWNER` role.
    For example:
        CONNECT sec_admin_owen -- Or, leo_dvowner@hrpdb
        Enter password: password
2.  Remove the `HR.EMPLOYEES_pol` Database Vault policy.
        EXEC DBMS_MACADM.DROP_POLICY('HR.EMPLOYEES_pol');

    You first must remove the policy before you can drop its contents.
3.  Remove the `HR.EMPLOYEES_realm` realm.
        EXEC DBMS_MACADM.DELETE_REALM('HR.EMPLOYEES_realm');
4.  Remove the simulation mode log data that was accumulated.
    Because the simulation mode log only captured information about user `tjones_dba`, you can remove only the rows that relate to this user.

        DELETE FROM DVSYS.SIMULATION_LOG$ WHERE USERNAME = 'TJONES_DBA';
5.  Connect as user `HR`.
        CONNECT HR -- Or, CONNECT HR@hrpdb
        Enter password: password
6.  Revert `smavris`’s salary back to its pre-violated state.
        UPDATE HR.EMPLOYEES
        SET SALARY = 6500
        WHERE EMAIL = 'SMAVRIS';
7.  Connect as a user who has been granted the `DV_ACCTMGR` role.
    For example:

        CONNECT accts_admin_ace -- Or, accts_admin_ace@hrpdb
        Enter password: password
8.  Remove the users `psmith`, `smavris`, and `tjones_dba`.
        DROP USER psmith;
        DROP USER smavris;
        DROP USER tjones_dba;

**Parent topic:** Tutorial: Tracking Violations to a Realm Using Simulation Mode
