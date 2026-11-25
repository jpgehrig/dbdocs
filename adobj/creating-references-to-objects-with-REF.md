You can create views using a `REF` modifier to get references to objects.

Example 6-7 Query References to Objects with REF

    -- Requires Ex. 6-2, Ex. 6-4, and Ex. 6-6
    CREATE OR REPLACE VIEW emp_view OF emp_t WITH OBJECT IDENTIFIER(empno)
       AS SELECT e.empno, e.empname, e.salary, REF(d)
             FROM emp e, dept_view d
              WHERE e.deptno = d.deptno;

In Example 6-7, the `dept_view` joins the `emp` table on the `deptno` key.

The advantage of using the `MAKE_REF` operator, as in [Example 6-6](references-created-to-view-objects.md), instead of the `REF` modifier is that with the former, you can create circular references. For example, you can create an employee view that has a reference to the employee's department, while the department view has a list of references to the employees who work in that department.

As with synthesized objects, you can also select persistently stored references as view columns and use them seamlessly in queries. However, the object references to view objects cannot be stored persistently.

**See Also:**

"[Object Cache](oracle-call-interface-oci.md)"
