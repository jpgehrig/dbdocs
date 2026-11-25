You can use indexes on typeids and attributes.

Topics:

- Indexing a Type-Discriminant Column

- Indexing Subtype Attributes of a Substitutable Column

### 8.2.1 Indexing a Type-Discriminant Column

Using the `SYS_TYPEID` function, you can build an index on the hidden type-discriminant column of substitutable columns. The type-discriminant column contains typeids that identify the most specific type of every object instance stored in the substitutable column.

The system uses this information to evaluate queries that filter by type using the `IS OF` predicate, but you can access the typeids for your own purposes using the `SYS_TYPEID` function.

Generally, a type-discriminant column contains only a small number of distinct typeids: at most, there can be only as many as there are types in the related type hierarchy. The low cardinality of this column makes it a good candidate for a bitmap index.

For example, the following statement creates a bitmap index on the type-discriminant column underlying the substitutable `contact` column of table `contacts`. The function `SYS_TYPEID` references the type-discriminant column:

Example 8-3 Create bitmap index on type-discriminant column

    -- Requires Ex. 8-1
    CREATE TABLE contacts (
      contact         person_typ,
      contact_date    DATE );
    INSERT INTO contacts VALUES (
      person_typ (65,'Vrinda Mills', '1-650-555-0125'),'24 Jun 2003' );
    INSERT INTO contacts VALUES (
      person_typ (12, 'Bob Jones', '650-555-0130'),'24 Jun 2003' );
    INSERT INTO contacts VALUES (
      student_typ(51, 'Joe Lane', '1-650-555-0140', 12, 'HISTORY'),'24 Jun 2003' );
    INSERT INTO contacts VALUES ( part_time_student_typ(52, 'Kim Patel', '1-650-555-0135', 14, 'PHYSICS', 20),'24 Jun 2003' );
    CREATE BITMAP INDEX typeid_idx ON contacts (SYS_TYPEID(contact));

### 8.2.2 Indexing Subtype Attributes of a Substitutable Column

You can build an index on attributes for any types that can be stored in a substitutable column.

You can reference attributes of subtypes in the `CREATE INDEX` statement by filtering out types other than the desired subtype (and its subtypes) using the `TREAT` function; you then use dot notation to specify the desired attribute.

For example, the following statement creates an index on the `major` attribute of all students in the `contacts` table. The declared type of the `contact` column is `person_typ`, of which `student_typ` is a subtype, so the column may contain instances of `person_typ`, `student_typ`, and subtypes of either one:

Example 8-4 Create index on attribute of all students

    -- Requires Ex.8-1- and 8-3
    CREATE INDEX major1_idx ON contacts
      (TREAT(contact AS student_typ).major);

The `student_typ` type first defined the `major` attribute: the `person_typ` supertype does not have it. Consequently, all the values in the hidden column for the `major` attribute are values for persons of type `student_typ` or `parttimestudent_typ` (a `student_typ` subtype). This means that the values of the hidden column are identical to the values returned by the `TREAT` expression, `major` values for all students, including student subtypes: both the hidden column and the `TREAT` expression list majors for students and nulls for non-students. The system exploits this fact and creates index `major1_idx` as an ordinary B-tree index on the hidden column.

Values in a hidden column are only identical to the values returned by the `TREAT` expression just described if the type named as the target of the `TREAT` function (`student_typ`) is the type that first defined the `major` attribute. If the target of the `TREAT` function is a subtype that merely inherited the attribute, as in the following example, the `TREAT` expression returns non-null `major` values for the subtype (part-time students) but not for its supertype (other students).

    CREATE INDEX major2_idx ON contacts
      (TREAT(contact AS part_time_student_typ).major);

Here, the values stored in the hidden column for `major` may be different from the results of the `TREAT` expression. Consequently, an ordinary B-tree index cannot be created on the underlying column. Therefore, the database treats the `TREAT` expression like any other function-based expression and tries to create the index as a function-based index on the result.

The following example, like the previous one, creates a function-based index on the `major` attribute of part-time students, but in this case, the hidden column for `major` is associated with a substitutable object table `person_obj_table`:

    CREATE INDEX major3_idx ON person_obj_table p
      (TREAT(VALUE(p) AS part_time_student_typ).major);
