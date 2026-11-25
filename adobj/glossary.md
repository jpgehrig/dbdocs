### atomically null object

An object whose value is `NULL` is called atomically null. An atomically null object is different from an object that has null values for all its attributes.

### Binary Large Object (BLOB)

A large object data type whose value consists of raw binary data.

### character large object (CLOB)

The large object (LOB) data type whose value is composed of character data corresponding to the database character set.

### column object

An object that is stored as a column of a relational database table (as opposed to an object table). A column object can also be an attribute of another object. A column object is also known as a stored inline object or an embedded object.

### embedded object attribute

An attribute of a column object.

### dynamic method dispatch

A method call that is dispatched at run-time to the nearest method implementation when there are multiple implementations of the same method using overriding.

### leaf-level scalar object

An object that is not a collection and is not composed of other types.

### leaf-level scalar attribute

An attribute of a leaf-level scalar object.

### literal invocation

An invocation where all arguments are literals or invocations of literal methods. Arguments cannot be variables.

### materialized view

A view that contains both the query and its results.

### multilevel collection type

Collection types whose elements are collection types, either directly or indirectly.

### multiset operators

An operator that combines elements of two nested tables into a single nested table.

### nested table

An unordered set of data elements of the same data type.

### normalize

The process of removing redundancy in data by separating the data into multiple tables.

### object column

A column of user-defined types or abstract data types (ADT)s .

### object identifier

Identifier for a row object which can be either system-generated (default) or based on a primary key using the `CREATE` `TABLE` statement.

### object instance

An instance of an object type. Also referred to as an object.

### object table

A table in which each row represents an object. See row object.

### object type

The type of the object instance. It is similar to a record that has methods. Object types are user-defined.

### outer table

A table that contains a nested table.

### pinning

Fetching.

### PL/SQL

The Oracle procedural language extension to SQL.

### polymorphism

Allows handling data types and methods generically using the same interface. In polymorphic overriding, subtypes redefine a method they have inherited. In polymorphic overloading, there may be several versions of the same method, with different parameters.

### primary key

The column or set of columns specified in the PRIMARY KEY constraint of a table.

### REF

An Oracle built-in data type that encapsulates references to row objects of a specified object type.

### row object

An object that is stored in a complete row in an object table.

### specializing

Adding new attributes or methods to a subtype that the parent supertype does not have, or changing the implementation of a method or methods.

### stored procedure

A PL/SQL block that is stored in the database and can be executed from an application.

### substitutability

A supertype is substitutable if one of its subtypes can substitute or stand in for it in a variable or column whose declared type is the supertype.

### type evolution

The modification of a subtype of a type, typically using an `ALTER` statement.

### VARRAY

An ordered set of data elements, that are of the same data type or a subtype of the declared data type.
