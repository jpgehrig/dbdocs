The following case studies for Sybase demonstrate some of the features of the Oracle Database Gateway. You can verify that the gateway is installed and operating correctly by using the demonstration files included on the distribution media.

The demonstration files are automatically copied to disk when the gateway is installed.

Topics:

- Case Descriptions

- Distribution Media Contents

- Accessing the Demonstration Files

- Demonstration Requirements

- Creating Demonstration Tables

- Case 1: Simple Queries

- Case 2: A More Complex Query

- Case 3: Joining Sybase Tables

- Case 4: Write Capabilities

- Case 5: Data Dictionary Query

- Case 6: The Pass-Through Feature

- Case 7: Executing Stored Procedures

### 3.1 Case Descriptions

The cases illustrate:

- A simple query (Case 1)

- A more complex query (Case 2)

- Joining Sybase tables (Case 3)

- Write capabilities (Case 4)

- A data dictionary query (Case 5)

- The pass-through feature (Case 6)

- Executing stored procedures (Case 7)

### 3.2 Distribution Media Contents

The distribution media contains the following:

- Demonstration files

- One SQL script file that creates the demonstration tables and stored procedures in the Sybase database

- One SQL script file that drops the demonstration tables and stored procedures from the Sybase database

### 3.3 Accessing the Demonstration Files

After a successful gateway installation, use the demonstration files stored in the directory `$ORACLE_HOME/dg4sybs/demo,` where `$ORACLE_HOME `is the directory under which the gateway is installed. The directory contains the following demonstration files:

| Demonstration Files | Demonstration Files |
|:--------------------|:--------------------|
| `bldsybs.sql`       | `case4c.sql`        |
| `case1.sql`         | `case5.sql`         |
| `case2.sql`         | `case6a.sql`        |
| `case3.sql`         | `case6b.sql`        |
| `case4a.sql`        | `case7.sql`         |
| `case4b.sql`        | `dropsybs.sql`      |

### 3.4 Demonstration Requirements

The case studies assume these requirements have been met:

- The gateway demonstration tables and stored procedures are installed in the Sybase database

- The Oracle database has an account named `SCOTT` with a password of `TIGER`

- The Oracle database has a database link called `GTWLINK` (set up as public or private to the user `SCOTT`) that connects the gateway to a Sybase database as `SCOTT` with password `TIGER2`.

  For example, you can create the database link as follows:

      SQL> CREATE DATABASE LINK GTWLINK CONNECT TO SCOTT
        2    IDENTIFIED BY TIGER2 USING 'GTWSID';

- Oracle Net Services is configured correctly and running

- The Sybase environment variable, `SYBASE`, is set correctly

### 3.5 Creating Demonstration Tables

The case studies are based on the `GTW_EMP`, `GTW_DEPT`, and `GTW_SALGRADE` tables and the stored procedures `InsertDept` and `GetDept`. If the demonstration tables and stored procedures have not been created in the Sybase database, use the `bldsybs.sql` script to create them. Enter the following:

    $ isql -USCOTT -PTIGER2 -ibldsybs.sql

The script creates the demonstration tables and stored procedures in the Sybase database accordingly:

    CREATE TABLE GTW_EMP (
    EMPNO      SMALLINT NOT NULL
    ENAME      VARCHAR(10),
    JOB        VARCHAR(9),
    MGR        SMALLINT,
    HIREDATE   DATETIME,
    SAL        NUMERIC(7,2),
    COMM       NUMERIC(7,2),
    DEPTNO     SMALLINT)
    go

    CREATE TABLE GTW_DEPT (
    DEPTNO     SMALLINT NOT NULL,
    DNAME      VARCHAR(14),
    LOC        VARCHAR(13))
    go

    CREATE TABLE GTW_SALGRADE (
    GRADE      MONEY,
    LOSAL      NUMERIC(9,4),
    HISAL      NUMERIC(9,4))
    go

    SET CHAINED ON
    go

    DROP PROCEDURE InsertDept
    go

    CREATE PROCEDURE InsertDept (@dno INTEGER,
       @dname VARCHAR(14), @loc VARCHAR(13))
    AS INSERT INTO GTW_DEPT VALUES (@dno, @dname, @loc)
    go

    DROP PROCEDURE GetDept
    go

    CREATE PROCEDURE GetDept (@dno INTEGER, @dname VARCHAR(14) OUTPUT)
    AS SELECT @dname=DNAME FROM GTW_DEPT WHERE DEPTNO=@dno
    go

#### 3.5.1 Demonstration Table Definitions

The table definitions are listed in the following table using information retrieved by the SQL\*PLUS `DESCRIBE` command:

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
    GRADE                                    NUMBER(19,4)
    LOSAL                                    NUMBER(9,4)
    HISAL                                    NUMBER(9,4)

#### 3.5.2 Demonstration Table Contents

The contents of the Sybase tables are:

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

### 3.6 Case 1: Simple Queries

Case 1 demonstrates the following:

- A simple query

- A simple query retrieving full date information

The first query retrieves all the data from `GTW_DEPT` and confirms that the gateway is working correctly. The second query retrieves all the data from `GTW_EMP` including the time portion of the hire date because the default date format was set to `DD-MON-YY HH24:MM:SS` for the session by an `ALTER SESSION` command.

### 3.7 Case 2: A More Complex Query

Case 2 demonstrates the following:

- The functions `SUM(``expression``)` and `NVL(``expr1, expr2``)` in the `SELECT` list

- The `GROUP BY` and `HAVING` clauses

This query retrieves the departments from `GTW_EMP` whose total monthly expenses are higher than `$10,000`.

### 3.8 Case 3: Joining Sybase Tables

Case 3 demonstrates the following:

- Joins between Sybase tables

- Subselects

The query retrieves information from three Sybase tables and relates the employees to their department name and salary grade, but only for those employees earning more than the average salary.

### 3.9 Case 4: Write Capabilities

Case 4 is split into three cases and demonstrates the following:

- DELETE Statement

- UPDATE Statement

- INSERT Statement

#### 3.9.1 DELETE Statement

Case 4a demonstrates bind values and subselect. All employees in department `20` and one employee, `WARD`, in department `30` are deleted.

#### 3.9.2 UPDATE Statement

Case 4b provides an example of a simple `UPDATE` statement. In this example, employees are given a `$100` a month salary increase.

#### 3.9.3 INSERT Statement

Case 4c is an example of a simple insert statement that does not provide information for all columns.

### 3.10 Case 5: Data Dictionary Query

Case 5 demonstrates data dictionary mapping. It retrieves all the tables and views that exist in the Sybase database that begin with "`GTW`".

### 3.11 Case 6: The Pass-Through Feature

Case 6 demonstrates the gateway pass-through feature that allows an application to send commands or statements to Sybase.

This case demonstrates:

- A pass-through `UPDATE` statement using bind variables

- A pass-through `SELECT` statement

#### 3.11.1 UPDATE Statement

Case 6a provides an example of a pass-through `UPDATE` statement with bind variables. In this example, the salary for `EMPNO 7934` is set to `4000`.

#### 3.11.2 SELECT Statement

Case 6b provides an example of a pass-through `SELECT` statement. The data that is returned from the `SELECT` statement is inserted into a local table at the Oracle database.

### 3.12 Case 7: Executing Stored Procedures

Case 7 demonstrates the gateway executing a stored procedure in the Sybase database.

Before running the script, make sure that chained mode is set on, by issuing the following command in Sybase:

    set chained on
