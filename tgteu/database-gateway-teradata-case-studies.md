The following case studies for Teradata demonstrate some of the features of the Oracle Database Gateway. You can verify that the gateway is installed and operating correctly by using the demonstration files included on the distribution media.

The demonstration files are automatically copied to disk when the gateway is installed.

Topics:

- Case Descriptions

- Installation Media Contents

- Demonstration Files

- Demonstration Requirements

- Creating Demonstration Tables

- Case 1: Simple Queries

- Case 2: A More Complex Query

- Case 3: Joining Teradata Tables

- Case 4: Write Capabilities

- Case 5: Data Dictionary Query

- Case 6: The Pass-Through Feature

### Case Descriptions

The cases illustrate:

- A simple query (Case 1)

- A more complex query (Case 2)

- Joining Teradata tables (Case 3)

- Write capabilities (Case 4)

- A data dictionary query (Case 5)

- The pass-through feature (Case 6)

### Installation Media Contents

The distribution media contains the following:

- Demonstration files.

- One SQL script file that creates the demonstration tables in the Teradata database.

- One SQL script file that drops the demonstration tables from the Teradata database.

### Demonstration Files

After a successful gateway installation, use the demonstration files stored in the directory `$ORACLE_HOME/dg4tera/demo` where `$ORACLE_HOME` is the directory under which the gateway is installed. The directory contains the following demonstration files:

- `bldtera.sql`

- `case1.sql`

- `case2.sql`

- `case3.sql`

- `case4a.sql`

- `case4b.sql`

- `case4c.sql`

- `case5.sql`

- `case6a.sql`

- `case6b.sql`

- `droptera.sql`

### Demonstration Requirements

The case studies assume these requirements have been met:

- The gateway demonstration tables are installed in the Teradata database.

- The Oracle database has an account named `SCOTT` with a password of `TIGER`.

- The Oracle database has a database link called `GTWLINK` (set up as public or private to the user `SCOTT`) that connects the gateway to a Teradata database as `SCOTT` with password `TIGER2`.

  For example, you can create the database link as follows:

      SQL> CREATE DATABASE LINK GTWLINK CONNECT TO SCOTT
        2    IDENTIFIED BY TIGER2 USING 'GTWSID';

- Oracle Net Services is configured correctly and running.

### Creating Demonstration Tables

The case studies are based on the `GTW_EMP`, `GTW_DEPT`, and `GTW_SALGRADE` tables. If the demonstration tables have not been created in the Teradata database, use the `bldtera.sql` script to create them.

The script creates the demonstration tables in the Teradata database accordingly:

    CREATE TABLE GTW_EMP (
    EMPNO      SMALLINT NOT NULL
    ENAME      VARCHAR(10),
    JOB        VARCHAR(9),
    MGR        SMALLINT,
    HIREDATE   DATETIME,
    SAL        NUMERIC(7,2),
    COMM       NUMERIC(7,2),
    DEPTNO     SMALLINT)
    CREATE TABLE GTW_DEPT (
    DEPTNO     SMALLINT NOT NULL,
    DNAME      VARCHAR(14),
    LOC        VARCHAR(13))
    CREATE TABLE GTW_SALGRADE (
    GRADE      REAL,
    LOSAL      NUMERIC(9,4),
    HISAL      NUMERIC(9,4))

#### Demonstration Table Definitions

The table definitions are listed here using information retrieved by the SQL\*PLUS `DESCRIBE` command:

GTW_EMP

    Name                            Null?    Type
    ------------------------------- -------- ----
    EMPNO                           NOT NULL NUMBER(5)
    ENAME                                    VARCHAR2(10)
    JOB                                      VARCHAR2(9)
    MGR                                      NUMBER(5)
    HIREDATE                                 DATE
    SAL                                      NUMBER(7,2)
    COMM                                     NUMBER(7,2)
    DEPTNO                                   NUMBER(5)

GTW_DEPT

    Name                            Null?    Type
    ------------------------------- -------- ----
    DEPTNO                          NOT NULL NUMBER(5)
    DNAME                                    VARCHAR2(14)
    LOC                                      VARCHAR2(13)

GTW_SALGRADE

    Name                            Null?    Type
    ------------------------------- -------- ----
    GRADE                                    FLOAT(53)
    LOSAL                                    NUMBER(9,4)
    HISAL                                    NUMBER(9,4)

#### Demonstration Table Contents

The contents of the Teradata tables are:

GTW_EMP

    EMPNO ENAME   JOB         MGR   HIREDATE   SAL   COMM   DEPTNO
    ----- -----   ---         ---   --------   ---   ----   ------
    7369  SMITH   CLERK       7902  17-DEC-80   800             20
    7499  ALLEN   SALESMAN    7698  20-FEB-81  1600   300       30
    7521  WARD    SALESMAN    7698  22-FEB-81  1250   500       30
    7566  JONES   MANAGER     7839  02-APR-81  2975             20
    7654  MARTIN  SALESMAN    7698  28-SEP-81  1250  1400       30
    7698  BLAKE   MANAGER     7839  01-MAY-81  2850             30
    7782  CLARK   MANAGER     7839  09-JUN-81  2450             10
    7788  SCOTT   ANALYST     7566  09-DEC-82  3000             20
    7839  KING    PRESIDENT         17-NOV-81  5000             10
    7844  TURNER  SALESMAN    7698  08-SEP-81  1500     0       30
    7876  ADAMS   CLERK       7788  12-JAN-83  1100             20
    7900  JAMES   CLERK       7698  03-DEC-81   950             30
    7902  FORD    ANALYST     7566  03-DEC-81  3000             20
    7934  MILLER  CLERK       7782  23-JAN-82  1300             10

GTW_DEPT

    DEPTNO DNAME          LOC
    ----- -------------- --------
       10 ACCOUNTING     NEW YORK
       20 RESEARCH       DALLAS
       30 SALES          CHICAGO
       40 OPERATIONS     BOSTON

GTW_SALGRADE

    GRADE      LOSAL      HISAL
    ------     ------     -----
        1        700      1200
        2       1201      1400
        3       1401      2000
        4       2001      3000
        5       3001      9999

### Case 1: Simple Queries

Case 1 demonstrates the following:

- A simple query.

- A simple query retrieving full date information.

The first query retrieves all the data from `GTW_DEPT` and confirms that the gateway is working correctly.

### Case 2: A More Complex Query

Case 2 demonstrates the following:

- The functions `SUM(``expression``)` and `NVL(``expr1, expr2``) `in the `SELECT` list.

- The `GROUP BY` and `HAVING` clauses.

This query retrieves the departments from `GTW_EMP` whose total monthly expenses are higher than `$10,000`.

### Case 3: Joining Teradata Tables

Case 3 demonstrates the following:

- Joins between Teradata tables.

- Subselects.

The query retrieves information from three Teradata tables and relates the employees to their department name and salary grade, but only for those employees earning more than the average salary.

### Case 4: Write Capabilities

Case 4 is split into three cases and demonstrates the following:

- DELETE Statement

- UPDATE Statement

- INSERT Statement

#### DELETE Statement

Case 4a demonstrates bind values and subselect. All employees in department `20` and one employee, `WARD`, in department `30` are deleted.

#### UPDATE Statement

Case 4b provides an example of a simple `UPDATE` statement. In this example, employees are given a `$100` a month salary increase.

#### INSERT Statement

Case 4c is an example of a simple insert statement that does not provide information for all columns.

### Case 5: Data Dictionary Query

Case 5 demonstrates data dictionary mapping. It retrieves all the tables and views that exist in the Teradata database that begin with "`GTW`".

### Case 6: The Pass-Through Feature

Case 6 demonstrates the gateway pass-through feature that allows an application to send commands or statements to Teradata.

This case demonstrates:

- A pass-through `UPDATE` statement using bind variables.

- A pass-through `SELECT` statement.

#### UPDATE Statement

Case 6a provides an example of a pass-through `UPDATE` statement with bind variables. In this example, the salary for `EMPNO` `7934` is set to `4000`.

#### SELECT Statement

Case 6b provides an example of a pass-through `SELECT` statement. The data that is returned from the `SELECT` statement is inserted into a local table at the Oracle database.
