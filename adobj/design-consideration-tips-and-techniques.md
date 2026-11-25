There are assorted tips on various aspects of working with Oracle object types.

Topics:

- Whether to Evolve a Type or Create a Subtype

- How ANYDATA Differs from User-Defined Types

- Polymorphic Views: An Alternative to an Object View Hierarchy

- The SQLJ Object Type

- Miscellaneous Design Tips

### 9.13.1 Whether to Evolve a Type or Create a Subtype

As an application goes through its life cycle, the question often arises whether to change an existing object type or to create a specialized subtype to meet new requirements. The answer depends on the nature of the new requirements and their context in the overall application semantics. Here are two examples:

#### Changing a Widely Used Base Type

Suppose that we have an object type `address` with attributes `Street`, `State`, and `ZIP`:

    CREATE TYPE address AS OBJECT (
      Street  VARCHAR2(80),
      State   VARCHAR2(20),
      ZIP     VARCHAR2(10));
    /

We later find that we need to extend the `address` type by adding a `Country` attribute to support addresses internationally. Is it better to create a subtype of `address` or to evolve the `address` type itself?

With a general base type that has been widely used throughout an application, it is better to implement the change using type evolution.

#### Adding Specialization

Suppose that an existing type hierarchy of Graphic types (for example, curve, circle, square, text) needs to accommodate an additional variation, namely, Bezier curve. To support a new specialization of this sort that does not reflect a shortcoming of the base type, we should use inheritance and create a new subtype `BezierCurve` under the `Curve` type.

To sum up, the semantics of the required change dictates whether we should use type evolution or inheritance. For a change that is more general and affects the base type, use type evolution. For a more specialized change, implement the change using inheritance.

### 9.13.2 How ANYDATA Differs from User-Defined Types

`ANYDATA` is an Oracle-supplied type that can hold instances of any Oracle data type, whether built-in or user-defined. `ANYDATA` is a self-describing type and supports a reflection-like API that you can use to determine the shape of an instance.

While both inheritance, through the substitutability feature, and `ANYDATA` provide the polymorphic ability to store any of a set of possible instances in a placeholder, the two models give the capability two very different forms.

In the inheritance model, the polymorphic set of possible instances must form part of a single type hierarchy. A variable can potentially hold instances only of its defined type or of its subtypes. You can access attributes of the supertype and call methods defined in the supertype (and potentially overridden by the subtype). You can also test the specific type of an instance using the IS OF and the TREAT operators.

`ANYDATA` variables, however, can store heterogeneous instances. You cannot access attributes or call methods of the actual instance stored in an `ANYDATA` variable (unless you extract out the instance). You use the `ANYDATA` methods to discover and extract the type of the instance. `ANYDATA` is a very useful mechanism for parameter passing when the function/procedure does not care about the specific type of the parameter(s).

Inheritance provides better modeling, strong typing, specialization, and so on. Use `ANYDATA` when you simply want to be able to hold one of any number of possible instances that do not necessarily have anything in common.

### 9.13.3 Polymorphic Views: An Alternative to an Object View Hierarchy

[Applying an Object Model to Relational Data](applying-an-object-model-to-relational-data.md) describes how to build up a view hierarchy from a set of object views each of which contains objects of a single type. Such a view hierarchy enables queries on a view within the hierarchy to see a polymorphic set of objects contained by the queried view or its subviews.

As an alternative way to support such polymorphic queries, you can define an object view based on a query that returns a polymorphic set of objects. This approach is especially useful when you want to define a view over a set of tables or views that already exists.

For example, an object view of `Person_t` can be defined over a query that returns `Person_t` instances, including `Employee_t` instances. The following statement creates a view based on queries that select persons from a `persons` table and employees from an `employees` table.

    CREATE VIEW Persons_view OF Person_t AS
    SELECT Person_t(...) FROM persons
    UNION ALL
    SELECT TREAT(Employee_t(...) AS Person_t) FROM employees;

An `INSTEAD OF` trigger defined for this view can use the `VALUE` function to access the current object and to take appropriate action based on the object's most specific type.

Polymorphic views and object view hierarchies have these important differences:

- Addressability: In a view hierarchy, each subview can be referenced independently in queries and DML statements. Thus, every set of objects of a particular type has a logical name. However, a polymorphic view is a single view, so you must use predicates to obtain the set of objects of a particular type.

- Evolution: If a new subtype is added, a subview can be added to a view hierarchy without changing existing view definitions. With a polymorphic view, the single view definition must be modified by adding another `UNION` branch.

- DML Statements: In a view hierarchy, each subview can be either inherently updatable or can have its own `INSTEAD OF` trigger. With a polymorphic view, only one `INSTEAD OF` trigger can be defined for a given operation on the view.

### 9.13.4 The SQLJ Object Type

This section discusses the SQLJ object type.

Topics:

- The Intended Use of SQLJ Object Types

- Actions Performed When Creating a SQLJ Object Type

- Uses of SQLJ Object Types

- Uses of Custom Object Types

- Differences Between SQLJ and Custom Object Types Through JDBC

#### 9.13.4.1 The Intended Use of SQLJ Object Types

According to the Information Technology - SQLJ - Part 2 document (SQLJ Standard), a SQLJ object type is a database object type designed for Java. A SQLJ object type maps to a Java class. Once the mapping is registered through the extended SQL `CREATE TYPE` command (a DDL statement), the Java application can insert or select the Java objects directly into or from the database through an Oracle JDBC driver. This enables the user to deploy the same class in the client, through JDBC, and in the server, through SQL method dispatch.

#### 9.13.4.2 Actions Performed When Creating a SQLJ Object Type

The extended SQL `CREATE TYPE` command:

- Populates the database catalog with the external names for attributes, functions, and the Java class. Also, dependencies between the Java class and its corresponding SQLJ object type are maintained.

- Validates the existence of the Java class and validates that it implements the interface corresponding to the value of the `USING` clause.

- Validates the existence of the Java fields (as specified in the `EXTERNAL NAME` clause) and whether these fields are compatible with corresponding SQL attributes.

- Generates an internal class to support constructors, external variable names, and external functions that return `self` as a result.

#### 9.13.4.3 Uses of SQLJ Object Types

The SQLJ object type is a special case of SQL object type in which all methods are implemented in a Java class.

The mapping between a Java class and its corresponding SQL type is managed by the SQLJ object type specification. That is, the SQLJ Object type specification cannot have a corresponding type body specification.

Also, the inheritance rules among SQLJ object types specify the legal mapping between a Java class hierarchy and its corresponding SQLJ object type hierarchy. These rules ensure that the SQLJ Type hierarchy contains a valid mapping. That is, the supertype or subtype of a SQLJ object type has to be another SQLJ object type.

#### 9.13.4.4 Uses of Custom Object Types

The custom object type is the Java interface for accessing SQL object types. A SQL object type may include methods that are implemented in languages such as PLSQL, Java, and C. Methods implemented in Java in a given SQL object type can belong to different unrelated classes. That is, the SQL object type does not map to a specific Java class.

In order for the client to access these objects, Oracle JVM Web Services Call-Out Utility can be used to generate the corresponding Java class. Furthermore, the user has to augment the generated classes with the code of the corresponding methods. Alternatively, the user can create the class corresponding to the SQL object type.

At runtime, the JDBC user has to register the correspondence between a SQL Type name and its corresponding Java class in a map.

**See Also:**

[Oracle Database Java Developer’s Guide](../jjdev/database-as-web-service-consumer.md)

#### 9.13.4.5 Differences Between SQLJ and Custom Object Types Through JDBC

The following table summarizes the differences between SQLJ object types and custom object types.

Table 9-1 Differences Between SQLJ and Custom Object Types

| Feature        | SQLJ Object Type Behavior                                                                                                                                                                                                                          | Custom Object Type Behavior                                                                                                                                                                                                                |
|:---------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Typecodes      | Use the `OracleTypes.JAVA_STRUCT` typecode to register a SQLJ object type as a SQL `OUT` parameter. The `OracleTypes.JAVA_STRUCT` typecode is also used in the `_SQL_TYPECODE` field of a class implementing the `ORAData` or `SQLData` interface. | Use the `OracleTypes.STRUCT` typecode to register a custom object type as a SQL `OUT` parameter. The `OracleTypes.STRUCT` typecode is also used in the `_SQL_TYPECODE` field of a class implementing the `ORAData` or `SQLData` interface. |
| Creation       | Create a Java class implementing the `SQLData` or `ORAData` and `ORADataFactory `interfaces first and then load the Java class into the database. Next, you issue the extended SQL `CREATE TYPE` command for SQLJ object type.                     | Issue the extended SQL `CREATE TYPE` command for a custom object type and then create the `SQLData` or `ORAData` Java wrapper class using Oracle JVM Web Services Call-Out Utility or do this manually.                                    |
| Method Support | Supports external names, constructor calls, and calls for member functions with side effects.                                                                                                                                                      | There is no default class for implementing type methods as Java methods. Some methods may also be implemented in SQL.                                                                                                                      |
| Type Mapping   | Type mapping is automatically done by the extended SQL `CREATE TYPE` command. However, the SQLJ object type must have a defining Java class on the client.                                                                                         | Register the correspondence between SQL and Java in a type map. Otherwise, the type is materialized as `oracle.sql.STRUCT`.                                                                                                                |
| Inheritance    | There are rules for mapping SQL hierarchy to a Java class hierarchy. See the [Oracle Database SQL Language Reference](../sqlrf/Introduction-to-Oracle-SQL.md) for a complete description of these rules.                                           | There are no mapping rules.                                                                                                                                                                                                                |

### 9.13.5 Miscellaneous Design Tips

You should know these miscellaneous tips for designing with Oracle objects.

#### 9.13.5.1 Column Substitutability and the Number of Attributes in a Hierarchy

If a column or table is of type `T`, Oracle adds a hidden column for each attribute of type `T` and, if the column or table is substitutable, for each attribute of every subtype of `T`, to store attribute data. A hidden `typeid` column is added as well, to keep track of the type of the object instance in a row.

The number of columns in a table is limited to 1,000. A type hierarchy with a number of total attributes approaching 1,000 puts you at risk of running up against this limit when using substitutable columns of a type in the hierarchy. To avoid problems as a result of this, consider one of the following options for dealing with a hierarchy that has a large number of total attributes:

- Use views

- Use `REF`s

- Break up the hierarchy

#### 9.13.5.2 Circular Dependencies Among Types

Avoid creating circular dependencies among types. In other words, do not create situations in which a method of type `T` returns a type `T1`, which has a method that returns a type `T`.
