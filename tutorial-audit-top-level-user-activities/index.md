## Before You Begin

This 15-minute tutorial shows you how to audit top-level user activities in a database without collecting recursive user activity.

### Background

Before Oracle Database 19c, the audit policies records user activities including both directly issued events and recursive SQL statements.

In Oracle Database 19c, auditing can exclude recursive SQL statements. Top-level statements are SQL statements that users directly issue. These statements can be important for both security and compliance. SQL statements run from within PL/SQL procedures or functions are not considered top-level because they may be less relevant for auditing purposes.

### What Do You Need?

- Oracle Database 19c installed
- A database, either non-CDB or CDB with a PDB
- The ` `[`create_proc.sql`](files/create_proc.sql) SQL script. Download the SQL script to the labs directory created on your server `/home/oracle/labs`

------------------------------------------------------------------------

## Create The Table and The Procedure

1.  Execute the Oracle script `$ORACLE_HOME/demo/schema/human_resource/hr_main.sql` that creates the `HR` schema in `PDB1` in the tablespace `USERS`. The password in the command is the password for the `HR` schema.

        sqlplus system@PDB1 @$ORACLE_HOME/demo/schema/human_resources/hr_main.sql password users temp /tmp
        Enter password: password

2.  Query the `HR.EMPLOYEES` table.

        SELECT employee_id, salary FROM hr.employees;

    Read the rows from the `HR.EMPLOYEES` table. Read the result from the ` `[`result1`](files/result1.txt) text file.

3.  Create a procedure that allows the `HR` user to raise the employees’ salaries in `PDB1`.

        @/home/oracle/labs/create_proc.sql

    Read the result from the ` `[`result2`](files/result2.txt) text file.

------------------------------------------------------------------------

## Create and Enable The Audit Policy

1.  Create the security officer. The security officer is the one responsible for managing audit policies.

        CREATE USER auditor_admin IDENTIFIED BY password;

2.  Grant the security officer the `CREATE SESSION` system privilege and the `AUDIT_ADMIN` role.

        GRANT create session, audit_admin TO auditor_admin;

3.  Connect to `PDB1` as auditor_admin.

        CONNECT auditor_admin@PDB1
        Enter password: password

4.  Create an audit policy that audits any salary increase.

        CREATE AUDIT POLICY pol_sal_increase
                            ACTIONS UPDATE ON hr.employees;

5.  Enable the audit policy.

        AUDIT POLICY pol_sal_increase WHENEVER SUCCESSFUL;

------------------------------------------------------------------------

## Audit The User Activities Including Recursive Statements

1.  In another session, session2, connect as `HR` and increase the salary for employee ID 106 through the `RAISE_SALARY` procedure.

        sqlplus hr@PDB1
        Enter password: password

        EXEC emp_admin.raise_salary(106,10)

2.  Still in session2, update the row directly and commit.

        UPDATE hr.employees SET salary=salary*0.1
        WHERE  employee_id = 106;

        COMMIT;

3.  Quit the session.

        EXIT

------------------------------------------------------------------------

## Display the Activities Audited

1.  Verify from session1 that the update actions executed through the PL/SQL procedure and directly by the `UPDATE` command are audited.

        SELECT action_name, object_name, sql_text
             FROM   unified_audit_trail
             WHERE  unified_audit_policies = 'POL_SAL_INCREASE';

    Read the result from the ` `[`result3`](files/result3.txt) text file.

2.  Disable the audit policy.

        NOAUDIT POLICY pol_sal_increase;

3.  Drop the audit policy.

        DROP AUDIT POLICY pol_sal_increase;

------------------------------------------------------------------------

## Audit the Top-Level Statements Only

1.  Create an audit policy that audits any salary increase executed directly with an `UPDATE` command only.

        CREATE AUDIT POLICY pol_sal_increase_direct
                            ACTIONS UPDATE ON hr.employees ONLY TOPLEVEL;

2.  Enable the audit policy.

        AUDIT POLICY pol_sal_increase_direct WHENEVER SUCCESSFUL;

3.  In session2, connect as `HR` to `PDB1`.

        sqlplus hr@PDB1
        Enter password: password

4.  Increase the salary for employee ID 107 through the `RAISE_SALARY` procedure.

        EXEC emp_admin.raise_salary(107,30)

5.  Still in session2, update the row directly and commit.

        UPDATE hr.employees SET salary=salary*0.1
        WHERE  employee_id = 107;

        COMMIT;

6.  Quit the session.

        EXIT

------------------------------------------------------------------------

## Display The Top-Level Activities Audited

1.  Verify from session1 that the update actions executed through the PL/SQL procedure are not audited.

        SELECT action_name, object_name, sql_text FROM unified_audit_trail
        WHERE  unified_audit_policies = 'POL_SAL_INCREASE_DIRECT';

        ACTION_NAME  OBJECT_NAME
        ------------ ------------
        SQL_TEXT
        ---------------------------------------------------------
        UPDATE       EMPLOYEES
        UPDATE hr.employees SET salary=salary*0.1 WHERE employee_id = 107

    Observe that only the direct `UPDATE` statement is audited as this is the purpose of the `ONLY TOPLEVEL` clause of the `CREATE AUDIT POLICY` command.

------------------------------------------------------------------------

## Clean Up the Environment

1.  In session1, disable the audit policy.

        NOAUDIT POLICY pol_sal_increase_direct;

2.  Drop the audit policy.

        DROP AUDIT POLICY pol_sal_increase_direct;

3.  Connect as `SYSTEM` to `PDB1`.

        CONNECT system@PDB1
        Enter password: password

4.  Drop the `HR` schema.

        DROP USER hr CASCADE;

5.  Drop the `auditor_admin` user.

        DROP USER auditor_admin CASCADE;

6.  Quit the session.

        EXIT
