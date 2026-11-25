The Oracle C++ Call Interface (OCCI) is a C++ API that enables you to use the object-oriented features, native classes, and methods of the C++ programing language to access the Oracle database.

Topics:

- About Oracle C++ Call Interface (OCCI)

- OCCI Associative Relational and Object Interfaces

- The OCCI Navigational Interface

### 4.6.1 About Oracle C++ Call Interface (OCCI)

The OCCI interface is modeled on the JDBC interface and, like the JDBC interface, is easy to use. OCCI itself is built on top of OCI and provides the power and performance of OCI using an object-oriented paradigm.

OCI is a C API to the Oracle database. It supports the entire Oracle feature set and provides efficient access to both relational and object data, but it can be challenging to use—particularly if you want to work with complex, object data types. Object types are not natively supported in C, and simulating them in C is not easy. OCCI addresses this by providing a simpler, object-oriented interface to the functionality of OCI. It does this by defining a set of wrappers for OCI. By working with these higher-level abstractions, developers can avail themselves of the underlying power of OCI to manipulate objects in the server through an object-oriented interface that is significantly easier to program.

The Oracle C++ Call Interface, OCCI, can be roughly divided into three sets of functionalities, namely:

- Associative relational access

- Associative object access

- Navigational access

### 4.6.2 OCCI Associative Relational and Object Interfaces

The associative relational API and object classes provide SQL access to the database.

Through these interfaces, SQL is executed on the server to create, manipulate, and fetch object or relational data. Applications can access any data type on the server, including the following:

- Large objects

- Objects/Structured types

- Arrays

- References

### 4.6.3 The OCCI Navigational Interface

The navigational interface is a C++ interface that lets you seamlessly access and modify object-relational data in the form of C++ objects without using SQL.

The C++ objects are transparently accessed and stored in the database as needed.

With the OCCI navigational interface, you can retrieve an object and navigate through references from that object to other objects. Server objects are materialized as C++ class instances in the application cache.

An application can use OCCI object navigational calls to perform the following functions on the server's objects:

- Create, access, lock, delete, and flush objects

- Get references to the objects and navigate through them

  **See Also:**

  [Oracle C++ Call Interface Programmer's Guide](../lncpp/introduction-to-occi.md) for a complete account of how to build applications with the Oracle C++ API
