Multilevel collection types are collection types whose elements are themselves directly or indirectly another collection type.

Possible multilevel collection types are:

- Nested table of nested table type

- Nested table of varray type

- Varray of nested table type

- Varray of varray type

- Nested table or varray of a user-defined type that has an attribute that is a nested table or varray type

Like single-level collection types, multilevel collection types:

- Can be used as columns in a relational table or with object attributes in an object table.

- Require that both the source and the target be of the same declared data type for assignment.

Topics:

- Nested Table Storage Tables for Multilevel Collection Types

- Varray Storage for Multilevel Collections

- Constructors for Multilevel Collections

### 5.2.1 Nested Table Storage Tables for Multilevel Collection Types

To use a multilevel nested table collection of nested tables, you must specify a nested-table storage clause.

A nested table type column or object table attribute requires a storage table to store rows for all its nested tables as described in "[Storing Elements of Nested Tables](collection-data-types.md)".

With a multilevel nested table collection of nested tables, you must specify a nested-table storage clause (`STORE AS`) for both the inner set and the outer set of nested tables. You must have as many nested table storage clauses as you have levels of nested tables in a collection.

Every nested table storage table contains a column, referenceable by `NESTED_TABLE_ID`, that keys rows in the storage table to the associated row in the parent table. A parent table that is itself a nested table has two system-supplied ID columns:

- A system-supplied ID column that is referenceable by `NESTED_TABLE_ID`, which keys its rows back to rows in its parent table.

- A system-supplied ID column that is hidden and referenced by the `NESTED_TABLE_ID` column in its nested table children.

If you do not specify a primary key with a `NESTED_TABLE_ID` column, then the database automatically creates a b-tree index on the `NESTED_TABLE_ID` column for better performance.

**See Also:**

- "[Nested Table Storage](design-considerations-for-collections.md)"

- "[Unnesting Queries with Multilevel Collections](operations-on-collection-data-types.md)"

- See Example 5-12 for an example where the nested table has a primary key in which the first column is `NESTED_TABLE_ID`.

Topics:

- Creating Multilevel Nested Table Storage

- Creating Multilevel Nested Table Storage Using the COLUMN_VALUE Keyword

- Specifying Physical Attributes for Nested Table Storage

#### 5.2.1.1 Creating Multilevel Nested Table Storage

You can create a nested table of nested tables.

Example 5-10 creates the multilevel collection type `nt_country_typ`, a nested table of nested tables. The example models a system of corporate regions in which each region has a nested table collection of the countries, and each country has a nested table collection of its locations. This example requires the `regions`, `countries`, and `locations` tables of the Oracle `HR` sample schema.

In Example 5-10, the SQL statements create the table `region_tab`, which contains the column `countries`, whose type is a multilevel collection, `nt_country_typ`. This multilevel collection is a nested table of an object type that has the nested table attribute `locations`. Separate nested table clauses are provided for the outer `countries` nested table and for the inner `locations` nested table.

In Example 5-10 you can refer to the inner nested table `locations` by name because this nested table is a named attribute of an object. However, if the inner nested table is not an attribute of an object, it has no name. The keyword `COLUMN_VALUE` is provided for this case. See Example 5-11

Example 5-10 Multilevel Nested Table Storage

    -- Requires the HR sample schema
    CREATE TYPE location_typ AS OBJECT (
      location_id      NUMBER(4),
      street_address   VARCHAR2(40),
      postal_code      VARCHAR2(12),
      city             VARCHAR2(30),
      state_province   VARCHAR2(25));
    /

    CREATE TYPE nt_location_typ AS TABLE OF location_typ;  -- nested table type
    /

    CREATE TYPE country_typ AS OBJECT (
      country_id     CHAR(2),
      country_name   VARCHAR2(40),
      locations      nt_location_typ); -- inner nested table
    /

    CREATE TYPE nt_country_typ AS TABLE OF country_typ;  -- multilevel collection type
    /

    CREATE TABLE region_tab (
      region_id     NUMBER,
      region_name   VARCHAR2(25),
      countries     nt_country_typ) -- outer nested table
      NESTED TABLE countries STORE AS nt_countries_tab
       (NESTED TABLE locations STORE AS nt_locations_tab);

**See Also:**

[Oracle Database Sample Schemas](../comsc/introduction-to-sample-schemas.md) for information on using sample schemas

#### 5.2.1.2 Creating Multilevel Nested Table Storage Using the COLUMN_VALUE Keyword

You can use the keyword `COLUMN_VALUE` place of a name for an inner nested table.

In Example 5-11 an inner nested table is unnamed and represented by the keyword `COLUMN_VALUE`.

Example 5-11 Multilevel Nested Table Storage Using the COLUMN_VALUE Keyword

    CREATE TYPE inner_table AS TABLE OF NUMBER;
    /
    CREATE TYPE outer_table AS TABLE OF inner_table;
    /
    CREATE TABLE tab1 (
      col1 NUMBER,  -- inner nested table, unnamed
      col2 outer_table)
    NESTED TABLE col2 STORE AS col2_ntab
      (NESTED TABLE COLUMN_VALUE STORE AS cv_ntab);

#### 5.2.1.3 Specifying Physical Attributes for Nested Table Storage

You can physical attributes for nested table storage.

Example 5-12 shows how to specify physical attributes for the storage tables in the nested table clause.

Specifying a primary key with `NESTED_TABLE_ID` as the first column and index-organizing the table causes Oracle database to physically cluster all the nested table rows that belong to the same parent row, for more efficient access. In Example 5-12 the nested table has a primary key in which the first column is `NESTED_TABLE_ID`. This column contains the ID of the row in the parent table with which a storage table row is associated.

Example 5-12 Specifying Physical Attributes for Nested Table Storage

    -- Requires Ex. 5-10
    -- drop the following if you have previously created it
    DROP TABLE region_tab FORCE;

    CREATE TABLE region_tab (
      region_id     NUMBER,
      region_name   VARCHAR2(25),
      countries     nt_country_typ)
      NESTED TABLE countries STORE AS nt_countries_tab (
       (PRIMARY KEY (NESTED_TABLE_ID, country_id))
          NESTED TABLE locations STORE AS nt_locations_tab);

### 5.2.2 Varray Storage for Multilevel Collections

Multilevel varrays are stored in one of two ways, depending on whether the varray is a varray of varrays or a varray of nested tables.

- In a varray of varrays, the entire varray is stored inline in the row unless it is larger than approximately 4000 bytes or `LOB` storage is explicitly specified.

- In a varray of nested tables, the entire varray is stored in a LOB, with only the LOB locator stored in the row. There is no storage table associated with nested table elements of a varray.

You can explicitly specify LOB storage for varrays.

**See Also:**

- "[Storage Considerations for Varrays](design-considerations-for-collections.md)"

- Oracle Database SecureFiles and Large Objects Developer's Guide for a general understanding of LOBs

### 5.2.3 Specifying LOB Storage for VARRAY of VARRAY Type

You can explicitly specify LOB storage for `VARRAY`s of `VARRAY` type.

Example 5-13 shows explicit `LOB` storage specified for a `VARRAY`of `VARRAY` type..

Example 5-13 Specifying LOB Storage for a VARRAY of VARRAY Type

    -- Requires Ex. 5-8, drop following if created

    DROP TYPE email_varray_typ FORCE;
    CREATE TYPE email_list_typ2 AS OBJECT (
        section_no   NUMBER,
        emails       email_list_arr);
    /

    CREATE TYPE email_varray_typ AS VARRAY(5) OF email_list_typ2;
    /

    CREATE TABLE dept_email_list2 (
      dept_no NUMBER,
      email_addrs email_varray_typ)
      VARRAY email_addrs STORE AS LOB dept_emails_lob2;

### 5.2.4  Specifying LOB Storage for a Nested Table of VARRAYs

You can explicitly specify LOB storage for a nested table of varray elements.

Example 5-14 shows the `COLUMN_VALUE` keyword used with varrays. See Example 5-11 for discussion of this keyword and its use with nested tables.

Example 5-14 Specifying LOB Storage for a Nested Table of VARRAYs

    -- drop the following types if you have created them
    DROP TYPE email_list_typ FORCE;
    DROP TABLE dept_email_list FORCE;
    DROP TYPE email_list_arr FORCE;

    CREATE TYPE email_list_arr AS VARRAY(10) OF VARCHAR2(80);
    /

    CREATE TYPE email_list_typ AS TABLE OF email_list_arr;
    /

    CREATE TABLE dept_email_list (
      dept_no NUMBER,
      email_addrs email_list_typ)
      NESTED TABLE email_addrs STORE AS email_addrs_nt
      (
    VARRAY COLUMN_VALUE STORE AS LOB
     dept_emails_lob);

### 5.2.5 Constructors for Multilevel Collections

Multilevel collection types are created by calling the constructor of the respective type, just like single-level collections and other object types.

The constructor for a multilevel collection type is a system-defined function that has the same name as the type and returns a new instance of it. Constructor parameters have the names and types of the attributes of the object type.

Example 5-15 shows the constructor call for the multilevel collection type `nt_country_typ`. The `nt_country_typ` constructor calls the `country_typ` constructor, which calls the `nt_location_typ`, which calls the `location_typ` constructor.

**Note:**

`nt_country_typ` is a multilevel collection because it is a nested table that contains another nested table as an attribute.

Example 5-15 Using Constructors for Multilevel Collections

    -- Requires 5-10 and HR sample schema
    INSERT INTO region_tab
    VALUES(1, 'Europe', nt_country_typ(
      country_typ( 'IT', 'Italy', nt_location_typ (
        location_typ(1000, '1297 Via Cola di Rie','00989','Roma', ''),
        location_typ(1100, '93091 Calle della Testa','10934','Venice','') )
        ),
      country_typ( 'CH', 'Switzerland', nt_location_typ (
        location_typ(2900, '20 Rue des Corps-Saints', '1730', 'Geneva', 'Geneve'),
        location_typ(3000, 'Murtenstrasse 921', '3095', 'Bern', 'BE') )
        ),
      country_typ( 'UK', 'United Kingdom', nt_location_typ (
        location_typ(2400, '8204 Arthur St', '', 'London', 'London'),
        location_typ(2500, 'Magdalen Centre, The Oxford Science Park', 'OX9 9ZB',
                     'Oxford', 'Oxford'),
        location_typ(2600, '9702 Chester Road', '09629850293', 'Stretford',
                     'Manchester') )
          )
      )
    );
