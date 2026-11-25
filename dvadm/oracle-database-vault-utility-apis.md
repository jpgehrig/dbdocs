Oracle Database Vault provides a set of utility APIs in the `DBMS_MACUTL` PL/SQL package.

- DBMS_MACUTL Constants
  You can use a set of constants, available in the `DBMS_MACUTL` PL/SQL package.
- DBMS_MACUTL Package Procedures and Functions
  The `DBMS_MACUTL` PL/SQL package can perform tasks such as finding a time value or whether a user has the the appropriate privileges.

### 20.1 DBMS_MACUTL Constants

You can use a set of constants, available in the `DBMS_MACUTL` PL/SQL package.

- DBMS_MACUTL Listing of Constants
  The `DBMS_MACUTL` PL/SQL package provides constants (fields) to use with Oracle Database Vault PL/SQL packages.
- Example: Creating a Realm Using DBMS_MACUTL Constants
  Constants can be used to answer simple Yes or No settings when you create objects in Oracle Database Vault.
- Example: Creating a Rule Set Using DBMS_MACUTL Constants
  Constants can be used to set options such as the type of auditing used or fail options.
- Example: Creating a Factor Using DBMS_MACUTL Constants
  Constants can be used to set information specific to factors, such as identity or labeling.

**Parent topic:** Oracle Database Vault Utility APIs

#### 20.1.1 DBMS_MACUTL Listing of Constants

The `DBMS_MACUTL` PL/SQL package provides constants (fields) to use with Oracle Database Vault PL/SQL packages.

Table 20-1 summarizes constant (that is, fields) descriptions for the `DBMS_MACUTL` package.

Many of these constants have equivalents in the Oracle Database Vault package. For example, the `enabled` parameter, which is available in several procedures, can accept either `Y` (for Yes) or the constant `G_YES`. Choosing one over the other is a matter of personal preference. They both have the same result.

Table 20-1 DBMS_MACUTL Listing of Constants

| Constant Name                 | Data Type           | Description                                                                                                                                                                                                                                                                            |
|:------------------------------|:--------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `G_ALL_OBJECT`                | `VARCHAR2(1)`       | Used with the realm API `object_name` and `object_type` parameters as a wildcard to indicate all object names or all object types.                                                                                                                                                     |
| `G_AUDIT_ALWAYS`              | `NUMBER`            | Used with the factor API `audit_options` parameter to enable an audit.                                                                                                                                                                                                                 |
| `G_AUDIT_OFF`                 | `NUMBER`            | Used with the factor API `audit_options` parameter to disable auditing.                                                                                                                                                                                                                |
| `G_AUDIT_ON_GET_ERROR`        | `NUMBER`            | Used with the factor API `audit_options` parameter to audit if the expression specified in the `get_expr` parameter returns an error.                                                                                                                                                  |
| `G_AUDIT_ON_GET_NULL`         | `NUMBER`            | Used with the factor API `audit_options` parameter to audit if the expression in the `get_expr` field is null.                                                                                                                                                                         |
| `G_AUDIT_ON_TRUST_LEVEL_NEG`  | `NUMBER`            | Used with the factor API `audit_options` parameter to audit if the trust level is negative.                                                                                                                                                                                            |
| `G_AUDIT_ON_TRUST_LEVEL_NULL` | `NUMBER`            | Used with the factor API `audit_options` parameter to audit if no trust level exists.                                                                                                                                                                                                  |
| `G_AUDIT_ON_VALIDATE_ERROR`   | `NUMBER`            | Used with the factor API `audit_options` parameter to audit if the validation function returns an error.                                                                                                                                                                               |
| `G_AUDIT_ON_VALIDATE_FALSE`   | `NUMBER`            | Used with the factor API `audit_options` parameter to audit if validation function is false.                                                                                                                                                                                           |
| `G_DISABLE`                   | `NUMBER`            | Used to disnable Oracle Database Vault policies and command rules                                                                                                                                                                                                                      |
| `G_ENABLE`                    | `NUMBER`            | Used to enable Oracle Database Vault policies and command rules                                                                                                                                                                                                                        |
| `G_EVAL_ON_ACCESS`            | `NUMBER`            | Used with the factor API `eval_options` parameter to reevaluate the factor each time it is accessed.                                                                                                                                                                                   |
| `G_EVAL_ON_SESSION`           | `NUMBER`            | Used with the factor API `eval_options` parameter to evaluate the factor only once, when the user logs in to the session.                                                                                                                                                              |
| `G_FAIL_SILENTLY`             | `NUMBER`            | Used with the `fail_options` parameter to fail and show no error message.                                                                                                                                                                                                              |
| `G_FAIL_WITH_MESSAGE`         | `NUMBER`            | Used with the `fail_options` parameter to fail and show an error message.                                                                                                                                                                                                              |
| `G_IDENTIFY_BY_CONSTANT`      | `NUMBER`            | Used with the factor API `identify_by` parameter: Fixed value in PL/SQL expression defined in the `get_expr` parameter.                                                                                                                                                                |
| `G_IDENTIFY_BY_CONTEXT`       | `NUMBER`            | Used with the factor API `identify_by` parameter to indicate context.                                                                                                                                                                                                                  |
| `G_IDENTIFY_BY_FACTOR`        | `NUMBER`            | Used with the factor API `identify_by` parameter for subfactors through the `factor_link$` table.                                                                                                                                                                                      |
| `G_IDENTIFY_BY_METHOD`        | `NUMBER`            | Used with the factor API `identify_by` parameter: Expression in `get_expr` field                                                                                                                                                                                                       |
| `G_IDENTIFY_BY_RULESET`       | `NUMBER`            | Used with the factor API `identify_by` parameter: Expression and Rule Set with the `factor_expr$` table                                                                                                                                                                                |
| `G_LABELED_BY_FACTORS`        | `NUMBER`            | Used with the factor API `labeled_by` parameter to derive the label from subfactor and merge algorithm.                                                                                                                                                                                |
| `G_LABELED_BY_SELF`           | `NUMBER`            | Used with the factor API `labeled_by` parameter to label the factor identities.                                                                                                                                                                                                        |
| `G_MAX_SESSION_LABEL`         | `VARCHAR2(30)`      | This is the highest label a user could set based on the factors. It does not consider the label for a user.                                                                                                                                                                            |
| `G_MIN_POLICY_LABEL`          | `VARCHAR2(30)`      | The label to which a factor with a null label defaults.                                                                                                                                                                                                                                |
| `G_NO`                        | `VARCHAR2(1)`       | Used with the following APIs:<br>• The factor API `label_indicator` parameter to indicate that a child factor linked to a parent factor does not contribute to the label of the parent factor in an Oracle Label Security integration.<br>• Any API that uses the `enabled` parameter. |
| `G_OLS_SESSION_LABEL`         | `VARCHAR2(30)`      | The Oracle Label Security session label for a user at the time `init_session` is run.                                                                                                                                                                                                  |
| `G_PARTIAL`                   | `NUMBER`            | Sets the enforcement state of the realms and command rules under an Oracle Database Vault policy to be changed individually                                                                                                                                                            |
| `G_REALM_AUDIT_FAIL`          | `NUMBER`            | Used with the realm API `audit_options` parameter to audit when the realm is violated.                                                                                                                                                                                                 |
| `G_REALM_AUDIT_OFF`           | `NUMBER`            | Used with the realm API `audit_options` parameter to disable auditing.                                                                                                                                                                                                                 |
| `G_REALM_AUDIT_SUCCESS`       | `NUMBER`            | Used with the realm API `audit_options parameter`: Audit on successful realm access                                                                                                                                                                                                    |
| `G_REALM_AUTH_OWNER`          | `NUMBER`            | Used with the realm API `auth_options` parameter to set the realm authorization to Owner.                                                                                                                                                                                              |
| `G_REALM_AUTH_PARTICIPANT`    | `NUMBER`            | Used with the realm API `auth_options` parameter to set the realm authorization to Participant.                                                                                                                                                                                        |
| `G_RULESET_AUDIT_FAIL`        | `NUMBER`            | Used with the rule set API `audit_options` parameter to audit on rule set failure.                                                                                                                                                                                                     |
| `G_RULESET_AUDIT_OFF`         | `NUMBER`            | Used with the rule set API `audit_options` parameter to disable auditing.                                                                                                                                                                                                              |
| `G_RULESET_AUDIT_SUCCESS`     | `NUMBER`            | Used with the rule set API `audit_options` parameter to audit on rule set success.                                                                                                                                                                                                     |
| `G_RULESET_EVAL_ALL`          | `NUMBER`            | Used with the rule set API `eval_options` parameter to enable the rule set to succeed if all rules evaluate to true.                                                                                                                                                                   |
| `G_RULESET_EVAL_ANY`          | `NUMBER`            | Used with the rule set API `eval_options` parameter to succeed if any of the rules evaluate to true.                                                                                                                                                                                   |
| `G_RULESET_FAIL_SHOW`         | `NUMBER`            | Used with the rule set API `fail_options` parameter to show an error message if the rule set fails.                                                                                                                                                                                    |
| `G_RULESET_FAIL_SILENT`       | `NUMBER`            | Used with the rule set API `fail_options` parameter to not show an error message if the rule set fails.                                                                                                                                                                                |
| `G_RULESET_HANDLER_FAIL`      | `NUMBER`            | Used with the rule set API `handler_options` parameter to call a handler (specified by the `handler` parameter) if the rule set fails.                                                                                                                                                 |
| `G_RULESET_HANDLER_OFF`       | `NUMBER`            | Used with the rule set API `handler_options` parameter to disable calls to a handler or if no handler is used.                                                                                                                                                                         |
| `G_RULESET_HANDLER_SUCCESS`   | `NUMBER`            | Used with the rule set API `handler_options` parameter to call a handler if the rule set succeeds.                                                                                                                                                                                     |
| `G_SIMULATION`                | `NUMBER`            | Used to set the enforcement state of a policy to simulation mode. This mode does not raise errors for realm or command rule violations. Instead, an error is logged in a designated log table with sufficient information relevant to the error (for example, users or SQL command.)   |
| `G_USER_POLICY_LABEL`         | `VARCHAR2(30)`      | This is what Oracle Label Security has decided the user's label should be set to after factoring in the preceding values.                                                                                                                                                              |
| `G_YES`                       | `VARCHAR2(1)`       | Used with the following APIs:<br>• The factor API `label_indicator` parameter to indicate that a child factor linked to a parent factor contributes to the label of the parent factor in an Oracle Label Security integration.<br>• Any API that uses the `enabled` parameter.         |

**Parent topic:** DBMS_MACUTL Constants

#### 20.1.2 Example: Creating a Realm Using DBMS_MACUTL Constants

Constants can be used to answer simple Yes or No settings when you create objects in Oracle Database Vault.

Example 20-1 shows how to use the `G_YES` and `G_REALM_AUDIT_FAIL` `DBMS_MACUTL` constants when creating a realm.

Example 20-1 Creating a Realm Using DBMS_MACUTL Constants

    BEGIN
     DBMS_MACADM.CREATE_REALM(
      realm_name    => 'Performance Statistics Realm',
      description   => 'Realm to measure performance',
      enabled       =>  DBMS_MACUTL.G_YES,
      audit_options =>  DBMS_MACUTL.G_REALM_AUDIT_FAIL);
    END;
    /

**Parent topic:** DBMS_MACUTL Constants

#### 20.1.3 Example: Creating a Rule Set Using DBMS_MACUTL Constants

Constants can be used to set options such as the type of auditing used or fail options.

Example 20-2 shows how to use several `DBMS_MACUTL` constants when creating a rule set.

Example 20-2 Creating a Rule Set Using DBMS_MACUTL Constants

    BEGIN
     DBMS_MACADM.CREATE_RULE_SET(
      rule_set_name    => 'Limit_DBA_Access',
      description      => 'DBA access through predefined processes',
      enabled          => DBMS_MACUTL.G_YES,
      eval_options     => DBMS_MACUTL.G_RULESET_EVAL_ALL,
      audit_options    => DBMS_MACUTL.G_RULESET_AUDIT_FAIL,
      fail_options     => DBMS_MACUTL.G_RULESET_FAIL_SHOW,
      fail_message     => 'Rule Set Limit_DBA_Access has failed.',
      fail_code        => 20000,
      handler_options  => DBMS_MACUTL.G_RULESET_HANDLER_FAIL,
      handler          => 'dbavowner.email_alert');
    END;
    /

**Parent topic:** DBMS_MACUTL Constants

#### 20.1.4 Example: Creating a Factor Using DBMS_MACUTL Constants

Constants can be used to set information specific to factors, such as identity or labeling.

Example 20-3 shows how to use constants when creating a factor.

Example 20-3 Creating a Factor Using DBMS_MACUTL Constants

    BEGIN
     DBMS_MACADM.CREATE_FACTOR(
      factor_name       => 'Sector2_DB',
      factor_type_name  => 'Instance',
      description       => ' ',
      rule_set_name     => 'DB_access',
      get_expr          => 'UPPER(SYS_CONTEXT(''USERENV'',''DB_NAME''))',
      validate_expr     => 'dbavowner.check_db_access',
      identify_by       => DBMS_MACUTL.G_IDENTIFY_BY_FACTOR,
      labeled_by        => DBMS_MACUTL.G_LABELED_BY_SELF,
      eval_options      => DBMS_MACUTL.G_EVAL_ON_SESSION,
      audit_options     => DBMS_MACUTL.G_AUDIT_ALWAYS,
      fail_options      => DBMS_MACUTL.G_FAIL_SILENTLY);
    END;
    /

**Parent topic:** DBMS_MACUTL Constants

### 20.2 DBMS_MACUTL Package Procedures and Functions

The `DBMS_MACUTL` PL/SQL package can perform tasks such as finding a time value or whether a user has the the appropriate privileges.

- CHECK_DVSYS_DML_ALLOWED Procedure
  The `CHECK_DVSYS_DML_ALLOWED` procedure checks if a user can issue Data Modification Language (DML) commands to access the `DVSYS` objects.
- GET_CODE_VALUE Function
  The `GET_CODE_VALUE` function finds the value for a code within a code group, and then returns a `VARCHAR2` value.
- GET_SECOND Function
  The `GET_SECOND` function returns the seconds in Oracle SS (seconds) format (00–59), and then returns a `NUMBER` value.
- GET_MINUTE Function
  The `GET_MINUTE` function returns the minute in Oracle MI (minute) format (00–59), in a `NUMBER` value.
- GET_HOUR Function
  The `GET_HOUR` function returns the hour in Oracle HH24 (hour) format (00–23), in a `NUMBER` value.
- GET_DAY Function
  The `GET_DAY` function returns the day in Oracle DD (day) format (01–31), in a `NUMBER` value.
- GET_MONTH Function
  The `GET_MONTH` function returns the month in Oracle MM (month) format (01–12), in a `NUMBER` value.
- GET_YEAR Function
  The `GET_YEAR` function returns the year in Oracle YYYY (year) format (0001–9999), in a `NUMBER` value.
- IS_ALPHA Function
  The `IS_ALPHA` function returns a `BOOLEAN` value indicating if a character is alphabetic.
- IS_DIGIT Function
  The `IS_DIGIT` function checks returns a `BOOLEAN` value indicating if a character is numeric.
- IS_DVSYS_OWNER Function
  The `IS_DVSYS_OWNER` function returns a `BOOLEAN` value indicating if a user is authorized to manage the Oracle Database Vault configuration.
- IS_OLS_INSTALLED Function
  The `IS_OLS_INSTALLED` function returns a `BOOLEAN` value indicating if Oracle Label Security is installed.
- IS_OLS_INSTALLED_VARCHAR Function
  The `IS_OLS_INSTALLED_VARCHAR` function returns a `BOOLEAN` value indicating if Oracle Label Security is installed.
- ROLE_GRANTED_ENABLED_VARCHAR Function
  The `ROLE_GRANTED_ENABLED_VARCHAR` function returns a `VARCHAR2` value indicating the role grant and enablement status of a user.
- USER_HAS_OBJECT_PRIVILEGE Function
  The `USER_HAS_OBJECT_PRIVILEGE` function returns a `BOOLEAN` value indicating if user or role can access an object through a single specified object privilege grant.
- USER_HAS_ROLE Function
  The `USER_HAS_ROLE` function returns a `BOOLEAN` value indicating if a user has a role privilege, directly or indirectly (through another role).
- USER_HAS_ROLE_VARCHAR Function
  The `USER_HAS_ROLE_VARCHAR` function returns a `VARCHAR2` value indicating if a user has a role privilege, directly or indirectly (through another role).
- USER_HAS_SYSTEM_PRIVILEGE Function
  The `USER_HAS_SYSTEM_PRIVILEGE` function returns a `BOOLEAN` value indicating if a user has a system privilege, directly or indirectly (through a role).

**Parent topic:** Oracle Database Vault Utility APIs

#### 20.2.1 CHECK_DVSYS_DML_ALLOWED Procedure

The `CHECK_DVSYS_DML_ALLOWED` procedure checks if a user can issue Data Modification Language (DML) commands to access the `DVSYS` objects.

##### Syntax

    DBMS_MACUTL.CHECK_DVSYS_DML_ALLOWED(
      p_user IN VARCHAR2 DEFAULT USER);

##### Parameter

Table 20-2 CHECK_DVSYS_DML_ALLOWED Parameter

| Parameter | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_user`  | User to check.<br>To find existing users in the current database instance, query the following views:<br>• `DBA_USERS`: Finds available users for the current database instance. See [Oracle Database Reference](../refrn/DBA_USERS.md).<br>• `DBA_DV_REALM_AUTH`: Finds the authorization of a particular user or role. See [DBA_DV_REALM_AUTH View](oracle-database-vault-data-dictionary-views.md).<br>• `DBA_DV_ROLE`: Finds existing secure application roles used in privilege management. See [DBA_DV_ROLE View](oracle-database-vault-data-dictionary-views.md). |

##### Example

User `SYSTEM` fails the check:

    EXEC DBMS_MACUTL.CHECK_DVSYS_DML_ALLOWED('system');

    ERROR at line 1:
    ORA-47920: Authorization failed for user system to perform this operation
    ORA-06512: at "DBMS_MACUTL", line 23
    ORA-06512: at "DBMS_MACUTL", line 372
    ORA-06512: at "DBMS_MACUTL", line 508
    ORA-06512: at "DBMS_MACUTL", line 572
    ORA-06512: at line 1

User `sec_admin_owen`, who has the `DV_OWNER` role, passes the check:

    EXEC DBMS_MACUTL.CHECK_DVSYS_DML_ALLOWED('sec_admin_owen');

    PL/SQL procedure successfully completed.

**Parent topic:** DBMS_MACUTL Package Procedures and Functions

#### 20.2.2 GET_CODE_VALUE Function

The `GET_CODE_VALUE` function finds the value for a code within a code group, and then returns a `VARCHAR2` value.

##### Syntax

    DBMS_MACUTL.GET_CODE_VALUE(
      p_code_group IN VARCHAR2,
      p_code       IN VARCHAR2)
    RETURN VARCHAR2;

##### Parameters

Table 20-3 GET_CODE_VALUE Parameters

| Parameter      | Description                                                                                                                                                                                                                              |
|:---------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_code_group` | Code group (for example, `AUDIT_EVENTS` or `BOOLEAN`).<br>To find available code groups in the current database instance, query the `DBA_DV_CODE` view, described in [DBA_DV_CODE View](oracle-database-vault-data-dictionary-views.md). |
| `p_code`       | ID of the code.<br>This ID is listed when you run the `DBA_DV_CODE` view.                                                                                                                                                                |

##### Example

    BEGIN
     DBMS_MACADM.CREATE_RULE(
      rule_name => 'Get Label Algorithm for Maximum Level/Union/Null',
      rule_expr => 'DBMS_MACUTL.GET_CODE_VALUE(''LABEL_ALG'', ''HUN'') = ''Union''');
    END;
    /

**Parent topic:** DBMS_MACUTL Package Procedures and Functions

#### 20.2.3 GET_SECOND Function

The `GET_SECOND` function returns the seconds in Oracle SS (seconds) format (00–59), and then returns a `NUMBER` value.

It is useful for rule expressions based on time data.

##### Syntax

    DBMS_MACUTL.GET_SECOND(
      p_date IN DATE DEFAULT SYSDATE)
    RETURN NUMBER;

##### Parameter

Table 20-4 GET_SECOND Parameter

| Parameter | Description                                                                                                                                                                                                                                      |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_date`  | Date in SS format (for example, `59`).<br>If you do not specify a date, then Oracle Database Vault uses the Oracle Database `SYSDATE` function to retrieve the current date and time set for the operating system on which the database resides. |

##### Example

    SET SERVEROUTPUT ON
    DECLARE
      seconds number;
    BEGIN
      seconds := DBMS_MACUTL.GET_SECOND(TO_DATE('03-APR-2009 6:56 PM',
      'dd-mon-yyyy hh:mi PM'));
      DBMS_OUTPUT.PUT_LINE('Seconds: '||seconds);
    END;
    /

This example, which uses a fixed date and time, returns the following:

    Seconds: 56

**Parent topic:** DBMS_MACUTL Package Procedures and Functions

#### 20.2.4 GET_MINUTE Function

The `GET_MINUTE` function returns the minute in Oracle MI (minute) format (00–59), in a `NUMBER` value.

It is useful for rule expressions based on time data.

##### Syntax

    DBMS_MACUTL.GET_MINUTE(
      p_date IN DATE DEFAULT SYSDATE)
    RETURN NUMBER;

##### Parameter

Table 20-5 GET_MINUTE Parameter

| Parameter | Description                                                                                                                                                                                                                                                  |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_date`  | Date in MI format (for example, `30`, as in 2:30).<br>If you do not specify a date, then Oracle Database Vault uses the Oracle Database `SYSDATE` function to retrieve the current date and time set for the operating system on which the database resides. |

##### Example

    SET SERVEROUTPUT ON
    DECLARE
      minute number;
    BEGIN
      minute := DBMS_MACUTL.GET_MINUTE(SYSDATE);
      DBMS_OUTPUT.PUT_LINE('Minute: '||minute);
    END;
    /

Output similar to the following appears:

    Minute: 17

**Parent topic:** DBMS_MACUTL Package Procedures and Functions

#### 20.2.5 GET_HOUR Function

The `GET_HOUR` function returns the hour in Oracle HH24 (hour) format (00–23), in a `NUMBER` value.

It is useful for rule expressions based on time data.

##### Syntax

    DBMS_MACUTL.GET_HOUR(
      p_date IN DATE DEFAULT SYSDATE)
    RETURN NUMBER;

##### Parameter

Table 20-6 GET_HOUR Parameter

| Parameter | Description                                                                                                                                                                                                                                                     |
|:----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_date`  | Date in HH24 format (for example, `14` for 2:00 p.m.)<br>If you do not specify a date, then Oracle Database Vault uses the Oracle Database `SYSDATE` function to retrieve the current date and time set for the operating system on which the database resides. |

##### Example

    SET SERVEROUTPUT ON
    DECLARE
      hours number;
    BEGIN
      hours := DBMS_MACUTL.GET_HOUR(SYSDATE);
      DBMS_OUTPUT.PUT_LINE('Hour: '||hours);
    END;
    /

Output similar to the following appears:

    Hour: 12

**Parent topic:** DBMS_MACUTL Package Procedures and Functions

#### 20.2.6 GET_DAY Function

The `GET_DAY` function returns the day in Oracle DD (day) format (01–31), in a `NUMBER` value.

It is useful for rule expressions based on time data.

##### Syntax

    DBMS_MACUTL.GET_DAY(
      p_date IN DATE DEFAULT SYSDATE)
    RETURN NUMBER;

##### Parameter

Table 20-7 GET_DAY Parameter

| Parameter | Description                                                                                                                                                                                                                                                                     |
|:----------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_date`  | Date in DD format (for example, `01` for the first day of the month).<br>If you do not specify a date, then Oracle Database Vault uses the Oracle Database `SYSDATE` function to retrieve the current date and time set for the operating system on which the database resides. |

##### Example

    SET SERVEROUTPUT ON
    DECLARE
      day number;
    BEGIN
      day := DBMS_MACUTL.GET_DAY(SYSDATE);
      DBMS_OUTPUT.PUT_LINE('Day: '||day);
    END;
    /

Output similar to the following appears:

    Day: 3

**Parent topic:** DBMS_MACUTL Package Procedures and Functions

#### 20.2.7 GET_MONTH Function

The `GET_MONTH` function returns the month in Oracle MM (month) format (01–12), in a `NUMBER` value.

It is useful for rule expressions based on time data.

##### Syntax

    DBMS_MACUTL.GET_MONTH(
      p_date IN DATE DEFAULT SYSDATE)
    RETURN NUMBER;

##### Parameter

Table 20-8 GET_MONTH Parameter

| Parameter | Description                                                                                                                                                                                                                                                              |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_date`  | Date in MM format (for example, `08` for the month of August).<br>If you do not specify a date, then Oracle Database Vault uses the Oracle Database `SYSDATE` function to retrieve the current date and time set for the operating system on which the database resides. |

##### Example

    SET SERVEROUTPUT ON
    DECLARE
      month number;
    BEGIN
      month := DBMS_MACUTL.GET_MONTH(SYSDATE);
      DBMS_OUTPUT.PUT_LINE('Month: '||month);
    END;
    /

Output similar to the following appears:

    Month: 4

**Parent topic:** DBMS_MACUTL Package Procedures and Functions

#### 20.2.8 GET_YEAR Function

The `GET_YEAR` function returns the year in Oracle YYYY (year) format (0001–9999), in a `NUMBER` value.

It is useful for rule expressions based on time data.

##### Syntax

    DBMS_MACUTL.GET_YEAR(
      p_date IN DATE DEFAULT SYSDATE)
    RETURN NUMBER;

##### Parameter

Table 20-9 GET_YEAR Parameter

| Parameter | Description                                                                                                                                                                                                                          |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_date`  | Date in YYYY format (for example, `1984`).<br>If you do not specify a date, then Oracle Database Vault uses the `SYSDATE` function to retrieve the current date and time set for the operating system on which the database resides. |

##### Example

    SET SERVEROUTPUT ON
    DECLARE
      year number;
    BEGIN
      year := DBMS_MACUTL.GET_YEAR(SYSDATE);
      DBMS_OUTPUT.PUT_LINE('Year: '||year);
    END;
    /

**Parent topic:** DBMS_MACUTL Package Procedures and Functions

#### 20.2.9 IS_ALPHA Function

The `IS_ALPHA` function returns a `BOOLEAN` value indicating if a character is alphabetic.

`IS_ALPHA` returns `TRUE` if the character is alphabetic.

##### Syntax

    DBMS_MACUTL.IS_ALPHA(
      c IN VARCHAR2)
    RETURN BOOLEAN;

##### Parameter

Table 20-10 IS_ALPHA Parameter

| Parameter | Description               |
|:----------|:--------------------------|
| `c`       | String with one character |

##### Example

    SET SERVEROUTPUT ON
    BEGIN
     IF DBMS_MACUTL.IS_ALPHA('z')
      THEN DBMS_OUTPUT.PUT_LINE('The alphabetic character was found');
     ELSE
      DBMS_OUTPUT.PUT_LINE('No alphabetic characters today.');
     END IF;
    END;
    /

**Parent topic:** DBMS_MACUTL Package Procedures and Functions

#### 20.2.10 IS_DIGIT Function

The `IS_DIGIT` function checks returns a `BOOLEAN` value indicating if a character is numeric.

`IS_DIGIT` returns `TRUE` if the character is a digit.

##### Syntax

    DBMS_MACUTL.IS_DIGIT(
      c IN VARCHAR2)
    RETURN BOOLEAN;

##### Parameter

Table 20-11 IS_DIGIT Parameter

| Parameter | Description               |
|:----------|:--------------------------|
| `c`       | String with one character |

##### Example

    SET SERVEROUTPUT ON
    BEGIN
     IF DBMS_MACUTL.IS_DIGIT('7')
      THEN DBMS_OUTPUT.PUT_LINE('The numeric character was found');
     ELSE
      DBMS_OUTPUT.PUT_LINE('No numeric characters today.');
     END IF;
    END;
    /

**Parent topic:** DBMS_MACUTL Package Procedures and Functions

#### 20.2.11 IS_DVSYS_OWNER Function

The `IS_DVSYS_OWNER` function returns a `BOOLEAN` value indicating if a user is authorized to manage the Oracle Database Vault configuration.

`IS_DVSYS_OWNER` returns `TRUE` if the user is authorized.

##### Syntax

    DBMS_MACUTL.IS_DVSYS_OWNER(
      p_user IN VARCHAR2 DEFAULT USER)
    RETURN BOOLEAN;

##### Parameter

Table 20-12 IS_DVSYS_OWNER Parameter

| Parameter | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:----------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_user`  | User to check.<br>To find existing users, query the following views:<br>• `DBA_USERS`: Finds available users for the current database instance. See [Oracle Database Reference](../refrn/DBA_USERS.md).<br>• `DBA_DV_REALM_AUTH`: Finds the authorization of a particular user or role. See [DBA_DV_REALM_AUTH View](oracle-database-vault-data-dictionary-views.md).<br>• `DBA_DV_ROLE`: Finds existing secure application roles used in privilege management. See [DBA_DV_ROLE View](oracle-database-vault-data-dictionary-views.md). |

##### Example

    SET SERVEROUTPUT ON
    BEGIN
     IF DBMS_MACUTL.IS_DVSYS_OWNER('PSMITH')
      THEN DBMS_OUTPUT.PUT_LINE('PSMITH is authorized to manage Database Vault.');
     ELSE
      DBMS_OUTPUT.PUT_LINE('PSMITH is not authorized to manage Database Vault.');
     END IF;
    END;
    /

**Parent topic:** DBMS_MACUTL Package Procedures and Functions

#### 20.2.12 IS_OLS_INSTALLED Function

The `IS_OLS_INSTALLED` function returns a `BOOLEAN` value indicating if Oracle Label Security is installed.

If Oracle Label Security is installed, `IS_OLS_INSTALLED` returns `TRUE`.

##### Syntax

    DBMS_MACUTL.IS_OLS_INSTALLED()
    RETURN BOOLEAN;

##### Parameters

None

##### Example

    SET SERVEROUTPUT ON
    BEGIN
     IF DBMS_MACUTL.IS_OLS_INSTALLED()
      THEN DBMS_OUTPUT.PUT_LINE('OLS is installed');
     ELSE
      DBMS_OUTPUT.PUT_LINE('OLS is not installed');
     END IF;
    END;
    /

**Parent topic:** DBMS_MACUTL Package Procedures and Functions

#### 20.2.13 IS_OLS_INSTALLED_VARCHAR Function

The `IS_OLS_INSTALLED_VARCHAR` function returns a `BOOLEAN` value indicating if Oracle Label Security is installed.

If Oracle Label Security is installed, then `IS_OLS_INSTALLED_VARCHAR` returns `Y`.

##### Syntax

    DBMS_MACUTL.IS_OLS_INSTALLED_VARCHAR()
    RETURN VARCHAR2;

##### Parameters

None

##### Example

See IS_OLS_INSTALLED Function for an example.

**Parent topic:** DBMS_MACUTL Package Procedures and Functions

#### 20.2.14 ROLE_GRANTED_ENABLED_VARCHAR Function

The `ROLE_GRANTED_ENABLED_VARCHAR` function returns a `VARCHAR2` value indicating the role grant and enablement status of a user.

`ROLE_GRANTED_ENABLED_VARCHAR` function checks whether a user has a role granted directly or indirectly (through another role) with a sufficient scope or the role currently is enabled in the session while the role is not granted. If either of these conditions are true, then it returns `Y`.

Because the `SYS_SESSION_ROLES` namespace of the `SYS_CONTEXT` function does not represent the logged in user roles when it is evaluated as a `DVSYS` command rule, Oracle recommends that you use the `ROLE_GRANTED_ENABLED_VARCHAR` function to check if a role is enabled for a logged in user.

##### Syntax

    DBMS_MACUTL.ROLE_GRANTED_ENABLED_VARCHAR(
      p_role IN VARCHAR2,
      p_user IN VARCHAR2 DEFAULT USER,
      p_profile IN NUMBER(38) DEFAULT 1,
      p_scope IN VARCHAR2 DEFAULT LOCAL)
    RETURN VARCHAR2;

##### Parameters

Table 20-13 ROLE_GRANTED_ENABLED_VARCHAR Parameters

| Parameter   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_role`    | Role to check.<br>To find existing roles, query the following views:<br>• `DBA_ROLES`: Finds available roles in the current database instance. See [Oracle Database Reference](../refrn/DBA_ROLES.md).<br>• `DBA_DV_REALM_AUTH`: Finds the authorization of a particular user or role. See [DBA_DV_REALM_AUTH View](oracle-database-vault-data-dictionary-views.md).<br>• `DBA_DV_ROLE`: Finds existing secure application roles used in privilege management. See [DBA_DV_ROLE View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                                 |
| `p_user`    | User to check. If you want to use `ROLE_GRANTED_ENABLED_VARCHAR` function as part of a rule evaluation, then you cannot set `p_user` to `CURRENT_USER` when `ROLE_GRANTED_ENABLED_VARCHAR` is being evaluated as an Oracle Database Vault rule. Instead, you can use the `SYS_CONTEXT` function `USERENV` namespace `SESSION_USER` to represent the login user.<br>To find existing users, query the following views:<br>• `DBA_USERS`: Finds available users for the current database instance. See [Oracle Database Reference](../refrn/DBA_USERS.md).<br>• `DBA_DV_REALM_AUTH`: Finds the authorization of a particular user or role. See [DBA_DV_REALM_AUTH View](oracle-database-vault-data-dictionary-views.md). |
| `p_profile` | If you are using privilege analysis and the role being checked is used, then specify `1` so that privilege analysis can capture the usage of the role. Otherwise, enter `0`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `p_scope`   | Specify either `COMMON` for a commonly granted role, or `LOCAL` for a locally granted role.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

##### Example

This example shows how to use the `DBMS_MACUTL.ROLE_GRANTED_ENABLED_VARCHAR` function in a command rule to check if the logged in user has the enabled role of `EMPLOYEE`.

    BEGIN
    DBMS_MACADM.CREATE_RULE(
      rule_name  => 'does role exist',
      rule_expr  => 'DVSYS.DBMS_MACUTL.ROLE_GRANTED_ENABLED_VARCHAR(''EMPLOYEE'',''"''||dvsys.dv_login_user||''"'') = ''Y''');
    END;
    /

**Parent topic:** DBMS_MACUTL Package Procedures and Functions

#### 20.2.15 USER_HAS_OBJECT_PRIVILEGE Function

The `USER_HAS_OBJECT_PRIVILEGE` function returns a `BOOLEAN` value indicating if user or role can access an object through a single specified object privilege grant.

If the user or role has the object privilege, then `USER_HAS_OBJECT_PRIVILEGE` returns `TRUE`.

##### Syntax

    DBMS_MACUTL.USER_HAS_OBJECT_PRIVILEGE(
      p_user          VARCHAR2,
      p_object_owner  VARCHAR2,
      p_object_name   VARCHAR2,
      p_privilege     VARCHAR2)
    RETURNS BOOLEAN;

##### Parameters

Table 20-14 USER_HAS_OBJECT_PRIVILEGE Parameters

| Parameter        | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:-----------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_user`         | User or role to check.<br>To find existing users, query they following views:<br>• `DBA_USERS`: Finds available users for the current database instance. See [Oracle Database Reference](../refrn/DBA_USERS.md).<br>• `DBA_ROLES`: Finds available roles in the current database instance. See [Oracle Database Reference](../refrn/DBA_ROLES.md).<br>• `DVA_DV_REALM_AUTH`: Finds the authorization of a particular user or role. See [DBA_DV_REALM_AUTH View](oracle-database-vault-data-dictionary-views.md).<br>• `DBA_DV_ROLE`: Finds existing secure application roles used in privilege management. See [DBA_DV_ROLE View](oracle-database-vault-data-dictionary-views.md). |
| `p_object_owner` | Object owner, such as a schema.<br>To find the available users, query they `DBA_USERS` view, described in [Oracle Database Reference](../refrn/DBA_USERS.md).<br>To find the authorization of a particular user, query they `DVA_DV_REALM_AUTH` view.                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `p_object_name`  | Object name, such as a table within the schema specified in the `p_object_owner` parameter.<br>To find the available objects, query the `ALL_OBJECTS` view, described in [Oracle Database Reference](../refrn/ALL_OBJECTS.md).<br>To find objects that are secured by existing realms, query they `DBA_DV_REALM_OBJECT` view.                                                                                                                                                                                                                                                                                                                                                      |
| `p_privilege`    | Object privilege, such as, `UPDATE`.<br>To find privileges for a database account excluding `PUBLIC` privileges, query they `DBA_DV_USER_PRIVS` view.<br>To find all privileges for a database account, query the `DBA_DV_USER_PRIVS_ALL`. view                                                                                                                                                                                                                                                                                                                                                                                                                                    |

##### Example

    SET SERVEROUTPUT ON
    BEGIN
     IF DBMS_MACUTL.USER_HAS_OBJECT_PRIVILEGE(
       'SECTOR2_APP_MGR', 'OE', 'ORDERS', 'UPDATE')
      THEN DBMS_OUTPUT.PUT_LINE('SECTOR2_APP_MGR has the UPDATE privilege for the OE.ORDERS table');
       ELSE
      DBMS_OUTPUT.PUT_LINE('SECTOR2_APP_MGR does not have the UPDATE privilege for the OE.ORDERS table.');
     END IF;
    END;
    /

**Parent topic:** DBMS_MACUTL Package Procedures and Functions

#### 20.2.16 USER_HAS_ROLE Function

The `USER_HAS_ROLE` function returns a `BOOLEAN` value indicating if a user has a role privilege, directly or indirectly (through another role).

If the user has a role privilege, then `USER_HAS_ROLE` returns `TRUE`.

##### Syntax

    DBMS_MACUTL.USER_HAS_ROLE(
      p_role IN VARCHAR2,
      p_user IN VARCHAR2 DEFAULT USER)
    RETURN BOOLEAN;

##### Parameters

Table 20-15 USER_HAS_ROLE Parameters

| Parameter | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:----------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_role`  | Role privilege to check.<br>To find existing roles, query the following views:<br>• `DBA_ROLES`: Finds available roles in the current database instance. See [Oracle Database Reference](../refrn/DBA_ROLES.md).<br>• `DBA_DV_REALM_AUTH`: Finds the authorization of a particular user or role. See [DBA_DV_REALM_AUTH View](oracle-database-vault-data-dictionary-views.md).<br>• `DBA_DV_ROLE`: Finds existing secure application roles used in privilege management. See [DBA_DV_ROLE View](oracle-database-vault-data-dictionary-views.md). |
| `p_user`  | User to check.<br>To find existing users, query the following views:<br>• `DBA_USERS`: Finds available users for the current database instance. See [Oracle Database Reference](../refrn/DBA_USERS.md).<br>• `DBA_DV_REALM_AUTH`: Finds the authorization of a particular user or role. See [DBA_DV_REALM_AUTH View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                            |

##### Example

    SET SERVEROUTPUT ON
    BEGIN
     IF DBMS_MACUTL.USER_HAS_ROLE('SECTOR2_APP_MGR', 'PSMITH')
      THEN DBMS_OUTPUT.PUT_LINE('User PSMITH has the SECTOR2_APP_MGR role');
       ELSE
      DBMS_OUTPUT.PUT_LINE('User PSMITH does not have the SECTOR2_APP_MGR role.');
     END IF;
    END;
    /

**Parent topic:** DBMS_MACUTL Package Procedures and Functions

#### 20.2.17 USER_HAS_ROLE_VARCHAR Function

The `USER_HAS_ROLE_VARCHAR` function returns a `VARCHAR2` value indicating if a user has a role privilege, directly or indirectly (through another role).

If the user has the role privilege specified, then `USER_HAS_ROLE_VARCHAR` returns `Y`.

##### Syntax

    DBMS_MACUTL.USER_HAS_ROLE_VARCHAR(
      p_role IN VARCHAR2,
      p_user IN VARCHAR2 DEFAULT USER)
    RETURN VARCHAR2;

##### Parameters

Table 20-16 USER_HAS_ROLE_VARCHAR Parameters

| Parameter | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_role`  | Role to check.<br>To find existing roles, query the following views:<br>• `DBA_ROLES`: Finds available roles in the current database instance. See [Oracle Database Reference](../refrn/DBA_ROLES.md).<br>• `DBA_DV_REALM_AUTH`: Finds the authorization of a particular user or role. See [DBA_DV_REALM_AUTH View](oracle-database-vault-data-dictionary-views.md).<br>• `DBA_DV_ROLE`: Finds existing secure application roles used in privilege management. See [DBA_DV_ROLE View](oracle-database-vault-data-dictionary-views.md). |
| `p_user`  | User to check.<br>To find existing users, query the following views:<br>• `DBA_USERS`: Finds available users for the current database instance. See [Oracle Database Reference](../refrn/DBA_USERS.md).<br>• `DBA_DV_REALM_AUTH`: Finds the authorization of a particular user or role. See [DBA_DV_REALM_AUTH View](oracle-database-vault-data-dictionary-views.md).                                                                                                                                                                  |

**Parent topic:** DBMS_MACUTL Package Procedures and Functions

#### 20.2.18 USER_HAS_SYSTEM_PRIVILEGE Function

The `USER_HAS_SYSTEM_PRIVILEGE` function returns a `BOOLEAN` value indicating if a user has a system privilege, directly or indirectly (through a role).

If the user has the system privilege specified, then `USER_HAS_SYSTEM_PRIVILEGE` returns `TRUE`.

##### Syntax

    DBMS_MACUTL.USER_HAS_SYSTEM_PRIVILEGE(
      p_privilege  IN VARCHAR2,
      p_user       IN VARCHAR2 DEFAULT USER)
    RETURN BOOLEAN;

##### Parameters

Table 20-17 USER_HAS_SYSTEM_PRIVILEGE Parameters

| Parameter     | Description                                                                                                                                                                                                                                                                                                                                                                                                     |
|:--------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `p_privilege` | System privilege to check for.<br>To find privileges for a database account excluding `PUBLIC` privileges, query the `DBA_DV_USER_PRIVS` view, described in [DBA_DV_USER_PRIVS View](oracle-database-vault-data-dictionary-views.md).<br>To find all privileges for a database account, use `DBA_DV_USER_PRIVS_ALL`, described in [DBA_DV_USER_PRIVS_ALL View](oracle-database-vault-data-dictionary-views.md). |
| `p_user`      | User to check.<br>To find existing users, query the following views:<br>• `DBA_USERS`: Finds available users for the current database instance. See [Oracle Database Reference](../refrn/DBA_USERS.md).<br>• `DBA_DV_REALM_AUTH`: Finds the authorization of a particular user or role. See [DBA_DV_REALM_AUTH View](oracle-database-vault-data-dictionary-views.md).                                           |

##### Example

    SET SERVEROUTPUT ON
    BEGIN
     IF DBMS_MACUTL.USER_HAS_SYSTEM_PRIVILEGE('EXECUTE', 'PSMITH')
      THEN DBMS_OUTPUT.PUT_LINE('User PSMITH has the EXECUTE ANY PRIVILEGE privilege.');
       ELSE
      DBMS_OUTPUT.PUT_LINE('User PSMITH does not have the EXECUTE ANY PRIVILEGE privilege.');
     END IF;
    END;
    /

**Parent topic:** DBMS_MACUTL Package Procedures and Functions
