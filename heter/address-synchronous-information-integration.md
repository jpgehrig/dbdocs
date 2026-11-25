Using an Oracle Database gateway, you can access data anywhere in a distributed database system without being required to know either the location of the data or how it is stored.

If a client program must access or modify data on several Oracle databases, it can open connections to each of them. This approach, however, has several drawbacks, including the following:

- To join data from the databases, the client must have logic allowing that.

- To guarantee data integrity, the client must have transaction coordination logic.

Oracle provides another approach called distributed processing, where the client connects to one Oracle database and shifts the burden of joining data and transaction coordination to that database. The database to which the client program connects is called the local database. Any database other than this one is a remote database. The client program can access objects at any of the remote databases using database links. The Oracle query processor takes care of the joins and its transaction engine takes care of the transaction coordination.

The approach that Oracle took to solve the heterogeneous connectivity problem is to allow a non-Oracle system to be one of the remote nodes in the previously described scenario. The remote non-Oracle system functions as a remote Oracle system. The non-Oracle system uses the same SQL dialect and the same data dictionary structure as an Oracle system. Access to a non-Oracle system is done through Heterogeneous Services.

The work done by the Heterogeneous Services component is, for the most part, completely transparent to the end user. With only a few exceptions (these are noted in later chapters), you are not required to do anything different to access a non-Oracle system than is required for accessing an Oracle system. The Heterogeneous Services component is used as the foundation for implementing Oracle's access to non-Oracle databases.

An Oracle Database gateway works in conjunction with the Heterogeneous Services component of Oracle Database to access a particular, commercially available, non-Oracle system for which that Oracle Database gateway was designed. For example, you use the Oracle Database Gateway for Sybase to access a Sybase database. Oracle also provides an Oracle Database Gateway for ODBC which enables you to use ODBC drivers to access non-Oracle databases.

**Note:**

The ODBC drivers that are required by Oracle Database Gateway for ODBC are not supplied by Oracle. Users must obtain these drivers from other vendors.

Oracle also offers asynchronous information integration products. Those products are not discussed in this guide. Briefly, these products include:

- Oracle GoldenGate

  Oracle GoldenGate provides real-time capture, transformation, routing, and delivery of database transactions across heterogeneous systems. The software facilitates high-performance, low-impact data movement with low latency to a wide variety of databases and platforms while maintaining transaction integrity.

- Messaging Gateway

  The Messaging Gateway enables communication between Oracle Database and non-Oracle messaging systems.

- Open System Interfaces

  Oracle offers a number of open interfaces, such as OCI, JDBC, and ODBC, that enable customers to use third-party applications or to write their own client applications to access Oracle Database.

**Parent topic:** [Introduction to Heterogeneous Connectivity](introduction.md)
