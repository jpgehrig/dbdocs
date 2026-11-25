Oracle database automatically maps the complex structure of object types into simple table structure for storage.

Topics:

- Leaf-Level Attributes

- How Row Objects Are Split Across Columns

- Hidden Columns for Tables with Column Objects

- Hidden Columns for Substitutable Columns and Object Tables

- Storage of REFs

- Internal Layout of Nested Tables

- Internal Layout of VARRAYs

### 8.1.1 Leaf-Level Attributes

An object type is like a tree structure, where the branches represent the attributes. Attributes that are objects sprout subbranches with their own attributes.

Ultimately, each branch ends at an attribute that is a built-in type; such as `NUMBER`, `VARCHAR2`, or `REF`, or a collection type, such as `VARRAY` or nested table. Each of these leaf-level attributes of the original object type is stored in a table column.

Leaf-level attributes that are not collection types are called the [leaf-level scalar attribute](glossary.md)s of the object type.

The following topics relate to the discussion of object tables and relational tables in "[How Objects are Stored in Tables](key-features-object-relational-model.md) ".

### 8.1.2 How Row Objects Are Split Across Columns

In an [object table](glossary.md), Oracle database stores the data for every leaf-level scalar or `REF` attribute in a separate column.

**Note:**

Each `VARRAY` is also stored in a column, unless it is too large. Oracle database stores leaf-level attributes of nested table types in separate tables associated with the object table. You must declare these tables as part of the object table declaration.

When you retrieve or change attributes of [row object](glossary.md)s in an object table, the database performs the corresponding operations on the columns of the table. Accessing the value of the [row object](glossary.md) itself invokes the default constructor for the type, using the columns of the object table as arguments and produces a copy of the object.

The database stores the system-generated object identifier in a hidden column. The database uses the object identifier to construct `REF`s to the object.

**See Also:**

- "Internal Layout of VARRAYs"

- "Internal Layout of Nested Tables"

### 8.1.3 Hidden Columns for Tables with Column Objects

When a table (relational table) is defined with a column of an object type, the database adds hidden columns to the table for the leaf-level attributes of the object type.

Each object-type column also has a corresponding hidden column to store the NULL information for the column objects (that is, the atomic nulls of the top-level and the nested objects).

### 8.1.4 Hidden Columns for Substitutable Columns and Object Tables

A substitutable column or object table has a hidden column not only for each attribute of the object type of the column but also for each attribute added in any subtype of the object type.

Hidden columns store the values of those attributes for any subtype instances inserted in the substitutable column.

Besides the type-discriminant column and the null-image column, the following are associated with a substitutable column of `person_typ`, created by Example 8-1

- A hidden column for each of the attributes of `person_typ`: `idno`, `name`, and `phone`

- Hidden columns for attributes of the subtypes of `person_typ`

Thus, the following might be associated with a substitutable column of `person_typ`: the attributes `dept_id` and `major` (for `student_typ`) and `number_hours` (for `part_time_student_typ`).

When you create a subtype, the database automatically adds hidden columns for new attributes in the subtype to tables containing a substitutable column of any of the ancestor types of the new subtype. These retrofit the tables to store data of the new type. If, for some reason, the columns cannot be added, creation of the subtype is rolled back.

When you drop a subtype using `DROP TYPE` with the `VALIDATE` option, the database automatically drops hidden columns for attributes unique to the subtype that do not contain data. Errors are raised if these columns contain data.

Example 8-1 creates types needed for related examples.

Example 8-1 Creating Types and Inserting in Tables

    -- drop any of these objects created for Ex.7-10
    CREATE TYPE person_typ AS OBJECT (
      idno           NUMBER,
      name           VARCHAR2(30),
      phone          VARCHAR2(20),
      MAP MEMBER FUNCTION get_idno RETURN NUMBER )
      NOT FINAL;
    /
    CREATE TYPE BODY person_typ AS
      MAP MEMBER FUNCTION get_idno RETURN NUMBER IS
      BEGIN
        RETURN idno;
      END;
    END;
    /
    CREATE TYPE student_typ UNDER person_typ (
        dept_id NUMBER,
        major VARCHAR2(30))
    NOT FINAL;
    /
    CREATE TYPE part_time_student_typ UNDER student_typ (
      number_hours NUMBER);
    /
    CREATE TYPE employee_typ UNDER person_typ (
        emp_id NUMBER,
        mgr VARCHAR2(30));
    /
    CREATE TABLE person_obj_table OF person_typ;  // an object table
    INSERT INTO person_obj_table
      VALUES (person_typ(12, 'Bob Jones', '650-555-0130'));
    INSERT INTO person_obj_table
      VALUES (student_typ(51, 'Joe Lane', '1-650-555-0140', 12, 'HISTORY'));
    INSERT INTO person_obj_table
      VALUES (part_time_student_typ(52, 'Kim Patel', '1-650-555-0135', 14,
              'PHYSICS', 20));

Substitutable columns are associated with hidden type-discriminant columns. The hidden columns contains an identifier, called a typeid, that identifies the most specific type of each object in the substitutable columns. Typically, a typeid (`RAW`) is one byte, though it can be as big as four bytes for a large hierarchy.

You can find the typeid of a specified object instance using the function `SYS_TYPEID`.

Example 8-2 retrieves typeids of object instances stored in the substitutable object table created in Example 8-1.

### 8.1.5 Querying for Typeids of Objects Stored in Tables

You can retrieve typeids of object instances stored in a substitutable object table. See Example 8-2.

Example 8-2 Querying for Typeids of Objects Stored in the Table

    -- Requires Ex. 8-1
    SELECT name, SYS_TYPEID(VALUE(p)) typeid
      FROM person_obj_table p;

Output:

    NAME                           TYPEID
    ------------------------------ ---------------------------
    Bob Jones                      01
    Joe Lane                       02
    Kim Patel                      03

The catalog views `USER_TYPES`, `DBA_TYPES,` and `ALL_TYPES` contain a `TYPEID` column (not hidden) that gives the typeid value for each type. You can join on this column to get the type names corresponding to the typeids in a type-discriminant column.

**See Also:**

"[SYS_TYPEID](functions-and-operators-useful-with-objects.md)" for more information about `SYS_TYPEID`, typeids, and type-discriminant columns.

### 8.1.6 Storage of REFs

When the database constructs a `REF` to a row object, the constructed `REF` is made up of the object identifier (OID), some metadata of the object table, and, optionally, the `ROWID`.

The size of a `REF` in a column of `REF` type depends on the storage requirements associated with the column, as follows:

- If the column is declared as a `REF` `WITH` `ROWID`, the database stores the `ROWID` in the `REF` column. The `ROWID` hint is ignored for object references in constrained `REF` columns.

- If a column is declared as a `REF` with a `SCOPE` clause, the column decreases due to the omission of the object table metadata and the `ROWID`. A scoped `REF` is 16 bytes long.

### 8.1.7 Internal Layout of Nested Tables

The rows of a nested table are stored in a separate storage table. Each nested table column has a single associated storage table. The storage table holds all the elements for all of the nested tables in that column. The storage table has a hidden `NESTED_TABLE_ID` column with a system-generated value that lets Oracle database map the nested table elements back to the appropriate row.

You can speed up queries that retrieve entire collections by making the storage table index-organized. Include the `ORGANIZATION INDEX` clause inside the `STORE AS` clause.

A nested table type can contain objects or scalars:

- If the elements are objects, the storage table is like an object table: the top-level attributes of the object type become the columns of the storage table. However, you cannot construct `REF`s to objects in a nested table because a nested table row has no object identifier column.

- If the elements are scalars, the storage table contains a single column called `COLUMN_VALUE` that contains the scalar values.

**See Also:**

See "[Nested Table Storage](design-considerations-for-collections.md)".

### 8.1.8 Internal Layout of VARRAYs

All the elements of a `VARRAY` are stored in a single column. Depending upon the size of the array, it may be stored inline or in a `BLOB`.

**See Also:**

See [Storage Considerations for Varrays](design-considerations-for-collections.md) for details.
