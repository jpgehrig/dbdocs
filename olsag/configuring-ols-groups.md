This tutorial demonstrates how to create an Oracle Label Security parent group that has four child groups.

- About This Tutorial
  In this tutorial, you will use the `OE` schema to learn how to use Oracle Label Security groups.
- Step 1: Create a Role and User Accounts
  The role that you create will enable any user who is granted it to have the `SELECT` privilege on the `OE.CUSTOMERS` table. The user accounts are for four sales representatives and the
- Step 2: Create the Oracle Label Security Policy Container
  As an Oracle Label Security administrator, you must create and then enable the policy container.
- Step 3: Create and Authorize a Level Component for the Oracle Label Security Policy
  After you create the Oracle Label Security policy container, you are ready to create and authorize a level component.
- Step 4: Create and Authorize Groups for the Oracle Label Security Policy
  You will create and authorize one parent group and four child groups for this parent group. Each user will be authorized for a group.
- Step 5: Apply and Authorize the Policy to the Table
  You must apply the `OE_OLS_POL` policy to the `OE.CUSTOMERS` table and then authorize the `OE` schema user to have read privileges for the policy.
- Step 6: Add the Policy Labels to the OE.CUSTOMERS Table Data
  The `OE` user will add the policy labels to the `OE.CUSTOMERS` table data in the `ACCOUNT_MGR_ID` column.
- Step 7: Test the Oracle Label Security Policy
  To test the policy, each user will query the `OE.CUSTOMERS` table.
- Step 8: Optionally, Remove the Oracle Label Security Policy Components
  You can remove the Oracle Label Security policy, `OE_CUST` role, and the user accounts.

**Parent topic:** [Oracle Label Security Tutorials](oracle-label-security-tutorials.md)

### 10.1 About This Tutorial

In this tutorial, you will use the `OE` schema to learn how to use Oracle Label Security groups.

Each sales manager must have access to the records of his or her customers in the `OE.CUSTOMERS` table. The company president of advertising, Steven King, who each sales manager reports to, must have access to all customer records. The customer records are divided into groups based on the sales managers' territories.

The Oracle Label Security policy that you create will assign each of the sales managers a group, and this group will be used to label the appropriate rows in the `OE.CUSTOMERS` table. The groups will have a parent group, `GLOBAL_SALES`, which will be associated with advertising president Steven King. The child groups of `GLOBAL_SALES` are as follows:

- `EUROPE`, with access by sales manager Alberto Errazuriz
- `ASIA`, with access by sales manager Gerald Cambrault
- `UNITED_STATES_1`, with access by sales manager John Russell
- `UNITED_STATES_2`, with access by sales manager Eleni Zlotkey

By default, the `OE` schema is not installed. You can download this schema from GitHub, as explained in Oracle Database Sample Schemas.

**Related Topics**

- [Oracle Database Sample Schemas](../comsc/installing-sample-schemas.md)

**Parent topic:** Tutorial: Configuring Groups in Oracle Label Security

### 10.2 Step 1: Create a Role and User Accounts

The role that you create will enable any user who is granted it to have the `SELECT` privilege on the `OE.CUSTOMERS` table. The user accounts are for four sales representatives and the

1.  Log in to SQL\*Plus as a user who has privileges to create roles, grant privileges, and create user accounts.
    For example:
        sqlplus sec_admin
        Enter password: password
2.  Ensure that the `OE` schema has been downloaded from GitHub and installed.
    Oracle Database Sample Schemas explains how to download and install this schema.
3.  Create the role as follows:
        CREATE ROLE OE_CUST;
4.  Grant the `SELECT` privilege on `OE.CUSTOMERS` to `OE_CUST`.
        GRANT SELECT ON OE.CUSTOMERS TO OE_CUST;
5.  Create the user accounts and grant them the `OE_CUST` role.
        GRANT CONNECT, OE_CUST TO SKING IDENTIFIED BY password; --For Steven King, president
        GRANT CONNECT, OE_CUST TO AERRAZURIZ IDENTIFIED BY password; --For Alberto Errazuriz, sales manager
        GRANT CONNECT, OE_CUST TO GCAMBRAULT IDENTIFIED BY password; --For Gerald Cambrault, sales manager
        GRANT CONNECT, OE_CUST TO JRUSSELL IDENTIFIED BY password; --For John Russell, sales manager
        GRANT CONNECT, OE_CUST TO EZLOTKEY IDENTIFIED BY password; --For Eleni Zlotkey, sales manager

**Related Topics**

- [Oracle Database Sample Schemas](../comsc/installing-sample-schemas.md)

**Parent topic:** Tutorial: Configuring Groups in Oracle Label Security

### 10.3 Step 2: Create the Oracle Label Security Policy Container

As an Oracle Label Security administrator, you must create and then enable the policy container.

1.  Connect as a user who can create and manage Oracle Label Security policies.
    For example:
        sqlplus psmith_ols
        Enter password: password
2.  Create the policy.
        BEGIN
         SA_SYSDBA.CREATE_POLICY (
          policy_name      => 'OE_OLS_POL',
          column_name      => 'OLS_COL');
        END;
        /

    In this specification, the `default_options` parameter is omitted because you can add it later on in another procedure.
3.  Enable the policy.
        EXEC SA_SYSDBA.ENABLE_POLICY ('OE_OLS_POL');

**Parent topic:** Tutorial: Configuring Groups in Oracle Label Security

### 10.4 Step 3: Create and Authorize a Level Component for the Oracle Label Security Policy

After you create the Oracle Label Security policy container, you are ready to create and authorize a level component.

Levels are used for this policy but you do need to have a default level in order for the data labels that will be created later on to work.

1.  If necessary, connect as a user who can create and manage Oracle Label Security policies.
    For example:
        sqlplus psmith_ols
        Enter password: password
2.  Create the levels as follows:
        BEGIN
           SA_COMPONENTS.CREATE_LEVEL (
              policy_name => 'OE_OLS_POL',
              level_num   => 50,
              short_name  => 'D',
              long_name   => 'DEFAULT');
        END;
        /

    In this specification:

    - `policy_name` associates the levels with the policy container that you just created.
    - `level_num` determines how much access a user can have. Level number `50` enables a user to have access to this level and any level number below it. However, this tutorial only uses one level.
    - `short_name` is a short-hand name for the `long_name` of the level, and will be used in other procedures to refer to the `long_name` version of the level.
3.  Authorize the level for the five users who will access the `OE.EMPLOYEES` table.
        BEGIN
           SA_USER_ADMIN.SET_LEVELS (
              policy_name  => 'OE_OLS_POL',
              user_name    => 'SKING',
              max_level    => 'D');

           SA_USER_ADMIN.SET_LEVELS (
              policy_name  => 'OE_OLS_POL',
              user_name    => 'AERRAZURIZ',
              max_level    => 'D');

           SA_USER_ADMIN.SET_LEVELS (
              policy_name  => 'OE_OLS_POL',
              user_name    => 'GCAMBRAULT',
              max_level    => 'D');

           SA_USER_ADMIN.SET_LEVELS (
              policy_name  => 'OE_OLS_POL',
              user_name    => 'JRUSSELL',
              max_level    => 'D');

           SA_USER_ADMIN.SET_LEVELS (
              policy_name  => 'OE_OLS_POL',
              user_name    => 'EZLOTKEY',
              max_level    => 'D');
        END;
        /

**Parent topic:** Tutorial: Configuring Groups in Oracle Label Security

### 10.5 Step 4: Create and Authorize Groups for the Oracle Label Security Policy

You will create and authorize one parent group and four child groups for this parent group. Each user will be authorized for a group.

1.  If necessary, connect as a user who can create and manage Oracle Label Security policies.
    For example:
        sqlplus psmith_ols
        Enter password: password
2.  Create the `GLOBAL_SALES` parent group.
        BEGIN
          SA_COMPONENTS.CREATE_GROUP (
           policy_name     => 'OE_OLS_POL',
           group_num       => 2000,
           short_name      => 'GS',
           long_name       => 'GLOBAL_SALES');
        END;
        /

    In this specification, `group_num` is used for identification purposes only. It does not control any hierarchy in this set of groups.
3.  Create the child groups.
    Any user who is authorized for the parent group, `GLOBAL_SALES` (`GS`), will have authorization for these child groups as well.
        BEGIN
          SA_COMPONENTS.CREATE_GROUP (
           policy_name     => 'OE_OLS_POL',
           group_num       => 2100,
           short_name      => 'EU',
           long_name       => 'EUROPE',
           parent_name     => 'GS');

          SA_COMPONENTS.CREATE_GROUP (
           policy_name     => 'OE_OLS_POL',
           group_num       => 2200,
           short_name      => 'AS',
           long_name       => 'ASIA',
           parent_name     => 'GS');

          SA_COMPONENTS.CREATE_GROUP (
           policy_name     => 'OE_OLS_POL',
           group_num       => 2300,
           short_name      => 'US1',
           long_name       => 'UNITED_STATES_1',
           parent_name     => 'GS');

          SA_COMPONENTS.CREATE_GROUP (
           policy_name     => 'OE_OLS_POL',
           group_num       => 2400,
           short_name      => 'US2',
           long_name       => 'UNITED_STATES_2',
           parent_name     => 'GS');
        END;
        /

    In this specification, the `parent_name` parameter designates the parent group, `GS`.
4.  Authorize the users that you created earlier for these groups.
        BEGIN
         SA_USER_ADMIN.SET_GROUPS (
          policy_name    => 'OE_OLS_POL',
          user_name      => 'SKING',
          read_groups    => 'GS');

         SA_USER_ADMIN.SET_GROUPS (
          policy_name    => 'OE_OLS_POL',
          user_name      => 'AERRAZURIZ',
          read_groups    => 'EU');

         SA_USER_ADMIN.SET_GROUPS (
          policy_name    => 'OE_OLS_POL',
          user_name      => 'GCAMBRAULT',
          read_groups    => 'AS');

         SA_USER_ADMIN.SET_GROUPS (
          policy_name    => 'OE_OLS_POL',
          user_name      => 'JRUSSELL',
          read_groups    => 'US1');

         SA_USER_ADMIN.SET_GROUPS (
          policy_name    => 'OE_OLS_POL',
          user_name      => 'EZLOTKEY',
          read_groups    => 'US2');
        END;
        /

    In this specification, user `SKING` is authorized for the parent group, `GS`, and the remaining users, who are all sales managers, are authorized for the groups that represent their sales territories.

After you set the authorization for these groups, and because you have not yet created data labels, Oracle Label Security automatically creates the data labels for you. In earlier tutorials, you learned how to manually create the data labels, but for this tutorial, you get to allow Oracle Label Security to create them for you. You can see the labels by querying the `DBA_SA_LABELS` data dictionary view. For example:

    SELECT POLICY_NAME, LABEL, LABEL_TAG FROM DBA_SA_LABELS ORDER BY LABEL_TAG;

Output similar to the following appears:

    POLICY_NAME     LABEL      LABEL_TAG
    ------------    ------     -----------
    OE_OLS_POL      D          1000000085
    OE_OLS_POL      D::GS      1000000086
    OE_OLS_POL      D::EU      1000000087
    OE_OLS_POL      D::AS      1000000088
    OE_OLS_POL      D::US1     1000000089
    OE_OLS_POL      D::US2     1000000090

**Parent topic:** Tutorial: Configuring Groups in Oracle Label Security

### 10.6 Step 5: Apply and Authorize the Policy to the Table

You must apply the `OE_OLS_POL` policy to the `OE.CUSTOMERS` table and then authorize the `OE` schema user to have read privileges for the policy.

1.  If necessary, connect as a user who can create and manage Oracle Label Security policies.
    For example:
        sqlplus psmith_ols
        Enter password: password
2.  Apply the `OE_OLS_POL` policy to the `OE.CUSTOMERS` table.
        BEGIN
          SA_POLICY_ADMIN.APPLY_TABLE_POLICY (
            policy_name    => 'OE_OLS_POL',
            schema_name    => 'OE',
            table_name     => 'CUSTOMERS',
            table_options  => 'READ_CONTROL');
        END;
        /

    Earlier, when you created the policy with the `SA_SYSDBA.CREATE_POLICY` procedure, you did not set the `default_options` parameter, which defines the policy enforcement options. Therefore, you must set the policy enforcement here, with the `table_options` parameter of ` SA_POLICY_ADMIN.APPLY_TABLE_POLICY`. `READ_CONTROL` enforces the OLS policy during the `SELECT` statement processing that the users will perform later. (It also applies to `UPDATE` and `DELETE` statement processing.)
3.  Enable the `OE_OLS_POL` policy for `OE.CUSTOMERS`.
        BEGIN
           SA_POLICY_ADMIN.ENABLE_TABLE_POLICY (
              policy_name => 'OE_OLS_POL',
              schema_name => 'OE',
              table_name  => 'CUSTOMERS');
        END;
        /
4.  Set user privileges for `OE` so that `OE` can apply the labels to the `OE.CUSTOMERS` data rows.
        BEGIN
           SA_USER_ADMIN.SET_USER_PRIVS (
              policy_name => 'OE_OLS_POL',
              user_name   => 'OE',
              privileges  => 'READ');
        END;
        /

**Parent topic:** Tutorial: Configuring Groups in Oracle Label Security

### 10.7 Step 6: Add the Policy Labels to the OE.CUSTOMERS Table Data

The `OE` user will add the policy labels to the `OE.CUSTOMERS` table data in the `ACCOUNT_MGR_ID` column.

1.  Connect as the `OE` user.
        connect OE
        Enter password: password
2.  Perform the following `UPDATE` statement to apply the `GLOBAL_SALES` (`GS`) group to `OE.CUSTOMERS`.
        UPDATE customers
        SET    ols_col = CHAR_TO_LABEL('OE_OLS_POL','D::GS')
        WHERE  UPPER(account_mgr_id) IN (145, 147, 148, 149);

    In this specification, the user who is authorized for the label identifier `D::GS` (Steven King) will have access to the rows that are available to users whose `account_mgr_id` IDs are `145`, `147`, `148`, and `149`.
3.  Perform the following `UPDATE` statements for the sales managers.
    For European sales manager Alberto Errazuriz, whose ID is `147`:
        UPDATE customers
        SET    ols_col = CHAR_TO_LABEL('OE_OLS_POL','D::EU')
        WHERE  UPPER(account_mgr_id) = 147;

    For Asian sales manager Gerald Cambrault, whose ID is `148`:

        UPDATE customers
        SET    ols_col = CHAR_TO_LABEL('OE_OLS_POL','D::AS')
        WHERE  UPPER(account_mgr_id) = 148;

    For US sales manager John Russell, whose ID is `145`:

        UPDATE customers
        SET    ols_col = CHAR_TO_LABEL('OE_OLS_POL','D::US1')
        WHERE  UPPER(account_mgr_id) = 145;

    For US sales manager Elena Zlotkey, whose ID is `149`:

        UPDATE customers
        SET    ols_col = CHAR_TO_LABEL('OE_OLS_POL','D::US2')
        WHERE  UPPER(account_mgr_id) = 149;

**Parent topic:** Tutorial: Configuring Groups in Oracle Label Security

### 10.8 Step 7: Test the Oracle Label Security Policy

To test the policy, each user will query the `OE.CUSTOMERS` table.

1.  Connect as user Alberto Errazuriz.
        connect aerrazuriz
        Enter password: password
2.  Set column widths for the table output.
        column cust_first_name format a25
        column cust_last_name format a25
        column ols_label format a10
3.  Execute the following query:
        SELECT CUST_FIRST_NAME, CUST_LAST_NAME, ACCOUNT_MGR_ID,
        LABEL_TO_CHAR(OLS_COL) OLS_LABEL
        FROM OE.CUSTOMERS
        ORDER BY OLS_COL;

    The output should be similar to the following:

        CUST_FIRST_NAME           CUST_LAST_NAME            ACCOUNT_MGR_ID OLS_LABEL
        ------------------------- ------------------------- -------------- ----------
        Hal                       Olin                                 147 D::EU
        Hannah                    Kanth                                147 D::EU
        Hannah                    Field                                147 D::EU
        Margret                   Powell                               147 D::EU
        Harry Mean                Taylor                               147 D::EU
        Margrit                   Garner                               147 D::EU
        Maria                     Warden                               147 D::EU
        Marilou                   Landis                               147 D::EU
        ...
        76 rows selected.

    Because Alberto Errazuriz is assigned the `D` level with the `EU` group, the output is `D:EU`.
4.  Repeat this query for the other sales managers:
    - Asian sales manager Gerald Cambrault (`gcambrault`), whose output in the `OLS_LABEL` column should be `D:AS`, with 58 rows returned.
    - US sales manager John Russell (`jrussell`), whose output in the `OLS_LABEL` column should be `D:US1`, with 111 rows returned.
    - Elena Zlotkey (`ezlotkey`), whose output in the `OLS_LABEL` column should be `D:US2`, with 74 rows returned.
5.  Connect as president Steven King.
        connect sking
        Enter password: password
6.  Execute the query.
        SELECT CUST_FIRST_NAME, CUST_LAST_NAME, ACCOUNT_MGR_ID,
        LABEL_TO_CHAR(OLS_COL) OLS_LABEL
        FROM OE.CUSTOMERS
        ORDER BY OLS_COL;

    The output should be similar to the following:

        CUST_FIRST_NAME           CUST_LAST_NAME            ACCOUNT_MGR_ID OLS_LABEL
        ------------------------- ------------------------- -------------- ----------
        Kelly                     Lange                                147 D::EU
        Kenneth                   Redford                              147 D::EU
        Rick                      Lyon                                 147 D::EU
        Mammutti                  Sutherland                           147 D::EU
        Margaret                  Ustinov                              147 D::EU
        Kevin                     Cleveland                            147 D::EU
        Klaus Maria               Russell                              147 D::EU
        Kris                      de Niro                              147 D::EU
        Alain                     Barkin                               147 D::EU
        Albert                    Dutt                                 147 D::EU
        Amanda                    Finney                               147 D::EU

        ...

        Dom                       McQueen                              149 D::US2
        Dom                       Hoskins                              149 D::US2
        Don                       Siegel                               149 D::US2
        Gvtz                      Bradford                             149 D::US2
        Holly                     Kurosawa                             149 D::US2
        Rob                       MacLaine                             149 D::US2
        Don                       Barkin                               149 D::US2
        Meg                       Sen                                  149 D::US2
        ...
        319 rows selected.

    Because Steven King is assigned the `GS` parent group, the output in the `OLS_LABEL` column is includes all four child groups: `D::EU`, `D::AS`, `D::US1`, and `D::US2`.

**Parent topic:** Tutorial: Configuring Groups in Oracle Label Security

### 10.9 Step 8: Optionally, Remove the Oracle Label Security Policy Components

You can remove the Oracle Label Security policy, `OE_CUST` role, and the user accounts.

1.  Connect as a user who can create and manage Oracle Label Security policies.
    For example:
        sqlplus psmith_ols
        Enter password: password
2.  Drop the Oracle Label Security policy.
    This procedure also removes the levels, groups, and from the `OE.CUSTOMERS` table, the `OLS_COL` column.
        BEGIN
          SA_SYSDBA.DROP_POLICY (
            policy_name  => 'OE_OLS_POL',
            drop_column  => TRUE);
        END;
        /
3.  Connect as user who has privileges to drop roles and user accounts.
    For example:
        connect sec_admin
        Enter password: password
4.  Drop the `OE_CUST` role.
        DROP ROLE OE_CUST;
5.  Drop the user accounts.
        DROP USER SKING;
        DROP USER AERRAZURIZ;
        DROP USER GCAMBRAULT;
        DROP USER JRUSSELL;
        DROP USER EZLOTKEY;

**Parent topic:** Tutorial: Configuring Groups in Oracle Label Security
