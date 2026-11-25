Although you cannot directly access remote tables as object tables, object views let you access remote tables as if they were object tables.

Consider a company with two branches; one in Washington D.C. and another in Chicago. Each site has an employee table. The headquarters in Washington has a department table with a list of all the departments. To get a total view of the entire organization, you can create views over the individual remote tables and then a overall view of the organization.

To this requires the following:

- Update the entry in `listener.ora`, such as: `(ADDRESS=(PROTOCOL=tcp)` `(HOST=stadv07.us.example.com)(PORT=1640))`

- Add entries to `tnsnames.ora`, such as: `chicago=(DESCRIPTION= (ADDRESS=(PROTOCOL=ipc)(KEY=linux)) (CONNECT_DATA=(SERVICE_NAME=linux.regress.rdbms.dev.us.example.com)))`

- Provide `CREATE` `DATABASE` `LINK` code as shown in Example 6-9

Example 6-9 begins by creating an object view for each employee table and then creates the global view.

Example 6-9 Creating an Object View to Access Remote Tables

    -- Requires Ex. 6-2, Ex. 6-4, and Ex. 6-6
    -- Example requires DB links, such as these, modify for your use and uncomment
    -- CREATE DATABASE LINK chicago CONNECT TO hr IDENTIFIED BY hr USING 'inst1';
    -- CREATE DATABASE LINK washington CONNECT TO hr IDENTIFIED BY hr USING 'inst1';
    CREATE VIEW emp_washington_view (eno, ename, salary, job)
       AS SELECT e.empno, e.empname, e.salary, e.job
              FROM emp@washington e;

    CREATE VIEW emp_chicago_view (eno, ename, salary, job)
       AS SELECT e.empno, e.empname, e.salary, e.job
              FROM emp@chicago e;

    CREATE VIEW orgnzn_view OF dept_t WITH OBJECT IDENTIFIER (deptno)
        AS SELECT d.deptno, d.deptname,
              address_t(d.deptstreet,d.deptcity,d.deptstate,d.deptzip) AS deptaddr,
              CAST( MULTISET (
                          SELECT e.eno, e.ename, e.salary, e.job
                          FROM emp_washington_view e)
                       AS employee_list_t) AS emp_list
           FROM dept d
           WHERE d.deptcity = 'Washington'
       UNION ALL
           SELECT d.deptno, d.deptname,
               address_t(d.deptstreet,d.deptcity,d.deptstate,d.deptzip) AS deptaddr,
                  CAST( MULTISET (
                           SELECT e.eno, e.ename, e.salary, e.job
                           FROM emp_chicago_view e)
                        AS employee_list_t) AS emp_list
           FROM dept d
           WHERE d.deptcity = 'Chicago';

This view has a list of all employees for each department. The `UNION` `ALL` clause is used because employees cannot work in more than one department.
