Collections, both nested tables and `VARRAY`s, can be columns in views. You can select these collections from underlying collection columns or you can synthesize them using subqueries. The `CAST-MULTISET` operator provides a way of synthesizing such collections.

This section contains the following topics:

- Single-Level Collections in Object Views

- Multilevel Collections in Object Views

### 6.6.1 Single-Level Collections in Object Views

You can create an object view with a single level connection.

Using [Example 6-1](defining-object-views.md) and [Example 6-2](objects-nested-in-object-views.md) as starting points, each employee in an `emp` relational table has the structure in Example 6-4. Using this relational table, you can construct a `dept_view` with the department number, name, address and a collection of employees belonging to the department.

First, define a nested table type for the employee type `employee_t`. Next, define a department type with a department number, name, address, and a nested table of employees. Finally, define the object view `dept_view`.

The `SELECT` subquery inside the `CAST-MULTISET` block selects the list of employees that belong to the current department. The `MULTISET` keyword indicates that this is a list as opposed to a singleton value. The `CAST` operator casts the result set into the appropriate type, in this case to the `employee_list_t` nested table type.

A query on this view could provide the list of departments, with each department row containing the department number, name, the address object and a collection of employees belonging to the department.

Example 6-4 Creating a View with a Single-Level Collection

    -- Requires Ex. 6-1 and Ex. 6-2
    CREATE TABLE emp (
       empno    NUMBER PRIMARY KEY,
       empname  VARCHAR2(20),
       salary   NUMBER,
       job      VARCHAR2 (20),
       deptno   NUMBER REFERENCES dept(deptno));

    CREATE TYPE employee_list_t AS TABLE OF employee_t;  -- nested table
    /
    CREATE TYPE dept_t AS OBJECT (
        deptno     NUMBER,
        deptname   VARCHAR2(20),
        address    address_t,
        emp_list   employee_list_t);
    /
    CREATE VIEW dept_view OF dept_t WITH OBJECT IDENTIFIER (deptno) AS
        SELECT d.deptno, d.deptname,
         address_t(d.deptstreet,d.deptcity,d.deptstate,d.deptzip) AS deptaddr,
                 CAST( MULTISET (
                               SELECT e.empno, e.empname, e.salary, e.job
                               FROM emp e
                               WHERE e.deptno = d.deptno)
                            AS employee_list_t)
                       AS emp_list
       FROM dept d;

    insert into dept values(100,'ST','400 Oracle Pkwy','Redwood S','CA',94065);
    insert into dept values(200,'Sales','500 Oracle Pkwy','Redwood S','CA',94065);
    insert into emp values(1,'John',900,'Developer1',100);

    insert into emp values(2,'Robert',1000,'Developer2',100);
    insert into emp values(3,'Mary', 1000,'Apps1',200);
    insert into emp values(4,'Maria',1500,'Developer3',200);
    select * from dept_view where deptno = 100;

        DEPTNO DEPTNAME
    ---------- --------------------
    ADDRESS(STREET, CITY, STATE, ZIP)
    --------------------------------------------------------------------------------
    EMP_LIST(EMPNO, ENAME, SALARY, JOB)
    --------------------------------------------------------------------------------
           100 ST
    ADDRESS_T('400 Oracle Pkwy', 'Redwood S', 'CA', '94065')
    EMPLOYEE_LIST_T(EMPLOYEE_T(1, 'John', 900, 'Developer1'), EMPLOYEE_T(2, 'Robert'
    , 1000, 'Developer2'))


    select emp_list from dept_view where deptno = 100;

    EMP_LIST(EMPNO, ENAME, SALARY, JOB)
    --------------------------------------------------------------------------------
    EMPLOYEE_LIST_T(EMPLOYEE_T(1, 'John', 900, 'Developer1'), EMPLOYEE_T(2, 'Robert'
    , 1000, 'Developer2'))

### 6.6.2 Multilevel Collections in Object Views

You can create to view and query objects.

Multilevel collections and single-level collections are created and used in object views in the same way. The only difference is that, for a multilevel collection, you must create an additional level of collections.

Example 6-5 builds an object view containing a multilevel collection. The view is based on flat relational tables that contain no collections. As a preliminary to building the object view, the example creates the object and collection types it uses. An object type (for example, `emp_t`) is defined to correspond to each relational table, with attributes whose types correspond to the types of the respective table columns. In addition, the employee type has a nested table (attribute) of projects, and the department type has a nested table (attribute) of employees. The latter nested table is a multilevel collection. The `CAST-MULTISET` operator is used in the `CREATE` `VIEW` statement to build the collections.

Example 6-5 Creating a View with Multilevel Collections

    CREATE TABLE depts
      ( deptno     NUMBER,
        deptname   VARCHAR2(20));

    CREATE TABLE emps
      ( ename VARCHAR2(20),
        salary     NUMBER,
        deptname   VARCHAR2(20));

    CREATE TABLE projects
      ( projname   VARCHAR2(20),
        mgr        VARCHAR2(20));

    CREATE TYPE project_t AS OBJECT
      ( projname   VARCHAR2(20),
        mgr        VARCHAR2(20));
    /
    CREATE TYPE nt_project_t AS TABLE OF project_t;
    /
    CREATE TYPE emp_t AS OBJECT
    (  ename      VARCHAR2(20),
       salary     NUMBER,
       deptname   VARCHAR2(20),
       projects   nt_project_t );
    /
    CREATE TYPE nt_emp_t AS TABLE OF emp_t;
    /
    CREATE TYPE depts_t AS OBJECT
      ( deptno     NUMBER,
        deptname   VARCHAR2(20),
        emps       nt_emp_t );
    /
    CREATE VIEW v_depts OF depts_t WITH OBJECT IDENTIFIER (deptno) AS
      SELECT d.deptno, d.deptname,
        CAST(MULTISET(SELECT e.ename, e.salary, e.deptname,
            CAST(MULTISET(SELECT p.projname, p.mgr
              FROM projects p
              WHERE p.mgr = e.ename)
            AS nt_project_t)
          FROM emps e
          WHERE e.deptname = d.deptname)
        AS nt_emp_t)
      FROM depts d;
