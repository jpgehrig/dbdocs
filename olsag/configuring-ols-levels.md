This tutorial demonstrates how to create Oracle Label Security levels.

- About This Tutorial
  In this tutorial, you will use the `HR` schema to learn how to use Oracle Label Security levels.
- Step 1: Create a Role and User Accounts
  The role that you create will enable any user who is granted it to have the `SELECT` privilege on the `HR.EMPLOYEES` table. The user accounts are for the two Human Resources employees, Susan Mavris and Ida Neau.
- Step 2: Create the Oracle Label Security Policy Container
  As an Oracle Label Security administrator, you must create and then enable the policy container.
- Step 3: Create the Two Level Components for the Oracle Label Security Policy
  After you create the Oracle Label Security policy container, you are ready to create two levels to represent two different levels of sensitivity.
- Step 4: Create the Data Labels for the Levels
  A data label tags data records for use with the Oracle Label Security policy.
- Step 5: Set User Authorizations for the Oracle Label Security Policy
  Setting user authorizations entails associating the user with the policy and the minimum and maximum levels that are associated with the Oracle Label Security policy.
- Step 6: Apply the Oracle Label Security Policy to the HR Schema
  After you apply the policy to the `HR` schema, you must enable the policy association with `HR`.
- Step 7: Add the Policy Labels to the HR.EMPLOYEES Table Data
  Both the Oracle Label Security administrator and the `HR` user will add the policy labels to the `HR.EMPLOYEES` table data in the `EMPLOYEE_ID` column.
- Step 8: Test the Oracle Label Security Policy
  To test the policy, each user will try to query the `HR.EMPLOYEES` table.
- Step 9: Optionally, Remove the Oracle Label Security Policy Components
  You can remove the Oracle Label Security policy, `HR_ROLE` role, and users Ida Neau and Susan Mavris.

**Parent topic:** [Oracle Label Security Tutorials](oracle-label-security-tutorials.md)

### 8.1 About This Tutorial

In this tutorial, you will use the `HR` schema to learn how to use Oracle Label Security levels.

The Human Resources representative, Susan Mavris, has an assistant working for her, Ida Neau. Susan Mavris must have access to all employee records, including records of employees who have left the company. Ida Neau must have access only to employees who are current.

You will create an Oracle Label Security policy that will use the following levels of sensitivity to govern access to current and former employees:

- `SENSITIVE` enables access to current employees only. User Ida Neau will be assigned this level.
- `HIGHLY_SENSITIVE` enables access to former employees. User Susan Mavris will be assigned this level. This level is a higher level than `SENSITIVE`, which means that it will also provide access to rows protected by `SENSITIVE`. In other words, Susan Mavris will have access to both former and current employee records.

**Parent topic:** Tutorial: Configuring Levels in Oracle Label Security

### 8.2 Step 1: Create a Role and User Accounts

The role that you create will enable any user who is granted it to have the `SELECT` privilege on the `HR.EMPLOYEES` table. The user accounts are for the two Human Resources employees, Susan Mavris and Ida Neau.

1.  Log in to SQL\*Plus as a user who has privileges to create roles, grant privileges, and create user accounts.
    For example:
        sqlplus sec_admin
        Enter password: password
2.  Create the role as follows:
        CREATE ROLE HR_ROLE;
3.  Grant the `SELECT` privilege on `HR.EMPLOYEES` to `HR_ROLE`.
        GRANT SELECT ON HR.EMPLOYEES TO HR_ROLE;
4.  Create the user accounts for Susan Mavris and Ida Neau, and grant them the `HR_ROLE` role.
        GRANT CONNECT, HR_ROLE TO SMAVRIS IDENTIFIED BY password;
        GRANT CONNECT, HR_ROLE TO INEAU IDENTIFIED BY password;

**Parent topic:** Tutorial: Configuring Levels in Oracle Label Security

### 8.3 Step 2: Create the Oracle Label Security Policy Container

As an Oracle Label Security administrator, you must create and then enable the policy container.

1.  Connect as a user who can create and manage Oracle Label Security policies.
    For example:
        sqlplus psmith_ols
        Enter password: password
2.  Create the policy.
        BEGIN
         SA_SYSDBA.CREATE_POLICY (
          policy_name      => 'HR_OLS_POL',
          column_name      => 'OLS_COL');
        END;
        /

    In this specification, the `default_options` parameter is omitted because you can add it later on in another procedure.
3.  Enable the policy.
        EXEC SA_SYSDBA.ENABLE_POLICY ('HR_OLS_POL');

**Parent topic:** Tutorial: Configuring Levels in Oracle Label Security

### 8.4 Step 3: Create the Two Level Components for the Oracle Label Security Policy

After you create the Oracle Label Security policy container, you are ready to create two levels to represent two different levels of sensitivity.

1.  If necessary, connect as a user who can create and manage Oracle Label Security policies.
    For example:
        sqlplus psmith_ols
        Enter password: password
2.  Create the levels as follows:
        BEGIN
           SA_COMPONENTS.CREATE_LEVEL (
              policy_name => 'HR_OLS_POL',
              level_num   => 3000,
              short_name  => 'HS',
              long_name   => 'HIGHLY_SENSITIVE');

           SA_COMPONENTS.CREATE_LEVEL (
              policy_name => 'HR_OLS_POL',
              level_num   => 2000,
              short_name  => 'S',
              long_name   => 'SENSITIVE');
        END;
        /

    In this specification:

    - `policy_name` associates the levels with the policy container that you just created.
    - `level_num` determines how much access the user can have. Level number `3000` enables a user to have access to this level and any level number below it, in this case, level number `2000`. In other words, a user who is authorized with the `HIGHLY_SENSITIVE` level can also access data assigned to the `SENSITIVE` level.
    - `short_name` is a short-hand name for the `long_name` of the level, and will be used in other procedures to refer to the `long_name` version of the level.

**Parent topic:** Tutorial: Configuring Levels in Oracle Label Security

### 8.5 Step 4: Create the Data Labels for the Levels

A data label tags data records for use with the Oracle Label Security policy.

In this procedure, the data labels will designate the rows that users Susan Mavris and Ida Neau will see in the `HR.EMPLOYEES` table. The rows labeled `HS` will correspond to the `HS` (`HIGHLY_SENSITIVE`) level to be assigned to Susan Mavris, and the rows labeled `S` will correspond with the `S` (`SENSITIVE`) level to be assigned to Ida Neau.

1.  If necessary, connect as a user who can create and manage Oracle Label Security policies.
    For example:
        sqlplus psmith_ols
        Enter password: password
2.  Create the data labels as follows:
        BEGIN
           SA_LABEL_ADMIN.CREATE_LABEL (
              policy_name  => 'HR_OLS_POL',
              label_tag    => 3100,
              label_value  => 'HS',
              data_label   => TRUE);

           SA_LABEL_ADMIN.CREATE_LABEL (
              policy_name  => 'HR_OLS_POL',
              label_tag    => 2100,
              label_value  => 'S',
              data_label   => TRUE);
        END;
        /

    In this specification:

    - `label_tag` is used internally by Oracle Label Security to identify the level. Unlike levels, it does not govern any sort of hierarchy with the labels.
    - `data_label` is set to `TRUE` so that the label can be applied to row data.

**Parent topic:** Tutorial: Configuring Levels in Oracle Label Security

### 8.6 Step 5: Set User Authorizations for the Oracle Label Security Policy

Setting user authorizations entails associating the user with the policy and the minimum and maximum levels that are associated with the Oracle Label Security policy.

1.  If necessary, connect as a user who can create and manage Oracle Label Security policies.
    For example:
        sqlplus psmith_ols
        Enter password: password
2.  Authorize the users as follows:
        BEGIN
           SA_USER_ADMIN.SET_LEVELS (
              policy_name  => 'HR_OLS_POL',
              user_name    => 'SMAVRIS',
              max_level    => 'HS',
              min_level    => 'S');

           SA_USER_ADMIN.SET_LEVELS (
              policy_name  => 'HR_OLS_POL',
              user_name    => 'INEAU',
              max_level    => 'S',
              min_level    => 'S');
        END;
        /

    In this specification, the `def_level` (default level) and `row_level` parameters are omitted so that their values can default to the `max_level` parameter setting.

**Parent topic:** Tutorial: Configuring Levels in Oracle Label Security

### 8.7 Step 6: Apply the Oracle Label Security Policy to the HR Schema

After you apply the policy to the `HR` schema, you must enable the policy association with `HR`.

1.  If necessary, connect as a user who can create and manage Oracle Label Security policies.
    For example:
        sqlplus psmith_ols
        Enter password: password
2.  Apply the policy to the `HR` schema.
        BEGIN
          SA_POLICY_ADMIN.APPLY_TABLE_POLICY (
            policy_name    => 'HR_OLS_POL',
            schema_name    => 'HR',
            table_name     => 'EMPLOYEES',
            table_options  => 'READ_CONTROL');
        END;
        /

    Earlier, when you created the policy with the `SA_SYSDBA.CREATE_POLICY` procedure, you did not set the `default_options` parameter, which defines the policy enforcement options. Therefore, you must set the policy enforcement here, with the `table_options` parameter of `SA_POLICY_ADMIN.APPLY_TABLE_POLICY`. `READ_CONTROL` enforces the OLS policy during the `SELECT` statement processing that the users will perform later. (It also applies to `UPDATE` and `DELETE` statement processing.)
3.  Enable the policy's association with the `HR` schema.
        BEGIN
           SA_POLICY_ADMIN.ENABLE_TABLE_POLICY (
              policy_name => 'HR_OLS_POL',
              schema_name => 'HR',
              table_name  => 'EMPLOYEES');
        END;
        /

**Parent topic:** Tutorial: Configuring Levels in Oracle Label Security

### 8.8 Step 7: Add the Policy Labels to the HR.EMPLOYEES Table Data

Both the Oracle Label Security administrator and the `HR` user will add the policy labels to the `HR.EMPLOYEES` table data in the `EMPLOYEE_ID` column.

1.  If necessary, connect as a user who can create and manage Oracle Label Security policies.
    For example:
        sqlplus psmith_ols
        Enter password: password
2.  Grant the `READ` privilege to the `HR_OLS_POL` policy for the `HR` user.
        BEGIN
           SA_USER_ADMIN.SET_USER_PRIVS (
              policy_name => 'HR_OLS_POL',
              user_name   => 'HR',
              privileges  => 'READ');
        END;
        /
3.  Connect as the `HR` user.
        connect hr
        Enter password: password
4.  Perform the following `UPDATE` statement to apply the `HIGHLY_SENSITIVE` level to the employee IDs of users who have left the company.
    This `UPDATE` statement controls the access that Susan Mavris will have to the `HR.EMPLOYEES` table because she is authorized for the `HIGHLY_SENSITIVE` level.
        UPDATE employees
        SET    ols_col = CHAR_TO_LABEL('HR_OLS_POL','HS')
        WHERE  UPPER(employee_id) IN (200, 101, 102, 176, 201, 122, 114);
5.  Perform the following `UPDATE` statement to apply the `SENSITIVE` level to the employee IDs of current employees in the company.
    This `UPDATE` statement controls the access that Ida Neau will have to the `HR.EMPLOYEES` table because she is authorized for the `SENSITIVE` level.
        UPDATE employees
        SET    ols_col = CHAR_TO_LABEL('HR_OLS_POL','S')
        WHERE  UPPER(employee_id) NOT IN (200, 101, 102, 176, 201, 122, 114);

    This `UPDATE` statement translates to "Apply the `SENSITIVE` label to any employee who is not a former employee."

**Parent topic:** Tutorial: Configuring Levels in Oracle Label Security

### 8.9 Step 8: Test the Oracle Label Security Policy

To test the policy, each user will try to query the `HR.EMPLOYEES` table.

1.  Connect as user Ida Neau.
        connect ineau
        Enter password: password
2.  Set column widths for the table output.
        column first_name format a25
        column last_name format a25
        column ols_label format a10
3.  Execute the following query:
        SELECT FIRST_NAME, LAST_NAME, EMPLOYEE_ID,
        LABEL_TO_CHAR(OLS_COL) OLS_LABEL
        FROM HR.EMPLOYEES
        ORDER BY OLS_COL;

    The output should be similar to the following:

        FIRST_NAME                LAST_NAME                 EMPLOYEE_ID OLS_LABEL
        ------------------------- ------------------------- ----------- ----------
        Steven                    King                              100 S
        Alexander                 Hunold                            103 S
        Bruce                     Ernst                             104 S
        David                     Austin                            105 S
        Valli                     Pataballa                         106 S
        Diana                     Lorentz                           107 S
        Nancy                     Greenberg                         108 S
        Daniel                    Faviet                            109 S
        ...
        100 rows selected

    Because Ida Neau was assigned the `SENSITIVE` label, the output in the column `OLS_LABEL` is `S` (for `SENSITIVE`) only. 100 rows are returned.

    Note that the Oracle Label Security restriction applies to any `SELECT` query the user makes. For example, if Ida Neau performs a `SELECT COUNT(*) FROM HR.EMPLOYEES;` query, then it would return these 100 rows, not the full 107.
4.  Connect as user Susan Mavris.
        connect smavris
        Enter password: password
5.  Execute the same query that Ida Neau executed.
        SELECT FIRST_NAME, LAST_NAME, EMPLOYEE_ID,
        LABEL_TO_CHAR(OLS_COL) OLS_LABEL
        FROM HR.EMPLOYEES
        ORDER BY OLS_COL;

    The output should be similar to the following:

        FIRST_NAME                LAST_NAME                 EMPLOYEE_ID OLS_LABEL
        ------------------------- ------------------------- ----------- ----------
        Steven                    King                              100 S
        Alexander                 Hunold                            103 S
        ...
        William                   Gietz                             206 S
        Neena                     Kochhar                           101 HS
        Lex                       De Haan                           102 HS
        Den                       Raphaely                          114 HS
        Michael                   Hartstein                         201 HS
        Jonathon                  Taylor                            176 HS
        Jennifer                  Whalen                            200 HS
        Payam                     Kaufling                          122 HS

        107 rows selected

    Because Susan Mavris was assigned the `HIGHLY_SENSITIVE` label, the output in the column `OLS_LABEL` is `HS` (for `HIGHLY_SENSITIVE`) and `S` (for `SENSITIVE`). 107 rows are returned.

**Parent topic:** Tutorial: Configuring Levels in Oracle Label Security

### 8.10 Step 9: Optionally, Remove the Oracle Label Security Policy Components

You can remove the Oracle Label Security policy, `HR_ROLE` role, and users Ida Neau and Susan Mavris.

However, if you want to try the tutorial on how to create Oracle Label Security compartments, then do not remove these components. The tutorial on compartments builds on this tutorial on levels.

1.  Connect as a user who can create and manage Oracle Label Security policies.
    For example:
        sqlplus psmith_ols
        Enter password: password
2.  Drop the Oracle Label Security policy.
    This procedure also removes the levels and the `OLS_COL` column from the `HR.EMPLOYEES` table.
        BEGIN
          SA_SYSDBA.DROP_POLICY (
            policy_name  => 'HR_OLS_POL',
            drop_column  => TRUE);
        END;
        /
3.  Connect as user who has privileges to drop roles and user accounts.
    For example:
        connect sec_admin
        Enter password: password
4.  Drop the `HR_ROLE` role.
        DROP ROLE HR_ROLE;
5.  Drop the `ineau` and `smavris` accounts.
        DROP USER INEAU;
        DROP USER SMAVRIS;

**Related Topics**

- [Tutorial: Configuring Compartments in Oracle Label Security](configuring-ols-compartments.md)

**Parent topic:** Tutorial: Configuring Levels in Oracle Label Security
