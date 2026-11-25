Information integration is a challenge that affects many organizations because they may run several different database systems.

Each of these systems store data and has a set of applications that run against the data. This data is just bits and bytes on a file system - and only a database can turn the bits and bytes of data into business information. Integration and consolidation of all business information allows an organization to take advantage of the synergies inherent in business information.

Consolidation of all data into one database system is often difficult. This is primarily because many of the applications that run against one database may not have an equivalent application that runs against another. Until migrating data to one consolidated database system is possible, the heterogeneous database systems must work together.

There are several problems to overcome before interoperability is possible. The database systems can be accessed using different interfaces, different data types, different capabilities, and different ways of handling errors. Even when one relational database tries to access another relational database, the differences are significant. In this situation, the common features of the databases include data access through SQL, two-phase commit protocol, and similar data types.

There are also significant differences. SQL dialects can be different, as can transaction semantics. There can be some data types in one database that do not exist in the other. The most significant area of difference is in the data dictionaries of the two databases. Most data dictionaries contain similar information, but the information is structured for each data dictionary in a different way. There are several ways of overcoming this problem. This guide describes Oracle's approach to synchronously access information from multiple sources.

**Parent topic:** [Introduction to Heterogeneous Connectivity](introduction.md)
