Oracle provides various ways to integrate Oracle object features with Java.

These interfaces enable you both to access SQL data from Java and to provide persistent database storage for Java objects.

Topics:

- JDBC Access to Oracle Object Data

- Data Mapping Strategies

- Java Object Storage

- Defining User-Defined Constructors in Java

- JDeveloper

### 4.7.1 JDBC Access to Oracle Object Data

JDBC (Java Database Connectivity) is a set of Java interfaces to the Oracle server.

Oracle provides tight integration between objects and JDBC. You can map SQL types to Java classes with considerable flexibility.

Oracle JDBC:

- Allows access to objects and collection types (defined in the database) in Java programs through dynamic SQL.

- Translates types defined in the database into Java classes through default or customizable mappings.

Version 2.0 of the JDBC specification supports object-relational constructs such as user-defined (object) types. JDBC materializes Oracle objects as instances of particular Java classes. Using JDBC to access Oracle objects involves creating the Java classes for the Oracle objects and populating these classes. You can either:

- Let JDBC materialize the object as a `STRUCT`. In this case, JDBC creates the classes for the attributes and populates them for you.

- Manually specify the mappings between Oracle objects and Java classes; that is, customize your Java classes for object data. The driver then populates the customized Java classes that you specify, which imposes a set of constraints on the Java classes. To satisfy these constraints, you can choose to define your classes according to either the `SQLData` interface or the `ORAData` interface.

  **See Also:**

  [Oracle Database JDBC Developer's Guide](../jjdbc/index.md) for complete information about JDBC

### 4.7.2 Data Mapping Strategies

Oracle SQLJ supports either strongly typed or weakly typed Java representations of object types, reference types (`REF`s), and collection types (varrays and nested tables) to be used in iterators or host expressions.

Strongly typed representations use a custom Java class that corresponds to a particular object type, `REF` type, or collection type and must implement the interface `oracle`.`sql`.`ORAData`. The Oracle JVM Web services Call-Out Utility can automatically generate such custom Java classes.

Weakly typed representations use the class `oracle`.`sql`.`STRUCT` (for objects), `oracle`.`sql`.`REF` (for references), or `oracle`.`sql`.`ARRAY` (for collections).

### 4.7.3 Java Object Storage

Oracle JVM Web services Call-Out Utility enables you to construct Java classes that map to existing SQL types. You can then access the SQL types from a Java application using JDBC.

You can also go in the other direction. That is, you can create SQL types that map to existing Java classes. This capability enables you to provide persistent storage for Java objects. Such SQL types are called SQL types of Language Java, or SQLJ object types. They can be used as the type of an object, an attribute, a column, or a row in an object table. You can navigationally access objects of such types—Java objects—through either object references or foreign keys, and you can query and manipulate such objects from SQL.

You create SQLJ types with a `CREATE TYPE` statement as you do other user-defined SQL types. For SQLJ types, two special elements are added to the `CREATE` `TYPE` statement:

- An `EXTERNAL` `NAME` phrase, used to identify the Java counterpart for each SQLJ attribute and method and the Java class corresponding to the SQLJ type itself

- A `USING` clause, to specify how the SQLJ type is to be represented to the server. The `USING` clause specifies the interface used to retrieve a SQLJ type and the kind of storage.

For example:

Example 4-2 Mapping SQL Types to Java Classes

    -- Mapping SQL Types to Java Classes example, not sample schema
    CREATE TYPE full_address AS OBJECT (a NUMBER);
    /

    CREATE OR REPLACE TYPE person_t AS OBJECT
      EXTERNAL NAME 'Person' LANGUAGE JAVA
      USING SQLData (
        ss_no NUMBER (9) EXTERNAL NAME 'socialSecurityNo',
        name varchar(100) EXTERNAL NAME 'name',
        address full_address EXTERNAL NAME 'addrs',
        birth_date date EXTERNAL NAME 'birthDate',
        MEMBER FUNCTION age  RETURN NUMBER EXTERNAL NAME 'age () return int',
        MEMBER FUNCTION addressf RETURN full_address
          EXTERNAL NAME 'get_address () return long_address',
        STATIC function createf RETURN person_t EXTERNAL NAME 'create ()
             return Person',
        STATIC function createf (name VARCHAR2, addrs full_address, bDate DATE)
          RETURN person_t EXTERNAL NAME 'create (java.lang.String, Long_address,
          oracle.sql.date) return Person',
        ORDER member FUNCTION compare (in_person person_t) RETURN NUMBER
          EXTERNAL NAME 'isSame (Person) return int')
    /

SQLJ types use the corresponding Java class as the body of the type; you do not specify a type body in SQL to contain implementations of the type's methods as you do with ordinary object types.

**See Also:**

[Oracle Database Java Developer’s Guide](../jjdev/database-as-web-service-consumer.md)

#### 4.7.3.1 Creating SQLJ Object Types

You can create SQLJ object types using SQL statements

The SQL statements to create SQLJ types and specify their mappings to Java are placed in a file called a deployment descriptor. Related SQL constraints and privileges are also specified in this file. The types are created when the file is executed.

Below is an overview of the process of creating SQL versions of Java types/classes:

1.  Design the Java types.
2.  Generate the Java classes.
3.  Create the SQLJ object type statements.
4.  Construct the JAR file. This is a single file that contains all the classes needed.
5.  Using the `loadjava` utility, install the Java classes defined in the JAR file.
6.  Execute the statements to create the SQLJ object types.

#### 4.7.3.2 Additional Notes About Mapping

The following are additional notes to consider when mapping of Java classes to SQL types:

- You can map a SQLJ static function to a user-defined constructor in the Java class. The return value of this function is of the user-defined type in which the function is locally defined.

- Java static variables are mapped to SQLJ static methods that return the value of the corresponding static variable identified by `EXTERNAL` `NAME`. The `EXTERNAL` `NAME` clause for an attribute is optional with a `SQLData` or `ORAData` representation.

- Every attribute in a SQLJ type of a SQL representation must map to a Java field, but not every Java field must be mapped to a corresponding SQLJ attribute: you can omit Java fields from the mapping.

- You can omit classes: you can map a SQLJ type to a non-root class in a Java class hierarchy without also mapping SQLJ types to the root class and intervening superclasses. Doing this enables you to hide the superclasses while still including attributes and methods inherited from them.

  However, you must preserve the structural correspondence between nodes in a class hierarchy and their counterparts in a SQLJ type hierarchy. In other words, for two Java classes `j_A` and `j_B` that are related through inheritance and are mapped to two SQL types `s_A` and `s_B`, respectively, there must be exactly one corresponding node on the inheritance path from `s_A` to `s_B` for each node on the inheritance path from `j_A` to `j_B`.

- You can map a Java class to multiple SQLJ types as long as you do not violate the restriction in the preceding paragraph. In other words, no two SQLJ types mapped to the same Java class can have a common supertype ancestor.

- If all Java classes are not mapped to SQLJ types, it is possible that an attribute of a SQLJ object type might be set to an object of an unmapped Java class. Specifically, to a class occurring above or below the class to which the attribute is mapped in an inheritance hierarchy. If the object's class is a superclass of the attribute's type/class, an error is raised. If it is a subclass of the attribute's type/class, the object is mapped to the most specific type in its hierarchy for which a SQL mapping exists

#### 4.7.3.3 SQLJ Type Evolution

You can evole SQLJ types using the `ALTER TYPE` statement.

The `ALTER` `TYPE` statement enables you to evolve a type by, for example, adding or dropping attributes or methods.

When a SQLJ type is evolved, an additional validation is performed to check the mapping between the class and the type. If the class and the evolved type match, the type is marked valid. Otherwise, the type is marked as pending validation.

Being marked as pending validation is not the same as being marked invalid. A type that is pending validation can still be manipulated with `ALTER` `TYPE` and `GRANT` statements, for example.

If a type that has a SQL representation is marked as pending evaluation, you can still access tables of that type using any DML or SELECT statement that does not require a method invocation.

You cannot, however, execute DML or `SELECT` statements on tables of a type that has a serializable representation and has been marked as pending validation. Data of a serializable type can be accessed only navigationally, through method invocations. These are not possible with a type that is pending validation. However, you can still re-evolve the type until it passes validation.

See "[Type Evolution](type-evolution.md)".

#### 4.7.3.4 Constraints

For SQLJ types having a SQL representation, the same constraints can be defined as for ordinary object types.

Constraints are defined on tables, not on types, and are defined at the column level. The following constraints are supported for SQLJ types having a SQL representation:

- Unique constraints

- Primary Key

- Check constraints

- `NOT NULL` constraints on attributes

- Referential constraints

The `IS` `OF` `TYPE` constraint on column substitutability is supported, too, for SQLJ types having a SQL representation. See "[Constraining Substitutability](inheritance-in-sql-object-types.md)".

#### 4.7.3.5 Querying SQLJ Objects

SQLJ types can be queried just like ordinary SQL object types.

- Query SQLJ types just like ordinary object types.

Methods called in a `SELECT` statement must not attempt to change attribute values.

#### 4.7.3.6 Inserting Java Objects

You can insert Java objects into tables.

Inserting a row in a table containing a column of a SQLJ type requires a call to the type's constructor function to create a Java object of that type.

- Use an implicit, system-generated constructor, or define a static function that maps to a user-defined constructor in the Java class.

#### 4.7.3.7 Updating SQLJ Objects

You can update SQLJ objects several ways.

SQLJ objects can be updated by:

- Using an `UPDATE` statement to modify the value of one or more attributes

- Invoking a method that updates the attributes and returns `SELF`—that is, returns the object itself with the changes made.

For example, suppose that `raise()` is a member function that increments the `salary` field/attribute by a specified amount and returns `SELF`. The following statement gives every employee in the object table `employee_objtab` a raise of `1000`:

`UPDATE employee_objtab SET c=c.raise(1000);`

A column of a SQLJ type can be set to `NULL` or to another column using the same syntax as for ordinary object types. For example, the following statement assigns column `d` to column `c`:

`UPDATE employee_reltab SET c=d;`

### 4.7.4 Defining User-Defined Constructors in Java

When you implement a user-defined constructor in Java, the supply the string supplied as the implementing routine must correspond to a static function. For the return type of the function, specify the Java type mapped to the SQL type.

When you implement a user-defined constructor in Java, the string supplied as the implementing routine must correspond to a static function. For the return type of the function, specify the Java type mapped to the SQL type.

Example 4-3 is an example of a type declaration that involves a user-defined constructor implemented in Java.

Example 4-3 Defining a User-Defined Constructor in Java

    -- Defining a User-Defined Constructor in Java example, not sample schema
    CREATE TYPE person1_typ AS OBJECT
     EXTERNAL NAME 'pkg1.J_Person' LANGUAGE JAVA
     USING SQLData(
      name VARCHAR2(30),
      age NUMBER,
      CONSTRUCTOR FUNCTION person1_typ(SELF IN OUT NOCOPY person1_typ, name VARCHAR2,
                                       age NUMBER) RETURN SELF AS RESULT
      AS LANGUAGE JAVA
        NAME 'pkg1.J_Person.J_Person(java.lang.String, int) return J_Person')
    /

### 4.7.5 JDeveloper

Oracle JDeveloper is a full-featured, cross-platform, integrated development environment for creating multitier Java applications that is well integrated with Oracle Application Server and Database.

Oracle JDeveloper enables you to develop, debug, and deploy Java client applications, dynamic HTML applications, web and application server components, JavaBean components, and database stored procedures based on industry-standard models.

JDeveloper is also the integrated development environment for ADF and TopLink.

#### 4.7.5.1 Application Development Framework (ADF)

ADF is a framework for building scalable enterprise Java EE applications. Developers can use ADF to build applications where the application data is persisted to Oracle Object tables as well as other schema objects.

#### 4.7.5.2 TopLink

TopLink is a framework for mapping Java objects to a variety of persistence technologies, including databases, and provides facilities to build applications leveraging Oracle Objects.
