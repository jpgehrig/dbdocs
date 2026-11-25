Operations on collection data types includes querying and comparing.

Topics:

- Collection Querying

- DML Operations on Collections

- Using BULK COLLECT to Return Entire Result Sets

- Conditions that Compare Nested Tables

- Multiset Operations for Nested Tables

### 5.3.1 Collection Querying

There are two general ways to query a table that contains a collection type as a column or attribute.

- Nest the collections in the result rows that contain them.

- Distribute or unnest collections so that each collection element appears on a row by itself.

Topics:

- Nesting Results of Collection Queries

- Unnesting Results of Collection Queries

- Unnesting Queries Containing Table Expression Subqueries

- Using a Table Expression in a CURSOR Expression

- Unnesting Queries with Multilevel Collections

#### 5.3.1.1 Nesting Results of Collection Queries

Querying a collection column in the `SELECT` list nests the elements of the collection in the result row that the collection is associated with.

The queries in Example 5-16 use the `department_persons` table shown in [Example 5-3](collection-data-types.md).

The column `dept_emps` is a nested table collection of `person_typ` type. The `dept_emps` collection column appears in the `SELECT` list like an ordinary scalar column

Example 5-16 Nesting Results of Collection Queries

    -- Requires Ex. 5-1 and Ex. 5-3
    SELECT d.dept_emps
      FROM department_persons d;

These queries retrieve this nested collection of employees.

    DEPT_EMPS(IDNO, NAME, PHONE)
    -------------------------------------------------------------
    PEOPLE_TYP(PERSON_TYP(1, 'John Smith', '1-650-555-0135'),
    PERSON_TYP(2, 'Diane Smith', '1-650-555-0135'))

The results are also nested if an object type column in the `SELECT` list contains a collection attribute, even if that collection is not explicitly listed in the `SELECT` list itself. For example, the query `SELECT` `*` `FROM` `department_persons` produces a nested result.

#### 5.3.1.2 Unnesting Results of Collection Queries

You can unnest the results of collection queries.

Unnesting collection query results is useful because not all tools or applications can deal with results in a nested format. To view Oracle collection data using tools that require a conventional format, you must unnest, or flatten, the collection attribute of a row into one or more relational rows. You can do this using a `TABLE` expression with the collection. `TABLE` expressions enable you to query a collection in the `FROM` clause like a table. In effect, you join the nested table with the row that contains the nested table.

`TABLE` expressions can be used to query any collection value expression, including transient values such as variables and parameters.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/SELECT.md) for further information on the `TABLE` expression and unnesting collections

The query inExample 5-17, like that of Example 5-16, retrieves the collection of employees, but here the collection is unnested.

Example 5-17 Unnesting Results of Collection Queries

    -- Requires Ex. 5-1 and 5-3
    SELECT e.*
      FROM department_persons d, TABLE(d.dept_emps) e;

Output:

    IDNO       NAME                           PHONE
    ---------- ------------------------------ ---------------
    1          John Smith                     1-650-555-0135
    2          Diane Smith                    1-650-555-0135

Example 5-17shows that a `TABLE` expression can have its own table alias. A table alias for the `TABLE` expression appears in the `SELECT` list to select columns returned by the `TABLE` expression.

The `TABLE` expression uses another table alias to specify the table that contains the collection column that the `TABLE` expression references. The expression `TABLE(d.dept_emps)` specifies the `department_persons` table as containing the `dept_emps` collection column. To reference a table column, a `TABLE` expression can use the table alias of any table appearing to the left of it in a `FROM` clause. This is called left correlation.

InExample 5-17, the `department_persons` table is listed in the `FROM` clause solely to provide a table alias for the `TABLE` expression to use. No columns from the `department_persons` table other than the column referenced by the `TABLE` expression appear in the result.

The following example produces rows only for departments that have employees.

    SELECT d.dept_no, e.*
      FROM department_persons d, TABLE(d.dept_emps) e;

To get rows for departments with or without employees, you can use outer-join syntax:

    SELECT d.dept_no, e.*
      FROM department_persons d, TABLE(d.dept_emps) (+) e;

The (+) indicates that the dependent join between `department_persons` and `e.dept_emps` should be `NULL`-augmented. That is, there will be rows of `department_persons` in the output for which `e.dept_emps` is `NULL` or empty, with `NULL` values for columns corresponding to `e.dept_emps`.

#### 5.3.1.3 Unnesting Queries Containing Table Expression Subqueries

A `TABLE` expression can contain a subquery of a collection.

This is an alternative to the examples in "Unnesting Results of Collection Queries" which show a `TABLE` expression that contains the name of a collection.

Example 5-18 returns the collection of employees whose department number is `101`.

Example 5-18 Using a Table Expression Containing a Subquery of a Collection

    -- Requires Ex. 5-1 and 5-3
    SELECT *
      FROM TABLE(SELECT d.dept_emps
                   FROM department_persons d
                   WHERE d.dept_no = 101);

Subqueries in a `TABLE` expression have these restrictions:

- The subquery must return a collection type.

- The `SELECT` list of the subquery must contain exactly one item.

- The subquery must return only a single collection; it cannot return collections for multiple rows. For example, the subquery `SELECT` `dept_emps` `FROM` `department_persons` succeeds in a `TABLE` expression only if table `department_persons` contains just a single row. If the table contains more than one row, the subquery produces an error.

#### 5.3.1.4 Using a Table Expression in a CURSOR Expression

You can use a `TABLE` expression in a `CURSOR` expression.

Example 5-19 shows a `TABLE` expression used in the `FROM` clause of a `SELECT` embedded in a `CURSOR` expression.

Example 5-19 Using a Table Expression in a CURSOR Expression

    -- Requires Ex. 5-1 and 5-3
    SELECT d.dept_no, CURSOR(SELECT * FROM TABLE(d.dept_emps))
      FROM department_persons d
       WHERE d.dept_no = 101;

#### 5.3.1.5 Unnesting Queries with Multilevel Collections

Unnesting queries can be also used with multilevel collections, both varrays and nested tables.

Example 5-20 shows an unnesting query on a multilevel nested table collection of nested tables. From the table `region_tab` where each region has a nested table of `countries` and each country has a nested table of `locations`, the query returns the names of all `regions`, `countries`, and `locations`.

Example 5-20 Unnesting Queries with Multilevel Collections Using the TABLE Function

    -- Requires Ex. 5-10 and 5-15
    SELECT r.region_name, c.country_name, l.location_id
      FROM region_tab r, TABLE(r.countries) c, TABLE(c.locations) l;

    -- the following query is optimized to run against the locations table
    SELECT l.location_id, l.city
      FROM region_tab r, TABLE(r.countries) c, TABLE(c.locations) l;

The output should be as follows:

    REGION_NAME               COUNTRY_NAME                             LOCATION_ID
    ------------------------- ---------------------------------------- -----------
    Europe                    Italy                                           1000
    Europe                    Italy                                           1100
    Europe                    Switzerland                                     2900
    Europe                    Switzerland                                     3000
    Europe                    United Kingdom                                  2400
    Europe                    United Kingdom                                  2500
    Europe                    United Kingdom                                  2600

    7 rows selected.

    LOCATION_ID CITY
    ----------- ------------------------------
           1000 Roma
           1100 Venice
           2900 Geneva
           3000 Bern
           2400 London
           2500 Oxford
           2600 Stretford

    7 rows selected.

Because no columns of the base table `region_tab` appear in the second `SELECT` list, the query is optimized to run directly against the `locations` storage table.

Outer-join syntax can also be used with queries of multilevel collections.

**See Also:**

"[Viewing Object Data in Relational Form with Unnesting Queries](design-considerations-for-collections.md)"

### 5.3.2 DML Operations on Collections

Oracle supports the following DML operations on collections:

- Inserts and updates that provide a new value for the entire collection

- Individual or piecewise updates of nested tables and multilevel nested tables, including inserting, deleting, and updating elements

Oracle does not support piecewise updates on `VARRAY` columns. However, `VARRAY` columns can be inserted into or updated as an atomic unit. This section contains these topics:

- Performing Piecewise Operations on Nested Tables

- Updating a Nested Table

- Performing Piecewise Operations on Multilevel Nested Tables

- Performing Piecewise INSERT to Inner Nested Table

- Performing Atomical Changes on VARRAYs and Nested Tables

- Updating Collections as Atomic Data Items

#### 5.3.2.1 Performing Piecewise Operations on Nested Tables

For piecewise operations on nested table columns, use the `TABLE` expression.

The `TABLE` expression uses a subquery to extract the nested table, so that the `INSERT`, `UPDATE`, or `DELETE` statement applies to the nested table rather than the top-level table.

`CAST` operators are also helpful. With them, you can do set operations on nested tables using SQL notation, without actually storing the nested tables in the database.

The DML statements in Example 5-21 demonstrate piecewise operations on nested table columns.

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/CAST.md)

- [CAST](functions-and-operators-useful-with-objects.md)

Example 5-21 Piecewise Operations on Collections

    -- Requires Ex. 5-1 and 5-3
    INSERT INTO TABLE(SELECT d.dept_emps
                      FROM department_persons d
                      WHERE d.dept_no = 101)
       VALUES (5, 'Kevin Taylor', '1-408-555-0199');

    UPDATE TABLE(SELECT d.dept_emps
                      FROM department_persons d
                      WHERE d.dept_no = 101) e
       SET VALUE(e) = person_typ(5, 'Kevin Taylor', '1-408-555-0199')
       WHERE e.idno = 5;

    DELETE FROM TABLE(SELECT d.dept_emps
                      FROM department_persons d
                      WHERE d.dept_no = 101) e
       WHERE e.idno = 5;

##### 5.3.2.1.1 Updating a Nested Table

You can use `VALUE` to return object instance rows for updating.

Example 5-22 shows `VALUE` used to return object instance rows for updating:

Example 5-22 Using VALUE to Update a Nested Table

    -- Requires Ex. 5-1, 5-3
    UPDATE TABLE(SELECT d.dept_emps FROM department_persons d
                   WHERE  d.dept_no = 101) p
       SET VALUE(p) = person_typ(2, 'Diane Smith', '1-650-555-0148')
       WHERE p.idno = 2;

#### 5.3.2.2 Performing Piecewise Operations on Multilevel Nested Tables

Piecewise DML is possible only on multilevel nested tables, not on multilevel varrays.

You can perform DML operations atomically on both VARRAYs and nested tables multilevel collections as described in "Updating Collections as Atomic Data Items".

Example 5-23 shows a piecewise insert operation on the `countries` nested table of nested tables. The example inserts a new country, complete with its own nested table of `location_typ`:

Example 5-23 Piecewise INSERT on a Multilevel Collection

    -- Requires Ex. 5-10 and 5-15
    INSERT INTO TABLE( SELECT countries FROM region_tab r WHERE r.region_id = 2)
      VALUES ( 'CA', 'Canada', nt_location_typ(
           location_typ(1800, '147 Spadina Ave', 'M5V 2L7', 'Toronto', 'Ontario')));

##### 5.3.2.2.1 Performing Piecewise INSERT to Inner Nested Table

You can use piecewise insert into an inner nested table to make an individual addition.

Example 5-24 performs a piecewise insert into an inner nested table to add a location for a country. Like the preceding example, this example uses a `TABLE` expression containing a subquery that selects the inner nested table to specify the target for the insert.

Example 5-24 Piecewise INSERT into an Inner Nested Table

    -- Requires Ex. 5-10 and 5-15
    INSERT INTO TABLE( SELECT c.locations
      FROM TABLE( SELECT r.countries FROM region_tab r WHERE r.region_id = 2) c
      WHERE c.country_id = 'US')
      VALUES (1700, '2004 Lakeview Rd', '98199', 'Seattle', 'Washington');

    SELECT r.region_name, c.country_name, l.location_id
      FROM region_tab r, TABLE(r.countries) c, TABLE(c.locations) l;

#### 5.3.2.3 Performing Atomical Changes on VARRAYs and Nested Tables

You can make atomical changes to nested tables and `VARRAY`s.

Note: While nested tables can also be changed in a piecewise fashions, varrays cannot.

Example 5-25 shows how you can manipulate SQL varray object types with PL/SQL statements. In this example, varrays are transferred between PL/SQL variables and SQL tables. You can insert table rows containing collections, update a row to replace its collection, and select collections into PL/SQL variables.

However, you cannot update or delete individual varray elements directly with SQL; you have to select the varray from the table, change it in PL/SQL, then update the table to include the new varray. You can also do this with nested tables, but nested tables have the option of doing piecewise updates and deletes.

Example 5-25 Using INSERT, UPDATE, DELETE, and SELECT Statements With Varrays

    CREATE TYPE dnames_var IS VARRAY(7) OF VARCHAR2(30);
    /
    CREATE TABLE depts (region VARCHAR2(25), dept_names dnames_var);
    BEGIN
       INSERT INTO depts VALUES('Europe', dnames_var('Shipping','Sales','Finance'));
       INSERT INTO depts VALUES('Americas', dnames_var('Sales','Finance','Shipping'));
       INSERT INTO depts
         VALUES('Asia', dnames_var('Finance','Payroll','Shipping','Sales'));
       COMMIT;
    END;
    /
    DECLARE
       new_dnames dnames_var := dnames_var('Benefits', 'Advertising', 'Contracting',
                                           'Executive', 'Marketing');
       some_dnames dnames_var;
    BEGIN
       UPDATE depts SET dept_names  = new_dnames WHERE region = 'Europe';
       COMMIT;
       SELECT dept_names INTO some_dnames FROM depts WHERE region = 'Europe';
       FOR i IN some_dnames.FIRST .. some_dnames.LAST
       LOOP
          DBMS_OUTPUT.PUT_LINE('dept_names = ' || some_dnames(i));
       END LOOP;
    END;
    /

#### 5.3.2.4 Updating Collections as Atomic Data Items

Multilevel collections (both `VARRAY` and nested tables) can also be updated atomically with an `UPDATE` statement. For example, suppose `v_country` is a variable declared to be of the `countries` nested table type `nt_country_typ`.

Example 5-26 updates `region_tab` by setting the `countries` collection as a unit to the value of `v_country`.

The section "[Constructors for Multilevel Collections](multilevel-collection-types.md)" shows how to insert an entire multilevel collection with an `INSERT` statement.

Example 5-26 Using UPDATE to Insert an Entire Multilevel Collection

    -- Requires Ex. 5-10 and 5-15
    INSERT INTO region_tab (region_id, region_name) VALUES(2, 'Americas');

    DECLARE
      v_country nt_country_typ;
    BEGIN
      v_country :=  nt_country_typ( country_typ(
       'US', 'United States of America', nt_location_typ (
       location_typ( 1500,'2011 Interiors Blvd','99236','San Francisco','California'),
       location_typ(1600,'2007 Zagora St','50090','South Brunswick','New Jersey'))));
      UPDATE region_tab r
        SET r.countries = v_country WHERE r.region_id = 2;
    END;
    /
    -- Invocation:
    SELECT r.region_name, c.country_name, l.location_id
      FROM region_tab r, TABLE(r.countries) c, TABLE(c.locations) l
         WHERE r.region_id = 2;

### 5.3.3 Using BULK COLLECT to Return Entire Result Sets

The PL/SQL `BULK` `COLLECT` clause is an alternative to using DML statements, which can be time consuming to process. You can return an entire result set in one operation.

In Example 5-27, `BULK` `COLLECT` is used with a multilevel collection that includes an object type.

Example 5-27 Using BULK COLLECT with Collections

    -- unrelated to other examples in this chapter
    CREATE TYPE dnames_var IS VARRAY(7) OF VARCHAR2(30);
    /
    CREATE TABLE depts (region VARCHAR2(25), dept_names dnames_var);
    BEGIN
       INSERT INTO depts VALUES('Europe', dnames_var('Shipping','Sales','Finance'));
       INSERT INTO depts VALUES('Americas', dnames_var('Sales','Finance','Shipping'));
       INSERT INTO depts
         VALUES('Asia', dnames_var('Finance','Payroll','Shipping','Sales'));
       COMMIT;
    END;
    /
    DECLARE
       TYPE dnames_tab IS TABLE OF dnames_var;
       v_depts dnames_tab;
    BEGIN
        SELECT dept_names BULK COLLECT INTO v_depts FROM depts;
        DBMS_OUTPUT.PUT_LINE(v_depts.COUNT); -- prints 3
    END;
    /

### 5.3.4 Conditions that Compare Nested Tables

Using certain conditions, you can compare nested tables, including multilevel nested tables. There is no mechanism for comparing varrays.

The SQL examples in this section use the nested tables created in [Example 5-5](collection-data-types.md), and contain the objects created in [Example 5-1](collection-data-types.md).

Topics:

- Comparing Equal and Not Equal Conditions

- Comparing the IN Condition

- Comparing Subset of Multiset Conditions

- Determing Members of a Nested Table

- Determining Empty Conditions

- Determining Set Conditions

#### 5.3.4.1 Comparing Equal and Not Equal Conditions

The equal (=) and not equal (\<\>) conditions determine whether the input nested tables are identical or not, returning the result as a Boolean value.

Two nested tables are equal if they have the same named type, have the same cardinality, and their elements are equal. Elements are equal depending on whether they are equal by the elements own equality definitions, except for object types which require a map method. Equality is determined in the existing order of the elements, because nested tables are unordered.

In Example 5-28, the nested tables contain `person_typ` objects, which have an associated map method. See [Example 5-1](collection-data-types.md). Since the two nested tables in the `WHERE` clause are not equal, no rows are selected.

Example 5-28 Using an Equality Comparison with Nested Tables

    -- Requires Ex. 5-1 and 5-5
    SELECT p.name
      FROM students, TABLE(physics_majors) p
    WHERE math_majors = physics_majors;

#### 5.3.4.2 Comparing the IN Condition

The `IN` condition checks whether or not a nested table is in a list of nested tables, returning the result as a Boolean value. NULL is returned if the nested table is a null nested table.

Example 5-29 Using an IN Comparison with Nested Tables

    -- Requires Ex. 5-1 and 5-5
    SELECT p.idno, p.name
      FROM students, TABLE(physics_majors) p
    WHERE physics_majors IN (math_majors, chem_majors);

#### 5.3.4.3 Comparing Subset of Multiset Conditions

The `SUBMULTISET` `[OF]` condition checks whether or not a nested table is a subset of another nested table, returning the result as a Boolean value. The `OF` keyword is optional and does not change the functionality of `SUBMULTISET`.

This condition is implemented only for nested tables.

**See Also:**

"Multiset Operations for Nested Tables"

Example 5-30 Testing the SUBMULTISET OF Condition on a Nested Table

    -- Requires Ex. 5-1 and 5-5
    SELECT p.idno, p.name
      FROM students, TABLE(physics_majors) p
    WHERE physics_majors SUBMULTISET OF math_majors;

#### 5.3.4.4 Determing Members of a Nested Table

The `MEMBER` `[OF]` or `NOT` `MEMBER` `[OF]` condition tests whether or not an element is a member of a nested table, returning the result as a Boolean value. The `OF` keyword is optional and has no effect on the output.

In Example 5-31, the `person_typ` is an element of the same type as the elements of the nested table `math_majors`.

Example 5-32 presents an alternative approach to the `MEMBER` `OF` condition, which performs more efficiently for large collections.

Example 5-31 Using MEMBER OF on a Nested Table

    -- Requires Ex. 5-1 and 5-5
    SELECT graduation
      FROM students
    WHERE person_typ(12, 'Bob Jones', '1-650-555-0130') MEMBER OF math_majors;

Example 5-32 Alternative to Using MEMBER OF on a Nested Table

    -- Requires Ex. 5-1 and 5-5
    SELECT graduation
      FROM students
    WHERE person_typ(12, 'Bob Jones', '1-650-555-0130') in (select value(p)
        from TABLE( math_majors) p);

#### 5.3.4.5 Determining Empty Conditions

The `IS` `[NOT]` `EMPTY` condition checks whether a given nested table is empty or not empty, regardless of whether any of the elements are NULL. If a NULL is given for the nested table, the result is NULL. The result is returned as a Boolean value.

Example 5-33 Using IS NOT on a Nested Table

    -- Requires Ex. 5-1 and 5-5
    SELECT p.idno, p.name
      FROM students, TABLE(physics_majors) p
    WHERE physics_majors IS NOT EMPTY;

#### 5.3.4.6 Determining Set Conditions

The `IS` `[NOT]` `A` `SET` condition checks whether or not a given nested table is composed of unique elements, returning a Boolean value.

Example 5-34 Using IS A SET on a Nested Table

    -- Requires Ex. 5-1 and 5-5
    SELECT p.idno, p.name
      FROM students, TABLE(physics_majors) p
    WHERE physics_majors IS A SET;

### 5.3.5 Multiset Operations for Nested Tables

You can use[multiset operators](glossary.md) for nested tables. Multiset operations are not available for varrays.

The SQL examples in this section use the nested tables created in [Example 5-5](collection-data-types.md) and the objects created in [Example 5-1](collection-data-types.md).

**See Also:**

- "[Functions and Operators Useful with Objects](functions-and-operators-useful-with-objects.md)" for a description of additional operations

- [Oracle Database SQL Language Reference](../sqlrf/Operators.md).for more information about using operators with nested tables

#### 5.3.5.1 CARDINALITY

The `CARDINALITY` function returns the number of elements in a nested table. The return type is `NUMBER`. If the nested table is a null collection, `NULL` is returned.

Example 5-35 Determining the CARDINALITY of a Nested Table

    -- Requires Ex. 5-1 and 5-5
    SELECT CARDINALITY(math_majors)
      FROM students;

For more information about the `CARDINALITY` function, see [Oracle Database SQL Language Reference](../sqlrf/CARDINALITY.md).

#### 5.3.5.2 COLLECT

The `COLLECT` function is an aggregate function which creates a multiset from a set of elements. The function takes a column of the element type as input and creates a multiset from rows selected. To get the results of this function, you must use it within a `CAST` function to specify the output type of `COLLECT`.

**See Also:**

- See "[CAST](functions-and-operators-useful-with-objects.md)" for an example of the `COLLECT` function.

- For more information about the `COLLECT` function, see [Oracle Database SQL Language Reference](../sqlrf/COLLECT.md).

#### 5.3.5.3 MULTISET EXCEPT

The `MULTISET` `EXCEPT` operator inputs two nested tables and returns a nested table whose elements are in the first nested table but not the second. The input nested tables and the output nested table will all be of the same nested table type.

The `ALL` or `DISTINCT` options can be used with the operator. The default is `ALL`.

- With the `ALL` option, for `ntab1` `MULTISET` `EXCEPT` `ALL` `ntab2`, all elements in `ntab1` other than those in `ntab2` are part of the result. If a particular element occurs `m` times in `ntab1` and `n` times in `ntab2`, the result shows (`m` - `n`) occurrences of the element if `m` is greater than `n`, otherwise, `0` occurrences of the element.

- With the `DISTINCT` option, any element that is present in `ntab1` and is also present in `ntab2` is eliminated, irrespective of the number of occurrences.

Example 5-36 Using the MULTISET EXCEPT Operation on Nested Tables

    -- Requires Ex. 5-1 and 5-5
    SELECT math_majors MULTISET EXCEPT physics_majors
      FROM students
    WHERE graduation = '01-JUN-03';

**See Also:**

For more information about the `MULTISET` `EXCEPT` operator, see [Oracle Database SQL Language Reference](../sqlrf/Multiset-Operators.md).

#### 5.3.5.4 MULTISET INTERSECT

The `MULTISET` `INTERSECT` operator returns a nested table whose values are common to the two input nested tables. The input nested tables and the output nested table are all type name equivalent.

There are two options associated with the operator: `ALL` or `DISTINCT`. The default is `ALL`. With the `ALL` option, if a particular value occurs `m` times in `ntab1` and `n` times in `ntab2`, the result contains the element `MIN`(`m`, `n`) times. With the `DISTINCT` option, the duplicates from the result are eliminated, including duplicates of `NULL` values if they exist.

Example 5-37 Using the MULTISET INTERSECT Operation on Nested Tables

    -- Requires Ex. 5-1 and 5-5
    SELECT math_majors MULTISET INTERSECT physics_majors
      FROM students
    WHERE graduation = '01-JUN-03';

**See Also:**

For more information about the `MULTISET` `INTERSECT` operator, see [Oracle Database SQL Language Reference](../sqlrf/Multiset-Operators.md).

#### 5.3.5.5 MULTISET UNION

The `MULTISET` `UNION` operator returns a nested table whose values are those of the two input nested tables. The input nested tables and the output nested table are all type name equivalent.

There are two options associated with the operator: `ALL` or `DISTINCT`. The default is `ALL`. With the `ALL` option, all elements in `ntab1` and `ntab2` are part of the result, including all copies of `NULL`s. If a particular element occurs `m` times in `ntab1` and `n` times in `ntab2`, the result contains the element (`m` + `n`) times. With the `DISTINCT` option, the duplicates from the result are eliminated, including duplicates of `NULL` values if they exist.

Example 5-38 Using the MULTISET UNION Operation on Nested Tables

    -- Requires Ex. 5-1 and 5-5
    SELECT math_majors MULTISET UNION DISTINCT physics_majors
      FROM students
    WHERE graduation = '01-JUN-03';

    PEOPLE_TYP(PERSON_TYP(12, 'Bob Jones', '1-650-555-0130'),
        PERSON_TYP(31, 'Sarah Chen', '1-415-555-0120'),
        PERSON_TYP(45, 'Chris Woods', '1-408-555-0128'))

    -- Requires Ex. 5-1 and 5-5
    SELECT math_majors MULTISET UNION ALL physics_majors
      FROM students
    WHERE graduation = '01-JUN-03';

Output:

    PEOPLE_TYP(PERSON_TYP(12, 'Bob Jones', '1-650-555-0130'),
        PERSON_TYP(31, 'Sarah Chen', '1-415-555-0120'),
        PERSON_TYP(45, 'Chris Woods', '1-408-555-0128'),
        PERSON_TYP(12, 'Bob Jones', '1-650-555-0130'),
        PERSON_TYP(45, 'Chris Woods', '1-408-555-0128'))

**See Also:**

For more information about the `MULTISET` `UNION` operator, see [Oracle Database SQL Language Reference](../sqlrf/Multiset-Operators.md).

#### 5.3.5.6 POWERMULTISET

The `POWERMULTISET` function generates all non-empty submultisets from a given multiset. The input to the `POWERMULTISET` function can be any expression which evaluates to a multiset. The limit on the cardinality of the multiset argument is 32.

Example 5-39 Using the POWERMULTISET Operation on Multiset

    -- Requires Ex. 5-1 and 5-5
    SELECT * FROM TABLE(POWERMULTISET( people_typ (
               person_typ(12, 'Bob Jones', '1-650-555-0130'),
               person_typ(31, 'Sarah Chen', '1-415-555-0120'),
               person_typ(45, 'Chris Woods', '1-415-555-0124'))));

**See Also:**

For more information about the `POWERMULTISET` function, see [Oracle Database SQL Language Reference](../sqlrf/POWERMULTISET.md).

#### 5.3.5.7 POWERMULTISET_BY_CARDINALITY

The `POWERMULTISET_BY_CARDINALITY` function returns all non-empty submultisets of a nested table of the specified cardinality. The output is rows of nested tables.

`POWERMULTISET_BY_CARDINALITY(x, l)` is equivalent to `TABLE(POWERMULTISET(x))` `p` where `CARDINALITY(value(p))` `=` `l`, where `x` is a multiset and l is the specified cardinality.

The first input parameter to the `POWERMULTISET_BY_CARDINALITY` can be any expression which evaluates to a nested table. The length parameter must be a positive integer, otherwise an error is returned. The limit on the cardinality of the nested table argument is 32.

Example 5-40 Using the POWERMULTISET_BY_CARDINALITY Function

    -- Requires Ex. 5-1 and 5-5
    SELECT * FROM TABLE(POWERMULTISET_BY_CARDINALITY( people_typ (
               person_typ(12, 'Bob Jones', '1-650-555-0130'),
               person_typ(31, 'Sarah Chen', '1-415-555-0120'),
               person_typ(45, 'Chris Woods', '1-415-555-0124')),2));

**See Also:**

For more information about the `POWERMULTISET_BY_CARDINALITY` function, see [Oracle Database SQL Language Reference](../sqlrf/POWERMULTISET_BY_CARDINALITY.md).

#### 5.3.5.8 SET

The `SET` function converts a nested table into a set by eliminating duplicates, and returns a nested table whose elements are distinct from one another. The nested table returned is of the same named type as the input nested table.

Example 5-41 Using the SET Function on a Nested Table

    -- Requires Ex. 5-1 and 5-5
    SELECT SET(physics_majors)
      FROM students
    WHERE graduation = '01-JUN-03';

**See Also:**

For more information about the `SET` function, see [Oracle Database SQL Language Reference](../sqlrf/SET.md).
