You can update, insert, and delete data in an object view using the same SQL DML you use for object tables. Oracle updates the base tables of the object view if there is no ambiguity.

Views are not always directly updatable.

A view is not directly updatable if the view query contains joins, set operators, aggregate functions, or `GROUP BY` or `DISTINCT` clauses. Also, individual columns of a view are not directly updatable if they are based on pseudocolumns or expressions in the view query.

If a view is not directly updatable, you can still update it indirectly using `INSTEAD OF` triggers. To do so, you define an `INSTEAD` `OF` trigger for each kind of DML statement you want to execute on the view. In the `INSTEAD` `OF` trigger, code the operations that must take place on the underlying tables of the view to accomplish the desired change in the view. Then, when you issue a DML statement for which you have defined an `INSTEAD` `OF` trigger, Oracle transparently runs the associated trigger.

**Note:**

In an object view hierarchy, `UPDATE` and `DELETE` statements operate polymorphically just as `SELECT` statements do: the set of rows picked out by an `UPDATE` or `DELETE` statement on a view implicitly includes qualifying rows in any subviews of the specified view as well.

For example, the following statement, which deletes all persons from `Person_v`, also deletes all students from `Student_v` and all employees from the `Employee_v` view.

`DELETE FROM Person_v;`

To exclude subviews and restrict the affected rows to just those in the view specified, use the `ONLY` keyword. For example, the following statement updates only persons and not employees or students.

`UPDATE ONLY(Person_v) SET address = ...`

**See Also:**

- "INSTEAD OF Triggers to Control Mutating and Validation" for an example of an `INSTEAD` `OF` trigger

- "[Object View Hierarchies](object-vew-hierarchies.md)" for a discussion of object view hierarchy and examples defining `Student_v` and `Employee_v` views

### 6.11.1 Nested Table Columns Updated in Views

You can modify a nested table by inserting new elements and updating or deleting existing elements. Nested table columns that are virtual or synthesized, as in a view, are not usually updatable. To overcome this, Oracle allows `INSTEAD` `OF` triggers to be created on these columns.

The `INSTEAD` `OF` trigger defined on a nested table column (of a view) is fired when the column is modified. Note that if the entire collection is replaced (by an update of the parent row), the `INSTEAD` `OF` trigger on the nested table column is not fired.

### 6.11.2 INSTEAD OF Triggers to Control Mutating and Validation

You can update complex views with `INSTEAD` `OF` triggers.

`INSTEAD` `OF` triggers provide a way to update complex views that otherwise could not be updated. They can also be used to enforce constraints, check privileges, and validate DML statements. Using these triggers, you can control mutation that might be caused by inserting, updating, and deleting in the objects created though an object view.

For instance, to enforce the condition that the number of employees in a department cannot exceed 10, you can write an `INSTEAD` `OF` trigger for the employee view. The trigger is not needed to execute the DML statement because the view can be updated, but you need it to enforce the constraint.

Example 6-8 shows how to implement the trigger by means of SQL statements.

Example 6-8 Creating INSTEAD OF Triggers on a View

    -- Requires Ex. 6-2, Ex. 6-4, and Ex. 6-6
    CREATE TRIGGER emp_instr INSTEAD OF INSERT on emp_view
    FOR EACH ROW
    DECLARE
      dept_var dept_t;
      emp_count integer;
    BEGIN
      -- Enforce the constraint
      -- First get the department number from the reference
      UTL_REF.SELECT_OBJECT(:NEW.deptref, dept_var);

      SELECT COUNT(*) INTO emp_count
        FROM emp
       WHERE deptno = dept_var.deptno;
      IF emp_count < 9 THEN
         -- Do the insert
         INSERT INTO emp (empno, empname, salary, deptno)
            VALUES (:NEW.empno, :NEW.ename, :NEW.salary, dept_var.deptno);
      END IF;
    END;
    /

**See Also:**

"[Defining Triggers for Object Tables](Sql-object-types-and-references.md)"
