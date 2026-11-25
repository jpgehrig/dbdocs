In this connected group of examples, [Example 6-2](objects-nested-in-object-views.md) and [Example 6-4](nested-tables-and-varrays-used-in-object-views.md), each object selected out of the `dept_view` view has a unique object identifier derived from the department number value. In the relational case, the foreign key `deptno` in the `emp` employee table matches the `deptno` primary key value in the `dept` department table. The primary key value creates the object identifier in the `dept_view`, allowing the foreign key value in the `emp_view` to create a reference to the primary key value in `dept_view`.

To synthesize a primary key object reference, use the `MAKE_REF` operator. This takes the view or table name that the reference points to, and a list of foreign key values, to create the object identifier portion of the reference that matches a specific object in the referenced view.

Example 6-6 creates an `emp_view` view which has the employee's number, name, salary and a reference to the employee's department, by first creating the employee type `emp_t` and then the view based on that type.

Example 6-6 Creating a Reference to Objects in a View

    -- Requires Ex. 6-2 and Ex. 6-4
    -- if you have previously created emp_t, you must drop it
    CREATE TYPE emp_t AS OBJECT (
      empno    NUMBER,
      ename    VARCHAR2(20),
      salary   NUMBER,
      deptref  REF dept_t);
    /
    CREATE OR REPLACE VIEW emp_view OF emp_t WITH OBJECT IDENTIFIER(empno)
       AS SELECT e.empno, e.empname, e.salary,
                          MAKE_REF(dept_view, e.deptno)
             FROM emp e;

The `deptref` column in the view holds the department reference. The following simple query retrieves all employees whose departments are located in the city of Redwood S:

    SELECT e.empno, e.salary, e.deptref.deptno
      FROM emp_view e
     WHERE e.deptref.address.city = 'Redwood S';

       EMPNO     SALARY DEPTREF.DEPTNO
    ---------- ---------- --------------
             2       1000            100
             1        900            100
             4       1500            200
             3       1000            200

Note that you can also create `emp_view` using the `REF` modifier instead of `MAKE_REF `as shown in [Example 6-7](creating-references-to-objects-with-REF.md) to get the reference to the `dept_view` objects:
