### Application requester (AR)

Used by the application, AR assumes the client component in a classical client/server configuration acting on the behalf of the application making all DRDA protocol requests.

### Application server (AS)

Application Server. Assumes the Server component in a classical client/server configuration, acting as the DRDA protocol front end for the server, processing DRDA requests, performing server function calls and returning results to the client.

### AS/400

Application System/400, an IBM platform.

### CCSID

Coded Character Set Identifier (IBM/DRDA terminology). A 16bit number that includes a specific set of encoding scheme identifiers, character set identifiers code page identifiers, and other information that uniquely identifies the coded graphic character representation.

Examples include: 500 INTL EBCDIC \[CECP: Belgium, Canada (AS/400\*), Switzerland, International Latin1\], 819 ISO 88591 ASCII \[ISO 88591: Latin Alphabet Number 1Latin1 countries and regions\], 850 LATIN1 PCDATA \[PC Data: MLP 222 Latin Alphabet Number 1Latin1 Countries and Regions\]

Special cases: CCSID 65534 (defer codepage to lower level definition) and CCSID 65535 (binary data).

### Database Request Module (DBRM)

(IBM/DRDA terminology). This is a proprietary on-disk file that contains the SQL statements of an embedded SQL application after it has been preprocessed. The post-processed application source will then contain only a statement reference number indicating the SQL statement to be used in the DBRM. The statements are externalized so that the database system can fully analyze and optimize execution of the SQL.

### DB2

Short for IBM DB2, the database produced by IBM.

### DBCS

In IBM terminology, this is a Doublebyte Character Set, any character set that has character code points of exactly 2 bytes in length.

### Dedicated Instance Configuration

an Oracle Database Provider for DRDA configuration where a single `RDB_MAP` entry is made for each Oracle Database Provider for DRDA instance. This approach is used for IBM DB2 Database for z/OS DRDA clients. See Multiplexed Instance Configuration.

### Distributed Data Management (DDM)

DDM architecture provides the overall command and reply structure used by the distributed database. Fewer than 20 commands are required to implement all of the distributed database functions for communication between the application requester (client) and the application server.

### Distributed Relational Database Architecture

Distributed Relational Database Architecture (DRDA) is an open, published architecture that enables communication between applications and database systems on disparate platforms, whether those applications and database systems are provided by the same or different vendors and whether the platforms are the same or different hardware/software architectures. DRDA is a combination of other architectures and the environmental rules and process model for using them. The architectures that actually comprise DRDA are Distributed Data Management (DDM) and Formatted Data Object Content Architecture (FD:OCA).

### DRDA

See Distributed Relational Database Architecture.

### DRDA Package

(IBM/DRDA terminology). A "package" is a collection of SQL statements and attributes defined in an embedded SQL application. A Package is created by binding a resource file (DBRM) though DRDA BIND request commands.

### Dynamic SQL

A Package may contain a mix of Static SQL and Dynamic SQL. Dynamic SQL is SQL that is not preformed in the application (and generally considered adhoc, even if it is constructed by the application). The primary differences between static and dynamic SQL is that static SQL is preloaded into the database as part of the Package and dynamic SQL must be sent to the database a runtime for execution. Historically, Oracle only implements dynamic SQL, relying on the strength of it's cursor caching facility to enhance the speed of SQL execution which largely negates the need for static SQL. See Static SQL.

### FD:OCA

See Formatted Data Object Content Architecture.

### Formatted Data Object Content Architecture

The Formatted Data Object Content Architecture (FD:OCA) provides the data definition architectural base for DRDA. Descriptors defined by DRDA provide layout and datatype information for all the information routinely exchanged between the application requesters and servers. A descriptor organization is defined by DRDA to allow dynamic definition of user data that flows as part of command or reply data. DRDA also specifies that the descriptors only have to flow once per answer set, regardless of the number of rows actually returned, thus minimizing data traffic on the wire.

### IBM

International Business Machines, the company responsible DB2 Database and DB2 group of products.

### MBCS

In IBM terminology, this is a Multibyte Character Set, any character set that may contain variable-length character code points. An example is Unicode (UTF-8). Another example is when a singlebyte character set and a doublebyte character set are combined to make a multibyte character set.

### Multiplexed Instance Configuration

an Oracle Database Provider for DRDA configuration where additional `DATA_PORT` entries may be specified with different host name or IP addresses, and unallocated network port numbers. See Dedicated Instance Configuration.

### Oracle Call Interface (OCI)

OCI is a set of C-language software APIs that provide an interface to the Oracle database.

OCI consists of procedural APIs that perform database administration tasks and for using PL/SQL or SQL to query, access, and manipulate data.

### SBCS

In IBM terminology, this is a Singlebyte Character Set, any character set that has character code points of exactly 1 byte in length.

### Special Register

In DB2, a special register is a storage area defined for an application process, and used to store information that can be referenced in SQL statements. A reference to a special register is a reference to a value provided by the current server. If the value is a string, its CCSID is a default CCSID of the current server.

### Static SQL

A Package may contain a mix of Static SQL and Dynamic SQL. Static SQL is SQL that is already written as part of the application. It's syntax and use of in-program variables (bind variables) is fixed in the code and cannot be changed during execution. Also, the SQL is not part of the application. It is extracted from the source and uploaded as part of the Package, further fixing its form and preventing malicious modification of it's function. It is presumed that static SQL is also heavily analyzed in advance to allow for a more efficient execution plan. Historically, DB2 invented static SQL for applications that were primarily batch oriented and thus not subject to the idea of dynamic construction. See Dynamic SQL.

### SQL Type

In IBM's DB2 terminology, this is an interface value for datatype.

### SQLAM Level

SQLAM stands for SQL Application Manager. SQLAM Level 8 is the support level provided by Oracle's implementation of DRDA.

### UOW

In IBM terminology, this is a Unit of Work, a resource designation for all changes to a database within the scope of a transaction. DRDA maintains a Distributed (or Remote) Unit of Work between a client and a database for the duration of the application's transaction.
