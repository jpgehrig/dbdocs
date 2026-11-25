OCI is a set of C library functions that applications can use to manipulate data and schemas in an Oracle database.

- About Oracle Call Interface (OCI)

- Associative Access in OCI Programs

- Navigational Access in OCI Programs

### 4.4.1 About Oracle Call Interface (OCI)

OCI supports both traditional 3GL and object-oriented techniques for database access, as explained in the following sections.

An important component of OCI is a set of calls to manage a workspace called the object cache. The object cache is a memory block on the client side that allows programs to store entire objects and to navigate among them without additional round trips to the server.

The object cache is completely under the control and management of the application programs using it. The Oracle server has no access to it. The application programs using it must maintain data coherency with the server and protect the workspace against simultaneous conflicting access.

OCI provides functions to

- Access objects on the server using SQL.

- Access, manipulate and manage objects in the object cache by traversing pointers or `REF`s.

- Convert Oracle dates, strings and numbers to C data types.

- Manage the size of the object cache's memory.

OCI improves concurrency by allowing individual objects to be locked. It improves performance by supporting complex object retrieval.

OCI developers can use the object type translator to generate the C data types corresponding to a Oracle object types.

**See Also:**

[Oracle Call Interface Programmer's Guide](../lnoci/oci-object-relational-programming.md) for more information about using objects with OCI

### 4.4.2 Associative Access in OCI Programs

OCI programs support associative access to objects with an API that can manipulate object data.

Traditionally, 3GL programs manipulate data stored in a relational database by executing SQL statements and PL/SQL procedures. Data is usually manipulated on the server without incurring the cost of transporting the data to the client(s). OCI supports this associative access to objects by providing an API for executing SQL statements that manipulate object data. Specifically, OCI enables you to:

- Execute SQL statements that manipulate object data and object type schema information

- Pass object instances, object references (`REF`s), and collections as input variables in SQL statements

- Return object instances, `REF`s, and collections as output of SQL statement fetches

- Describe the properties of SQL statements that return object instances, `REF`s, and collections

- Describe and execute PL/SQL procedures or functions with object parameters or results

- Synchronize object and relational functionality through enhanced commit and rollback functions

See "[Associative Access in Pro\*C/C++](pro-c-cpp.md)".

### 4.4.3 Navigational Access in OCI Programs

OCI programs provide navigational access by means of an API.

In the object-oriented programming paradigm, applications model their real-world entities as a set of inter-related objects that form graphs of objects. The relationships between objects are implemented as references. An application processes objects by starting at some initial set of objects, using the references in these initial objects to traverse the remaining objects, and performing computations on each object. OCI provides an API for this style of access to objects, known as navigational access. Specifically, OCI enables you to:

- Cache objects in memory on the client machine

- Dereference an object reference and pin the corresponding object in the object cache. The pinned object is transparently mapped in the host language representation.

- Notify the cache when the pinned object is no longer needed

- Fetch a graph of related objects from the database into the client cache in one call

- Lock objects

- Create, update, and delete objects in the cache

- Flush changes made to objects in the client cache to the database

See "[Navigational Access in Pro\*C/C++](pro-c-cpp.md)".

### 4.4.4 Object Cache

To support high-performance navigational access of objects, OCI runtime provides an object cache for caching objects in memory.

The object cache supports references (`REF`s) to database objects in the object cache, the database objects can be identified (that is, pinned) through their references. Applications do not need to allocate or free memory when database objects are loaded into the cache, because the object cache provides transparent and efficient memory management for database objects.

Also, when database objects are loaded into the cache, they are transparently mapped into the host language representation. For example, in the C programming language, the database object is mapped to its corresponding C structure. The object cache maintains the association between the object copy in the cache and the corresponding database object. Upon transaction commit, changes made to the object copy in the cache are propagated automatically to the database.

The object cache maintains a fast look-up table for mapping `REF`s to objects. When an application dereferences a `REF` and the corresponding object is not yet cached in the object cache, the object cache automatically sends a request to the server to fetch the object from the database and load it into the object cache. Subsequent dereferences of the same `REF` are faster because they become local cache access and do not incur network round-trips.

To notify the object cache that an application is accessing an object in the cache, the application pins the object; when it is finished with the object, it unpins it. The object cache maintains a pin count for each object in the cache. The count is incremented upon a pin call and decremented upon an unpin call. When the pin count goes to zero, it means the object is no longer needed by the application.

The object cache uses a least-recently used (LRU) algorithm to manage the size of the cache. When the cache reaches the maximum size, the LRU algorithm frees candidate objects with a pin count of zero.

### 4.4.5 Building an OCI Program That Manipulates Objects

You can build an OCI program to manipulate objects by representing types in the C host language format.

When you build an OCI program that manipulates objects, you must complete the following general steps

1.  Define the object types that correspond to the application objects.
2.  Execute the SQL DDL statements to populate the database with the necessary object types.
3.  Represent the object types in the host language format.
    For example, to manipulate instances of the object types in a C program, you must represent these types in the C host language format. You can do this by representing the object types as C structs. You can use a tool provided by Oracle called the Object Type Translator (OTT) to generate the C mapping of the object types. The OTT puts the equivalent C structs in header (\*.h) files. You include these \*.h files in the \*.c files containing the C functions that implement the application.
4.  Construct the application executable by compiling and linking the application's \*.c files with the OCI library.
    **See Also:**

    [Oracle Call Interface Programmer's Guide](../lnoci/oci-object-relational-programming.md) for tips and techniques for using OCI program effectively with objects

### 4.4.6 Defining User-Defined Constructors in C

When defining a user-defined constructor in C, you must specify `SELF` (and you may optionally specify `SELF` `TDO`) in the `PARAMETERS` clause.

On entering the C function, the attributes of the C structure that the object maps to are all initialized to `NULL`. The value returned by the function is mapped to an instance of the user-defined type.

Example 4-1 shows how to define a user-defined constructor in C.

Example 4-1 Defining a User-Defined Constructor in C

    CREATE LIBRARY person_lib TRUSTED AS STATIC
    /

    CREATE TYPE person AS OBJECT
      (  name VARCHAR2(30),
         CONSTRUCTOR FUNCTION person(SELF IN OUT NOCOPY person, name VARCHAR2)
             RETURN SELF AS RESULT);
    /

    CREATE TYPE BODY person IS
        CONSTRUCTOR FUNCTION person(SELF IN OUT NOCOPY person, name VARCHAR2)
             RETURN SELF AS RESULT
        IS EXTERNAL NAME "cons_person_typ" LIBRARY person_lib WITH CONTEXT
        PARAMETERS(context, SELF, name OCIString, name INDICATOR sb4);
    END;/

The `SELF` parameter is mapped like an `IN` parameter, so in the case of a `NOT` `FINAL` type, it is mapped to `(dvoid *)`, not `(dvoid **)`. The return value's `TDO` must match the `TDO` of `SELF` and is therefore implicit. The return value can never be null, so the return indicator is implicit as well.
