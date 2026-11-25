## 14 Configuring Oracle Data Redaction Policies

An Oracle Data Redaction policy defines how to redact data in a column based on the table column type and the type of redaction you want to use.

- About Oracle Data Redaction Policies
  An Oracle Data Redaction policy defines the conditions in which redaction must occur for a table or view.
- Who Can Create Oracle Data Redaction Policies?
  Because data redaction involves the protection of highly sensitive data, only trusted users should create Oracle Data Redaction policies.
- Planning an Oracle Data Redaction Policy
  Before you create a Oracle Data Redaction policy, you should plan the data redaction policy that best suits your site’s needs.
- General Syntax of the DBMS_REDACT.ADD_POLICY Procedure
  To create a Data Redaction policy, you must use the `DBMS_REDACT.ADD_POLICY` procedure.
- Using Expressions to Define Conditions for Data Redaction Policies
  The `expression` parameter in the `DBMS_REDACT.ADD_POLICY` procedure sets the conditions to which the policy applies.
- Creating and Managing Multiple Named Policy Expressions
  A named, centrally managed Oracle Data Redaction policy expression can be used in multiple redaction policies and applied to multiple tables or views.
- Creating a Full Redaction Policy and Altering the Full Redaction Value
  You can create a full redaction policy to redact all contents in a data column, and optionally, you can alter the default full redaction value.
- Creating a DBMS_REDACT.NULLIFY Redaction Policy
  You can create Oracle Data Redaction policies that return null values for the displayed value of the table or view column.
- Creating a Partial Redaction Policy
  In partial data redaction, you can redact portions of data, and for different kinds of data types.
- Creating a Regular Expression-Based Redaction Policy
  A regular expression-based redaction policy enables you to redact data based on a search-and-replace model.
- Creating a Random Redaction Policy
  A random redaction policy presents redacted data as randomly generated values, such as `Ukjsl32[[]]]s`.
- Creating a Policy That Uses No Redaction
  You can create policies that use no redaction at all, for when you want to test the policy in a development environment.
- Exemption of Users from Oracle Data Redaction Policies
  You can exempt users from having Oracle Data Redaction policies applied to the data they access.
- Altering an Oracle Data Redaction Policy
  The `DBMS_REDACT.ALTER_POLICY` procedure enables you to modify Oracle Data Redaction policies.
- Redacting Multiple Columns
  You can redact more than one column in a Data Redaction policy.
- Disabling and Enabling an Oracle Data Redaction Policy
  You can disable and then reenable Oracle Data Redactions policies as necessary.
- Dropping an Oracle Data Redaction Policy
  The `DBMS_REDACT.DROP_POLICY` procedure drops Oracle Data Redaction policies.
- Tutorial: SQL Expressions to Build Reports with Redacted Values
  SQL expressions can be used to build reports based on columns that have Oracle Data Redaction policies defined on them.
- Using Trace Files to Troubleshoot Oracle Data Redaction Policies
  Trace files for Oracle Data Redaction can be generated for either the system level or the session level.
- Oracle Data Redaction Policy Data Dictionary Views
  Oracle Database provides data dictionary views that list information about Data Redaction policies.

**Parent topic:** [Using Oracle Data Redaction](asopart2.md)

### 14.1 About Oracle Data Redaction Policies

An Oracle Data Redaction policy defines the conditions in which redaction must occur for a table or view.

A Data Redaction policy has the following characteristics:

- The Data Redaction policy defines the following: What kind of redaction to perform, how the redaction should occur, and when the redaction takes place. Oracle Database performs the redaction at execution time, just before the data is returned to the application.

- A Data Redaction policy can fully redact values, partially redact values, or randomly redact values. In addition, you can define a Data Redaction policy to not redact any data at all, for when you want to test your policies in a test environment.

- A Data Redaction policy can be defined with a policy expression which allows for different application users to be presented with either redacted data or [actual data](glossary.md), based on whether the policy expression returns `TRUE` or `FALSE`. Redaction takes place when the boolean result of evaluating the policy expression is `TRUE`. For security reasons, the functions and operators that can be used in the policy expression are limited to `SYS_CONTEXT` and a few others. User-created functions are not allowed. Policy expressions can make use of the `SYS_SESSION_ROLES` namespace with the `SYS_CONTEXT` function to check for enabled roles.

- Different Data Redaction policy expressions can be created and then applied individually for different columns within the same table or view.

Table 14-1 lists the procedures in the `DBMS_REDACT` package.

Table 14-1 DBMS_REDACT Procedures

| Procedure                                  | Description                                                                                                                                    |
|:-------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------|
| `DBMS_REDACT.ADD_POLICY`                   | Adds a Data Redaction policy to a table or view                                                                                                |
| `DBMS_REDACT.ALTER_POLICY`                 | Modifies a Data Redaction policy                                                                                                               |
| `DBMS_REDACT.APPLY_POLICY_EXPR_TO_COL`     | Applies a Data Redaction policy expression to a table or view column                                                                           |
| `DBMS_REDACT.CREATE_POLICY_EXPRESSION`     | Creates a Data Redaction policy expression                                                                                                     |
| `DBMS_REDACT.DISABLE_POLICY`               | Disables a Data Redaction policy                                                                                                               |
| `DBMS_REDACT.DROP_POLICY`                  | Drops a Data Redaction policy                                                                                                                  |
| `DBMS_REDACT.DROP_POLICY_EXPRESSION`       | Drops a Data Redaction policy expression                                                                                                       |
| `DBMS_REDACT.ENABLE_POLICY`                | Enables a Data Redaction policy                                                                                                                |
| `DBMS_REDACT.UPDATE_FULL_REDACTION_VALUES` | Globally updates the full redaction value for a given data type. You must restart the database instance before the updated values can be used. |
| `DBMS_REDACT.UPDATE_POLICY_EXPRESSION`     | Updates a Data Redaction policy expression                                                                                                     |

**See Also:**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_REDACT.md) for detailed information about the `DBMS_REDACT` PL/SQL package

- [Managing Oracle Data Redaction Policies in Oracle Enterprise Manager](using-oracle-data-redaction-in-oracle-enterprise-manager.md) for information about using Oracle Enterprise Manager Cloud Control to create and manage Oracle Data Redaction policies and formats

**Parent topic:** Configuring Oracle Data Redaction Policies

### 14.2 Who Can Create Oracle Data Redaction Policies?

Because data redaction involves the protection of highly sensitive data, only trusted users should create Oracle Data Redaction policies.

To create redaction policies, you must have the `EXECUTE` privilege on the `DBMS_REDACT` PL/SQL package. To find the privileges that a user has been granted, you can query the `DBA_SYS_PRIVS` data dictionary view.

You do not need any privileges to access the underlying tables or views that will be protected by the policy.

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_REDACT.md)

**Parent topic:** Configuring Oracle Data Redaction Policies

### 14.3 Planning an Oracle Data Redaction Policy

Before you create a Oracle Data Redaction policy, you should plan the data redaction policy that best suits your site’s needs.

1.  Ensure that you have been granted the `EXECUTE` privilege on the `DBMS_REDACT` PL/SQL package.

2.  Determine the data type of the table or view column that you want to redact.

3.  Determine if the base object to which you want to add the Data Redaction policy has dependent objects. If it does have dependent objects, then these objects will become invalid when the Data Redaction policy is added to the base object, and these objects will be recompiled automatically when they are used.

    Alternatively, you can proactively recompile them yourself by using an `ALTER ... COMPILE` statement. Be aware that invalidating dependent objects (by adding a Data Redaction policy on their base object) and causing them to need to be recompiled can decrease performance in the overall system. Oracle recommends that you only add a Data Redaction policy to an object that has dependent objects during off-peak hours or during a scheduled downtime.

4.  Ensure that this column is not used in an Oracle Virtual Private Database (VPD) row filtering condition. That is, it must not be part of the VPD predicate generated by the VPD policy function.

5.  Decide on the type of redaction that you want to perform: full, random, partial, regular expressions, or none.

6.  Decide which users to apply the Data Redaction policy to.

7.  Based on this information, create the Data Redaction policy by using the `DBMS_REDACT.ADD_POLICY` procedure.

8.  Configure the policy to have additional columns to be redacted.

After you create the Data Redaction policy, it is automatically enabled and ready to redact data.

**Related Topics**

- Redacting Multiple Columns

**Parent topic:** Configuring Oracle Data Redaction Policies

### 14.4 General Syntax of the DBMS_REDACT.ADD_POLICY Procedure

To create a Data Redaction policy, you must use the `DBMS_REDACT.ADD_POLICY` procedure.

The complete syntax for the `DBMS_REDACT.ADD_POLICY` procedure is as follows:

    DBMS_REDACT.ADD_POLICY (
     object_schema               IN VARCHAR2 := NULL,
     object_name                 IN VARCHAR2 := NULL,
     policy_name                 IN VARCHAR2,
     policy_description          IN VARCHAR2 := NULL,
     column_name                 IN VARCHAR2 := NULL,
     column_description          IN VARCHAR2 := NULL,
     function_type               IN BINARY_INTEGER := DBMS_REDACT.FULL,
     function_parameters         IN VARCHAR2 := NULL,
     expression                  IN VARCHAR2,
     enable                      IN BOOLEAN := TRUE,
     regexp_pattern              IN VARCHAR2 := NULL,
     regexp_replace_string       IN VARCHAR2 := NULL,
     regexp_position             IN BINARY_INTEGER :=1,
     regexp_occurrence           IN BINARY_INTEGER :=0,
     regexp_match_parameter      IN VARCHAR2 := NULL);

In this specification:

- `object_schema`: Specifies the schema of the object on which the Data Redaction policy will be applied. If you omit this setting (or enter `NULL`), then Oracle Database uses the current user's name. Be aware that the meaning of "current user" here can change, depending on where you invoke the `DBMS_REDACT.ADD_POLICY` procedure.

  For example, suppose user `mpike` grants user `fbrown` the `EXECUTE` privilege on a definer's rights PL/SQL package called `mpike.protect_data` in `mpike`'s schema. From within this package, `mpike` has coded a procedure called `protect_cust_data`, which invokes the `DBMS_REDACT.ADD_POLICY` procedure. User `mpike` has set the `object_schema` parameter to `NULL`.

  When `fbrown` invokes the `protect_cust_data` procedure in the `mpike.protect_data` package, Oracle Database attempts to define the Data Redaction policy around the object `cust_data` in the `mpike` schema, not the `cust_data` object in the schema that belongs to `fbrown`.

- `object_name`: Specifies the name of the table or view to which the Data Redaction policy applies.

- `policy_name`: Specifies the name of the policy to be created. Ensure that this name is unique in the database instance. You can find a list of existing Data Redaction policies by querying the `POLICY_NAME` column of the `REDACTION_POLICIES` data dictionary view.

- `policy_description`: Specifies a brief description of the purpose of the policy.

- `column_name`: Specifies the column whose data you want to redact. Note the following:

  - You can apply the Data Redaction policy to multiple columns. If you want to apply the Data Redaction policy to multiple columns, then after you use `DBMS_REDACT.ADD_POLICY` to create the policy, run the `DBMS_REDACT.ALTER_POLICY` procedure as many times as necessary to add each of the remaining required columns to the policy. See Altering an Oracle Data Redaction Policy.

  - Only one policy can be defined on a table or view. You can, however, create a new view on the table, and by defining a second redaction policy on this new view, you can choose to redact the columns in a different way when a query is issued against this new view. When deciding how to redact a given column, Oracle Database uses the policy of the earliest view in a view chain.

  - If you do not specify a column (for example, by entering NULL), then no columns are redacted by the policy. This enables you to create your policies so that they are in place, and then later on, you can add the column specification when you are ready.

  - Do not use a column that is currently used in an Oracle Virtual Private Database (VPD) row filtering condition. In other words, the column should not be part of the VPD predicate generated by the VPD policy function. (See [Oracle Data Redaction and Oracle Virtual Private Database](oracle-data-redaction-use-with-oracle-database-features.md) for more information about using Data Redaction with VPD.)

  - You cannot define a Data Redaction policy on a virtual column. In addition, you cannot define a Data Redaction policy on a column that is involved in the SQL expression of any virtual column. If you are using the `DBMS_STATS` PL/SQL package to collect database statistics, then be aware that `DBMS_STATS` will add an invisible virtual column to the table internally when you create column groups. As a result, Oracle Database returns an` ORA-28073: The column ``column_name`` has an unsupported data type or attribute` error if you add a Data Redaction policy on a column that is also the column that is used to create column groups.

    A user with access to the `DBA_STAT_EXTENSIONS` data dictionary view can look in the `EXTENSION` column of `DBA_STAT_EXTENSIONS` using the following query to find the virtual column expression (that is internally created by `DBMS_STATS`), to see if it contains any column name that is being provided to a `DBMS_REDACT.ADD_POLICY` call to create a Data Redaction policy.

        SELECT EXTENSION_NAME, EXTENSION, CREATOR
         FROM DBA_STAT_EXTENSIONS
         WHERE TABLE_NAME='table_name_that_you_attempted_to_redact';

- `column_description`: Specifies a brief description of the column that you are redacting.

- `function_type`: Specifies a function that sets the type of redaction. See the following sections for more information:

  - Syntax for Creating a Full Redaction Policy

  - Syntax for Creating a Partial Redaction Policy

  - Syntax for Creating a Regular Expression-Based Redaction Policy

  - Syntax for Creating a Random Redaction Policy

  - Syntax for Creating a Policy with No Redaction

  If you omit the `function_type` parameter, then the default redaction `function_type` setting is `DBMS_REDACT.FULL`.

- `function_parameters`: Specifies how the column redaction should appear for partial redaction. See Syntax for Creating a Partial Redaction Policy.

- `expression`: Specifies a Boolean SQL expression to determine how the policy is applied. Redaction takes place only if this policy expression evaluates to `TRUE`. See Using Expressions to Define Conditions for Data Redaction Policies.

  By default, a Data Redaction policy expression applies to all the columns that belong to the Data Redaction policy defined on that table or view. Alternatively, you can choose to create and associate a policy expression for individual columns to override the existing expression. These column level expressions are called as named policy expressions. See Creating and Managing Multiple Named Policy Expressions.

- `enable`: When set to `TRUE`, enables the policy upon creation. When set to `FALSE`, it creates the policy as a disabled policy. The default is `TRUE`. After you create the policy, you can disable or enable it. See the following sections:

  - Disabling an Oracle Data Redaction Policy

  - Enabling an Oracle Data Redaction Policy

- `regexp_pattern`, `regexp_replace_string`, `regexp_position`, `regexp_position`, `regexp_occurrence`, `regexp_match_parameter`: Enable you to use regular expressions to redact data, either fully or partially. If the `regexp_pattern` does not match anything in the [actual data](glossary.md), then full redaction will take place, so be careful when specifying the `regexp_pattern`. Ensure that all of the values in the column conform to the semantics of the regular expression you are using. See Syntax for Creating a Regular Expression-Based Redaction Policy for more information.

**Parent topic:** Configuring Oracle Data Redaction Policies

### 14.5 Using Expressions to Define Conditions for Data Redaction Policies

The `expression` parameter in the `DBMS_REDACT.ADD_POLICY` procedure sets the conditions to which the policy applies.

- About Using Expressions in Data Redaction Policies
  The `DBMS_REDACT.ADD_POLICY` and `DBMS_REDACT.ALTER_POLICY` `expression` parameter defines a Boolean expression that must evaluate to `TRUE` to enable a redaction.
- Supported Functions for Data Redaction Expressions
  You can create expressions that use functions to return specific types of data, such as `SYS_CONTEXT` namespaces.
- Applying the Redaction Policy Based on User Environment
  You can apply a Data Redaction policy based on the user’s environment, such as the session user name or a client identifier.
- Applying the Redaction Policy Based on Database Roles
  You can apply a Data Redaction policy based on a database role, such as the `DBA` role.
- Applying the Redaction Policy Based on Oracle Label Security Label Dominance
  You can set a condition on which to apply a Data Redaction policy based on the dominance of Oracle Label Security labels.
- Applying the Redaction Policy Based on Application Express Session States
  You can apply a Data Redaction policy based on an Oracle Application Express (APEX) session state.
- Applying the Redaction Policy to All Users
  You can apply the policy irrespective of the context to any user, with no filtering.

**Parent topic:** Configuring Oracle Data Redaction Policies

#### 14.5.1 About Using Expressions in Data Redaction Policies

The `DBMS_REDACT.ADD_POLICY` and `DBMS_REDACT.ALTER_POLICY` `expression` parameter defines a Boolean expression that must evaluate to `TRUE` to enable a redaction.

The expression that is defined in the `expression` parameter is the default expression for the Oracle Data Redaction policy. If you apply a named policy expression for the columns that will be redacted by the Data Redaction policy, then the named policy expression takes precedence over the expression defined in the Data Redaction policy.

You can create expressions that make use of other Oracle Database features. For example, you can create expressions that are based on a user’s environment (using the `SYS_CONTEXT` and `XS_SYS_CONTEXT` functions), character string functions, the Oracle Label Security label dominance functions, or Oracle Application Express functions.

Follow these guidelines when you write the expression:

- Use only the following operators: `AND`, `OR`, `IN`, `NOT IN`, `=`, `!=`, `<>`, `<`, `>`, `>=`, `<=`

- Because the expression must evaluate to `TRUE` for redaction, be careful when making comparisons with `NULL`. Remember that in SQL the value `NULL` is undefined, so comparisons with `NULL` tend to return `FALSE`.

- Do not use user-created functions in the `expression` parameter; this is not permitted.

- Remember that for user `SYS` and users who have the `EXEMPT REDACTION POLICY` privilege, all of the Data Redaction policies are bypassed, so the results of their queries are not redacted. See the following topics for more information about users who are exempted from Data Redaction policies:

  - Exemption of Users from Oracle Data Redaction Policies

  - [Oracle Data Pump Security Model for Oracle Data Redaction](oracle-data-redaction-use-with-oracle-database-features.md)

**Parent topic:** Using Expressions to Define Conditions for Data Redaction Policies

#### 14.5.2 Supported Functions for Data Redaction Expressions

You can create expressions that use functions to return specific types of data, such as `SYS_CONTEXT` namespaces.

- Expressions Using Namespace Functions
  You can use the `SYS_CONTEXT` and `XS_SYS_CONTEXT` namespace functions in Data Redaction expressions.
- Expressions Using the SUBSTR Function
  You can use the `SUBSTR` function, which returns portion (such as characters 1–3) of the character string specified, in Data Redaction expressions. The first parameter must be a constant string or a call to the `SYS_CONTEXT` function or the `XS_SYS_CONTEXT` function.
- Expressions Using Length of Character String Functions
  You can use the following functions, which return the length of character strings, in Data Redaction expressions. Oracle Database also checks that the arguments to each of these operators is either a constant string or a call to the `SYS_CONTEXT` or `XS_SYS_CONTEXT` function.
- Expressions Using Oracle Application Express Functions
  You can use Oracle Application Express functions in Data Redaction expressions.
- Expressions Using Oracle Label Security Functions
  You can use Oracle Label Security functions with Data Redaction expressions.

**Parent topic:** Using Expressions to Define Conditions for Data Redaction Policies

##### 14.5.2.1 Expressions Using Namespace Functions

You can use the `SYS_CONTEXT` and `XS_SYS_CONTEXT` namespace functions in Data Redaction expressions.

Table 14-2 Expressions Using Namespace Functions

| Namespace Function | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|:-------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `SYS_CONTEXT`      | Returns the value associated with a namespace. The following namespace functions are valid:<br>• `USERENV` (default namespace), which includes values such as `SESSION_USER` and `CLIENT_IDENTIFIER`.<br>• `SYS_SESSION_ROLES`, which contains attributes for each role<br>• `XS$SESSION`, which contains attributes for the user session.<br>• User-defined namespaces, but these must exist in the `DBA_CONTEXT` catalog view before the policy expression is created. |
| `XS_SYS_CONTEXT`   | Similar to `SYS_CONTEXT` but designed for an Oracle Real Application Security environment.<br>`XS_SYS_CONTEXT` supports the same namespaces that `SYS_CONTEXT` supports.                                                                                                                                                                                                                                                                                                 |

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/SYS_CONTEXT.md) for more information about `SYS_CONTEXT`

- [Oracle Database Real Application Security Administrator's and Developer's Guide](../dbfsg/real-application-security-sql-functions.md) for more information about `XS_SYS_CONTEXT`

**Parent topic:** Supported Functions for Data Redaction Expressions

##### 14.5.2.2 Expressions Using the SUBSTR Function

You can use the `SUBSTR` function, which returns portion (such as characters 1–3) of the character string specified, in Data Redaction expressions. The first parameter must be a constant string or a call to the `SYS_CONTEXT` function or the `XS_SYS_CONTEXT` function.

Table 14-3 Expressions Using SUBSTR String Functions

| SUBSTR String Function | Description                                                                                                                                                                                            |
|:-----------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `SUBSTR`               | Returns a portion of the input `char` value, beginning at `character position`, `substring_length` characters long. `SUBSTR` calculates length using characters as defined by the input character set. |
| `SUBSTRB`              | Returns the specified portion of the input value in bytes                                                                                                                                              |
| `SUBSTRC`              | Returns the specified portion of the input value in Unicode complete characters                                                                                                                        |
| `SUBSTR2`              | Returns the specified portion of the input value in UCS2 code points                                                                                                                                   |
| `SUBSTR4`              | Returns the specified portion of the input value in UCS4 code points                                                                                                                                   |

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/SUBSTR.md) for more information about the `SUBSTR` functions

**Parent topic:** Supported Functions for Data Redaction Expressions

##### 14.5.2.3 Expressions Using Length of Character String Functions

You can use the following functions, which return the length of character strings, in Data Redaction expressions. Oracle Database also checks that the arguments to each of these operators is either a constant string or a call to the `SYS_CONTEXT` or `XS_SYS_CONTEXT` function.

Table 14-4 Expressions Using Character String Functions

| Character String Function | Description                                                                                                                      |
|:--------------------------|:---------------------------------------------------------------------------------------------------------------------------------|
| `LENGTH`                  | Returns the length of the input `char` value. `LENGTH` calculates length using characters as defined by the input character set. |
| `LENGTHB`                 | Returns the length of the input value in bytes                                                                                   |
| `LENGTHC`                 | Returns the length of the input value in Unicode complete characters                                                             |
| `LENGTH2`                 | Returns the length of the input value in UCS2 code points                                                                        |
| `LENGTH4`                 | Returns the length of the input value in UCS4 code points                                                                        |

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/LENGTH.md) for more information about the `LENGTH` functions

**Parent topic:** Supported Functions for Data Redaction Expressions

##### 14.5.2.4 Expressions Using Oracle Application Express Functions

You can use Oracle Application Express functions in Data Redaction expressions.

Table 14-5 Oracle Application Express Functions

| Oracle Application Express Function | Description                                                                                                          |
|:------------------------------------|:---------------------------------------------------------------------------------------------------------------------|
| `V`                                 | Returns the session state for an item. It is a wrapper for the `APEX_UTIL.GET_SESSION_STATE` function                |
| `NV`                                | Returns the numeric value for a numeric item. It is a wrapper for the `APEX_UTIL.GET_NUMERIC_SESSION_STATE` function |

**Related Topics**

- [Oracle Application Express API Reference](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/asoag&id=AEAPI-GUID-5ECE5C10-1A88-4D37-8A7D-C51925ADB2B9)

**Parent topic:** Supported Functions for Data Redaction Expressions

##### 14.5.2.5 Expressions Using Oracle Label Security Functions

You can use Oracle Label Security functions with Data Redaction expressions.

For the functions in the bold font, Oracle Data Redaction checks that their parameters are either constants or calls to only one of the `SA_UTL.NUMERIC_LABEL`, `CHAR_TO_LABEL`, and `SA_SESSION.LABEL` functions, and that the arguments to those functions are constant.

Table 14-6 Oracle Label Security Functions

| Oracle Label Security Function | Description                                                                                                                                                                                      |
|:-------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `LBACSYS.OLS_LABEL_DOMINATES`  | Checks if the session label of an Oracle Label Security policy dominates or is equal to another OLS label                                                                                        |
| `DOMINATES`                    | Checks if one OLS label is dominant to a second OLS label.<br>Deprecated in Oracle Database 12c release 1 (12.1); use the `OLS_DOMINATES` or `OLS_DOM ` function instead.                        |
| `OLS_DOMINATES`                | Checks if one OLS label is dominant to a second OLS label                                                                                                                                        |
| `OLS_DOM`                      | Checks if one OLS label is dominant to a second OLS label                                                                                                                                        |
| `DOM`                          | Checks if one OLS label is dominant to a second OLS label                                                                                                                                        |
| `OLS_STRICTLY_DOMINATES`       | Checks if one OLS label is dominant to a second OLS label and is not equal to it                                                                                                                 |
| `STRICTLY_DOMINATES`           | Checks if one OLS label is dominant to a second OLS label and is not equal to it                                                                                                                 |
| `S_DOM`                        | Checks if one OLS label is dominant to a second OLS label and is not equal to it.<br>Deprecated in Oracle Database 12c release 1 (12.1); use the `OLS_DOMINATES` or `OLS_DOM ` function instead. |
| `SA_UTL.DOMINATES`             | Checks if one OLS label dominates a second OLS label or if the session label for a given OLS policy dominates an OLS label                                                                       |
| `SA_UTL.CHECK_READ`            | Checks if a user can read a policy-protected row                                                                                                                                                 |
| `SA_UTL.NUMERIC_LABEL`         | Returns the current session OLS label                                                                                                                                                            |
| `CHAR_TO_LABEL`                | Converts a character string to an OLS label tag                                                                                                                                                  |
| `SA_SESSION.LABEL`             | Returns the label that is associated with the specified OLS policy                                                                                                                               |

**Related Topics**

- [Oracle Label Security Administrator’s Guide](../olsag/advanced-topics-in-oracle-label-security.md)

**Parent topic:** Supported Functions for Data Redaction Expressions

#### 14.5.3 Applying the Redaction Policy Based on User Environment

You can apply a Data Redaction policy based on the user’s environment, such as the session user name or a client identifier.

- Use the `USERENV` namespace of the `SYS_CONTEXT` function in the `DBMS_REDACT.ADD_POLICY` `expression` parameter to apply the policy based on a user’s environment.

For example, to apply the policy only to the session user name `psmith`:

    expression  => 'SYS_CONTEXT(''USERENV'',''SESSION_USER'') = ''PSMITH'''

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/SYS_CONTEXT.md) for information about more namespaces that you can use with the `SYS_CONTEXT` function

**Parent topic:** Using Expressions to Define Conditions for Data Redaction Policies

#### 14.5.4 Applying the Redaction Policy Based on Database Roles

You can apply a Data Redaction policy based on a database role, such as the `DBA` role.

- Use the `SYS_SESSION_ROLES` namespace in the `SYS_CONTEXT` function to apply the policy based on a user role.
  This namespace contains attributes for each role. The value of the attribute is `TRUE` if the specified role is enabled for the querying application user; the value is `FALSE` if the role is not enabled.
  For example, suppose you wanted only supervisors to be allowed to see the actual data. The following example shows how to use the `DBMS_REDACT.ADD_POLICY` `expression` parameter to set the policy to show the actual data to any application user who has the `supervisor` role enabled, but redact the data for all of the other application users.
      expression  => 'SYS_CONTEXT(''SYS_SESSION_ROLES'',''SUPERVISOR'') = ''FALSE'''

  You can specify multiple roles with the `expression` parameter. The following example checks for the presence of the `supervisor`, `clerk`, and `temp_worker` roles.

      expression => 'SYS_CONTEXT(''SYS_SESSION_ROLES'',''SUPERVISOR'') = ''TRUE''
      OR SYS_CONTEXT(''SYS_SESSION_ROLES'',''CLERK'') = ''TRUE''
      OR SYS_CONTEXT(''SYS_SESSION_ROLES'',''TEMP_WORKER'') = ''TRUE'''

**Related Topics**

- [Oracle Database SQL Language Reference](../sqlrf/SYS_CONTEXT.md)

**Parent topic:** Using Expressions to Define Conditions for Data Redaction Policies

#### 14.5.5 Applying the Redaction Policy Based on Oracle Label Security Label Dominance

You can set a condition on which to apply a Data Redaction policy based on the dominance of Oracle Label Security labels.

- Use the public standalone function `OLS_LABEL_DOMINATES` to check the dominance of a session label. This function returns `1` (`TRUE`) if the session label of the specified `policy_name` value dominates or is equal to the label that is specified by the `label` parameter; otherwise, it returns `0` (`FALSE`).

For example, to apply a Data Redaction policy only in cases where the session label for the policy `hr_ols_pol` does not dominate nor is equal to label `hs`:

    expression  => 'OLS_LABEL_DOMINATES (''hr_ols_pol'',''hs'') = 0'

**Parent topic:** Using Expressions to Define Conditions for Data Redaction Policies

#### 14.5.6 Applying the Redaction Policy Based on Application Express Session States

You can apply a Data Redaction policy based on an Oracle Application Express (APEX) session state.

- Use either of the following public Application Express APIs in the `DBMS_REDACT.ADD_POLICY` `expression` parameter to apply the policy on an Oracle Application Express session state:

  - `V`, which is a synonym for the `APEX_UTIL.GET_SESSION_STATE` function

  - `NV`, which is a synonym for the `APEX_UTIL.GET_NUMERIC_SESSION_STATE` function

For example, to set the `DBMS_REDACT.ADD_POLICY` `expression` parameter if you wanted redaction to take place when the application item called `G_JOB` has the value `CLERK`:

    expression => 'V(''APP_USER'') != ''mavis@example.com'' or V(''APP_USER'') is null'

You can, for example, use these functions to redact data based on a job or a privilege role that is stored in a session state in an APEX application.

If you want redaction to take place when the querying user is not within the context of an APEX application (when the query is issued from outside the APEX framework, for example directly through SQL\*Plus), then use an `IS NULL` clause as follows. This policy expression causes actual data to be shown to user `mavis` only when her query comes from within an APEX application. Otherwise, the query result is redacted.

**See Also:**

[Oracle Application Express API Reference](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/asoag&id=AEAPI101)

**Parent topic:** Using Expressions to Define Conditions for Data Redaction Policies

#### 14.5.7 Applying the Redaction Policy to All Users

You can apply the policy irrespective of the context to any user, with no filtering.

However, be aware that user `SYS` and users who have the `EXEMPT REDACTION POLICY` privilege are always except from Oracle Data Redaction policies.

- To apply the policy to users who are not `SYS` or have been granted the `EXEMPT REDACTION POLICY` privilege, write the `DBMS_REDACT.ADD_POLICY` `expression` parameter to evaluate to `TRUE`.

For example:

    expression  => '1=1'

**See Also:**

Exemption of Users from Oracle Data Redaction Policies

**Parent topic:** Using Expressions to Define Conditions for Data Redaction Policies

### 14.6 Creating and Managing Multiple Named Policy Expressions

A named, centrally managed Oracle Data Redaction policy expression can be used in multiple redaction policies and applied to multiple tables or views.

- About Data Redaction Policy Expressions to Define Conditions
  A named Oracle Data Redaction policy expression is designed to work as an alternative to the policy expression that is used in existing Data Redaction policies.
- Creating and Applying a Named Data Redaction Policy Expression
  The `DBMS_REDACT.CREATE_POLICY_EXPRESSION` and `DBMS_REDACT.APPLY_POLICY_EXPR_TO_COL` enable you to create and apply a named Data Redaction policy expression.
- Updating a Named Data Redaction Policy Expression
  You can use the `DBMS_REDACT.UPDATE_POLICY_EXPRESSION` procedure to update a Data Redaction policy expression. The update takes place immediately and is reflected in all columns that use the policy expression.
- Dropping a Named Data Redaction Expression Policy
  You can use the `DBMS_REDACT.DROP_POLICY_EXPRESSION` procedure to drop a Data Redaction expression policy.
- Tutorial: Creating and Sharing a Named Data Redaction Policy Expression
  This tutorial shows how to create an Oracle Data Redaction policy expression, apply it to multiple tables, and centrally manage the policy expression.

**Parent topic:** Configuring Oracle Data Redaction Policies

#### 14.6.1 About Data Redaction Policy Expressions to Define Conditions

A named Oracle Data Redaction policy expression is designed to work as an alternative to the policy expression that is used in existing Data Redaction policies.

A named policy expression enables you to redact data based on runtime conditions. This type of policy can only affect whether or not redaction takes place on columns of the table or view on which the redaction policy is defined. By default, a Data Redaction policy expression applies to all the columns that belong to the Data Redaction policy defined on that table or view. Alternatively, you can choose to create and associate a policy expression for individual columns of a table or view. These column level expressions are called as named policy expressions; in other words, a policy expression with a name. A named policy expressions has the following properties:

You can use Data Redaction policy expressions in the following ways.:

- A single Data Redaction policy expression can be shared by more than one Data Redaction policy by applying it to columns that are a part of separate Data Redaction policies.

- Each named policy expression can be associated with multiple columns of the same or different tables or views.

- Each named policy expression can be associated with columns within the same or different Data Redaction policies.

- The named policy expression overrides the default policy expression of the associated columns. The default policy expression still applies to redaction columns that have no named policy expressions applied to them.

- Any updates made to a named policy expression apply to all of the column associations of the expression.

- You cannot associate multiple named policy expressions for the same column.

- In a multitenant environment, you cannot associate named policy expressions with columns in a different pluggable database (PDB).

The column to which you apply a named policy expression must already be redacted by a Data Redaction policy. After the named policy expression is applied, the result of its evaluation takes precedence over that of the default policy expression when deciding whether or not to redact the column. When you modify a named policy expression, the changes are applied to all the tables and views that use it. In a multitenant environment, as with Data Redaction policies, a named policy expression is valid only in the PDB in which it was created, and can only be applied to columns of objects within the PDB in which it was created.

Table 14-7 describes the `DBMS_REDACT` PL/SQL procedures that you can use to create and manage named policy expressions. To find information about policy expressions, query the `REDACTION_EXPRESSIONS` data dictionary view.

Table 14-7 DBMS_REDACT Policy Expression Procedures

| Procedure                              | Description                                                            |
|:---------------------------------------|:-----------------------------------------------------------------------|
| `DBMS_REDACT.CREATE_POLICY_EXPRESSION` | Creates a Data Redaction policy expression                             |
| `DBMS_REDACT.UPDATE_POLICY_EXPRESSION` | Updates a Data Redaction policy expression                             |
| `DBMS_REDACT.APPLY_POLICY_EXPR_TO_COL` | Applies a Data Redaction policy expression to a table or a view column |
| `DBMS_REDACT.DROP_POLICY_EXPRESSION`   | Drops a Data Redaction policy expression                               |

**Related Topics**

- [Managing Named Data Redaction Policy Expressions Using Enterprise Manager](using-oracle-data-redaction-in-oracle-enterprise-manager.md)

**Parent topic:** Creating and Managing Multiple Named Policy Expressions

#### 14.6.2 Creating and Applying a Named Data Redaction Policy Expression

The `DBMS_REDACT.CREATE_POLICY_EXPRESSION` and `DBMS_REDACT.APPLY_POLICY_EXPR_TO_COL` enable you to create and apply a named Data Redaction policy expression.

1.  Connect to the PDB as a user who has the `EXECUTE` privilege on the `DBMS_REDACT` PL/SQL package.
2.  Ensure that the `COMPATIBLE` initialization parameter is set to `12.2.0.0` or later.
    To find the current `COMPATIBLE` setting, use the `SHOW PARAMETER` command.
3.  To create the policy expression, run the `DBMS_REDACT.CREATE_POLICY_EXPRESSION` procedure.
    For example:

        BEGIN
         DBMS_REDACT.CREATE_POLICY_EXPRESSION (
          policy_expression_name        => 'redact_pol',
          expression                    => '1=1',
          policy_expression_description => 'Determines whether the column will be redacted');
        END;
        /
4.  Run the `DBMS_REDACT.APPLY_POLICY_EXPR_TO_COL` procedure to apply the policy expression to a table or view column.
    For example, assume that you have already created a Data Redaction policy on the `SALARY` column of the `HR.EMPLOYEES` table, as follows:

        BEGIN
          DBMS_REDACT.ADD_POLICY  (
           object_schema           => 'hr',
           object_name             => 'employees',
           policy_name             => 'overall_policy',
           expression              => '1=0');
        END;
        /
        BEGIN
          DBMS_REDACT.ALTER_POLICY (
           object_schema           => 'hr',
           object_name             => 'employees' ,
           policy_name             => 'overall_policy',
           function_type           => DBMS_REDACT.FULL,
           action                  => DBMS_REDACT.ADD_COLUMN,
           column_name             => 'SALARY );
        END;
        /

    Then you can apply the policy expression to the `SALARY` table as follows:

        BEGIN
         DBMS_REDACT.APPLY_POLICY_EXPR_TO_COL (
           object_schema           => 'hr',
           object_name             => 'employees',
           column_name             => 'salary',
           policy_expression_name  => 'redact_pol');
        END;
        /

    In this specification:

    - `object_schema`: Specifies the schema of the object on which the policy expression will be used. If you omit this setting (or enter `NULL`), then Oracle Database uses the name of the current schema.

    - `object_name`: Specifies the name of the table or view to be used for the policy expression.

    - `column_name`: Specifies the column to which you want to apply the policy expression.

    - `policy_expression_name`: Specifies the name of the policy expression.

    After you create an Oracle Data Redaction policy expression, you can apply it to a column of a table or view which is part of an existing Data Redaction policy.

**Parent topic:** Creating and Managing Multiple Named Policy Expressions

#### 14.6.3 Updating a Named Data Redaction Policy Expression

You can use the `DBMS_REDACT.UPDATE_POLICY_EXPRESSION` procedure to update a Data Redaction policy expression. The update takes place immediately and is reflected in all columns that use the policy expression.

You can query the `REDACTION_EXPRESSIONS` data dictionary view to find existing Data Redaction policy expressions.

1.  Connect to the PDB as a user who has the `EXECUTE` privilege on the `DBMS_REDACT` PL/SQL package.
2.  Ensure that the `COMPATIBLE` initialization parameter is set to `12.2.0.0` or later.
    To find the current `COMPATIBLE` setting, use the `SHOW PARAMETER` command.
3.  Run the `DBMS_REDACT.UPDATE_POLICY_EXPRESSION` procedure to perform the update.
    For example:

        BEGIN
         DBMS_REDACT.UPDATE_POLICY_EXPRESSION(
          policy_expression_name => 'redact_pol',
          expression             => '1=0');
        END;
        /

**Parent topic:** Creating and Managing Multiple Named Policy Expressions

#### 14.6.4 Dropping a Named Data Redaction Expression Policy

You can use the `DBMS_REDACT.DROP_POLICY_EXPRESSION` procedure to drop a Data Redaction expression policy.

You can query the `REDACTION_EXPRESSIONS` data dictionary view to find existing Data Redaction policy expressions.

1.  Connect to the PDB as a user who has the `EXECUTE` privilege on the `DBMS_REDACT` PL/SQL package.
2.  Ensure that the `COMPATIBLE` initialization parameter is set to `12.2.0.0` or later.
    To find the current `COMPATIBLE` setting, use the `SHOW PARAMETER` command.
3.  Remove the named policy expression's association with any table or view column.
    You cannot drop a policy expression if it is associated with an existing table or view column. To remove a given column’s association with a named policy expression (to revert to redacting that column based on the evaluation result of the default policy expression), you must set the `policy_expression_name` parameter of the `DBMS_REDACT.APPLY_POLICY_EXPR_TO_COL` procedure to `NULL`.
    For example:

        BEGIN
         DBMS_REDACT.APPLY_POLICY_EXPR_TO_COL(
           object_schema          => 'hr',
           object_name            => 'employees',
           column_name            => 'salary',
           policy_expression_name =>  null);
        END;
        /
4.  Run `DBMS_REDACT.DROP_POLICY_EXPRESSION` to drop the policy expression.
    For example:

        BEGIN
         DBMS_REDACT.DROP_POLICY_EXPRESSION(
          policy_expression_name  => 'redact_pol');
        END;
        /

**Parent topic:** Creating and Managing Multiple Named Policy Expressions

#### 14.6.5 Tutorial: Creating and Sharing a Named Data Redaction Policy Expression

This tutorial shows how to create an Oracle Data Redaction policy expression, apply it to multiple tables, and centrally manage the policy expression.

- Step 1: Create Users for This Tutorial
  You must create two users for this tutorial: `dr_admin`, who will create the Oracle Data Redaction policies, and `hr_clerk`, who will test them.
- Step 2: Create an Oracle Data Redaction Policy
  User `dr_admin` is ready to create an Oracle Data Redaction policy to protect the `HR.EMPLOYEES` and `HR.JOBS` tables.
- Step 3: Test the Oracle Data Redaction Policy
  User `hr_clerk` is ready to query the tables that have redacted data.
- Step 4: Create and Apply a Policy Expression to the Redacted Table Columns
  Next, user `dr_admin` is ready to create a Data Redaction policy expression and apply it to two of the three redacted table columns.
- Step 5: Test the Data Redaction Policy Expression
  User `hr_clerk` is now ready to test the `hr_redact_pol` policy expression.
- Step 6: Modify the Data Redaction Policy Expression
  User `dr_admin` decides to modify the Data Redaction policy expression so that user `HR` will have access to the redacted data, not user `hr_clerk`.
- Step 7: Test the Modified Policy Expression
  Users `HR` and `hr_clerk` are ready to test the modified Data Redaction policy expression.
- Step 8: Remove the Components of This Tutorial
  If you do not need the components of this tutorial, then you can remove them.

**Parent topic:** Creating and Managing Multiple Named Policy Expressions

##### 14.6.5.1 Step 1: Create Users for This Tutorial

You must create two users for this tutorial: `dr_admin`, who will create the Oracle Data Redaction policies, and `hr_clerk`, who will test them.

Before you begin this tutorial, ensure that the `COMPATIBLE` initialization parameter is set to `12.2.0.0` or later. You can check this setting by using the `SHOW PARAMETER` command.

1.  Connect to a PDB as user `SYS` with the `SYSDBA` administrative privilege.
2.  Create the `dr_admin` and `hr_clerk` user accounts.
        GRANT CREATE SESSION TO dr_admin IDENTIFIED BY password;
        GRANT CREATE SESSION TO hr_clerk IDENTIFIED BY password;
3.  Grant the `EXECUTE` privilege to the `dr_admin` user.
        GRANT EXECUTE ON DBMS_REDACT TO dr_admin;
4.  Connect as user `HR`.
5.  Grant `hr_clerk` the `SELECT` privilege on the `EMPLOYEES` and `JOBS` tables.
        GRANT SELECT on EMPLOYEES to hr_clerk;
        GRANT SELECT on JOBS to hr_clerk;

**Parent topic:** Tutorial: Creating and Sharing a Named Data Redaction Policy Expression

##### 14.6.5.2 Step 2: Create an Oracle Data Redaction Policy

User `dr_admin` is ready to create an Oracle Data Redaction policy to protect the `HR.EMPLOYEES` and `HR.JOBS` tables.

1.  Connect to the PDB as user `dr_admin`.
2.  Create the `hr_emp_redact_comp_pol` policy, which will perform full redaction of the `HR.EMPLOYEES.SALARY` column.
        BEGIN
         DBMS_REDACT.ADD_POLICY(
           object_schema       => 'hr',
           object_name         => 'employees',
           column_name         => 'salary',
           policy_name         => 'hr_emp_redact_comp_pol',
           function_type       => DBMS_REDACT.FULL,
           expression          => '1=1');
        END;
        /
3.  Alter the `hr_redact_comp_pol` policy to also redact the `COMMISSION_PCT` column of the `HR.EMPLOYEES` table.
        BEGIN
         DBMS_REDACT.ALTER_POLICY(
           object_schema       => 'hr',
           object_name         => 'employees',
           policy_name         => 'hr_emp_redact_comp_pol',
           action              => DBMS_REDACT.ADD_COLUMN,
           column_name         => 'commission_pct',
           function_type       => DBMS_REDACT.FULL);
        END;
        /
4.  Create the `hr_jobs_redact_comp_pol` policy for the `max_salary` column of the `HR.JOBS` table.
        BEGIN
         DBMS_REDACT.ADD_POLICY(
           object_schema       => 'hr',
           object_name         => 'jobs',
           column_name         => 'max_salary',
           policy_name         => 'hr_jobs_redact_comp_pol',
           function_type       => DBMS_REDACT.FULL,
           expression          => '1=1');
        END;
        /

At this stage, the data in the `HR.EMPLOYEES.SALARY`, `HR.EMPLOYEES.COMMISSION_PCT`, and `HR.JOBS.MAX_SALARY` columns are redacted.

**Parent topic:** Tutorial: Creating and Sharing a Named Data Redaction Policy Expression

##### 14.6.5.3 Step 3: Test the Oracle Data Redaction Policy

User `hr_clerk` is ready to query the tables that have redacted data.

1.  Connect as user `hr_clerk`.
2.  Query the `HR.EMPLOYEES` table.
        SELECT SALARY, COMMISSION_PCT FROM HR.EMPLOYEES WHERE SALARY > 15000;

    The output should be as follows:
            SALARY COMMISSION_PCT
        ---------- --------------
                 0
                 0
                 0
3.  Query the `HR.JOBS` table.
        SELECT MAX_SALARY FROM HR.JOBS WHERE MAX_SALARY > 15000;

    The output should be as follows:
        MAX_SALARY
        ----------
                 0
                 0
                 0
                 0
                 0

**Parent topic:** Tutorial: Creating and Sharing a Named Data Redaction Policy Expression

##### 14.6.5.4 Step 4: Create and Apply a Policy Expression to the Redacted Table Columns

Next, user `dr_admin` is ready to create a Data Redaction policy expression and apply it to two of the three redacted table columns.

This policy expression will enable user `hr_clerk` to view the redacted data.

1.  Connect as user `dr_admin.`
2.  Create the policy expression.
        BEGIN
         DBMS_REDACT.CREATE_POLICY_EXPRESSION(
           policy_expression_name  => 'hr_redact_pol',
           expression              => 'SYS_CONTEXT(''USERENV'',''SESSION_USER'') != ''HR_CLERK''');
        END;
        /

    This expression returns `FALSE` for the `hr_clerk` user, which enables the `hr_clerk` user to view actual data in the `HR.EMPLOYEES` and `HR.JOBS` tables that are subject to the Data Redaction policies.
3.  Apply the `hr_redact_pol` policy expression to the `HR.EMPLOYEES.SALARY` column.
        BEGIN
         DBMS_REDACT.APPLY_POLICY_EXPR_TO_COL(
           object_schema          => 'hr',
           object_name            => 'employees',
           column_name            => 'salary',
           policy_expression_name => 'hr_redact_pol');
        END;
        /
4.  Apply the `hr_redact_pol` policy expression to the `HR.JOBS.MAX_SALARY` column.
        BEGIN
         DBMS_REDACT.APPLY_POLICY_EXPR_TO_COL(
           object_schema          => 'hr',
           object_name            => 'jobs',
           column_name            => 'max_salary',
           policy_expression_name => 'hr_redact_pol');
        END;
        /

User `hr_clerk` can view data in the `HR.EMPLOYEES.SALARY` and `HR.JOBS.MAX_SALARY`, but the data in the `HR.EMPLOYEES.COMMISSION_PCT` column will still be redacted for this user.

**Parent topic:** Tutorial: Creating and Sharing a Named Data Redaction Policy Expression

##### 14.6.5.5 Step 5: Test the Data Redaction Policy Expression

User `hr_clerk` is now ready to test the `hr_redact_pol` policy expression.

1.  Connect as user `hr_clerk`.
2.  Query the `HR.EMPLOYEES` table.
        SELECT SALARY, COMMISSION_PCT FROM HR.EMPLOYEES WHERE SALARY > 15000;

    The output should be as follows:
            SALARY COMMISSION_PCT
        ---------- --------------
             24000
             17000
             17000

    User `hr_clerk` now can view the `SALARY` column data, but still has not access to the `COMMISSION_PCT` column data.
3.  Query the `HR.JOBS` table.
        SELECT MAX_SALARY FROM HR.JOBS WHERE MAX_SALARY > 15000;

    The output should be as follows:
        MAX_SALARY
        ----------
             40000
             30000
             16000
             16000
             20080

    User `hr_clerk` now can view the `MAX_SALARY` column data.

**Parent topic:** Tutorial: Creating and Sharing a Named Data Redaction Policy Expression

##### 14.6.5.6 Step 6: Modify the Data Redaction Policy Expression

User `dr_admin` decides to modify the Data Redaction policy expression so that user `HR` will have access to the redacted data, not user `hr_clerk`.

1.  Connect as user `dr_admin`.
2.  Modify the `hr_redact_pol` policy as follows:
        BEGIN
         DBMS_REDACT.UPDATE_POLICY_EXPRESSION(
          policy_expression_name => 'hr_redact_pol',
          expression             => 'SYS_CONTEXT(''USERENV'',''SESSION_USER'') != ''HR''');
        END;
        /

**Parent topic:** Tutorial: Creating and Sharing a Named Data Redaction Policy Expression

##### 14.6.5.7 Step 7: Test the Modified Policy Expression

Users `HR` and `hr_clerk` are ready to test the modified Data Redaction policy expression.

1.  Connect as user `HR`.
2.  Query the `HR.EMPLOYEES` table.
        SELECT SALARY, COMMISSION_PCT FROM HR.EMPLOYEES WHERE SALARY > 15000;

    The output should be as follows:
            SALARY COMMISSION_PCT
        ---------- --------------
             24000
             17000
             17000

    User `HR` now has access to the redacted data. A query by `HR` on the `HR.JOBS.MAX_SALARY` column will produce similar results.

        SELECT MAX_SALARY FROM HR.JOBS WHERE MAX_SALARY > 15000;

        MAX_SALARY
        ----------
             40000
             30000
             16000
             16000
             20080
3.  Connect as user `hr_clerk`.
4.  Query the `HR.EMPLOYEES` and `HR.JOBS` tables and then observe the results.
        SELECT SALARY, COMMISSION_PCT FROM HR.EMPLOYEES WHERE SALARY > 15000;

            SALARY COMMISSION_PCT
        ---------- --------------
                 0
                 0
                 0

        SELECT MAX_SALARY FROM HR.JOBS WHERE MAX_SALARY > 15000;

        MAX_SALARY
        ----------
                 0
                 0
                 0
                 0
                 0

**Parent topic:** Tutorial: Creating and Sharing a Named Data Redaction Policy Expression

##### 14.6.5.8 Step 8: Remove the Components of This Tutorial

If you do not need the components of this tutorial, then you can remove them.

1.  Connect as user `dr_admin`.
2.  Modify the policy expression so that it is no longer associated with the table columns that are associated with the expression.
    To do so, you must set the `policy_expression_name` parameter to `NULL`.
        BEGIN
         DBMS_REDACT.APPLY_POLICY_EXPR_TO_COL(
           object_schema          => 'hr',
           object_name            => 'employees',
           column_name            => 'salary',
           policy_expression_name =>  null);
        END;
        /

        BEGIN
         DBMS_REDACT.APPLY_POLICY_EXPR_TO_COL(
           object_schema          => 'hr',
           object_name            => 'jobs',
           column_name            => 'max_salary',
           policy_expression_name =>  null);
        END;
        /
3.  Drop the policy expressions.
        BEGIN
         DBMS_REDACT.DROP_POLICY_EXPRESSION(
          policy_expression_name  => 'hr_redact_pol');
        END;
        /
4.  Drop the `hr_emp_redact_comp_pol` and `hr_jobs_redact_comp_pol` Data Redaction policies.
        BEGIN
          DBMS_REDACT.DROP_POLICY (
            object_schema  => 'hr',
            object_name    => 'employees',
            policy_name    => 'hr_emp_redact_comp_pol');
        END;
        /

        BEGIN
          DBMS_REDACT.DROP_POLICY (
            object_schema  => 'hr',
            object_name    => 'jobs',
            policy_name    => 'hr_jobs_redact_comp_pol');
        END;
        /
5.  Connect as the `SYSTEM` user or a user who has privileges to drop user accounts.
6.  Drop the `dr_admin` and `hr_clerk` user accounts.
        DROP USER dr_admin;
        DROP USER hr_clerk;

**Parent topic:** Tutorial: Creating and Sharing a Named Data Redaction Policy Expression

### 14.7 Creating a Full Redaction Policy and Altering the Full Redaction Value

You can create a full redaction policy to redact all contents in a data column, and optionally, you can alter the default full redaction value.

- Creating a Full Redaction Policy
  A full data redaction policy redacts all the contents of a data column.
- Altering the Default Full Data Redaction Value
  The `DBMS_REDACT.UPDATE_FULL_REDACTION_VALUES` procedure alters the default full data redaction value.

**Parent topic:** Configuring Oracle Data Redaction Policies

#### 14.7.1 Creating a Full Redaction Policy

A full data redaction policy redacts all the contents of a data column.

- About Creating Full Data Redaction Policies
  To set a redaction policy to redact all data in the column, you must set the `function_type` parameter to `DBMS_REDACT.FULL`.
- Syntax for Creating a Full Redaction Policy
  The `DBMS_REDACT.ADD_POLICY` procedure enables you to create a full redaction policy.
- Example: Full Redaction Policy
  You can use the `DBMS_REDACT.ADD_POLICY` PL/SQL procedure to create a full redaction policy.
- Example: Fully Redacted Character Values
  You can use the DBMS_REDACT.ADD_POLICY PL/SQL procedure to create a policy that fully redacts character values.

**Parent topic:** Creating a Full Redaction Policy and Altering the Full Redaction Value

##### 14.7.1.1 About Creating Full Data Redaction Policies

To set a redaction policy to redact all data in the column, you must set the `function_type` parameter to `DBMS_REDACT.FULL`.

By default, `NUMBER` data type columns are replaced with zero (`0`) and character data type columns are replaced with a single space (` `). You can modify this default by using the `DBMS_REDACT.UPDATE_FULL_REDACTION_VALUES` procedure.

**Related Topics**

- Altering the Default Full Data Redaction Value

**Parent topic:** Creating a Full Redaction Policy

##### 14.7.1.2 Syntax for Creating a Full Redaction Policy

The `DBMS_REDACT.ADD_POLICY` procedure enables you to create a full redaction policy.

The `DBMS_REDACT.ADD_POLICY` fields for creating a full data redaction policy are as follows:

    DBMS_REDACT.ADD_POLICY (
       object_schema           IN VARCHAR2 := NULL,
       object_name             IN VARCHAR2,
       column_name             IN VARCHAR2 := NULL,
       policy_name             IN VARCHAR2,
       function_type           IN BINARY_INTEGER := NULL,
       expression              IN VARCHAR2,
       enable                  IN BOOLEAN := TRUE);

In this specification:

- `object_schema`, `object_name`, `column_name`, `policy_name`, `expression`, `enable`: See General Syntax of the DBMS_REDACT.ADD_POLICY Procedure.

- `function_type`: Specifies the function used to set the type of redaction. Enter `DBMS_REDACT.FULL`.

  If you omit the `function_type` parameter, then the default redaction `function_type` setting is `DBMS_REDACT.FULL`.

  Remember that the data type of the column determines which `function_type` settings that you are permitted to use. See [Comparison of Full, Partial, and Random Redaction Based on Data Types](oracle-data-redaction-features-and-capabilities.md).

**Parent topic:** Creating a Full Redaction Policy

##### 14.7.1.3 Example: Full Redaction Policy

You can use the `DBMS_REDACT.ADD_POLICY` PL/SQL procedure to create a full redaction policy.

Example 14-1 shows how to use full redaction for all the values in the `HR.EMPLOYEES` table `COMMISSION_PCT` column. The expression parameter applies the policy to any user querying the table, except for users who have been granted the `EXEMPT REDACTION POLICY` system privilege.

Example 14-1 Full Data Redaction Policy

    BEGIN
     DBMS_REDACT.ADD_POLICY(
       object_schema    => 'hr',
       object_name      => 'employees',
       column_name      => 'commission_pct',
       policy_name      => 'redact_com_pct',
       function_type    => DBMS_REDACT.FULL,
       expression       => '1=1');
    END;
    /

Query and redacted result:

    SELECT COMMISSION_PCT FROM HR.EMPLOYEES;

    COMMISSION_PCT
    --------------
    0
    0
    0

**Related Topics**

- Exemption of Users from Oracle Data Redaction Policies

**Parent topic:** Creating a Full Redaction Policy

##### 14.7.1.4 Example: Fully Redacted Character Values

You can use the DBMS_REDACT.ADD_POLICY PL/SQL procedure to create a policy that fully redacts character values.

Example 14-2 shows how to redact fully the user IDs of the `user_id` column in the `mavis.cust_info` table. The `user_id` column is of the `VARCHAR2` data type. The output is a blank string. The `expression` setting enables users who have the `MGR` role to view the user IDs.

Example 14-2 Fully Redacted Character Values

    BEGIN
     DBMS_REDACT.ADD_POLICY(
       object_schema   => 'mavis',
       object_name     => 'cust_info',
       column_name     => 'user_id',
       policy_name     => 'redact_cust_user_ids',
       function_type   => DBMS_REDACT.FULL,
       expression      => 'SYS_CONTEXT(''SYS_SESSION_ROLES'',''MGR'') = ''FALSE''');
    END;
    /

Query and redacted result:

    SELECT user_id FROM mavis.cust_info;

    USER_ID
    ------------
    0
    0
    0

**Parent topic:** Creating a Full Redaction Policy

#### 14.7.2 Altering the Default Full Data Redaction Value

The `DBMS_REDACT.UPDATE_FULL_REDACTION_VALUES` procedure alters the default full data redaction value.

- About Altering the Default Full Data Redaction Value
  You can alter the default displayed values for full Data Redaction polices.
- Syntax for the DBMS_REDACT.UPDATE_FULL_REDACTION_VALUES Procedure
  The `DBMS_REDACT.UPDATE_FULL_REDACTION_VALUES` procedure accommodates the standard supported Oracle Database data types.
- Modifying the Default Full Data Redaction Value
  To modify the default full data redaction value, use the `DBMS_REDACT.UPDATE_FULL_REDACTION_VALUES` procedure.

**Parent topic:** Creating a Full Redaction Policy and Altering the Full Redaction Value

##### 14.7.2.1 About Altering the Default Full Data Redaction Value

You can alter the default displayed values for full Data Redaction polices.

By default, `0` is the redacted value when Oracle Database performs full redaction (`DBMS_REDACT.FULL`) on a column of the `NUMBER` data type. If you want to change it to another value (for example, `7`), then you can run the `DBMS_REDACT.UPDATE_FULL_REDACTION_VALUES` procedure to modify this value. The modification applies to all of the Data Redaction policies in the current database instance. After you modify a value, you must restart the database for it to take effect. You can find the current values by querying the `REDACTION_VALUES_FOR_TYPE_FULL` data dictionary view.

Be aware that this change affects all Data Redaction policies in the database that use full data redaction. Before you alter the default full data redaction value, examine the affect that this change would have on existing full Data Redaction policies.

**Parent topic:** Altering the Default Full Data Redaction Value

##### 14.7.2.2 Syntax for the DBMS_REDACT.UPDATE_FULL_REDACTION_VALUES Procedure

The `DBMS_REDACT.UPDATE_FULL_REDACTION_VALUES` procedure accommodates the standard supported Oracle Database data types.

The syntax is as follows:

    DBMS_REDACT.UPDATE_FULL_REDACTION_VALUES (
     number_val       IN NUMBER                    NULL,
     binfloat_val     IN BINARY_FLOAT              NULL,
     bindouble_val    IN BINARY_DOUBLE             NULL,
     char_val         IN CHAR                      NULL,
     varchar_val      IN VARCHAR2                  NULL,
     nchar_val        IN NCHAR                     NULL,
     nvarchar_val     IN NVARCHAR2                 NULL,
     date_val         IN DATE                      NULL,
     ts_val           IN TIMESTAMP                 NULL,
     tswtz_val        IN TIMESTAMP WITH TIME ZONE  NULL,
     blob_val         IN BLOB                      NULL,
     clob_val         IN CLOB                      NULL,
     nclob_val        IN NCLOB                     NULL);

In this specification:

- `number_val` modifies the default value for columns of the `NUMBER` data type.

- `binfloat_val` modifies the default value for columns of the `BINARY_FLOAT` data type.

- `bindouble_val` modifies the default value for columns of the `BINARY_DOUBLE` data type.

- `char_val` modifies the default value for columns of the `CHAR` data type.

- `varchar_val` modifies the default value for columns of the `VARCHAR2` data type.

- `nchar_val` modifies the default value for columns of the `NCHAR` data type.

- `nvarchar_val` modifies the default value for columns of the `NVARCHAR2` data type.

- `date_val` modifies the default value for columns of the `DATE` data type.

- `ts_val` modifies the default value for columns of the `TIMESTAMP` data type.

- `tswtz_val` modifies the default value for columns of the `TIMESTAMP WITH TIME ZONE` data type.

- `blob_val` modifies the default value for columns of the `BLOB` data type.

- `clob_val` modifies the default value for columns of the `CLOB` data type.

- `nclob` modifies the default value for columns of the `NCLOB` data type.

**Parent topic:** Altering the Default Full Data Redaction Value

##### 14.7.2.3 Modifying the Default Full Data Redaction Value

To modify the default full data redaction value, use the `DBMS_REDACT.UPDATE_FULL_REDACTION_VALUES` procedure.

1.  Connect to the PDB as a user who has the `EXECUTE` privilege on the `DBMS_REDACT` PL/SQL package and who has administrative privileges, such as users who have been granted the `DBA` role.
2.  Check the value that you want to change.
    For example, to check the current value for columns that use the `NUMBER` data type:
        SELECT NUMBER_VALUE FROM REDACTION_VALUES_FOR_TYPE_FULL;

        NUMBER_VALUE
        ------------
                   0
3.  Run the `DBMS_REDACT.UPDATE_FULL_REDACTION_VALUES` procedure to modify the value.
    For example:
        EXEC DBMS_REDACT.UPDATE_FULL_REDACTION_VALUES (number_val => 7);
4.  Close and then re-open the PDB.
        ALTER PLUGGABLE DATABASE pdb_name CLOSE IMMEDIATE;
        ALTER PLUGGABLE DATABASE pdb_name OPEN;

**Parent topic:** Altering the Default Full Data Redaction Value

### 14.8 Creating a DBMS_REDACT.NULLIFY Redaction Policy

You can create Oracle Data Redaction policies that return null values for the displayed value of the table or view column.

- About Creating a Policy That Returns Null Values
  The `DBMS_REDACT.NULLIFY` `function_type` parameter redacts all the data in a column and replace it with null values.
- Syntax for Creating a Policy That Returns Null Values
  The `DBMS_REDACT.ADD_POLICY` procedure can create a redaction policy that performs a full redaction and displays null values for the redacted columns.
- Example: Redaction Policy That Returns Null Values
  The DBMS_REDACT.ADD_POLICY procedure will return null values for the `COMMISSION_PCT` column of the `HR.EMPLOYEES` table.

**Parent topic:** Configuring Oracle Data Redaction Policies

#### 14.8.1 About Creating a Policy That Returns Null Values

The `DBMS_REDACT.NULLIFY` `function_type` parameter redacts all the data in a column and replace it with null values.

You can use this function type on all supported column types that the `DBMS_REDACT.FULL` function type supports. It also supports the `CLOB` and `NCLOB` data types. To use the `DBMS_REDACT.NULLIFY` function, you must first ensure that the `COMPATIBLE` parameter is set to `12.2.0.0` or later.

**Parent topic:** Creating a DBMS_REDACT.NULLIFY Redaction Policy

#### 14.8.2 Syntax for Creating a Policy That Returns Null Values

The `DBMS_REDACT.ADD_POLICY` procedure can create a redaction policy that performs a full redaction and displays null values for the redacted columns.

The syntax for using `DBMS_REDACT.ADD_POLICY` to return null values is as follows:

    DBMS_REDACT.ADD_POLICY (
       object_schema           IN VARCHAR2 := NULL,
       object_name             IN VARCHAR2,
       column_name             IN VARCHAR2 := NULL,
       policy_name             IN VARCHAR2,
       function_type           IN BINARY_INTEGER := NULL,
       expression              IN VARCHAR2,
       enable                  IN BOOLEAN := TRUE);

In this specification:

- `object_schema`, `object_name`, `column_name`, `policy_name`, `expression`, `enable`: See General Syntax of the DBMS_REDACT.ADD_POLICY Procedure.

- `function_type`: Specifies the function used to set the type of redaction. Enter `DBMS_REDACT.NULLIFY`.

  If you omit the `function_type` parameter, then the default setting is `DBMS_REDACT.FULL`.

  Remember that the data type of the column determines which `function_type` settings that you are permitted to use. See [Comparison of Full, Partial, and Random Redaction Based on Data Types](oracle-data-redaction-features-and-capabilities.md).

**Parent topic:** Creating a DBMS_REDACT.NULLIFY Redaction Policy

#### 14.8.3 Example: Redaction Policy That Returns Null Values

The DBMS_REDACT.ADD_POLICY procedure will return null values for the `COMMISSION_PCT` column of the `HR.EMPLOYEES` table.

The `expression` parameter applies the policy to any user who queries the table, except for users who have been granted the `EXEMPT REDACTION POLICY` system privilege.

Example 14-3 shows how to create the Oracle Data Redaction policy.

Example 14-3 Redaction Policy That Returns Null Values

    BEGIN
     DBMS_REDACT.ADD_POLICY(
       object_schema    => 'hr',
       object_name      => 'employees',
       column_name      => 'commission_pct',
       policy_name      => 'nullify_com_pct',
       function_type    => DBMS_REDACT.NULLIFY,
       expression       => '1=1');
    END;
    /

Query and redacted result:

    SELECT COMMISSION_PCT FROM HR.EMPLOYEES;

    COMMISSION_PCT
    --------------

**Related Topics**

- Exemption of Users from Oracle Data Redaction Policies

**Parent topic:** Creating a DBMS_REDACT.NULLIFY Redaction Policy

### 14.9 Creating a Partial Redaction Policy

In partial data redaction, you can redact portions of data, and for different kinds of data types.

- About Creating Partial Redaction Policies
  In partial data redaction, only a portion of the data, such as the first five digits of an identification number, are redacted.
- Syntax for Creating a Partial Redaction Policy
  The `DBMS_REDACT.ADD_POLICY` statement enables you to create policies that redact specific parts of the data returned to the application.
- Creating Partial Redaction Policies Using Fixed Character Formats
  The `DBMS_REDACT.ADD_POLICY` `function_parameters` parameter enables you to use fixed character formats.
- Creating Partial Redaction Policies Using Character Data Types
  The `DBMS_REDACT.ADD_POLICY` `function_parameters` parameter enables you to redact character data types.
- Creating Partial Redaction Policies Using Number Data Types
  The `DBMS_REDACT.ADD_POLICY` `function_parameters` parameter can redact number data types.
- Creating Partial Redaction Policies Using Date-Time Data Types
  The `DBMS_REDACT.ADD_POLICY` `function_parameters` parameter can redact date-time data types.

**Parent topic:** Configuring Oracle Data Redaction Policies

#### 14.9.1 About Creating Partial Redaction Policies

In partial data redaction, only a portion of the data, such as the first five digits of an identification number, are redacted.

For example, you can redact most of a credit card number with asterisks (\*), except for the last 4 digits. You can create policies for columns that use character, number, or date-time data types. For policies that redact character data types, you can use fixed character redaction formats. If you have the Enterprise Manager for Oracle Database 12.1.0.7 plug-in deployed on your system, then you can also create and save custom redaction formats.

**Note:**

In previous releases, the term shortcut was used for the term format.

**Parent topic:** Creating a Partial Redaction Policy

#### 14.9.2 Syntax for Creating a Partial Redaction Policy

The `DBMS_REDACT.ADD_POLICY` statement enables you to create policies that redact specific parts of the data returned to the application.

The `DBMS_REDACT.ADD_POLICY` fields for creating a partial redaction policy are as follows:

    DBMS_REDACT.ADD_POLICY (
       object_schema           IN VARCHAR2 := NULL,
       object_name             IN VARCHAR2,
       column_name             IN VARCHAR2 := NULL,
       policy_name             IN VARCHAR2,
       function_type           IN BINARY_INTEGER := NULL,
       function_parameters     IN VARCHAR2 := NULL,
       expression              IN VARCHAR2,
       enable                  IN BOOLEAN := TRUE);

In this specification:

- `object_schema`, `object_name`, `column_name`, `policy_name`, `expression`, `enable`: See General Syntax of the DBMS_REDACT.ADD_POLICY Procedure

- `function_type`: Specifies the function used to set the type of redaction. Enter `DBMS_REDACT.PARTIAL`.

- `function_parameters`: The parameters that you set here depend on the data type of the column specified for the `column_name` parameter. See the following sections for details:

  - Creating Partial Redaction Policies Using Fixed Character Formats

  - Creating Partial Redaction Policies Using Character Data Types

  - Creating Partial Redaction Policies Using Number Data Types

  - Creating Partial Redaction Policies Using Date-Time Data Types

**Parent topic:** Creating a Partial Redaction Policy

#### 14.9.3 Creating Partial Redaction Policies Using Fixed Character Formats

The `DBMS_REDACT.ADD_POLICY` `function_parameters` parameter enables you to use fixed character formats.

- Settings for Fixed Character Formats
  Oracle Data Redaction provides special predefined formats to configure policies that use fixed characters.
- Example: Partial Redaction Policy Using a Fixed Character Format
  You can use the `DBMS_REDACT.ADD_POLICY` PL/SQL procedure to create a partial redaction policy that uses a fixed character format.

**Parent topic:** Creating a Partial Redaction Policy

##### 14.9.3.1 Settings for Fixed Character Formats

Oracle Data Redaction provides special predefined formats to configure policies that use fixed characters.

Table 14-8 describes `DBMS_REDACT.ADD_POLICY` `function_parameters` parameter formats that you can use for commonly redacted identity numbers (such as Social Security numbers or Canadian Social Insurance Numbers), postal codes, and credit cards that use either the `VARCHAR2` or `NUMBER` data types for their columns.

Table 14-8 Partial Fixed Character Redaction Formats

| Format                                    | Description                                                                                                                                                                                                        |
|:------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DBMS_REDACT.REDACT_US_SSN_F5`            | Redacts the first 5 numbers of Social Security numbers when the column is a `VARCHAR2` data type. For example, the number `987-65-4320` becomes `XXX-XX-4320`.                                                     |
| `DBMS_REDACT.REDACT_US_SSN_L4`            | Redacts the last 4 numbers of Social Security numbers when the column is a `VARCHAR2` data type. For example, the number `987-65-4320` becomes `987-65-XXXX`.                                                      |
| `DBMS_REDACT.REDACT_US_SSN_ENTIRE`        | Redacts the entire Social Security number when the column is a `VARCHAR2` data type. For example, the number `987-65-4320` becomes `XXX-XX-XXXX`.                                                                  |
| `DBMS_REDACT.REDACT_NUM_US_SSN_F5`        | Redacts the first 5 numbers of Social Security numbers when the column is a `NUMBER` data type. For example, the number `987654320` becomes `XXXXX4320`.                                                           |
| `DBMS_REDACT.REDACT_NUM_US_SSN_L4`        | Redacts the last 4 numbers of Social Security numbers when the column is a `NUMBER` data type. For example, the number `987654320` becomes `98765XXXX`.                                                            |
| `DBMS_REDACT.REDACT_NUM_US_SSN_ENTIRE`    | Redacts the entire Social Security number when the column is a `NUMBER` data type. For example, the number `987654320` becomes `XXXXXXXXX`.                                                                        |
| `DBMS_REDACT.REDACT_SIN_NUMBER`           | Redacts the Canadian Social Insurance number by replacing the first 6 digits by `9` (number). For example, `123456789` is redacted to `999999789`.                                                                 |
| `DBMS_REDACT.REDACT_SIN_UNFORMATTED`      | Redacts the Canadian Social Insurance number by replacing the first 6 digits by `X` (string). For example, `123456789` is redacted to `XXXXXX789`.                                                                 |
| `DBMS_REDACT.REDACT_SIN_FORMATTED`        | Redacts the Canadian Social Insurance Number by replacing the first 6 digits by `X` (string). For example, `123-456-789` is redacted to `XXX-XXX-789`.                                                             |
| `DBMS_REDACT.REDACT_UK_NIN_FORMATTED`     | Redacts the UK National Insurance number by replacing the first 6 digits by `X` (string) but leaving the alphabetic characters as is. For example, `ET 27 02 23 D` is redacted to `ET XX XX XX D`.                 |
| `DBMS_REDACT.REDACT_UK_NIN_UNFORMATTED`   | Redacts the UK National Insurance number by replacing the first 6 digits by `X` (string) and leaving the alphabetic characters as is. For example, `ET270223D` is redacted to `ETXXXXXXD`.                         |
| `DBMS_REDACT.REDACT_CCN_FORMATTED`        | Redacts the credit card number (other than American Express) by replacing everything but the last 4 digits by `*`. For example, the credit card number `5105–1051–0510–5100` is redacted to `****—****—****—5100`. |
| `DBMS_REDACT.REDACT_CCN_NUMBER`           | Redacts the credit card number (other than American Express) by replacing everything but the last 4 digits by `0`. For example, the credit card number `5105105105105100` is redacted to `************5100`.       |
| `DBMS_REDACT.REDACT_CCN16_F12`            | Redacts a 16-digit credit card number (other than American Express), leaving the last 4 digits displayed. For example, `5105 1051 0510 5100` becomes `****-****-****-5100`.                                        |
| `DBMS_REDACT.REDACT_AMEX_CCN_FORMATTED`   | Redacts the American Express credit card number by replacing the digits with `*` except the last 5 digits. For example, the credit card number `3782 822463 10005` is redacted to `**** ****** 10005`.             |
| `DBMS_REDACT.REDACT_AMEX_CCN_NUMBER`      | Redacts the American Express Credit Card Number by replacing the digits with `0` except the last 5 digits. For example, the credit card number `3782 822463 10005` is redacted to `0000 000000 10005`.             |
| `DBMS_REDACT.REDACT_ZIP_CODE`             | Redacts a 5-digit postal code when the column is a `VARCHAR2` data type. For example, `95476` becomes `XXXXX`.                                                                                                     |
| `DBMS_REDACT.REDACT_NUM_ZIP_CODE`         | Redacts a 5-digit postal code when the column is a `NUMBER` data type. For example, `95476` becomes `XXXXX`.                                                                                                       |
| `DBMS_REDACT.REDACT_DATE_EPOCH`           | Redacts all dates to `01-JAN-70`.                                                                                                                                                                                  |
| `DBMS_REDACT.REDACT_NA_PHONE_FORMATTED`   | Redacts the North American phone number by leaving the area code, but replacing everything else with `X`. For example, `650-555–0100` is redacted to `650-XXX-XXXX`.                                               |
| `DBMS_REDACT.REDACT_NA_PHONE_NUMBER`      | Redacts the North American phone number by leaving the area code, but replacing everything else with `0`. For example, `6505550100` gets redacted to `650000000`.                                                  |
| `DBMS_REDACT.REDACT_NA_PHONE_UNFORMATTED` | Redacts the North American phone number by leaving the area code, but replacing everything else with `X`. For example, `6505550100` is redacted to `650XXXXXXX`.                                                   |
| `DBMS_REDACT.REDACT_DATE_MILLENNIUM`      | Redacts dates that are in the `DD-MON-YY` format to `01-JAN-00` (January 1, 2000).                                                                                                                                 |

**See Also:**

General Syntax of the DBMS_REDACT.ADD_POLICY Procedure for information about other `DBMS_REDACT.ADD_POLICY` parameters

**Parent topic:** Creating Partial Redaction Policies Using Fixed Character Formats

##### 14.9.3.2 Example: Partial Redaction Policy Using a Fixed Character Format

You can use the `DBMS_REDACT.ADD_POLICY` PL/SQL procedure to create a partial redaction policy that uses a fixed character format.

Example 14-4 shows how Social Security numbers in a `VARCHAR2` data type column and can be redacted using the `REDACT_US_SSN_F5 ` format.

Example 14-4 Partially Redacted Character Values

    BEGIN
     DBMS_REDACT.ADD_POLICY(
       object_schema       => 'mavis',
       object_name         => 'cust_info',
       column_name         => 'ssn',
       policy_name         => 'redact_cust_ssns3',
       function_type       => DBMS_REDACT.PARTIAL,
       function_parameters => DBMS_REDACT.REDACT_US_SSN_F5,
       expression          => '1=1',
       policy_description  => 'Partially redacts 1st 5 digits in SS numbers',
       column_description  => 'ssn contains Social Security numbers');
    END;
    /

Query and redacted result:

    SELECT ssn FROM mavis.cust_info;

    SSN
    -------
    XXX-XX-4320
    XXX-XX-4323
    XXX-XX-4325
    XXX-XX-4329

**Parent topic:** Creating Partial Redaction Policies Using Fixed Character Formats

#### 14.9.4 Creating Partial Redaction Policies Using Character Data Types

The `DBMS_REDACT.ADD_POLICY` `function_parameters` parameter enables you to redact character data types.

- Settings for Character Data Types
  Oracle Data Redaction provides special settings to configure policies that use character data types.
- Example: Partial Redaction Policy Using a Character Data Type
  The `DBMS_REDACT.ADD_POLICY` PL/SQL procedure can create a partial redaction policy that uses a character data type.

**Parent topic:** Creating a Partial Redaction Policy

##### 14.9.4.1 Settings for Character Data Types

Oracle Data Redaction provides special settings to configure policies that use character data types.

When you set the `DBMS_REDACT.ADD_POLICY` `function_parameters` parameter to define partial redaction of character data types, enter values for the following settings in the order shown. Separate each value with a comma

**Note:**

Be aware that you must use a fixed width character set for the partial redaction. In other words, each character redacted must be replaced by another of equal byte length. If you want to use a variable-length character set (for example, UTF-8), then you must use a regular expression-based redaction. See Syntax for Creating a Regular Expression-Based Redaction Policy for more information.

The settings are as follows:

1.  Input format: Defines how the data is currently formatted. Enter `V` for each character that potentially can be redacted, such as all of the digits in a credit card number. Enter `F` for each character that you want to format using a formatting character, such as hyphens or blank spaces in the credit card number. Ensure that each character has a corresponding `V` or `F` value. (The input format values are not case-sensitive.)

2.  Output format: Defines how the displayed data should be formatted. Enter `V` for each character to be potentially redacted. Replace each `F` character in the input format with the character that you want to use for the displayed output, such as a hyphen. (The output format values are not case-sensitive.)

3.  Mask character: Specifies the character to be used for the redaction. Enter a single character to use for the redaction, such as an asterisk (\*).

4.  Starting digit position: Specifies the starting `V` digit position for the redaction.

5.  Ending digit position: Specifies the ending `V` digit position for the redaction. Do not include the `F` positions when you decide on the ending position value.

For example, the following setting redacts the first 12 `V` digits of the credit card number `5105 1051 0510 5100`, and replaces the `F` positions (which are blank spaces) with hyphens to format it in a style normally used for credit card numbers, resulting in `****-****-****-4320`.

    function_parameters  => 'VVVVFVVVVFVVVVFVVVV,VVVV-VVVV-VVVV-VVVV,*,1,12',

**See Also:**

General Syntax of the DBMS_REDACT.ADD_POLICY Procedure for information about other `DBMS_REDACT.ADD_POLICY` parameters

**Parent topic:** Creating Partial Redaction Policies Using Character Data Types

##### 14.9.4.2 Example: Partial Redaction Policy Using a Character Data Type

The `DBMS_REDACT.ADD_POLICY` PL/SQL procedure can create a partial redaction policy that uses a character data type.

Example 14-5 shows how to redact Social Security numbers that are in a `VARCHAR2` data type column and to preserve the character hyphens in the Social Security number.

Example 14-5 Partially Redacted Character Values

    BEGIN
     DBMS_REDACT.ADD_POLICY(
       object_schema       => 'mavis',
       object_name         => 'cust_info',
       column_name         => 'ssn',
       policy_name         => 'redact_cust_ssns2',
       function_type       => DBMS_REDACT.PARTIAL,
       function_parameters => 'VVVFVVFVVVV,VVV-VV-VVVV,*,1,5',
       expression          => '1=1',
       policy_description  => 'Partially redacts Social Security numbers',
       column_description  => 'ssn contains character Social Security numbers');
    END;
    /

Query and redacted result:

    SELECT ssn FROM mavis.cust_info;

    SSN
    -----------
    ***-**-4320
    ***-**-4323
    ***-**-4325
    ***-**-4329

**Parent topic:** Creating Partial Redaction Policies Using Character Data Types

#### 14.9.5 Creating Partial Redaction Policies Using Number Data Types

The `DBMS_REDACT.ADD_POLICY` `function_parameters` parameter can redact number data types.

- Settings for Number Data Types
  When you set values for the number data type, you must specify a mask character, a starting digit position, and ending digit position.
- Example: Partial Redaction Policy Using a Number Data Type
  The `DBMS_REDACT.ADD_POLICY` procedure can create a partial redaction policy that uses a number data type.

**Parent topic:** Creating a Partial Redaction Policy

##### 14.9.5.1 Settings for Number Data Types

When you set values for the number data type, you must specify a mask character, a starting digit position, and ending digit position.

For partial redaction of number data types, you can enter values for the following settings for the `function_parameters` parameter of the `DBMS_REDACT.ADD_POLICY` procedure, in the order shown.

1.  Mask character: Specifies the character to display. Enter a number from 0 to 9.

2.  Starting digit position: Specifies the starting digit position for the redaction, such as `1` for the first digit.

3.  Ending digit position: Specifies the ending digit position for the redaction.

For example, the following setting redacts the first five digits of the Social Security number `987654321`, resulting in `999994321`.

    function_parameters  => '9,1,5',

**See Also:**

General Syntax of the DBMS_REDACT.ADD_POLICY Procedure for information about other `DBMS_REDACT.ADD_POLICY` parameters

**Parent topic:** Creating Partial Redaction Policies Using Number Data Types

##### 14.9.5.2 Example: Partial Redaction Policy Using a Number Data Type

The `DBMS_REDACT.ADD_POLICY` procedure can create a partial redaction policy that uses a number data type.

Example 14-6 shows how to partially redact a set of Social Security numbers in the `mavis.cust_info` table, for any application user who logs in. (Hence, the `expression` parameter evaluates to `TRUE`.)

This type of redaction is useful when the application is expecting a formatted number and not a string. In this scenario, the Social Security numbers are in a column of the data type `NUMBER`. In other words, the `ssn` column contains numbers only, not other characters such as hyphens or blank spaces.

Example 14-6 Partially Redacted Data Redaction Numeric Values

    BEGIN
     DBMS_REDACT.ADD_POLICY(
       object_schema       => 'mavis',
       object_name         => 'cust_info',
       column_name         => 'ssn',
       policy_name         => 'redact_cust_ssns1',
       function_type       => DBMS_REDACT.PARTIAL,
       function_parameters => '7,1,5',
       expression          => '1=1',
       policy_description  => 'Partially redacts Social Security numbers',
       column_description  => 'ssn contains numeric Social Security numbers');
    END;
    /

Query and redacted result:

    SELECT ssn FROM mavis.cust_info;

    SSN
    ---------
    777774320
    777774323
    777774325
    777774329

**Parent topic:** Creating Partial Redaction Policies Using Number Data Types

#### 14.9.6 Creating Partial Redaction Policies Using Date-Time Data Types

The `DBMS_REDACT.ADD_POLICY` `function_parameters` parameter can redact date-time data types.

- Settings for Date-Time Data Types
  Oracle Data Redaction provides special settings for configuring date-time data types.
- Example: Partial Redaction Policy Using Date-Time Data Type
  The `DBMS_REDACT.ADD_POLICY` procedure can create a partial redaction policy that uses the date-time data type.

**Parent topic:** Creating a Partial Redaction Policy

##### 14.9.6.1 Settings for Date-Time Data Types

Oracle Data Redaction provides special settings for configuring date-time data types.

For partial redaction of date-time data types, enter values for the following `DBMS_REDACT.ADD_POLICY` `function_parameters` parameter settings.

Enter these values in the order shown:

1.  m: Redacts the month. To redact with a month name, append `1`–`12` to lowercase `m`. For example, `m5` displays as `MAY`. To omit redaction, enter an uppercase `M`.

2.  d: Redacts the day of the month. To redact with a day of the month, append `1`–`31` to a lowercase `d`. For example, `d7` displays as `07`. If you enter a higher number than the days of the month (for example, `31` for the month of February), then the last day of the month is displayed (for example, `28`). To omit redaction, enter an uppercase `D`.

3.  y: Redacts the year. To redact with a year, append `1`–`9999` to a lowercase `y`. For example, `y1984` displays as `84`. To omit redaction, enter an uppercase `Y`.

4.  h: Redacts the hour. To redact with an hour, append `0`–`23` to a lowercase `h`. For example, `h20` displays as `20`. To omit redaction, enter an uppercase `H`.

5.  m: Redacts the minute. To redact with a minute, append `0`–`59` to a lowercase `m`. For example, `m30` displays as `30`. To omit redaction, enter an uppercase `M`.

6.  s: Redacts the second. To redact with a second, append `0`–`59` to a lowercase `s`. For example, `s45` displays as `45`. To omit redaction, enter an uppercase `S`.

**See Also:**

General Syntax of the DBMS_REDACT.ADD_POLICY Procedure for information about other `DBMS_REDACT.ADD_POLICY` parameters

**Parent topic:** Creating Partial Redaction Policies Using Date-Time Data Types

##### 14.9.6.2 Example: Partial Redaction Policy Using Date-Time Data Type

The `DBMS_REDACT.ADD_POLICY` procedure can create a partial redaction policy that uses the date-time data type.

Example 14-7 shows how to partially redact a date. This example redacts the birth year of customers; replacing it with `13`, but retaining the remaining values.

Example 14-7 Partially Redacted Data Redaction Using Date-Time Values

    BEGIN
     DBMS_REDACT.ADD_POLICY(
       object_schema       => 'mavis',
       object_name         => 'cust_info',
       column_name         => 'birth_date',
       policy_name         => 'redact_cust_bdate',
       function_type       => DBMS_REDACT.PARTIAL,
       function_parameters => 'mdy2013HMS',
       expression          => '1=1',
       policy_description  => 'Replaces birth year with 2013',
       column_description  => 'birth_date contains customer's birthdate');
    END;
    /

Query and redacted result:

    SELECT birth_date FROM mavis.cust_info;

    BIRTH_DATE
    07-DEC-13 09.45.40.000000 AM
    12-OCT-13 04.23.29.000000 AM

**Parent topic:** Creating Partial Redaction Policies Using Date-Time Data Types

### 14.10 Creating a Regular Expression-Based Redaction Policy

A regular expression-based redaction policy enables you to redact data based on a search-and-replace model.

- About Creating Regular Expression-Based Redaction Policies
  Regular expression-based redaction enables you to search for patterns of data to redact.
- Syntax for Creating a Regular Expression-Based Redaction Policy
  The `regexp_*` parameters of the `DBMS_REDACT.ADD_POLICY` procedure can create a regular expression-based redaction policy.
- Regular Expression-Based Redaction Policies Using Formats
  The `DBMS_REDACT.ADD_POLICY` procedure `regexp_pattern` and `regexp_replace_string` parameters both support formats.
- Custom Regular Expression Redaction Policies
  You can customize regular expressions in Data Redaction policies.

**Parent topic:** Configuring Oracle Data Redaction Policies

#### 14.10.1 About Creating Regular Expression-Based Redaction Policies

Regular expression-based redaction enables you to search for patterns of data to redact.

For example, you can use regular expressions to redact email addresses, which can have varying character lengths. It is designed for use with character data only. You can use formats for the search and replace operation, or you can create custom pattern formats.

You cannot use regular expressions to redact a subset of the values in a column. The `REGEXP_PATTERN` (regular expression pattern) must match all of the values in order for the `REGEXP_REPLACE_STRING` setting to take effect, and the `REGEXP_REPLACE_STRING` must change the value.

For rows where the `REGEXP_PATTERN` fails to match, Data Redaction performs `DBMS_REDACT.FULL` redaction. This mitigates the risk of a mistake in the `REGEXP_PATTERN` which causes the regular expression to fail to match all of the values in the column, from showing the actual data for those rows which it failed to match.

In addition, if no change to the value occurs as a result of the `REGEXP_REPLACE_STRING` setting during regular expression replacement operation, Data Redaction performs `DBMS_REDACT.FULL` redaction.

**Parent topic:** Creating a Regular Expression-Based Redaction Policy

#### 14.10.2 Syntax for Creating a Regular Expression-Based Redaction Policy

The `regexp_*` parameters of the `DBMS_REDACT.ADD_POLICY` procedure can create a regular expression-based redaction policy.

The `DBMS_REDACT.ADD_POLICY` fields for creating a regular expression-based data redaction policy are as follows:

    DBMS_REDACT.ADD_POLICY (
       object_schema           IN VARCHAR2 := NULL,
       object_name             IN VARCHAR2,
       column_name             IN VARCHAR2 := NULL,
       policy_name             IN VARCHAR2,
       function_type           IN BINARY_INTEGER := NULL,
       expression              IN VARCHAR2,
       enable                  IN BOOLEAN := TRUE,
       regexp_pattern          IN VARCHAR2 := NULL,
       regexp_replace_string   IN VARCHAR2 := NULL,
       regexp_position         IN BINARY_INTEGER := 1,
       regexp_occurrence       IN BINARY_INTEGER := 0,
       regexp_match_parameter  IN VARCHAR2 := NULL);

In this specification:

- `object_schema`, `object_name`, `column_name`, `policy_name`, `expression`, `enable`: See General Syntax of the DBMS_REDACT.ADD_POLICY Procedure.

- `function_type`: Specifies the type of redaction. For regular expression based redaction, use either `DBMS_REDACT.REGEXP` or `DBMS_REDACT.REGEXP_WIDTH`.

  If you use the `DBMS_REDACT.REGEXP` redaction type, then no truncation occurs. This applies even if the redacted value is wider than the column width, and if the Oracle Call Interface width attribute (`OCI_ATTR_CHAR_SIZE`) of the column is not preserved. (It becomes 4000, just as it does when the `REGEXP_REPLACE` SQL operator is used on a column.)

  Using the `DBMS_REDACT.REGEXP_WIDTH` redaction type truncates any redacted value that exceeds the width of the column, and ensures that the OCI width attribute of the column (`OCI_ATTR_CHAR_SIZE`) remains unchanged.

  Note the following:

  - Use the `DBMS_REDACT.REGEXP_WIDTH` function type if your applications depend on the value of the `OCI_ATTR_CHAR_SIZE` attribute. For example, applications that are built using the Oracle OLE DB Provider interface are sensitive to the value of the `OCI_ATTR_CHAR_SIZE` attribute. If you use `DBMS_REDACT.REGEXP` as the redaction type, then the `OCI_ATTR_CHAR_SIZE` always becomes 4000. This setting makes it unsuitable as the redaction type of policies on tables that are used by Oracle OLE DB based applications. See [Oracle Call Interface Programmer's Guide](../lnoci/describing-schema-metadata.md) for more information about Oracle Call Interface parameter attributes.

  - When you set the `function_type` parameter to `DBMS_REDACT.REGEXP` or `DBMS_REDACT.REGEXP_WIDTH`, omit the `function_parameters` parameter from the `DBMS_REDACT.ADD_POLICY` procedure.

  - Specify the regular expression parameters in much the same way that you specify the `pattern`, `replace`, `position`, `occurrence`, and `match_parameter` arguments to the `REGEXP_REPLACE` SQL function. See [Oracle Database SQL Language Reference](../sqlrf/REGEXP_REPLACE.md) for information about the `REGEXP_REPLACE` SQL function.

- `regexp_pattern`: Describes the search pattern for data that must be matched. If it finds a match, then Oracle Database replaces the data as specified by the `regexp_replace_string` setting. See the following sections for more information:

  - Regular Expression-Based Redaction Policies Using Formats

  - Custom Regular Expression Redaction Policies

- `regexp_replace_string`: Specifies how you want to replace the data to be redacted. See the following sections for more information:

  - Regular Expression-Based Redaction Policies Using Formats

  - Custom Regular Expression Redaction Policies

- `regexp_position`: Specifies the starting position for the string search. The value that you enter must be a positive integer indicating the character of the `column_name` data where Oracle Database should begin the search. The default is `1` or the `DBMS_REDACT.RE_BEGINNING` format, meaning that Oracle Database begins the search at the first character of the `column_name` data.

- `regexp_occurrence`: Specifies how to perform the search and replace operation. The value that you enter must be a nonnegative integer indicating the occurrence of the replace operation:

  - If you specify `0` or the `DBMS_REDACT.RE_ALL` format, then Oracle Database replaces all the occurrences of the match.

  - If you specify the `DBMS_REDACT.RE_FIRST` format, then Oracle Database replaces the first occurrence of the match.

  - If you specify a positive integer `n`, then Oracle Database replaces the `n`th occurrence of the match.

  If the occurrence is greater than 1, then the database searches for the second occurrence beginning with the first character following the first occurrence of pattern, and so forth.

- `regexp_match_parameter`: Specifies a text literal that lets you change the default matching behavior of the function. The behavior of this parameter is the same for this function as for the `REGEXP_REPLACE` SQL function. See [Oracle Database SQL Language Reference](../sqlrf/REGEXP_REPLACE.md) for detailed information.

  To filter the search so that it is not case sensitive, specify the `RE_CASE_INSENSITIVE` format.

**Parent topic:** Creating a Regular Expression-Based Redaction Policy

#### 14.10.3 Regular Expression-Based Redaction Policies Using Formats

The `DBMS_REDACT.ADD_POLICY` procedure `regexp_pattern` and `regexp_replace_string` parameters both support formats.

- Regular Expression Formats
  The regular expression formats represent commonly used expressions, such as the replacement of digits within a credit card number.
- Example: Regular Expression Redaction Policy Using Formats
  The DBMS_REDACT.ADD_POLICY procedure can create a regular expression redaction policy that uses formats.

**Parent topic:** Creating a Regular Expression-Based Redaction Policy

##### 14.10.3.1 Regular Expression Formats

The regular expression formats represent commonly used expressions, such as the replacement of digits within a credit card number.

Table 14-9 describes the formats that you can use with the `regexp_pattern` parameter in the `DBMS_REDACT.ADD_POLICY` procedure.

Table 14-9 Formats for the regexp_pattern Parameter

| Format                                 | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
|:---------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DBMS_REDACT.RE_PATTERN_ANY_DIGIT`     | Searches for any digit. Replaces the identified pattern with the characters specified by the`regexp_replace_string` parameter. The `DBMS_REDACT.RE_PATTERN_ANY_DIGIT` is commonly used with the following values of the `regexp_replace_string` parameter:<br>`regexp_replace_string => DBMS_REDACT.RE_REDACT_WITH_SINGLE_X, `<br>This setting replaces any matched digit with the `X` character.<br>The following setting replaces any matched digit with the `1` character.<br>`regexp_replace_string => DBMS_REDACT.RE_REDACT_WITH_SINGLE_1, ` |
| `DBMS_REDACT.RE_PATTERN_CC_L6_T4`      | Searches for the middle digits of any credit card (other than American Express) that has 6 leading digits and 4 trailing digits. Replaces the identified pattern with the characters specified by the `regexp_replace_string` parameter.<br>The appropriate `regexp_replace_string` setting to use with this format is `DBMS_REDACT.RE_REDACT_CC_MIDDLE_DIGITS`, which finds any credit card that could have 6 leading and 4 trailing digits left as [actual data](glossary.md). It then redacts the middle digits.                               |
| `DBMS_REDACT.RE_PATTERN_CCN`           | Matches credit card numbers other than American Express credit card numbers. The appropriate `regexp_replace_string` setting to use with this format is `DBMS_REDACT.RE_REDACT_CCN`. The end result is a redaction of all the digits except the last 4.                                                                                                                                                                                                                                                                                           |
| `DBMS_REDACT.RE_PATTERN_AMEX_CCN`      | Matches American Express credit card numbers. The appropriate `regexp_replace_string` setting to use with this format is `DBMS_REDACT.RE_REDACT_AMEX_CCN`. The end result is a redaction of all the digits except the last 5.                                                                                                                                                                                                                                                                                                                     |
| `DBMS_REDACT.RE_PATTERN_US_PHONE`      | Searches for any U.S. telephone number. Replaces the identified pattern with the characters specified by the`regexp_replace_string` parameter<br>The appropriate `regexp_replace_string` setting to use with this format is `DBMS_REDACT.RE_REDACT_US_PHONE_L7`, which finds United States phone numbers and then redacts the last 7 digits.                                                                                                                                                                                                      |
| `DBMS_REDACT.RE_PATTERN_EMAIL_ADDRESS` | Searches for any email address. Replaces the identified pattern with the characters specified by the`regexp_replace_string` parameter<br>The appropriate `regexp_replace_string` settings that you can use with this format are as follows:<br>`RE_REDACT_EMAIL_NAME`, which finds any email address and redacts the email user name<br>`RE_REDACT_EMAIL_DOMAIN`, which finds any email address and redacts the email domain<br>`RE_REDACT_EMAIL_ENTIRE`, which finds any email address and redacts the entire email address                      |
| `DBMS_REDACT.RE_PATTERN_IP_ADDRESS`    | Searches for an IP address. Replaces the identified pattern with the characters specified by the`regexp_replace_string` parameter.<br>The appropriate `regexp_replace_string` setting to use with this format is `DBMS_REDACT.RE_REDACT_IP_L3`, which replaces the last section of the dotted decimal string representation of an IP address with the characters `999` to indicate that it was redacted.                                                                                                                                          |

Table 14-10 describes formats that you can use with the `regexp_replace_string` parameter in the `DBMS_REDACT.ADD_POLICY` procedure.

Table 14-10 Formats for the regexp_replace_string Parameter

| Format                                   | Description                                                                                                                                                                                                                                                                                                                                                                                  |
|:-----------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DBMS_REDACT.RE_REDACT_WITH_SINGLE_X`    | Replaces the data with a single `X` character for each of the [actual data](glossary.md) characters. For example, the credit card number `5105 1051 0510 5100` could be replaced with `XXXX XXXX XXXX XXXX`.                                                                                                                                                                                 |
| `DBMS_REDACT.RE_REDACT_WITH_SINGLE_1`    | Replaces the data with a single `1` digit for each of the actual data digits. For example, the credit card number `5105 1051 0510 5100` could be replaced with `1111 1111 1111 1111`.                                                                                                                                                                                                        |
| `DBMS_REDACT.RE_REDACT_CC_MIDDLE_DIGITS` | Redacts the middle digits in credit card numbers, as specified by setting the `regexp_pattern` parameter with the `RE_PATTERN_CC_L6_T4` format. The redaction replaces each redacted character with an `X`. For example, the credit card number `5105 1051 0510 5100` could be replaced with `5105 10XX XXXX 5100`.                                                                          |
| `DBMS_REDACT.RE_REDACT_CCN`              | Redacts the first 12 digits of a credit card number other than an American Express card number. For example, `4012888888881881` is redacted to `************1881`.                                                                                                                                                                                                                           |
| `DBMS_REDACT.RE_REDACT_AMEX_CCN`         | Redacts the first 10 digits of an American Express number. For example, `378282246310005` is redacted to `**********10005`.                                                                                                                                                                                                                                                                  |
| `DBMS_REDACT.RE_REDACT_PHONE_L7`         | Redacts the last 7 digits of U.S. telephone numbers, as specified by setting the `regexp_pattern` parameter with the `RE_PATTERN_US_PHONE` format. The redaction replaces each redacted character with an `X`. This setting only applies to hyphenated phone numbers, not phone numbers with spaces. For example, the telephone number `415-555-0100` could be replaced with `415-XXX-XXXX`. |
| `DBMS_REDACT.RE_REDACT_EMAIL_NAME`       | Redacts the email name as specified by setting the `regexp_pattern` parameter with the `RE_PATTERN_EMAIL_ADDRESS` format. The redaction replaces the email user name with four `x` characters. For example, the email address `psmith@example.com` could be replaced with `xxxx@example.com`.                                                                                                |
| `DBMS_REDACT.RE_REDACT_EMAIL_DOMAIN`     | Redacts the email domain name as specified by setting the `regexp_pattern` parameter with the `RE_PATTERN_EMAIL_ADDRESS` format. The redaction replaces the domain with five `x` characters. For example, the email address `psmith@example.com` could be replaced with `psmith@xxxxx.com`.                                                                                                  |
| `DBMS_REDACT.RE_REDACT_IP_L3`            | Redacts the last three digits of the IP address as specified by setting the `regexp_pattern` parameter with the `RE_PATTERN_IP_ADDRESS` format. For example, the IP address `192.0.2.254` could be replaced with `192.0.2.999`, which is an invalid IP address.                                                                                                                              |

**See Also:**

General Syntax of the DBMS_REDACT.ADD_POLICY Procedure for information about other `DBMS_REDACT.ADD_POLICY` parameters

**Parent topic:** Regular Expression-Based Redaction Policies Using Formats

##### 14.10.3.2 Example: Regular Expression Redaction Policy Using Formats

The DBMS_REDACT.ADD_POLICY procedure can create a regular expression redaction policy that uses formats.

Example 14-8 shows how to use regular expression formats to redact credit card numbers.

Example 14-8 Regular Expression Data Redaction Character Values

    BEGIN
     DBMS_REDACT.ADD_POLICY(
       object_schema          => 'mavis',
       object_name            => 'cust_info',
       column_name            => 'cc_num',
       policy_name            => 'redact_cust_cc_nums',
       function_type          => DBMS_REDACT.REGEXP,
       function_parameters    => NULL,
       expression             => '1=1',
       regexp_pattern         => DBMS_REDACT.RE_PATTERN_CC_L6_T4,
       regexp_replace_string  => DBMS_REDACT.RE_REDACT_CC_MIDDLE_DIGITS,
       regexp_position        => DBMS_REDACT.RE_BEGINNING,
       regexp_occurrence      => DBMS_REDACT.RE_FIRST,
       regexp_match_parameter => DBMS_REDACT.RE_CASE_INSENSITIVE,
       policy_description     => 'Regular expressions to redact credit card numbers',
       column_description     => 'cc_num contains customer credit card numbers');
    END;
    /

Query and redacted result:

    SELECT cc_num FROM mavis.cust_info;

    CC_NUM
    -------
    401288XXXXXX1881
    411111XXXXXX1111
    555555XXXXXX1111
    511111XXXXXX1118

**Parent topic:** Regular Expression-Based Redaction Policies Using Formats

#### 14.10.4 Custom Regular Expression Redaction Policies

You can customize regular expressions in Data Redaction policies.

- Settings for Custom Regular Expressions
  Oracle Data Redaction provides special settings to configure policies that use regular expressions.
- Example: Custom Regular Expression Redaction Policy
  The `DBMS_REDACT.ADD_POLICY` procedure regexp\* parameters can create a custom regular expression redaction policy.

**Parent topic:** Creating a Regular Expression-Based Redaction Policy

##### 14.10.4.1 Settings for Custom Regular Expressions

Oracle Data Redaction provides special settings to configure policies that use regular expressions.

To create custom regular expression redaction policies, you use the following parameters in the `DBMS_REDACT.ADD_POLICY` procedure:

- `regexp_pattern`: This pattern is usually a text literal and can be of any of the data types `CHAR`, `VARCHAR2`, `NCHAR`, or `NVARCHAR2`. The pattern can contain up to 512 bytes. For further information about writing the regular expression for the `regexp_pattern` parameter, see the description of the `pattern` argument of the `REGEXP_REPLACE` SQL function in [Oracle Database SQL Language Reference](../sqlrf/Oracle-Regular-Expression-Support.md), because the support that Data Redaction provides for regular expression matching is similar to that of the `REGEXP_REPLACE` SQL function.

- `regexp_replace_string`: This data can be of any of the data types `CHAR`, `VARCHAR2`, `NCHAR`, or `NVARCHAR2`. The `regexp_replace_string` can contain up to 500 back references to subexpressions in the form `\``n`, where `n` is a number from 1 to 9. If you want to include a backslash (\\ in the `regexp_replace_string` setting, then you must precede it with the escape character, which is also a backslash. For example, to literally replace the matched pattern with `\2` (rather than replace it with the second matched subexpression of the matched pattern), you enter `\\2` in the `regexp_replace_string` setting. For more information, see [Oracle Database SQL Language Reference](../sqlrf/Multilingual-Regular-Expression-Syntax.md).

**See Also:**

General Syntax of the DBMS_REDACT.ADD_POLICY Procedure for information about other `DBMS_REDACT.ADD_POLICY` parameters

**Parent topic:** Custom Regular Expression Redaction Policies

##### 14.10.4.2 Example: Custom Regular Expression Redaction Policy

The `DBMS_REDACT.ADD_POLICY` procedure regexp\* parameters can create a custom regular expression redaction policy.

Example 14-9 shows how to use regular expressions to redact the `emp_id` column data. In this example, taken together, the `regexp_pattern` and `regexp_replace_string` parameters do the following: first, find the pattern of 9 digits. For reference, break them into three groups that contain the first 3, the next 2, and then the last 4 digits. Then, replace all 9 digits with `XXXXX` concatenated with the third group (the last 4 digits) as found in the original pattern.

Query and redacted result:

    SELECT emp_id FROM mavis.cust_info;

    EMP_ID
    ------------
    XXXXX1234
    XXXXX5678

Example 14-9 Partially Redacted Data Redaction Using Regular Expressions

    BEGIN
     DBMS_REDACT.ADD_POLICY(
       object_schema          => 'mavis',
       object_name            => 'cust_info',
       column_name            => 'emp_id',
       policy_name            => 'redact_cust_ids',
       function_type          => DBMS_REDACT.REGEXP,
       expression             => '1=1',
       regexp_pattern         => '(\d\d\d)(\d\d)(\d\d\d\d)',
       regexp_replace_string  => 'XXXXX\3',
       regexp_position        => 1,
       regexp_occurrence      => 0,
       regexp_match_parameter => 'i',
       policy_description     => 'Redacts customer IDs using regular expression',
       column_description     => 'emp_id contains employee ID numbers');
    END;
    /

**Parent topic:** Custom Regular Expression Redaction Policies

### 14.11 Creating a Random Redaction Policy

A random redaction policy presents redacted data as randomly generated values, such as `Ukjsl32[[]]]s`.

- Syntax for Creating a Random Redaction Policy
  A random redaction policy presents the redacted data to the querying application user as randomly generated values, based on the column data type.
- Example: Random Redaction Policy
  You can use the DBMS_REDACT.ADD_POLICY PL/SQL procedure create a random redaction policy.

**Parent topic:** Configuring Oracle Data Redaction Policies

#### 14.11.1 Syntax for Creating a Random Redaction Policy

A random redaction policy presents the redacted data to the querying application user as randomly generated values, based on the column data type.

Be aware that LOB columns are not supported.

The `DBMS_REDACT.ADD_POLICY` fields for creating a random redaction policy are as follows:

    DBMS_REDACT.ADD_POLICY (
       object_schema           IN VARCHAR2 := NULL,
       object_name             IN VARCHAR2,
       column_name             IN VARCHAR2 := NULL,
       policy_name             IN VARCHAR2,
       function_type           IN BINARY_INTEGER := NULL,
       expression              IN VARCHAR2,
       enable                  IN BOOLEAN := TRUE);

In this specification:

- `object_schema`, `object_name`, `column_name`, `policy_name`, `expression`, `enable`: See General Syntax of the DBMS_REDACT.ADD_POLICY Procedure.

- `function_type`: Specifies the function used to set the type of redaction. Enter `DBMS_REDACT.RANDOM`.

  If you omit the `function_type` parameter, then the default redaction `function_type` setting is `DBMS_REDACT.FULL`.

  Remember that the data type of the column determines which `function_type` settings that you are permitted to use. See [Comparison of Full, Partial, and Random Redaction Based on Data Types](oracle-data-redaction-features-and-capabilities.md).

**Parent topic:** Creating a Random Redaction Policy

#### 14.11.2 Example: Random Redaction Policy

You can use the DBMS_REDACT.ADD_POLICY PL/SQL procedure create a random redaction policy.

Example 14-10 shows how to generate random values. Each time you run the `SELECT` statement, the output will be different.

Example 14-10 Randomly Redacted Data Redaction Values

    BEGIN
     DBMS_REDACT.ADD_POLICY(
       object_schema   => 'mavis',
       object_name     => 'cust_info',
       column_name     => 'login_username',
       policy_name     => 'redact_cust_rand_username',
       function_type   => DBMS_REDACT.RANDOM,
       expression      => 'SYS_CONTEXT(''USERENV'',''SESSION_USER'') = ''APP_USER''');
    END;
    /

Query and redacted result:

    SELECT login_username FROM mavis.cust_info;

    LOGIN_USERNAME
    --------------
    N[CG{\pTVcK

**Parent topic:** Creating a Random Redaction Policy

### 14.12 Creating a Policy That Uses No Redaction

You can create policies that use no redaction at all, for when you want to test the policy in a development environment.

- Syntax for Creating a Policy with No Redaction
  The None redaction type option can be used to test the internal operation of redaction policies.
- Example: Performing No Redaction
  The `DBMS_REDACT.ADD_POLICY` procedure can create a policy that performs no redaction.

**Parent topic:** Configuring Oracle Data Redaction Policies

#### 14.12.1 Syntax for Creating a Policy with No Redaction

The None redaction type option can be used to test the internal operation of redaction policies.

The None redaction type has no effect on the query results against tables that have policies defined on them. You can use this option to test the redaction policy definitions before applying them to a production environment. Be aware that LOB columns are not supported.

The `DBMS_REDACT.ADD_POLICY` fields for creating a policy with no redaction are as follows:

    DBMS_REDACT.ADD_POLICY (
       object_schema           IN VARCHAR2 := NULL,
       object_name             IN VARCHAR2,
       column_name             IN VARCHAR2 := NULL,
       policy_name             IN VARCHAR2,
       function_type           IN BINARY_INTEGER := NULL,
       expression              IN VARCHAR2,
       enable                  IN BOOLEAN := TRUE);

In this specification:

- `object_schema`, `object_name`, `column_name`, `policy_name`, `expression`, `enable`: See General Syntax of the DBMS_REDACT.ADD_POLICY Procedure.

- `function_type`: Specifies the functions used to set the type of data redaction. Enter `DBMS_REDACT.NONE`.

  If you omit the `function_type` parameter, then the default redaction `function_type` setting is `DBMS_REDACT.FULL`.

**Parent topic:** Creating a Policy That Uses No Redaction

#### 14.12.2 Example: Performing No Redaction

The `DBMS_REDACT.ADD_POLICY` procedure can create a policy that performs no redaction.

Example 14-11 shows how to create a Data Redaction policy that does not redact any of the displayed values.

Example 14-11 No Redacted Data Redaction Values

    BEGIN
     DBMS_REDACT.ADD_POLICY(
       object_schema    => 'mavis',
       object_name      => 'cust_info',
       column_name      => 'user_name',
       policy_name      => 'redact_cust_no_vals',
       function_type    => DBMS_REDACT.NONE,
       expression       => '1=1');
    END;
    /

Query and redacted result:

    SELECT user_name FROM mavis.cust_info;

    USER_NAME
    ----------
    IDA NEAU

**Parent topic:** Creating a Policy That Uses No Redaction

### 14.13 Exemption of Users from Oracle Data Redaction Policies

You can exempt users from having Oracle Data Redaction policies applied to the data they access.

To do so, you should grant the users the `EXEMPT REDACTION POLICY` system privilege. Grant this privilege to trusted users only.

In addition to users who were granted this privilege, user `SYS` is also exempt from all Data Redaction policies. The person who creates the Data Redaction policy is by default not exempt from it, unless this person is user `SYS` or has the `EXEMPT REDACTION POLICY` system privilege.

Note the following:

- Users who have the `INSERT` privilege on a table can insert values into a redacted column, regardless of whether a Data Redaction policy exists on the table. Data Redaction only affects SQL `SELECT` statements (that is, queries) issued by a user, and has no effect on any other SQL issued by a user, including `INSERT`, `UPDATE`, or `DELETE` statements. (See the next bullet for exceptions to this rule.)

- Users cannot perform a `CREATE TABLE AS SELECT` where any of the columns being selected (source columns) is protected by a Data Redaction policy (and similarly, any DML operation where the source is a redacted column), unless the user was granted the `EXEMPT REDACTION POLICY` system privilege.

- The `EXEMPT REDACTION POLICY` system privilege is included in the `DBA` role, but this privilege must be granted explicitly to users because it is not included in the `WITH ADMIN OPTION` for `DBA` role grants. Users who were granted the `DBA` role are exempt from redaction policies because the `DBA` role contains the `EXP_FULL_DATABASE` role, which is granted the `EXEMPT REDACTION POLICY` system privilege.

**Related Topics**

- [Restriction of Administrative Access to Oracle Data Redaction Policies](security-considerations-for-using-oracle-data-redaction.md)
- [Oracle Data Pump Security Model for Oracle Data Redaction](oracle-data-redaction-use-with-oracle-database-features.md)

**Parent topic:** Configuring Oracle Data Redaction Policies

### 14.14 Altering an Oracle Data Redaction Policy

The `DBMS_REDACT.ALTER_POLICY` procedure enables you to modify Oracle Data Redaction policies.

- About Altering Oracle Data Redaction Policies
  The `DBMS_REDACT.ALTER_POLICY` procedure alters a Data Redaction policy.
- Syntax for the DBMS_REDACT.ALTER_POLICY Procedure
  The `DBMS_REDACT.ALTER_POLICY` procedure syntax can be used to alter all types of the Data Redaction policies.
- Parameters Required for DBMS_REDACT.ALTER_POLICY Actions
  The DBMS_REDACT.ALTER_POLICY procedure provides parameters than can perform various actions, such as adding or modifying a column.
- Tutorial: Altering an Oracle Data Redaction Policy
  You can redact multiple columns in a table or view, with each column having its own redaction setting.

**Parent topic:** Configuring Oracle Data Redaction Policies

#### 14.14.1 About Altering Oracle Data Redaction Policies

The `DBMS_REDACT.ALTER_POLICY` procedure alters a Data Redaction policy.

If the policy is already enabled, then you do not need to disable it first, and after you alter the policy, it remains enabled.

You can find the names of existing Data Redaction policies by querying the `POLICY_NAME` column of the `REDACTION_POLICIES` data dictionary view, and information about the columns, functions, and parameters specified in a policy by querying the `REDACTION_COLUMNS` view. To find the current value for policies that use full data redaction, you can query the `REDACTION_VALUES_FOR_TYPE_FULL` data dictionary view.

The `action` parameter specifies the type of modification that you want to perform. At a minimum, you must include the `object_name` and `policy_name` parameters when you run this procedure.

**Related Topics**

- [REDACTION_COLUMNS Data Dictionary View Behavior When a View Is Invalid](security-considerations-for-using-oracle-data-redaction.md)

**Parent topic:** Altering an Oracle Data Redaction Policy

#### 14.14.2 Syntax for the DBMS_REDACT.ALTER_POLICY Procedure

The `DBMS_REDACT.ALTER_POLICY` procedure syntax can be used to alter all types of the Data Redaction policies.

The syntax for the `DBMS_REDACT.ALTER_POLICY` procedure is as follows:

    DBMS_REDACT.ALTER_POLICY (
       object_schema          IN VARCHAR2 := NULL,
       object_name            IN VARCHAR2 := NULL,
       policy_name            IN VARCHAR2,
       action                 IN BINARY_INTEGER := DBMS_REDACT.ADD_COLUMN,
       column_name            IN VARCHAR2 := NULL,
       function_type          IN BINARY_INTEGER := DBMS_REDACT.FULL,
       function_parameters    IN VARCHAR2 := NULL,
       expression             IN VARCHAR2 := NULL,
       regexp_pattern         IN VARCHAR2 := NULL,
       regexp_replace_string  IN VARCHAR2 := NULL,
       regexp_position        IN BINARY_INTEGER := NULL,
       regexp_occurrence      IN BINARY_INTEGER := NULL,
       regexp_match_parameter IN VARCHAR2 := NULL,
       policy_description     IN VARCHAR2 := NULL,
       column_description     IN VARCHAR2 := NULL);

In this specification:

- `action`: Enter one of the following values to define the kind of action to use:

  - `DBMS_REDACT.MODIFY_COLUMN` if you plan to change the `column_name` value.

  - `DBMS_REDACT.ADD_COLUMN` if you plan to add a new column (in addition to columns that are already protected by the policy) for redaction. This setting is the default for the `action` parameter.

  - `DBMS_REDACT.DROP_COLUMN` if you want to remove redaction from a column.

  - `DBMS_REDACT.MODIFY_EXPRESSION` if you plan to change the `expression` value. Each policy can have only one policy expression. In other words, when you modify the policy expression, you are replacing the existing policy expression with a new policy expression.

  - `DBMS_REDACT.SET_POLICY_DESCRIPTION` if you want to change the description of the policy.

  - `DBMS_REDACT.SET_COLUMN_DESCRIPTION` if you want to change the description of the column.

**See Also:**

- Parameters Required for DBMS_REDACT.ALTER_POLICY Actions

- General Syntax of the DBMS_REDACT.ADD_POLICY Procedure for information about the remaining parameters

**Parent topic:** Altering an Oracle Data Redaction Policy

#### 14.14.3 Parameters Required for DBMS_REDACT.ALTER_POLICY Actions

The DBMS_REDACT.ALTER_POLICY procedure provides parameters than can perform various actions, such as adding or modifying a column.

Table 14-11 shows the combinations of these parameters.

Table 14-11 Parameters Required for Various DBMS_REDACT.ALTER_POLICY Actions

| Desired Alteration                   | Parameters to Set                                                                                                                                         |
|:-------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Add or modify a column               | • `action` (`DBMS_REDACT.MODIFY_COLUMN`)<br>• `column_name`<br>• `function_type`<br>• `function_parameters` (if necessary)<br>• `regexp`\* (if necessary) |
| Change the policy expression         | • `action` (`DBMS_REDACT.MODIFY_EXPRESSION`)<br>• `expression`                                                                                            |
| Change the description of the policy | • `action` (`DBMS_REDACT.SET_POLICY_DESCRIPTION`)<br>• `policy_description`                                                                               |
| Change the description of the column | • `action` (`DBMS_REDACT.SET_COLUMN_DESCRIPTION`)<br>• `column_description`                                                                               |
| Drop a column                        | • `action` (`DBMS_REDACT.DROP_COLUMN`)<br>• `column_name`                                                                                                 |

**Parent topic:** Altering an Oracle Data Redaction Policy

#### 14.14.4 Tutorial: Altering an Oracle Data Redaction Policy

You can redact multiple columns in a table or view, with each column having its own redaction setting.

The exercise in this section shows how to modify a Data Redaction policy so that multiple columns are redacted. It also shows how to change the `expression` setting for the policy. To accomplish this, you must run the `DBMS_REDACT.ALTER_POLICY` procedure in stages.

1.  Connect to the PDB as a user who has privileges to create users and grant them privileges.

2.  Create the following users:

        GRANT CREATE SESSION TO dr_admin IDENTIFIED BY password;
        GRANT CREATE SESSION TO sales_rep IDENTIFIED BY password;
        GRANT CREATE SESSION TO support_rep IDENTIFIED BY password;

3.  Grant `EXECUTE` on the `DBMS_REDACT` PL/SQL package to user `dr_admin`:

        GRANT EXECUTE ON DBMS_REDACT TO dr_admin;

4.  Connect as user `OE`.

5.  Create and populate a table that contains customer credit card information.

        CREATE TABLE cust_order_info(
         first_name varchar2(20),
         last_name varchar2(20),
         address varchar2(30),
         city varchar2(30),
         state varchar2(3),
         zip varchar2(5),
         cc_num varchar(19),
         cc_exp varchar2(7));

        INSERT INTO cust_order_info VALUES ('Jane','Dough','39 Mockingbird Lane', 'San Francisco', 'CA', 94114, '5105 1051 0510 5100', '10/2018');
        INSERT INTO cust_order_info VALUES ('Mary','Hightower','2319 Maple Street', 'Sonoma', 'CA', 95476, '5111 1111 1111 1118', '03/2019');
        INSERT INTO cust_order_info VALUES ('Herbert','Donahue','292 Winsome Way', 'San Francisco', 'CA', 94117, '5454 5454 5454 5454', '08/2018');

6.  Grant the `SELECT` privilege on the `cust_order_info` table to the `sales_rep` and `support_rep` users.
        GRANT SELECT ON cust_order_info TO sales_rep, support_rep;

7.  Connect as user `dr_admin`.

8.  Create and enable policy to redact the credit card number.

        BEGIN DBMS_REDACT.ADD_POLICY(
            object_schema              => 'oe',
            object_name                => 'cust_order_info',
            column_name                => 'cc_num',
            policy_name                => 'redact_cust_cc_info',
            function_type              => DBMS_REDACT.REGEXP,
            function_parameters        => NULL,
            expression                 => '1=1',
            regexp_pattern             => DBMS_REDACT.RE_PATTERN_CCN,
            regexp_replace_string      => DBMS_REDACT.RE_REDACT_CCN,
            regexp_position            => NULL,
            regexp_occurrence          => NULL,
            regexp_match_parameter     => NULL,
            policy_description         => 'Partially redacts credit card info',
            column_description         => 'cc_num_number lists credit card numbers');
        END;
        /

9.  Modify the policy to include redaction of the expiration date.
        BEGIN DBMS_REDACT.ALTER_POLICY(
            object_schema     => 'oe',
            object_name       => 'cust_order_info',
            policy_name       => 'redact_cust_cc_info',
            action            => DBMS_REDACT.ADD_COLUMN,
            column_name       => 'cc_exp',
            function_type     => DBMS_REDACT.RANDOM);
        END;
        /

10. Modify the policy again, to use a condition so that the `sales_rep` user views the redacted values and the `support_rep` user views the [actual data](glossary.md).

        BEGIN
           DBMS_REDACT.ALTER_POLICY(
           object_schema     => 'oe',
           object_name       => 'cust_order_info',
           policy_name       => 'redact_cust_cc_info',
           action            => DBMS_REDACT.MODIFY_EXPRESSION,
           expression        => 'SYS_CONTEXT(''USERENV'',''SESSION_USER'') = ''SALES_REP''');
        END;
        /

11. To test the policy, have the two users query the `cust_order_info` table.

    First, connect as `support_rep` and query the table.

        SELECT cc_num, cc_exp FROM OE.cust_order_info;

        CC_NUM               CC_EXP
        -------------------  -------
        5105 1051 0510 5100  10/2018
        5111 1111 1111 1118  03/2019
        5454 5454 5454 5454  08/2018

    User `support_rep` can view the actual data. Next, connect as `sales_rep` and query the table.

        SELECT cc_num, cc_exp FROM OE.cust_order_info;

        CC_NUM             CC_EXP
        ----------------   -------
        ************5100   lST=033
        ************1119   OZA.w4C
        ************5454   B(9+;O1

    The actual data is redacted using for user `sales_rep`.

12. As user `dr_admin`, alter the `cust_order_info` to include a condition so that only `support_rep` can see the redacted data but `sales_rep` cannot.

        BEGIN
           DBMS_REDACT.ALTER_POLICY(
           object_schema      => 'oe',
           object_name        => 'cust_order_info',
           policy_name        => 'redact_cust_cc_info',
           action             => DBMS_REDACT.MODIFY_EXPRESSION,
           expression         => 'SYS_CONTEXT(''USERENV'',''SESSION_USER'') = ''SUPPORT_REP''');
        END;
        /

13. Have the users test the policy again.

    First, `support_rep` tests the policy:

        SELECT cc_num, cc_exp FROM OE.cust_order_info;

        CC_NUM             CC_EXP
        ----------------   -------
        ************5100   1^XMF~`
        ************1119   qz+9=#S
        ************5454   *KCaUkm

    User `support_rep` can no longer view the actual data; it is now redacted.

    Next, connect as `sales_rep` and query the table.

        SELECT cc_num, cc_exp FROM OE.cust_order_info;

        CC_NUM               CC_EXP
        -------------------  -------
        5105 1051 0510 5100  10/2018
        5111 1111 1111 1118  03/2019
        5454 5454 5454 5454  08/2018

    User `sales_rep` now can view the actual data.

14. If you do not need the components of this tutorial, then you can remove them.

    Connect as `dr_admin` and then drop the policy.

        BEGIN
          DBMS_REDACT.DROP_POLICY (
            object_schema  => 'oe',
            object_name    => 'cust_order_info',
            policy_name    => 'redact_cust_cc_info');
        END;
        /

    Connect as a security administrator and drop the users.

        DROP USER dr_admin;
        DROP USER sales_rep;
        DROP USER support_rep;

    Connect as user `OE` and drop the `cust_order_info` table.

        DROP TABLE cust_order_info;

**Parent topic:** Altering an Oracle Data Redaction Policy

### 14.15 Redacting Multiple Columns

You can redact more than one column in a Data Redaction policy.

- Adding Columns to a Data Redaction Policy for a Single Table or View
  You can redact columns of different data types, using different redaction types, for one table or view.
- Example: Redacting Multiple Columns
  The `DBMS_REDACT.ALTER_POLICY` procedure can redact multiple columns.

**Parent topic:** Configuring Oracle Data Redaction Policies

#### 14.15.1 Adding Columns to a Data Redaction Policy for a Single Table or View

You can redact columns of different data types, using different redaction types, for one table or view.

1.  Create the policy for the first column that you want to redact.

2.  Use the `DBMS_REDACT.ALTER_POLICY` procedure to add the next column to the policy.

    As necessary, set the `action`, `column_name`, `function_type`, and `function_parameters` (or the parameters that begin with `regexp_`) parameters to define the redaction for the new column, but do not change the `object_schema`, `object_name`, `policy_name`, or `expression` parameters. Each redacted column continues to have the same redaction parameters that were used to create it.

**Parent topic:** Redacting Multiple Columns

#### 14.15.2 Example: Redacting Multiple Columns

The `DBMS_REDACT.ALTER_POLICY` procedure can redact multiple columns.

Example 14-12 shows how to add a column to an existing Data Redaction policy. In this example, the `action` parameter specifies that a new column must be added, using `DBMS_REDACT.ADD_COLUMN`. The name of the new column, `card_num`, is set by the `column_name` parameter.

Example 14-12 Adding a Column to a Data Redaction Policy

    BEGIN
     DBMS_REDACT.ALTER_POLICY(
      object_schema       => 'mavis',
      object_name         => 'cust_info',
      policy_name         => 'redact_cust_user_ids',
      action              => DBMS_REDACT.ADD_COLUMN,
      column_name         => 'card_num',
      function_type       => DBMS_REDACT.FULL,
      function_parameters => '',
      expression          => 'SYS_CONTEXT(''SYS_SESSION_ROLES'',''ADM'') = ''TRUE''');
    END;
    /

**Parent topic:** Redacting Multiple Columns

### 14.16 Disabling and Enabling an Oracle Data Redaction Policy

You can disable and then reenable Oracle Data Redactions policies as necessary.

- Disabling an Oracle Data Redaction Policy
  The `DBMS_REDACT.DISABLE_POLICY` procedure disables Oracle Data Redaction policies.
- Enabling an Oracle Data Redaction Policy
  The `DBMS_REDACT.ENABLE_POLICY` procedure enables Oracle Data Redaction policies.

**Parent topic:** Configuring Oracle Data Redaction Policies

#### 14.16.1 Disabling an Oracle Data Redaction Policy

The `DBMS_REDACT.DISABLE_POLICY` procedure disables Oracle Data Redaction policies.

You can find the names of existing Data Redaction policies and whether they are enabled by querying the `POLICY_NAME` and `ENABLE` columns of the `REDACTION_POLICIES` view. However, as long as the policy still exists, you cannot create another policy for that table or view, even if the original policy is disabled. In other words, if you want to create a different policy on the same table column, then you must drop the first policy before you can create and use the new policy.

- To disable a Data Redaction policy, run the `DBMS_REDACT.DISABLE_POLICY` procedure, using the following syntax:

      DBMS_REDACT.DISABLE_POLICY (
      object_schema       IN VARCHAR2 DEFAULT NULL,
         object_name         IN VARCHAR2,
         policy_name         IN VARCHAR2);

  In this specification:

  - `object_schema`: Specifies the schema of the object on which the Data Redaction policy will be applied. If you omit this setting (or enter `NULL`), then Oracle Database uses the name of the current schema.

  - `object_name`: Specifies the name of the table or view to be used for the Data Redaction policy.

  - `policy_name`: Specifies the name of the policy to be disabled.

Example 14-13 shows how to disable a Data Redaction policy.

Example 14-13 Disabling a Data Redaction Policy

    BEGIN
      DBMS_REDACT.DISABLE_POLICY (
        object_schema  => 'mavis',
        object_name    => 'cust_info',
        policy_name    => 'redact_cust_user_ids');
    END;
    /

**Parent topic:** Disabling and Enabling an Oracle Data Redaction Policy

#### 14.16.2 Enabling an Oracle Data Redaction Policy

The `DBMS_REDACT.ENABLE_POLICY` procedure enables Oracle Data Redaction policies.

Immediately after you create a new policy, you do not need to enable it; the creation process handles that for you. To find the names of existing Data Redaction policies and whether they are enabled, you can query the `POLICY_NAME` and `ENABLE` columns of the `REDACTION_POLICIES` view. After you run the procedure to enable the policy, the enablement takes effect immediately.

- To enable a Data Redaction policy, run the `DBMS_REDACT.ENABLE_POLICY` procedure, using the following syntax.

      DBMS_REDACT.ENABLE_POLICY (
      object_schema       IN VARCHAR2 DEFAULT NULL,
         object_name         IN VARCHAR2,
         policy_name         IN VARCHAR2);

  In this specification:

  - `object_schema`: Specifies the schema of the object on which the Data Redaction policy will be applied. If you omit this setting (or enter `NULL`), then Oracle Database uses the name of the current schema.

  - `object_name`: Specifies the name of the table or view to be used for the Data Redaction policy.

  - `policy_name`: Specifies the name of the policy to be enabled.

Example 14-14 shows how to enable a Data Redaction policy.

Example 14-14 Enabling a Data Redaction Policy

    BEGIN
      DBMS_REDACT.ENABLE_POLICY (
        object_schema  => 'mavis',
        object_name    => 'cust_info',
        policy_name    => 'redact_cust_user_ids');
    END;
    /

**Parent topic:** Disabling and Enabling an Oracle Data Redaction Policy

### 14.17 Dropping an Oracle Data Redaction Policy

The `DBMS_REDACT.DROP_POLICY` procedure drops Oracle Data Redaction policies.

You can drop an Oracle Data Redaction policy whether it is enabled or disabled. You can find the names of existing Data Redaction policies, by querying the `POLICY_NAME` column of the `REDACTION_POLICIES` view. When you drop a table or view that is associated with an Oracle Data Redaction policy, the policy is automatically dropped. As a best practice, drop the policy first, and then drop the table or view afterward. See [Dropped Oracle Data Redaction Policies When the Recycle Bin Is Enabled](security-considerations-for-using-oracle-data-redaction.md) for more information.

- To drop a Data Redaction policy, run the `DBMS_REDACT.DROP_POLICY` procedure.

  Use the following syntax:

      DBMS_REDACT.DROP_POLICY (
         object_schema       IN VARCHAR2 DEFAULT NULL,
         object_name         IN VARCHAR2,
         policy_name         IN VARCHAR2);

  In this specification:

  - `object_schema`: Specifies the schema of the object to which the Data Redaction policy applies. If you omit this setting (or enter `NULL`), then Oracle Database uses the name of the current schema.

  - `object_name`: Specifies the name of the table or view to be used for the Data Redaction policy.

  - `policy_name`: Specifies the name of the policy to be dropped.

After you run the `DBMS_REDACT.DROP_POLICY` procedure, the drop takes effect immediately.

Example 14-15 shows how to drop a Data Redaction policy.

Example 14-15 Dropping a Data Redaction Policy

    BEGIN
      DBMS_REDACT.DROP_POLICY (
        object_schema  => 'mavis',
        object_name    => 'cust_info',
        policy_name    => 'redact_cust_user_ids');
    END;
    /

**Parent topic:** Configuring Oracle Data Redaction Policies

### 14.18 Tutorial: SQL Expressions to Build Reports with Redacted Values

SQL expressions can be used to build reports based on columns that have Oracle Data Redaction policies defined on them.

The values used in the SQL expression will be redacted. This redaction occurs in such a way that the redaction takes place before the SQL expression is evaluated: the result value that is displayed in the report is the end result of the evaluated SQL expression over the redacted values, rather than the redacted result of the SQL expression as a whole.

1.  Create the following Data Redaction policy for the `HR.EMPLOYEES` table.

    This policy will replace the first 4 digits of the value from the `SALARY` column with the number `9` and the first digit of the value from the `COMMISSION_PCT` column with a `9`.

        BEGIN
         DBMS_REDACT.ADD_POLICY(
           object_schema          => 'HR',
           object_name            => 'EMPLOYEES',
           column_name            => 'SALARY',
           column_description     => 'emp_sal_comm shows employee salary and commission',
           policy_name            => 'redact_emp_sal_comm',
           policy_description     => 'Partially redacts the emp_sal_comm column',
           function_type          => DBMS_REDACT.PARTIAL,
           function_parameters    => '9,1,4',
           expression             => '1=1');
        END;
        /
        BEGIN
         DBMS_REDACT.ALTER_POLICY(
           object_schema          => 'HR',
           object_name            => 'EMPLOYEES',
           policy_name            => 'redact_emp_sal_comm',
           action                 => DBMS_REDACT.ADD_COLUMN,
           column_name            => 'COMMISSION_PCT',
           function_type          => DBMS_REDACT.PARTIAL,
           function_parameters    => '9,1,1',
           expression             => '1=1');
        END;
        /

2.  Log in to the `HR` schema and then run the following report.

    This report will use the SQL expression `(SALARY + COMMISSION_PCT)` to combine the employees' salaries and commissions.

        SELECT (SALARY + COMMISSION_PCT) total_emp_compensation
        FROM HR.EMPLOYEES
        WHERE DEPARTMENT_ID = 80;

        TOTAL_EMP_COMPENSATION
        ----------------------
                        9999.9
                       9999.95
                      99990.95
        ...

3.  Use SQL expressions for the report, including concatenation.

    For example:

        SELECT 'Employee ID '          || EMPLOYEE_ID ||
               ' has a salary of '     || SALARY ||
               ' and a commission of ' || COMMISSION_PCT || '.' detailed_emp_compensation
        FROM HR.EMPLOYEES
        WHERE DEPARTMENT_ID = 80
        ORDER BY EMPLOYEE_ID;

        DETAILED_EMP_COMPENSATION
        -------------------------------------------------------------
        Employee ID 150 has a salary of 99990 and a commission of .9.
        Employee ID 151 has a salary of 9999 and a commission of .95.
        Employee ID 152 has a salary of 9999 and a commission of .95.
        ...

4.  Connect the user who created the `redact_emp_sal_comm` Data Redaction policy and then run the following statement to drop the policy.

        BEGIN
          DBMS_REDACT.DROP_POLICY (
            object_schema => 'HR',
            object_name   => 'EMPLOYEES',
            policy_name   => 'redact_emp_sal_comm');
        END;
        /

**Parent topic:** Configuring Oracle Data Redaction Policies

### 14.19 Using Trace Files to Troubleshoot Oracle Data Redaction Policies

Trace files for Oracle Data Redaction can be generated for either the system level or the session level.

You must set the tracing to `high`. The is no `low` tracing level for Oracle Data Redaction.

1.  Connect to the PDB as a user who has the `ALTER SYSTEM` or `ALTER SESSION` privilege.
2.  Enable tracing.
    - At the system level, for all sessions:

          ALTER SYSTEM SET events 'TRACE[RADM] disk=high';

    - At the session level, for the current session:

          ALTER SESSION SET events 'TRACE[RADM] disk=high';

    To find problems with queries involving redacted columns, include `/* KZDMPRQB_DUMP */` in the query. For example:

        SELECT /* KZDMPRQB_DUMP */ redacted_column FROM table_with_redaction_policy;

    Search for `KCCF2MASK` and `KCCF2MASKDEP` in the dump. The subsequent part of the dump files gives Oracle Redaction-specific insights.
3.  To disable tracing:
    - At the system level, for all sessions:

          ALTER SYSTEM SET EVENTS 'TRACE[RADM] OFF';

    - At the session level, for the current session:

          ALTER SESSION SET EVENTS 'TRACE[RADM] OFF';

**Parent topic:** Configuring Oracle Data Redaction Policies

### 14.20 Oracle Data Redaction Policy Data Dictionary Views

Oracle Database provides data dictionary views that list information about Data Redaction policies.

Before you can query these views, you must be granted the `SELECT_CATALOG_ROLE` role.

Table 14-12 lists the Data Redaction data dictionary views.

Table 14-12 Data Redaction Views

| View                             | Description                                                                                                                                                                                                                                                                                                                                                                                                        |
|:---------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `REDACTION_COLUMNS`              | Describes all of the redacted columns in the database, providing the the owner of the table or view within which the column resides, the object name, the column name, the type of redaction function, the parameters to the redaction function (if any), and a description of the redaction policy. If a policy expression has been created, displays the default object-wide policy expression’s SQL expression. |
| `REDACTION_EXPRESSIONS`          | Displays the names of existing policy expressions and their SQL expressions                                                                                                                                                                                                                                                                                                                                        |
| `REDACTION_POLICIES`             | Describes all of the data redaction policies in the database. It includes information about the object owner, object name, policy name, policy expression, whether the policy is enabled, and a description of the Data Redaction policy.                                                                                                                                                                          |
| `REDACTION_VALUES_FOR_TYPE_FULL` | Shows the current redaction values for Data Redaction policies that use full redaction                                                                                                                                                                                                                                                                                                                             |

**Parent topic:** Configuring Oracle Data Redaction Policies
