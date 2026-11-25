Object views allow you to present only data that you want users to see.

The procedure for defining an object view is:

1.  Define an object type, where each attribute of the type corresponds to an existing column in a relational table.
2.  Write a query that specifies how to extract the data from the relational table. Specify the columns in the same order as the attributes in the object type.
3.  Specify a unique value, based on attributes of the underlying data, to serve as an object identifier, enabling you to create pointers (`REF`s) to the objects in the view. You can often use an existing primary key.
    **See Also:**

    "[Object Identifiers Used to Identify Row Objects](key-features-object-relational-model.md)"

To update an object view where the attributes of the object type do not correspond exactly to columns in existing tables, you may need to do the following:

Write an `INSTEAD` `OF` trigger procedure for Oracle to execute whenever an application program tries to update data in the object view. See "[Object View Manipulations](object-view-manipulations.md)".

After these steps, you can use an object view just like an object table.

Example 6-1 contains SQL statements to define an object view, where each row in the view is an object of type `employee_t`:

Example 6-1 Creating an Object View

    CREATE TABLE emp_table (
        empnum   NUMBER (5),
        ename    VARCHAR2 (20),
        salary   NUMBER (9,2),
        job      VARCHAR2 (20));

    CREATE TYPE employee_t AS OBJECT (
        empno    NUMBER (5),
        ename    VARCHAR2 (20),
        salary   NUMBER (9,2),
        job      VARCHAR2 (20));
    /

    CREATE VIEW emp_view1 OF employee_t
        WITH OBJECT IDENTIFIER (empno) AS
            SELECT e.empnum, e.ename, e.salary, e.job
                FROM emp_table e
                WHERE job = 'Developer';

    insert into emp_table values(1,'John',1000.00,'Architect');
    insert into emp_table values(2,'Robert',900.00,'Developer');
    insert into emp_table values(3,'James',2000.00,'Director');

    select * from emp_view1;

        EMPNO ENAME                    SALARY JOB
    ---------- -------------------- ---------- --------------------
             2 Robert                      900 Developer

To access the data from the `empnum` column of the relational table, access the `empno` attribute of the object type.
