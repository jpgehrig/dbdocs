## 14.10 CREATE PACKAGE BODY Statement

The `CREATE` `PACKAGE` `BODY` statement creates or replaces the body of a stored package, which is an encapsulated collection of related procedures, stored functions, and other program objects stored as a unit in the database.

The package body defines these objects. The package specification, defined in an earlier `CREATE` `PACKAGE` statement, declares these objects.

Packages are an alternative to creating procedures and functions as standalone schema objects.

### Topics

- Prerequisites

- Syntax

- Semantics

- Examples

- Related Topics

### Prerequisites

To create or replace a package in your schema, you must have the `CREATE` `PROCEDURE` system privilege. To create or replace a package in another user's schema, you must have the `CREATE` `ANY` `PROCEDURE` system privilege. In both cases, the package body must be created in the same schema as the package.

To embed a `CREATE` `PACKAGE` `BODY` statement inside an the database precompiler program, you must terminate the statement with the keyword `END-EXEC` followed by the embedded SQL statement terminator for the specific language.

### Syntax

### create_package_body ::=

![Description of create_package_body.eps follows](img/create_package_body.gif)
[Description of the illustration create_package_body.eps](img_text/create_package_body.md)

### plsql_package_body_source ::=

![Description of plsql_package_body_source.eps follows](img/plsql_package_body_source.gif)
[Description of the illustration plsql_package_body_source.eps](img_text/plsql_package_body_source.md)

([sharing_clause ::=](SHARING-clause.md), [declare_section ::=](block.md) )

### initialize_section ::=

![Description of initialize_section.eps follows](img/initialize_section.gif)
[Description of the illustration initialize_section.eps](img_text/initialize_section.md)

( [statement ::=](block.md) , [exception_handler ::=](exception-handler.md) )

### Semantics

### create_package_body

OR REPLACE

Re-creates the package body if it exists, and recompiles it.

Users who were granted privileges on the package body before it was redefined can still access the package without being regranted the privileges.

\[ EDITIONABLE \| NONEDITIONABLE \]

If you do not specify this property, then the package body inherits `EDITIONABLE` or `NONEDITIONABLE` from the package specification. If you do specify this property, then it must match that of the package specification.

IF NOT EXISTS

Creates the package body if it does not already exist. If a package body by the same name does exist, the statement is ignored without error and the original package body remains unchanged.

`IF NOT EXISTS` cannot be used in combination with `OR REPLACE`.

### plsql_package_body_source

schema

Name of the schema containing the package. Default: your schema.

package_name

Name of the package to be created.

declare_section

Has a definition for every cursor and subprogram declaration in the package specification. The headings of corresponding subprogram declarations and definitions must match word for word, except for white space.

Can also declare and define private items that can be referenced only from inside the package.

Restriction on declare_section

`PRAGMA` `AUTONOMOUS_TRANSACTION` cannot appear here.

### initialize_section

Initializes variables and does any other one-time setup steps.

### Examples

Example 14-20 Creating the emp_mgmt Package Body

This statement creates the body of the `emp_mgmt` package created in "[Example 14-19](CREATE-PACKAGE-statement.md)".

    CREATE OR REPLACE PACKAGE BODY emp_mgmt AS
       tot_emps NUMBER;
       tot_depts NUMBER;
    FUNCTION hire
       (last_name VARCHAR2, job_id VARCHAR2,
        manager_id NUMBER, salary NUMBER,
        commission_pct NUMBER, department_id NUMBER)
       RETURN NUMBER IS new_empno NUMBER;
    BEGIN
       SELECT employees_seq.NEXTVAL
          INTO new_empno
          FROM DUAL;
       INSERT INTO employees
          VALUES (new_empno, 'First', 'Last','first.example@example.com',
                  '(415)555-0100',
                  TO_DATE('18-JUN-2002','DD-MON-YYYY'),
                  'IT_PROG',90000000,00, 100,110);
          tot_emps := tot_emps + 1;
       RETURN(new_empno);
    END;
    FUNCTION create_dept(department_id NUMBER, location_id NUMBER)
       RETURN NUMBER IS
          new_deptno NUMBER;
       BEGIN
          SELECT departments_seq.NEXTVAL
             INTO new_deptno
             FROM dual;
          INSERT INTO departments
             VALUES (new_deptno, 'department name', 100, 1700);
          tot_depts := tot_depts + 1;
          RETURN(new_deptno);
       END;
    PROCEDURE remove_emp (employee_id NUMBER) IS
       BEGIN
          DELETE FROM employees
          WHERE employees.employee_id = remove_emp.employee_id;
          tot_emps := tot_emps - 1;
       END;
    PROCEDURE remove_dept(department_id NUMBER) IS
       BEGIN
          DELETE FROM departments
          WHERE departments.department_id = remove_dept.department_id;
          tot_depts := tot_depts - 1;
          SELECT COUNT(*) INTO tot_emps FROM employees;
       END;
    PROCEDURE increase_sal(employee_id NUMBER, salary_incr NUMBER) IS
       curr_sal NUMBER;
       BEGIN
          SELECT salary INTO curr_sal FROM employees
          WHERE employees.employee_id = increase_sal.employee_id;
          IF curr_sal IS NULL
             THEN RAISE no_sal;
          ELSE
             UPDATE employees
             SET salary = salary + salary_incr
             WHERE employee_id = employee_id;
          END IF;
       END;
    PROCEDURE increase_comm(employee_id NUMBER, comm_incr NUMBER) IS
       curr_comm NUMBER;
       BEGIN
          SELECT commission_pct
          INTO curr_comm
          FROM employees
          WHERE employees.employee_id = increase_comm.employee_id;
          IF curr_comm IS NULL
             THEN RAISE no_comm;
          ELSE
             UPDATE employees
             SET commission_pct = commission_pct + comm_incr;
          END IF;
       END;
    END emp_mgmt;

The package body defines the public program objects declared in the package specification:

- The functions `hire` and `create_dept`

- The procedures `remove_emp`, `remove_dept`, `increase_sal`, and `increase_comm`

These objects are declared in the package specification, so they can be called by application programs, procedures, and functions outside the package. For example, if you have access to the package, you can create a procedure `increase_all_comms` separate from the `emp_mgmt` package that invokes the `increase_comm` procedure.

These objects are defined in the package body, so you can change their definitions without causing the database to invalidate dependent schema objects. For example, if you subsequently change the definition of `hire`, then the database need not recompile `increase_all_comms` before running it.

The package body in this example also declares private program objects, the variables `tot_emps` and `tot_depts`. These objects are declared in the package body rather than the package specification, so they are accessible to other objects in the package, but they are not accessible outside the package. For example, you cannot develop an application that explicitly changes the value of the variable `tot_depts`. However, the function `create_dept` is part of the package, so `create_dept` can change the value of `tot_depts`.

### Related Topics

In this chapter:

- "[CREATE PACKAGE Statement](CREATE-PACKAGE-statement.md)"

In other chapters:

- "[PL/SQL Packages](plsql-packages.md)"

- "[Package Body](package-body.md)"

- "[Function Declaration and Definition](function-declaration-and-definition.md)"

- "[Procedure Declaration and Definition](procedure-declaration-and-definition.md)"
