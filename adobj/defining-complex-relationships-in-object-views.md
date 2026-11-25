You can define circular references in object views using the `MAKE_REF` operator: `view_A` can refer to `view_B` which in turn can refer to `view_A`. This allows an object view to synthesize a complex structure such as a graph from relational data.

For example, in the case of the department and employee, the department object currently includes a list of employees. To conserve space, you may want to put references to the employee objects inside the department object, instead of materializing all the employees within the department object. You can construct (pin) the references to employee objects, and later follow the references using the dot notation to extract employee information.

Because the employee object already has a reference to the department in which the employee works, an object view over this model contains circular references between the department view and the employee view.

You can create circular references between object views in two different ways:

**Note:**

Both ways to create circular references require the setup described in "Tables and Types to Demonstrate Circular View References".

- First View After Second View

  1.  Create view A without any reference to view B.

  2.  Create view B, which includes a reference to view A.

  3.  Replace view A with a new definition that includes the reference to view B.

  See the example in "Method 1: Re-create First View After Creating Second View"

- First View Using the `FORCE` Keyword

  1.  Create view A with a reference to view B using the `FORCE` keyword.

  2.  Create view B with a reference to view A. When view A is used, it is validated and re-compiled.

  See the example in "Method 2: Create First View Using FORCE Keyword"

Method 2 has fewer steps, but the `FORCE` keyword may hide errors in the view creation. You need to query the `USER_ERRORS` catalog view to see if there were any errors during the view creation. Use this method only if you are sure that there are no errors in the view creation statement.

Also, if errors prevent the views from being recompiled upon use, you must recompile them manually using the `ALTER` `VIEW` `COMPILE` command.

Perform the setup described next before attempting to use either method of creating circular view references.

### 6.13.1 Tables and Types to Demonstrate Circular View References

First, you need set up some relational tables and associated object types. Although the tables contain some objects, they are not object tables. To access the data objects, you will create object views later.

The `emp` table stores the employee information:

Example 6-10 Creating emp table to demonstrate circular references

    CREATE TABLE emp
    (  empno    NUMBER PRIMARY KEY,
       empname  VARCHAR2(20),
       salary   NUMBER,
       deptno   NUMBER );

    -- first create a dummy, that is, incomplete, department type, so emp_t type
    -- created later will succeed

    CREATE TYPE dept_t;
    /

    -- Create the employee type with a reference to the department, dept_t:
    CREATE TYPE emp_t AS OBJECT
    ( eno NUMBER,
      ename VARCHAR2(20),
      salary  NUMBER,
      deptref REF dept_t );
    /

    -- Represent the list of references to employees as a nested table:
    CREATE TYPE employee_list_ref_t AS TABLE OF REF emp_t;
    /

    -- Create the department table as a relational table
    CREATE TABLE dept
    (   deptno        NUMBER PRIMARY KEY,
        deptname      VARCHAR2(20),
        deptstreet    VARCHAR2(20),
        deptcity      VARCHAR2(10),
        deptstate     CHAR(2),
        deptzip       VARCHAR2(10) );

    -- Create object types that map to columns from the relational tables:
    CREATE TYPE address_t AS OBJECT
    ( street        VARCHAR2(20),
       city         VARCHAR2(10),
       state        CHAR(2),
       zip          VARCHAR2(10));
    /

    -- Fill in the definition for dept_t, the incomplete type you previously created:
    CREATE OR REPLACE TYPE dept_t AS OBJECT
    ( dno           NUMBER,
      dname         VARCHAR2(20),
      deptaddr      address_t,
      empreflist    employee_list_ref_t);
    /

As Example 6-10 indicates, you must create the `emp` table, then create a dummy department type, `dept_t` which will enable the `emp_t` type to succeed once you create it. After that, create `emp_t` with a reference to `dept_t`. Create a list of references to employees as a nested table, `employee_list_ref_t` and create the department table, `dept`. Then create an object type, `address_t` that has columns mapping to the relational tables, and finally fill in the definition for the incomplete `dept_t`.

The following is example data you could use:

    insert into emp values(1,'John','900',100);
    insert into emp values(2,'james','1000',100);
    insert into emp values(3,'jack',2000,200);

### 6.13.2 Creating Object Views with Circular References

You can create object views with circular references.

If you have established the underlying relational table definitions, as described in Defining Complex Relationships in Object Views, you can create the object views on top of them.

Topics:

- Method 1: Re-create First View After Creating Second View

- Method 2: Create First View Using FORCE Keyword

#### 6.13.2.1 Method 1: Re-create First View After Creating Second View

You can recreate the first view after creating the second view.

First create the employee view with a null in the `deptref` column. Later, you can turn that column into a reference.

Next, create the department view, which includes references to the employee objects. This creates a list of references to employee objects, instead of including the entire employee object.

Next, re-create the employee view with the reference to the department view.

Example 6-11 Creating an Object View with a Circular Reference, Method 1

    -- Requires Ex. 6-10
    CREATE VIEW emp_view OF emp_t WITH OBJECT IDENTIFIER(eno)
       AS SELECT e.empno, e.empname, e.salary, NULL
             FROM emp e;

    -- create department view, including references to the employee objects
    CREATE VIEW dept_view OF dept_t WITH OBJECT IDENTIFIER(dno)
       AS SELECT d.deptno, d.deptname,
                    address_t(d.deptstreet,d.deptcity,d.deptstate,d.deptzip),
                    CAST( MULTISET (
                               SELECT MAKE_REF(emp_view, e.empno)
                               FROM emp e
                               WHERE e.deptno = d.deptno)
                            AS employee_list_ref_t)
       FROM dept d;

    CREATE OR REPLACE VIEW emp_view OF emp_t WITH OBJECT IDENTIFIER(eno)
       AS SELECT e.empno, e.empname, e.salary,
                           MAKE_REF(dept_view, e.deptno)
             FROM emp e;

This creates the views.

#### 6.13.2.2 Method 2: Create First View Using FORCE Keyword

You can force creation of a first view even if the other view does not yet exist.

If you are sure that the view creation statement has no syntax errors, you can use the `FORCE` keyword to force the creation of the first view without the other view being present.

First, create an employee view that includes a reference to the department view, which does not exist at this point. This view cannot be queried until the department view is created properly.

Next, create a department view that includes references to the employee objects. You do not have to use the `FORCE` keyword here, because `emp_view` already exists. This allows you to query the department view, getting the employee object by dereferencing the employee reference from the nested table `empreflist`.

**Note:**

If you previously ran Example 6-11, remove the views you created before running Example 6-12.

Example 6-12 Creating view with FORCE Method 2

    -- Requires Ex. 6-10
    -- create employee view
    CREATE OR REPLACE FORCE VIEW emp_view OF emp_t WITH OBJECT IDENTIFIER(eno)
       AS SELECT e.empno, e.empname, e.salary,
                           MAKE_REF(dept_view, e.deptno)
             FROM emp e;

    -- create a department view that includes references to the employee objects
    CREATE OR REPLACE VIEW dept_view OF dept_t WITH OBJECT IDENTIFIER(dno)
       AS SELECT d.deptno, d.deptname,
                    address_t(d.deptstreet,d.deptcity,d.deptstate,d.deptzip),
                    CAST( MULTISET (
                               SELECT MAKE_REF(emp_view, e.empno)
                               FROM emp e
                               WHERE e.deptno = d.deptno)
                            AS employee_list_ref_t)
       FROM   dept d;

    -- Querying with DEREF method
    SELECT DEREF(e.COLUMN_VALUE)
      FROM TABLE( SELECT e.empreflist FROM dept_view e WHERE e.dno = 100) e;

`COLUMN_VALUE` is a special name that represents the scalar value in a scalar nested table. In this case, `COLUMN_VALUE` denotes the reference to the employee objects in the nested table `empreflist`.

You can also access the employee number only, for all those employees whose name begins with `John`.

Example 6-13 Querying with COLUMN_VALUE

    -- Requires Ex. 6-10 and 6-12
    SELECT e.COLUMN_VALUE.eno
      FROM TABLE(SELECT e.empreflist FROM dept_view e WHERE e.dno = 100) e
     WHERE e.COLUMN_VALUE.ename like 'John%';

To get a tabular output, unnest the list of references by joining the department table with the items in its nested table:

Example 6-14 Querying with COLUMN_VALUE, Unnesting References

    -- Requires Ex. 6-10 and 6-12
    SELECT d.dno, e.COLUMN_VALUE.eno, e.COLUMN_VALUE.ename
      FROM dept_view d, TABLE(d.empreflist) e
     WHERE e.COLUMN_VALUE.ename like 'John%'
      AND d.dno = 100;

Finally, you can rewrite the preceding query to use the `emp_view` instead of the `dept_view` to show how to navigate from one view to the other:

Example 6-15 Querying with COLUMN_VALUE, Querying emp_view

    -- Requires Ex. 6-10 and 6-12
    SELECT e.deptref.dno, DEREF(f.COLUMN_VALUE)
      FROM emp_view e, TABLE(e.deptref.empreflist) f
     WHERE e.deptref.dno = 100
      AND f.COLUMN_VALUE.ename like 'John%';
