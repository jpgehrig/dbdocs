You can identify null objects in object views.

Because the constructor for an object never returns a null, none of the address objects in the preceding view, [Example 6-2](objects-nested-in-object-views.md)can ever be null, even if the city, street, and similar columns in the relational table are all null. The relational table has no column that specifies whether or not the department address is null.

- Use the `DECODE` function, or a similar function, to return either a null or the constructed object.

In Example 6-3 the null `deptstreet` column can be used to indicate that the whole address is null.

The null `deptstreet` column can be used to indicate that the whole address is null.

Example 6-3 Identifying Null Objects in an Object View

    -- Requires Ex. 6-2
    CREATE OR REPLACE VIEW dept_view AS
      SELECT d.deptno, d.deptname,
            DECODE(d.deptstreet, NULL, NULL,
            address_t(d.deptstreet, d.deptcity, d.deptstate, d.deptzip)) AS deptaddr
      FROM dept d;

This technique makes it impossible to directly update the department address through the view, because it does not correspond directly to a column in the relational table. Instead, define an `INSTEAD` `OF` trigger over the view to handle updates to this column.
