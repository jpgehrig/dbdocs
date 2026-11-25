You can control the validity and visibility of data in Oracle Database with In-Database Archiving and Temporal Validity.

This section contains the following topics:

- Using In-Database Archiving

- Using Temporal Validity

- Creating a Table With Temporal Validity

- Limitations and Restrictions With In-Database Archiving and Temporal Validity

### 5.3.1 Using In-Database Archiving

In-Database Archiving enables you to archive rows within a table by marking them as inactive.

These inactive rows are in the database and can be optimized using compression, but are not visible to an application. The data in these rows is available for compliance purposes if needed by setting a session parameter.

With In-Database Archiving you can store more data for a longer period of time within a single database, without compromising application performance. Archived data can be compressed to help improve backup performance, and updates to archived data can be deferred during application upgrades to improve the performance of upgrades.

To manage In-Database Archiving for a table, you must enable `ROW` `ARCHIVAL` for the table and manipulate the `ORA_ARCHIVE_STATE` hidden column of the table. Optionally, you specify either `ACTIVE` or `ALL` for the `ROW` `ARCHIVAL` `VISIBILITY` session parameter.

For example, you can use the SQL statements similar to those in Example 5-10 to hide or show rows in a table. The purpose is to display only active data in most situations, but to maintain all data in case it is needed in specific situations.

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for information about using SQL statements to manage In-Database Archiving features

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_ILM.md) for information about the `ARCHIVESTATENAME` function in the `DBMS_ILM` package

**Live SQL:**

View and run a related example on Oracle Live SQL at [Oracle Live SQL: Using In-Database Archiving Example](https://livesql.oracle.com/apex/livesql/docs/vldbg/indbarchive/indatabase-archiving-example.html).

Example 5-10 Using In-Database Archiving

    /* Set visibility to ACTIVE to display only active rows of a table.*/
    ALTER SESSION SET ROW ARCHIVAL VISIBILITY = ACTIVE;

    CREATE TABLE employees_indbarch
     (employee_id NUMBER(6) NOT NULL,
      first_name VARCHAR2(20), last_name VARCHAR2(25) NOT NULL,
      email VARCHAR2(25) NOT NULL, phone_number VARCHAR2(20),
      hire_date DATE NOT NULL, job_id VARCHAR2(10) NOT NULL, salary  NUMBER(8,2),
      commission_pct NUMBER(2,2), manager_id NUMBER(6), department_id NUMBER(4)) ROW ARCHIVAL;

    /* Show all the columns in the table, including hidden columns */
    SELECT SUBSTR(COLUMN_NAME,1,22) NAME, SUBSTR(DATA_TYPE,1,20) DATA_TYPE, COLUMN_ID AS COL_ID,
      SEGMENT_COLUMN_ID AS SEG_COL_ID, INTERNAL_COLUMN_ID AS INT_COL_ID, HIDDEN_COLUMN, CHAR_LENGTH
      FROM USER_TAB_COLS WHERE TABLE_NAME='EMPLOYEES_INDBARCH';

    NAME                   DATA_TYPE                COL_ID SEG_COL_ID INT_COL_ID HID CHAR_LENGTH
    ---------------------- -------------------- ---------- ---------- ---------- --- -----------
    ORA_ARCHIVE_STATE      VARCHAR2                                 1          1 YES        4000
    EMPLOYEE_ID            NUMBER                        1          2          2 NO            0
    FIRST_NAME             VARCHAR2                      2          3          3 NO           20
    LAST_NAME              VARCHAR2                      3          4          4 NO           25
    EMAIL                  VARCHAR2                      4          5          5 NO           25
    PHONE_NUMBER           VARCHAR2                      5          6          6 NO           20
    HIRE_DATE              DATE                          6          7          7 NO            0
    JOB_ID                 VARCHAR2                      7          8          8 NO           10
    SALARY                 NUMBER                        8          9          9 NO            0
    COMMISSION_PCT         NUMBER                        9         10         10 NO            0
    MANAGER_ID             NUMBER                       10         11         11 NO            0
    DEPARTMENT_ID          NUMBER                       11         12         12 NO            0

    /* Insert some data into the table */
    INSERT INTO employees_indbarch(employee_id, first_name, last_name, email,
      hire_date, job_id, salary, manager_id, department_id)
      VALUES (251, 'Scott', 'Tiger', 'scott.tiger@example.com', '21-MAY-2009',
     'IT_PROG', 50000, 103, 60);

    INSERT INTO employees_indbarch(employee_id, first_name, last_name, email,
      hire_date, job_id, salary, manager_id, department_id)
      VALUES (252, 'Jane', 'Lion', 'jane.lion@example.com', '11-JUN-2009',
      'IT_PROG', 50000, 103, 60);

    /* Decrease the ORA_ARCHIVE_STATE column size to improve formatting in queries */
    COLUMN ORA_ARCHIVE_STATE FORMAT a18;

    /* The default value for ORA_ARCHIVE_STATE is '0', which means active */
    SELECT employee_id, ORA_ARCHIVE_STATE FROM employees_indbarch;

    EMPLOYEE_ID ORA_ARCHIVE_STATE
    ----------- ------------------
            251 0
            252 0

    /* Insert a value into ORA_ARCHIVE_STATE to set the record to inactive status*/
    UPDATE employees_indbarch SET ORA_ARCHIVE_STATE = '1' WHERE employee_id = 252;

    /* Only active records are in the following query */
    SELECT employee_id, ORA_ARCHIVE_STATE FROM employees_indbarch;

    EMPLOYEE_ID ORA_ARCHIVE_STATE
    ----------- ------------------
            251 0

    /* Set visibility to ALL to display all records */
    ALTER SESSION SET ROW ARCHIVAL VISIBILITY = ALL;

    SELECT employee_id, ORA_ARCHIVE_STATE FROM employees_indbarch;

    EMPLOYEE_ID ORA_ARCHIVE_STATE
    ----------- ------------------
            251 0
            252 1

### 5.3.2 Using Temporal Validity

Temporal Validity enables you to track time periods for real world validity. Valid times can be set by users and applications for data, and data can be selected by a specified valid time, or a valid time range.

Applications often note the validity (or effectivity) of a fact recorded in a database with dates or timestamps that are relevant to the management of a business. For example, the hire-date of an employee in a human resources (HR) application, which determines the effective date of coverage in the insurance industry, is a valid date. This date is in contrast to the date or time at which the employee record was entered in the database. The former temporal attribute (hire-date) is called the valid time (VT) while the latter (date entered into the database) is called the transaction time (TT). While the valid time is usually controlled by the user, the transaction-time is system-managed.

For ILM, the valid time attributes can signify when a fact is valid in the business world and when it is not. Using valid time attributes, a query could just show rows that are currently valid, while not showing rows that contains facts that are not currently valid, such as a closed order or a future hire.

Concepts that are integral to valid time temporal modeling include:

- Valid time

  This is a user-defined representation of time. Examples of a valid time include project start and finish dates, and employee hire and termination dates.

- Tables with valid-time semantics

  These tables have one or more dimensions of user-defined time, each of which has a start and an end.

- Valid-time flashback queries

  This is the ability to do as-of and versions queries using a valid-time dimension.

A valid-time period consists of two date-time columns specified in the table definition. You can add a valid-time period by explicitly adding columns, or the columns can be created automatically. A valid-time period can be added during the create table or alter table process.

To support session level visibility control for temporal table queries, the `DBMS_FLASHBACK_ARCHIVE` PL/SQL package provides the `ENABLE_AT_VALID_TIME` procedure. To execute the procedure, you need the required system and object privileges.

The following PL/SQL procedure sets the valid time visibility as of the given time.

    SQL> EXECUTE DBMS_FLASHBACK_ARCHIVE.enable_at_valid_time
              ('ASOF', '31-DEC-12 12.00.01 PM');

The following PL/SQL procedure sets the visibility of temporal data to currently valid data within the valid time period at the session level.

    SQL> EXECUTE DBMS_FLASHBACK_ARCHIVE.enable_at_valid_time('CURRENT');

The following procedure sets the visibility of temporal data to the full table, which is the default temporal table visibility.

    SQL> EXECUTE DBMS_FLASHBACK_ARCHIVE.enable_at_valid_time('ALL');

**See Also:**

- [Oracle Database Development Guide](../adfns/design_basics.md) for information about Oracle Temporal

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_FLASHBACK_ARCHIVE.md) for information about the `DBMS_FLASHBACK_ARCHIVE` package

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for information about using the `CREATE` `TABLE` or `ALTER` `TABLE` to initiate valid-time temporal modeling

- [Oracle Database Reference](../refrn/about-static-data-dictionary-views.md) for information about views used to monitor table information

### 5.3.3 Creating a Table With Temporal Validity

The example in this topic shows how to create a table with temporal validity.

Example 5-11 shows the use of temporal validity.

**Live SQL:**

View and run a related example on Oracle Live SQL at [Oracle Live SQL: Creating a Table with Temporal Validity](https://livesql.oracle.com/apex/livesql/docs/vldbg/temporalvalid/temporal-validity-example.html).

Example 5-11 Creating a table with temporal validity

    /* Create a time with an employee tracking timestamp */
    /* using the specified columns*/
    CREATE TABLE employees_temp (
           employee_id NUMBER(6) NOT NULL, first_name VARCHAR2(20), last_name VARCHAR2(25) NOT NULL,
           email VARCHAR2(25) NOT NULL, phone_number VARCHAR2(20), hire_date DATE NOT NULL,
           job_id VARCHAR2(10) NOT NULL, salary  NUMBER(8,2), commission_pct NUMBER(2,2),
           manager_id NUMBER(6), department_id NUMBER(4),
           PERIOD FOR emp_track_time);

    DESCRIBE employees_temp

     Name                                                    Null?    Type
     ------------------------------------------------------- -------- ---------------
     EMPLOYEE_ID                                             NOT NULL NUMBER(6)
     FIRST_NAME                                                       VARCHAR2(20)
     LAST_NAME                                               NOT NULL VARCHAR2(25)
     EMAIL                                                   NOT NULL VARCHAR2(25)
     PHONE_NUMBER                                                     VARCHAR2(20)
     HIRE_DATE                                               NOT NULL DATE
     JOB_ID                                                  NOT NULL VARCHAR2(10)
     SALARY                                                           NUMBER(8,2)
     COMMISSION_PCT                                                   NUMBER(2,2)
     MANAGER_ID                                                       NUMBER(6)
     DEPARTMENT_ID                                                    NUMBER(4)

    SQL> SELECT SUBSTR(COLUMN_NAME,1,22) NAME, SUBSTR(DATA_TYPE,1,28) DATA_TYPE, COLUMN_ID AS COL_ID,
         SEGMENT_COLUMN_ID AS SEG_COL_ID, INTERNAL_COLUMN_ID AS INT_COL_ID, HIDDEN_COLUMN
         FROM USER_TAB_COLS WHERE TABLE_NAME='EMPLOYEES_TEMP';

    NAME                   DATA_TYPE                    COL_ID SEG_COL_ID INT_COL_ID HID
    ---------------------- ---------------------------- ------ ---------- ---------- ---
    EMP_TRACK_TIME_START   TIMESTAMP(6) WITH TIME ZONE                  1          1 YES
    EMP_TRACK_TIME_END     TIMESTAMP(6) WITH TIME ZONE                  2          2 YES
    EMP_TRACK_TIME         NUMBER                                                  3 YES
    EMPLOYEE_ID            NUMBER                            1          3          4 NO
    FIRST_NAME             VARCHAR2                          2          4          5 NO
    LAST_NAME              VARCHAR2                          3          5          6 NO
    EMAIL                  VARCHAR2                          4          6          7 NO
    PHONE_NUMBER           VARCHAR2                          5          7          8 NO
    HIRE_DATE              DATE                              6          8          9 NO
    JOB_ID                 VARCHAR2                          7          9         10 NO
    SALARY                 NUMBER                            8         10         11 NO
    COMMISSION_PCT         NUMBER                            9         11         12 NO
    MANAGER_ID             NUMBER                           10         12         13 NO
    DEPARTMENT_ID          NUMBER                           11         13         14 NO

    /* Insert/update/delete with specified values for time columns */
    INSERT INTO employees_temp(emp_track_time_start, emp_track_time_end, employee_id, first_name,
       last_name, email, hire_date, job_id, salary, manager_id, department_id)
       VALUES (TIMESTAMP '2009-06-01 12:00:01 Europe/Paris',
               TIMESTAMP '2012-11-30 12:00:01 Europe/Paris', 251, 'Scott', 'Tiger',
              'scott.tiger@example.com', DATE '2009-05-21', 'IT_PROG', 50000, 103, 60);

    INSERT INTO employees_temp(emp_track_time_start, emp_track_time_end, employee_id, first_name,
         last_name, email, hire_date, job_id, salary, manager_id, department_id)
         VALUES (TIMESTAMP '2009-06-01 12:00:01 Europe/Paris',
                 TIMESTAMP '2012-12-31 12:00:01 Europe/Paris', 252, 'Jane', 'Lion',
                 'jane.lion@example.com', DATE '2009-06-11', 'IT_PROG', 50000, 103, 60);

    UPDATE employees_temp set salary = salary + salary * .05
           WHERE emp_track_time_start <= TIMESTAMP '2009-06-01 12:00:01 Europe/Paris';

    SELECT employee_id, SALARY FROM employees_temp;

    EMPLOYEE_ID     SALARY
    ----------- ----------
            251      52500
            252      52500

    /* No rows are deleted for the following statement because no records */
    /* are in the specified track time. */
    DELETE employees_temp WHERE emp_track_time_end < TIMESTAMP '2001-12-31 12:00:01 Europe/Paris';

    0 rows deleted.

    /* Show rows that are in a specified time period */
    SELECT employee_id FROM employees_temp
           WHERE emp_track_time_start > TIMESTAMP '2009-05-31 12:00:01 Europe/Paris' AND
                 emp_track_time_end < TIMESTAMP '2012-12-01 12:00:01 Europe/Paris';

    EMPLOYEE_ID
    -----------
            251

    /* Show rows that are in a specified time period */
    SELECT employee_id FROM employees_temp AS OF PERIOD FOR
           emp_track_time TIMESTAMP '2012-12-01 12:00:01 Europe/Paris';

    EMPLOYEE_ID
    -----------
            252

### 5.3.4 Limitations and Restrictions With In-Database Archiving and Temporal Validity

This topic lists the limitations and restrictions associated with In-Database Archiving and Temporal Validity.

The limitations and restrictions include:

- ILM is not supported with OLTP table compression for Temporal Validity. Segment-level ILM and compression is supported if partitioned on the end-time columns.

- ILM is not supported with OLTP table compression for in-database archiving. Segment-level ILM and compression is supported if partitioned on the `ORA_ARCHIVE_STATE` column.
