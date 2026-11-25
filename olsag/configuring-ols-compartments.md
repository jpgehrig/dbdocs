This tutorial demonstrates how to create Oracle Label Security compartments.

- About This Tutorial
  In this tutorial, you will use the `HR` schema to learn how to use Oracle Label Security compartments.
- Step 1: Create an Account for Lily Leagull
  Lily Leagull will initially have the same privileges as Susan Mavris and Ida Neau.
- Step 2: Authorize Lily Leagull for the HIGHLY_SENSITIVE Level
  After the `lleagull` account has been created, you can authorize it to use the `HIGHLY_SENSITIVE` level.
- Step 3: Create Two Compartments for the Oracle Label Security Policy
  All three users (Susan Mavris, Ida Neau, and Lily Leagull) will use compartments to access their data.
- Step 4: Create the Data Labels for the Compartments
  You will create three data labels for the compartments.
- Step 5: Assign the Labels to the Users
  Assigning the labels to the users will designate the rows to which these users will have access.
- Step 6: Add the Policy Labels to the HR.EMPLOYEES Table Data
  The `HR` user will add the policy labels to the `HR.EMPLOYEES` table data in the `EMPLOYEE_ID` column.
- Step 7: Test the Oracle Label Security Policy
  To test the policy, each user will try to query the `HR.EMPLOYEES` table.
- Step 8: Optionally, Remove the Oracle Label Security Policy Components
  You can remove the Oracle Label Security policy, `HR_ROLE` role, and users Ida Neau, Susan Mavris, and Lily Leagull.

**Parent topic:** [Oracle Label Security Tutorials](oracle-label-security-tutorials.md)

### 9.1 About This Tutorial

In this tutorial, you will use the `HR` schema to learn how to use Oracle Label Security compartments.

This tutorial builds on the previous tutorial, which demonstrates how to create Oracle Label Security levels to control the access that two users, Susan Mavris and Ida Neau, have to the records in the `HR.EMPLOYEES` schema. For this tutorial, a third user, Lily Leagull, is an attorney with the company's legal department. Two former employees are suing the company, and she must have access to their records. She must not have access to any other records. The access to the former users is set by the `HIGHLY_SENSITIVE` level, which you created in the previous tutorial. Access to the records of the two suing former employees will be possible through the use of a compartment within the `HIGHLY_SENSITIVE` data set, called `LEGAL`.

**Related Topics**

- [Tutorial: Configuring Levels in Oracle Label Security](configuring-ols-levels.md)

**Parent topic:** Tutorial: Configuring Compartments in Oracle Label Security

### 9.2 Step 1: Create an Account for Lily Leagull

Lily Leagull will initially have the same privileges as Susan Mavris and Ida Neau.

1.  Log in to SQL\*Plus as a user who has privileges to create user accounts and grant them roles.
    For example:
        sqlplus sec_admin
        Enter password: password
2.  Create the account for Lily Leagull and grant her the `HR_ROLE` role as follows:
        GRANT CONNECT, HR_ROLE TO LLEAGULL IDENTIFIED BY password;

**Parent topic:** Tutorial: Configuring Compartments in Oracle Label Security

### 9.3 Step 2: Authorize Lily Leagull for the HIGHLY_SENSITIVE Level

After the `lleagull` account has been created, you can authorize it to use the `HIGHLY_SENSITIVE` level.

1.  Connect as a user who can create and manage Oracle Label Security policies.
    For example:
        sqlplus psmith_ols
        Enter password: password
2.  Authorize `lleagull` to use the `HIGHLY_SENSITIVE` level.
    The short name for `HIGHLY_SENSITIVE` is `HS`.
        BEGIN
           SA_USER_ADMIN.SET_LEVELS (
              policy_name  => 'HR_OLS_POL',
              user_name    => 'LLEAGULL',
              max_level    => 'HS',
              min_level    => 'S');
        END;
        /

**Parent topic:** Tutorial: Configuring Compartments in Oracle Label Security

### 9.4 Step 3: Create Two Compartments for the Oracle Label Security Policy

All three users (Susan Mavris, Ida Neau, and Lily Leagull) will use compartments to access their data.

The two HR employees, Susan Mavris and Ida Neau, will use the `HR` compartment. The Legal department employee, Lily Leagull, will use the `LEGAL` (`LEG`) compartment.

1.  If necessary, connect as a user who can create and manage Oracle Label Security policies.
    For example:
        sqlplus psmith_ols
        Enter password: password
2.  Create the compartments as follows:
        BEGIN
          SA_COMPONENTS.CREATE_COMPARTMENT (
            policy_name      => 'HR_OLS_POL',
            long_name        => 'HR',
            short_name       => 'HR',
            comp_num         =>  1000);

          SA_COMPONENTS.CREATE_COMPARTMENT (
            policy_name      => 'HR_OLS_POL',
            long_name        => 'LEGAL',
            short_name       => 'LEG',
            comp_num         =>  2000);
        END;
        /

    In this specification, the `comp_num` does not denote hierarchy as the `level_num` setting does with levels. It is only used to help identify the compartment.

**Parent topic:** Tutorial: Configuring Compartments in Oracle Label Security

### 9.5 Step 4: Create the Data Labels for the Compartments

You will create three data labels for the compartments.

In this procedure, the data labels will designate the rows that users Susan Mavris, Ida Neau, and Lily Leagull will see in the `HR.EMPLOYEES` table.

1.  If necessary, connect as a user who can create and manage Oracle Label Security policies.
    For example:
        sqlplus psmith_ols
        Enter password: password
2.  Create the data labels as follows:
        BEGIN
           SA_LABEL_ADMIN.CREATE_LABEL (
              policy_name  => 'HR_OLS_POL',
              label_tag    => 1100,
              label_value  => 'S:HR:', -- SENSITIVE level for the HR compartment
              data_label   => TRUE);

           SA_LABEL_ADMIN.CREATE_LABEL (
              policy_name  => 'HR_OLS_POL',
              label_tag    => 1200,
              label_value  => 'HS:HR:', -- HIGHLY_SENSITIVE level for the HR compartment
              data_label   => TRUE);

           SA_LABEL_ADMIN.CREATE_LABEL (
              policy_name  => 'HR_OLS_POL',
              label_tag    => 1300,
              label_value  => 'HS:LEG:', --HIGHLY_SENSITIVE level for the LEG compartment
              data_label   => TRUE);

        END;
        /

    In this specification:

    - `label_value` `S:HR` will be assigned to the records of all current employees.
    - `label_value` `HS:HR` will be assigned to the records all current and former employees.
    - `label_value` `HS:LEG` will be assigned to the records of former employees who are suing the company.

**Parent topic:** Tutorial: Configuring Compartments in Oracle Label Security

### 9.6 Step 5: Assign the Labels to the Users

Assigning the labels to the users will designate the rows to which these users will have access.

1.  If necessary, connect as a user who can create and manage Oracle Label Security policies.
    For example:
        sqlplus psmith_ols
        Enter password: password
2.  Assign the labels to the users as follows:
        BEGIN
           SA_USER_ADMIN.SET_USER_LABELS (
              policy_name    => 'HR_OLS_POL',
              user_name      => 'ineau',
              max_read_label => 'S:HR:');

           SA_USER_ADMIN.SET_USER_LABELS (
              policy_name    => 'HR_OLS_POL',
              user_name      => 'smavris',
              max_read_label => 'HS:HR,LEG:');

           SA_USER_ADMIN.SET_USER_LABELS (
              policy_name    => 'HR_OLS_POL',
              user_name      => 'lleagull',
              max_read_label => 'HS:LEG:');
        END;
        /

    In this specification:

    - User `ineau` (Ida Neau), who is authorized for the `HR` compartment, will continue to have access to all current employees, but not the former or suing employees.
    - User `smavris` (Susan Mavris), who is authorized for both the `HR` and `LEG` compartments, will continue to have access to all current and former employees, and former employees who are suing the company.
    - User `lleagul` (Lily Leagul), who is authorized for the `LEG` compartment, will have access only to former employees who are suing the company.

**Parent topic:** Tutorial: Configuring Compartments in Oracle Label Security

### 9.7 Step 6: Add the Policy Labels to the HR.EMPLOYEES Table Data

The `HR` user will add the policy labels to the `HR.EMPLOYEES` table data in the `EMPLOYEE_ID` column.

1.  Connect as the `HR` user.
        connect hr
        Enter password: password
2.  Perform the following `UPDATE` statement to apply the `SENSITIVE` level and the `HR` compartment to the employee IDs of users who are still currently employed with the company.
    This `UPDATE` statement controls the access that Ida Neau will have to the `HR.EMPLOYEES` table because she is authorized for the `SENSITIVE` level and the `HR` compartment.
        UPDATE employees
        SET    ols_col = CHAR_TO_LABEL('HR_OLS_POL','S:HR')
        WHERE  UPPER(employee_id) NOT IN (200, 101, 102, 176, 201, 122, 114);
3.  Perform the following `UPDATE` statement to apply the `HIGHLY_SENSITIVE` level and `HR` compartment to the employee IDs of current and former employees.
    This `UPDATE` statement controls the access that Susan Mavris will have to the `HR.EMPLOYEES` table because she is authorized for the `SENSITIVE` level and the `HR` and `LEG` compartments.
        UPDATE employees
        SET    ols_col = CHAR_TO_LABEL('HR_OLS_POL','HS:HR,LEG')
        WHERE  UPPER(employee_id) IN (200, 101, 102, 176, 201, 122, 114);
4.  Perform the following `UPDATE` statement to apply the `HIGHLY_SENSITIVE` level and `LEG` compartment to the employee IDs of former employees who are suing the company.
    This `UPDATE` statement controls the access that Lily Leagull will have to the `HR.EMPLOYEES` table because she is authorized for the `HIGHLY_SENSITIVE` level and the `LEG` compartment.
        UPDATE employees
        SET    ols_col = CHAR_TO_LABEL('HR_OLS_POL','HS:LEG')
        WHERE  UPPER(employee_id) IN (200, 101);

**Parent topic:** Tutorial: Configuring Compartments in Oracle Label Security

### 9.8 Step 7: Test the Oracle Label Security Policy

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
        Steven                    King                              100 S:HR
        Alexander                 Hunold                            103 S:HR
        Bruce                     Ernst                             104 S:HR
        David                     Austin                            105 S:HR
        Valli                     Pataballa                         106 S:HR
        Diana                     Lorentz                           107 S:HR
        Nancy                     Greenberg                         108 S:HR
        Daniel                    Faviet                            109 S:HR
        John                      Chen                              110 S:HR
        Ismael                    Sciarra                           111 S:HR
        ...

        100 rows selected

    Because Ida Neau was assigned the `SENSITIVE` (`S`) label and the `HR` compartment, the output in the column `OLS_LABEL` is `S:HR`. 100 rows are returned.

    Note that the Oracle Label Security policy restriction applies to any `SELECT` query the user makes. For example, if Ida Neau performs a `SELECT COUNT(*) FROM HR.EMPLOYEES;` query, then it would return 100 rows, not the full 107.
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
        Steven                    King                              100 S:HR
        Alexander                 Hunold                            103 S:HR
        Bruce                     Ernst                             104 S:HR
        David                     Austin                            105 S:HR
        Valli                     Pataballa                         106 S:HR
        ...
        Jennifer                  Whalen                            200 HS:LEG
        Neena                     Kochhar                           101 HS:LEG
        Michael                   Hartstein                         201 HS:HR,LEG
        Jonathon                  Taylor                            176 HS:HR,LEG
        Den                       Raphaely                          114 HS:HR,LEG
        Lex                       De Haan                           102 HS:HR,LEG
        Payam                     Kaufling                          122 HS:HR,LEG

        107 rows selected

    Because Susan Mavris was assigned the `HIGHLY_SENSITIVE` (`HS`) level with the `HR` and `LEG` compartments, the output in the column `OLS_LABEL` is as follows:

    - `S:HR` to capture all current employees
    - `HS:HR, LEG` to capture all former employees
    - `HS:LEG` to capture former employees who are suing.

    107 rows are returned.
6.  Connect as user Lily Leagull.
        connect lleagull
        Enter password: password
7.  Execute the same query that Susan Mavris executed.
        SELECT FIRST_NAME, LAST_NAME, EMPLOYEE_ID,
        LABEL_TO_CHAR(OLS_COL) OLS_LABEL
        FROM HR.EMPLOYEES
        ORDER BY OLS_COL;

    The output should be similar to the following:

        FIRST_NAME                LAST_NAME                 EMPLOYEE_ID OLS_LABEL
        ------------------------- ------------------------- ----------- ----------
        Jennifer                  Whalen                            200 HS:LEG
        Neena                     Kochhar                           101 HS:LEG

        107 rows selected

    Because Lily Leagull was assigned the `HS` level with the `LEG` compartment, only former users who are suing are returned for her query.

**Parent topic:** Tutorial: Configuring Compartments in Oracle Label Security

### 9.9 Step 8: Optionally, Remove the Oracle Label Security Policy Components

You can remove the Oracle Label Security policy, `HR_ROLE` role, and users Ida Neau, Susan Mavris, and Lily Leagull.

1.  Connect as a user who can create and manage Oracle Label Security policies.
    For example:
        sqlplus psmith_ols
        Enter password: password
2.  Drop the Oracle Label Security policy.
    This procedure also removes the levels, compartments, and from the `HR.EMPLOYEES` table, the `OLS_COL` column.
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
5.  Drop the `ineau`, `smavris`, and `lleagull` accounts.
        DROP USER INEAU;
        DROP USER SMAVRIS;
        DROP USER LLEAGULL;

**Parent topic:** Tutorial: Configuring Compartments in Oracle Label Security
