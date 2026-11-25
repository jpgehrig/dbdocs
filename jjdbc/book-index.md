A  B  C  D  E  F  G  I  J  K  L  M  N  O  P  R  S  T  U  W  X  

------------------------------------------------------------------------

## A

- Accessing PL/SQL Associative Arrays [4.2.6](Oracle-extensions.md)
- ANYDATA [4.5.4](Oracle-extensions.md)
- ANYTYPE [4.5.4](Oracle-extensions.md)
- application continuity
  - configuring Oracle database [28.2](application-continuity.md)
  - configuring Oracle JDBC [28.1](application-continuity.md)
  - delaying the reconnection [28.7](application-continuity.md)
  - disabling replay [28.10](application-continuity.md)
  - identifying request boundaries [28.4](application-continuity.md)
  - logical transaction identifier [27.1](transaction-guard.md)
  - registering a connection callback [28.6](application-continuity.md)
  - retaining mutable values [28.8](application-continuity.md)
  - transaction guard [28](application-continuity.md)
- ARRAY
  - objects, creating [16.4.1](Oracle-collections.md)
- arrays
  - defined [16.1.1](Oracle-collections.md)
  - getting [16.4.2.6](Oracle-collections.md)
  - named [16.1.1](Oracle-collections.md)
  - passing to callable statement [16.4.3](Oracle-collections.md)
  - retrieving from a result set [16.4.2.1](Oracle-collections.md)
  - retrieving partial arrays [16.4.2.5](Oracle-collections.md)
  - using type maps [16.5](Oracle-collections.md)
  - working with [16.1.1](Oracle-collections.md)
- at-most-once execution [27.1](transaction-guard.md)
- authentication (security) [9.4](client-side-security.md)
- auto-commit [2.3.8](JDBC-getting-started.md)
- auto-commit mode
  - disabling [C.2.1](JDBC-coding-tips.md)
  - result set behavior [C.2.1](JDBC-coding-tips.md)

------------------------------------------------------------------------

## B

- batch jobs, authenticating users in [9.10](client-side-security.md)
- batch updates--see update batching [21.1](performance-extensions.md)
- BFILE
  - class [4.3.1](Oracle-extensions.md)
  - defined [12.4](Java-streams-in-JDBC.md)
- BFILE locator, selecting [4.3.1](Oracle-extensions.md)
- BLOB
  - class [4.3.1](Oracle-extensions.md)
  - locators
    - selecting [4.3.1](Oracle-extensions.md)
- branch qualifier (distributed transactions) [32.2.5](distributed-transactions.md)

------------------------------------------------------------------------

## C

- CachedRowSet [18.2](JDBC-Rowsets.md)
- caching, client-side
  - Oracle use for scrollable result sets [17.1](resultset.md)
- callable statement
  - using getOracleObject() method [11.4.2](accessing-and-manipulating-Oracle-data.md)
- cancelling
  - SQL statements [E.1.4](JDBC-troubleshooting.md)
- casting return values [11.4.5](accessing-and-manipulating-Oracle-data.md)
- catalog arguments (DatabaseMetaData) [A.5.4](JDBC-reference-information.md)
- character sets [4.4.3](Oracle-extensions.md)
- CHAR columns
  - using setFixedCHAR() to match in WHERE [11.4.7.2](accessing-and-manipulating-Oracle-data.md)
- CLOB
  - class [4.3.1](Oracle-extensions.md)
  - locators, selecting [4.3.1](Oracle-extensions.md)
- close() method [E.1.2](JDBC-troubleshooting.md)
- close method [20.3.2](statement-and-resultset-caching.md)
- collections
  - defined [16.1.1](Oracle-collections.md)
- collections (nested tables and arrays) [16.4.1](Oracle-collections.md)
- column types
  - defining [21.2.3](performance-extensions.md)
  - redefining [21.2](performance-extensions.md)
- commit a distributed transaction branch [32.2.4](distributed-transactions.md)
- commit changes to database [2.3.8](JDBC-getting-started.md)
- connection
  - closing [2.3.9](JDBC-getting-started.md)
  - opening [2.3.2](JDBC-getting-started.md)
- connection properties [8.1.5](data-sources-and-URLs.md)
  - put() method [8.1.9](data-sources-and-URLs.md)
- connections
  - read-only [C.3](JDBC-coding-tips.md)
- constants for SQL types [4.5.5.7](Oracle-extensions.md)
- CursorName
  - limitations [A.5.1](JDBC-reference-information.md)
- cursors [E.1.2](JDBC-troubleshooting.md)
- custom collection classes
  - defined [16.1.2](Oracle-collections.md)
- custom Java classes [4.2.3](Oracle-extensions.md)
  - defined [13.1](Oracle-object-types.md)
- custom object classes
  - creating [13.3.1](Oracle-object-types.md)
  - defined [13.1](Oracle-object-types.md)
- custom reference classes
  - defined [15.1](Oracle-object-references.md)

------------------------------------------------------------------------

## D

- database
  - connecting
    - with server-side internal driver [7.2](server-side-internal-driver.md)
  - connection testing [2.2.5](JDBC-getting-started.md)
- DatabaseMetaData calls [A.5.4](JDBC-reference-information.md)
- Database Resident Connection Pooling [23.1](database-resident-connection-pooling.md)
  - APIs [23.6](database-resident-connection-pooling.md)
  - DRCP [23](database-resident-connection-pooling.md)
  - enabling
    - client side [23.2.2](database-resident-connection-pooling.md)
    - server side [23.2.1](database-resident-connection-pooling.md)
  - sharing across multiple connections [23.3](database-resident-connection-pooling.md)
  - tagging [23.4](database-resident-connection-pooling.md)
- database specifiers [8.2](data-sources-and-URLs.md)
- database URL
  - including userid and password [2.3.2](JDBC-getting-started.md)
- database URL, specifying [2.3.2](JDBC-getting-started.md)
- database URLs
  - and database specifiers [8.2](data-sources-and-URLs.md)
- data conversions [11.2](accessing-and-manipulating-Oracle-data.md)
  - LONG [12.2.3](Java-streams-in-JDBC.md)
  - LONG RAW [12.2.2](Java-streams-in-JDBC.md)
- datasources [8.1](data-sources-and-URLs.md)
  - and JNDI [8.1.4](data-sources-and-URLs.md)
- data sources
  - creating and connecting (with JNDI) [8.1.4](data-sources-and-URLs.md)
  - creating and connecting (without JNDI) [8.1.3](data-sources-and-URLs.md)
  - Oracle implementation [8.1.2](data-sources-and-URLs.md)
  - properties [8.1.2](data-sources-and-URLs.md)
  - standard interface [8.1.2](data-sources-and-URLs.md)
- data streaming
  - avoiding [12.2.5](Java-streams-in-JDBC.md)
- data type mappings [11.1](accessing-and-manipulating-Oracle-data.md)
- data types
  - Java [11.1](accessing-and-manipulating-Oracle-data.md)
  - Java native [11.1](accessing-and-manipulating-Oracle-data.md)
  - JDBC [11.1](accessing-and-manipulating-Oracle-data.md)
  - Oracle SQL [11.1](accessing-and-manipulating-Oracle-data.md)
- DATE class [4.3.1](Oracle-extensions.md)
- DBOP tag [3.4.1](JDBC-standards-support.md)
- debugging JDBC programs [E.2](JDBC-troubleshooting.md)
- defaultConnection() method [7.2](server-side-internal-driver.md)
- detachServerConnection [23.6](database-resident-connection-pooling.md)
- distributed transaction ID component [32.2.5](distributed-transactions.md)
- distributed transactions
  - branch qualifier [32.2.5](distributed-transactions.md)
  - check for same resource manager [32.2.4](distributed-transactions.md)
  - commit a transaction branch [32.2.4](distributed-transactions.md)
  - components and scenarios [32.1.2](distributed-transactions.md)
  - concepts [32.1.3](distributed-transactions.md)
  - distributed transaction ID component [32.2.5](distributed-transactions.md)
  - end a transaction branch [32.2.4](distributed-transactions.md)
  - example of implementation [32.4](distributed-transactions.md)
  - forget [32.2.4](distributed-transactions.md)
  - global transaction identifier [32.2.5](distributed-transactions.md)
  - ID format identifier [32.2.5](distributed-transactions.md)
  - obtain the list of transaction brances during recovery [32.2.4](distributed-transactions.md)
  - Oracle XA connection implementation [32.2.2](distributed-transactions.md)
  - Oracle XA data source implementation [32.2.1](distributed-transactions.md)
  - Oracle XA ID implementation [32.2.5](distributed-transactions.md)
  - Oracle XA optimizations [32.3.4](distributed-transactions.md)
  - Oracle XA resource implementation [32.2.3](distributed-transactions.md)
  - overview [32.1](distributed-transactions.md)
  - prepare a transaction branch [32.2.4](distributed-transactions.md)
  - roll back a transaction branch [32.2.4](distributed-transactions.md)
  - start a transaction branch [32.2.4](distributed-transactions.md)
  - transaction branch ID component [32.2.5](distributed-transactions.md)
  - XA connection interface [32.2.2](distributed-transactions.md)
  - XA data source interface [32.2.1](distributed-transactions.md)
  - XA error handling [32.3.3](distributed-transactions.md)
  - XA exception classes [32.3.1](distributed-transactions.md)
  - XA ID interface [32.2.5](distributed-transactions.md)
  - XA resource functionality [32.2.4](distributed-transactions.md)
  - XA resource interface [32.2.3](distributed-transactions.md)
- DML Returning [4.2.5](Oracle-extensions.md), [4.6](Oracle-extensions.md)
  - example [4.6.3](Oracle-extensions.md)
  - limitations [4.6.4](Oracle-extensions.md)
  - Oracle-specific APIs [4.6.1](Oracle-extensions.md)
  - running statements [4.6.2](Oracle-extensions.md)
- Double.NaN
  - restrictions on use [4.3.1](Oracle-extensions.md)
- DRCP [23.1](database-resident-connection-pooling.md)

------------------------------------------------------------------------

## E

- end a distributed transaction branch [32.2.4](distributed-transactions.md)
- Enterprise Java Beans (EJB) [18.2](JDBC-Rowsets.md)
- errors
  - general JDBC messages, listed [D.2](JDBC-error-messages.md)
  - general JDBC message structure [D.1](JDBC-error-messages.md)
  - processing exceptions [2.13](JDBC-getting-started.md)
  - TTC messages, listed [D.4](JDBC-error-messages.md)
- explicit Statement caching
  - definition of [20.1.3](statement-and-resultset-caching.md)
- extensions to JDBC, Oracle [4](Oracle-extensions.md), [11](accessing-and-manipulating-Oracle-data.md), [13](Oracle-object-types.md), [15](Oracle-object-references.md), [16](Oracle-collections.md), [21](performance-extensions.md)
- external changes (result set)
  - defined [17.6](resultset.md)
  - visibility vs. detection [17.6.1](resultset.md)
- external file
  - defined [12.4](Java-streams-in-JDBC.md)

------------------------------------------------------------------------

## F

- fetch direction in result sets [17.4.2](resultset.md)
- fetch size, result sets [17.4](resultset.md)
- FilteredRowSet [18.5](JDBC-Rowsets.md)
- finalizer methods [E.1.2](JDBC-troubleshooting.md)
- Firewalls, using with JDBC [E.1.5](JDBC-troubleshooting.md)
- Float.NaN
  - restrictions on use [4.3.1](Oracle-extensions.md)
- floating-point compliance [A.5.3](JDBC-reference-information.md)
- format identifier, transaction ID [32.2.5](distributed-transactions.md)
- function call syntax, JDBC escape syntax [A.4.6](JDBC-reference-information.md)

------------------------------------------------------------------------

## G

- getBinaryStream() method [12.2.4](Java-streams-in-JDBC.md)
- getBytes() method [12.2.4](Java-streams-in-JDBC.md)
- getColumns [2.5](JDBC-getting-started.md)
- getConnection() method [7.2](server-side-internal-driver.md)
- getCursorName() method
  - limitations [A.5.1](JDBC-reference-information.md)
- getLogicalTransactionId method [27.4.1](transaction-guard.md)
- getMoreResultSet(int) [2.7](JDBC-getting-started.md)
- getObject() method
  - for ORAData objects [13.3.6](Oracle-object-types.md)
  - return types [11.4.3](accessing-and-manipulating-Oracle-data.md)
- getOracleObject() method
  - return types [11.4.2](accessing-and-manipulating-Oracle-data.md), [11.4.3](accessing-and-manipulating-Oracle-data.md)
  - using in callable statement [11.4.2](accessing-and-manipulating-Oracle-data.md)
  - using in result set [11.4.2](accessing-and-manipulating-Oracle-data.md)
- getStatementCacheSize() method
  - code example [20.2.1](statement-and-resultset-caching.md)
- getXXX() methods
  - casting return values [11.4.5](accessing-and-manipulating-Oracle-data.md)
  - for specific data types [11.4.4](accessing-and-manipulating-Oracle-data.md)
- globalization [19](globalization-support.md)
  - using [19](globalization-support.md)
- global transaction identifier (distributed transactions) [32.2.5](distributed-transactions.md)
- global transactions [32.1](distributed-transactions.md)

------------------------------------------------------------------------

## I

- IEEE 754 floating-point compliance [A.5.3](JDBC-reference-information.md)
- implicit Statement caching
  - definition of [20.1.2](statement-and-resultset-caching.md)
  - Least Recently Used (LRU) algorithm [20.1.2](statement-and-resultset-caching.md)
- installation
  - verifying on the client [2.2](JDBC-getting-started.md)
- Instant Client feature [6.4.1](JDBC-OCI-features.md)
- internal changes (result set)
  - defined [17.6](resultset.md)
- isColumnInvisible [2.5](JDBC-getting-started.md)
- isSameRM() (distributed transactions) [32.2.4](distributed-transactions.md)

------------------------------------------------------------------------

## J

- Java
  - compiling and running [2.2.3](JDBC-getting-started.md)
  - data types [11.1](accessing-and-manipulating-Oracle-data.md)
  - native data types [11.1](accessing-and-manipulating-Oracle-data.md)
  - stored procedures [2.12.2](JDBC-getting-started.md)
  - stream data [12](Java-streams-in-JDBC.md)
- java.sql.Connection interface
  - close method [20.3.2](statement-and-resultset-caching.md)
- java.sql.Statement interface
  - close method [20.3.2](statement-and-resultset-caching.md)
- java.util.Properties [22.3.4](OCI-connection-pooling.md)
- Java Naming and Directory Interface (JNDI) [8.1.1](data-sources-and-URLs.md)
- Java Sockets [1.1](introducing-JDBC.md)
- Java Virtual Machine (JVM) [7.1](server-side-internal-driver.md)
- JDBC
  - and IDEs [1.4.3](introducing-JDBC.md)
  - basic program [2.3](JDBC-getting-started.md)
  - data types [11.1](accessing-and-manipulating-Oracle-data.md)
  - defined [1](introducing-JDBC.md)
  - importing packages [2.3.1](JDBC-getting-started.md)
  - limitations of Oracle extensions [A.5](JDBC-reference-information.md)
  - sample files [2.2.3](JDBC-getting-started.md)
  - testing [2.2.5](JDBC-getting-started.md)
  - version support [3](JDBC-standards-support.md)
- JDBC 2.0 support
  - data type support [3.1.1](JDBC-standards-support.md)
  - extended feature support [3.1.3](JDBC-standards-support.md)
  - introduction [3.1](JDBC-standards-support.md)
  - JDK 1.2.x vs. JDK 1.1.x [3.1](JDBC-standards-support.md), [3.2](JDBC-standards-support.md)
  - standard feature support [3.1.2](JDBC-standards-support.md)
- JdbcCheckup program [2.2.5](JDBC-getting-started.md)
- JDBC drivers
  - choosing a driver for your needs [1.2](introducing-JDBC.md)
  - common problems [E.1](JDBC-troubleshooting.md)
  - introduction [1.1](introducing-JDBC.md)
  - JDBC escape syntax [A.4](JDBC-reference-information.md)
- JDBC escape syntax [A.4](JDBC-reference-information.md)
  - function call syntax [A.4.6](JDBC-reference-information.md)
  - LIKE escape characters [A.4.3](JDBC-reference-information.md)
  - outer joins [A.4.5](JDBC-reference-information.md)
  - scalar functions [A.4.2](JDBC-reference-information.md)
  - time and date literals [A.4.1](JDBC-reference-information.md)
  - translating to SQL example [A.4.7](JDBC-reference-information.md)
- JDBCRowSet [18.3](JDBC-Rowsets.md)
- JDBCSpy [E.2.2](JDBC-troubleshooting.md)
- JDBCTest [E.2.2](JDBC-troubleshooting.md)
- JDeveloper [1.4.3](introducing-JDBC.md)
- JNDI
  - and datasources [8.1.4](data-sources-and-URLs.md)
  - looking up data source [8.1.4](data-sources-and-URLs.md)
  - overview of Oracle support [8.1.1](data-sources-and-URLs.md)
  - registering data source [8.1.4](data-sources-and-URLs.md)
- JoinRowSet [18.6](JDBC-Rowsets.md)
- JVM [7.1](server-side-internal-driver.md)

------------------------------------------------------------------------

## K

- KPRB driver
  - overview [1.1](introducing-JDBC.md)
  - relation to the SQL engine [7.1](server-side-internal-driver.md)
  - session context [7.3](server-side-internal-driver.md)
  - testing [7.4](server-side-internal-driver.md)
  - transaction context [7.3](server-side-internal-driver.md)
  - URL for [7.2](server-side-internal-driver.md)

------------------------------------------------------------------------

## L

- Least Recently Used (LRU) algorithm [20.1.2](statement-and-resultset-caching.md), [22.3.5](OCI-connection-pooling.md)
- LIKE escape characters, JDBC escape syntax [A.4.3](JDBC-reference-information.md)
- limitations on setBytes() and setString(), use of streams to avoid [12.7.2](Java-streams-in-JDBC.md)
- LOB
  - defined [12.4](Java-streams-in-JDBC.md)
- logical transaction identifier
  - LTXID [27.1](transaction-guard.md)
- LONG
  - data conversions [12.2.3](Java-streams-in-JDBC.md)
- LONG RAW
  - data conversions [12.2.2](Java-streams-in-JDBC.md)
- LRU algorithm [20.1.2](statement-and-resultset-caching.md)
- LTXID [27.1](transaction-guard.md)

------------------------------------------------------------------------

## M

- memory leaks [E.1.2](JDBC-troubleshooting.md)
- monitoring database operations
  - DBOP [3.4.1](JDBC-standards-support.md)
  - setClientInfo [3.4.1](JDBC-standards-support.md)

------------------------------------------------------------------------

## N

- named arrays [16.1.1](Oracle-collections.md)
  - defined [16.4.1](Oracle-collections.md)
- nativeXA [8.1.2](data-sources-and-URLs.md)
- network events, trapping [E.2.1](JDBC-troubleshooting.md)
- NLS. See globalization [19](globalization-support.md)
- NULL
  - testing for [11.2.3](accessing-and-manipulating-Oracle-data.md)
- NUMBER class [4.3.1](Oracle-extensions.md)

------------------------------------------------------------------------

## O

- object references
  - accessing object values [15.2.1](Oracle-object-references.md), [15.3](Oracle-object-references.md)
  - described [15.1](Oracle-object-references.md)
  - passing to prepared statements [15.2.3](Oracle-object-references.md)
  - retrieving [15.2.1](Oracle-object-references.md)
  - retrieving from callable statement [15.2.2](Oracle-object-references.md)
  - updating object values [15.2.1](Oracle-object-references.md), [15.3](Oracle-object-references.md)
- OCI driver
  - described [1.1](introducing-JDBC.md)
- ODBCSpy [E.2.2](JDBC-troubleshooting.md)
- ODBCTest [E.2.2](JDBC-troubleshooting.md)
- optimization, performance [C.2](JDBC-coding-tips.md)
- oracle.jdbc., Oracle JDBC extensions [2.3.1](JDBC-getting-started.md)
- oracle.jdbc.LogicalTransactionIdEventListener interface [27.4.2](transaction-guard.md)
- oracle.jdbc.OracleCallableStatement interface [4.5.5.4](Oracle-extensions.md)
- oracle.jdbc.OracleConnection interface [4.5.5.1](Oracle-extensions.md)
- oracle.jdbc.OraclePreparedStatement interface [4.5.5.3](Oracle-extensions.md)
- oracle.jdbc.OracleResultSet interface [4.5.5.5](Oracle-extensions.md)
- oracle.jdbc.OracleResultSetMetaData interface [4.5.5.6](Oracle-extensions.md)
- oracle.jdbc.OracleSql class [A.4.7](JDBC-reference-information.md)
- oracle.jdbc.OracleStatement interface [4.5.5.2](Oracle-extensions.md)
- oracle.jdbc.OracleTypes class [4.5.5.7](Oracle-extensions.md)
- oracle.jdbc.xa package and subpackages [32.1.5](distributed-transactions.md)
- oracle.sql.ARRAY class
  - methods for Java primitive types [16.3.1](Oracle-collections.md)
- oracle.sql.BFILE class [4.3.1](Oracle-extensions.md)
- oracle.sql.BLOB class [4.3.1](Oracle-extensions.md)
- oracle.sql.CLOB class [4.3.1](Oracle-extensions.md)
- oracle.sql.data types
  - support [4.3.1](Oracle-extensions.md)
- oracle.sql.DATE class [4.3.1](Oracle-extensions.md)
- oracle.sql.NUMBER class [4.3.1](Oracle-extensions.md)
- oracle.sql.RAW class [4.3.1](Oracle-extensions.md)
- oracle.sql.STRUCT class [4.3.1](Oracle-extensions.md)
- Oracle Advanced Security
  - support by JDBC [9.3](client-side-security.md)
- OracleCallableStatement interface [4.5.5.4](Oracle-extensions.md)
- OracleCallableStatement object [20.1.2](statement-and-resultset-caching.md)
- OracleConnection class [4.5.5.1](Oracle-extensions.md)
- OracleData interface
  - advantages [13.3.2](Oracle-object-types.md)
- OracleDataSource class [8.1.2](data-sources-and-URLs.md)
- Oracle data types
  - using [11](accessing-and-manipulating-Oracle-data.md)
- Oracle extensions [4.2](Oracle-extensions.md)
  - data type support [4.2.2](Oracle-extensions.md)
  - limitations [A.5](JDBC-reference-information.md)
    - catalog arguments to DatabaseMetaData calls [A.5.4](JDBC-reference-information.md)
    - CursorName [A.5.1](JDBC-reference-information.md)
    - IEEE 754 floating-point compliance [A.5.3](JDBC-reference-information.md)
    - JDBC outer join escapes [A.5.2](JDBC-reference-information.md)
    - read-only connection [C.3](JDBC-coding-tips.md)
    - SQLWarning class [A.5.5](JDBC-reference-information.md)
  - object support [4.2.3](Oracle-extensions.md)
  - result sets [11.3](accessing-and-manipulating-Oracle-data.md)
  - statements [11.3](accessing-and-manipulating-Oracle-data.md)
  - to JDBC [4](Oracle-extensions.md), [11](accessing-and-manipulating-Oracle-data.md), [13](Oracle-object-types.md), [15](Oracle-object-references.md), [16](Oracle-collections.md), [21](performance-extensions.md)
- Oracle objects
  - and JDBC [13.1](Oracle-object-types.md)
  - Java classes which support [13.2.1](Oracle-object-types.md)
  - mapping to custom object classes [13.3.1](Oracle-object-types.md)
  - reading data by using SQLData interface [13.3.5](Oracle-object-types.md)
  - working with [13.1](Oracle-object-types.md)
  - writing data by using SQLData interface [13.3.5](Oracle-object-types.md)
- OraclePreparedStatement interface [4.5.5.3](Oracle-extensions.md)
- OraclePreparedStatement object [20.1.2](statement-and-resultset-caching.md)
- OracleResultSet interface [4.5.5.5](Oracle-extensions.md)
- OracleResultSetMetaData interface [4.5.5.6](Oracle-extensions.md)
- Oracle SQL data types [11.1](accessing-and-manipulating-Oracle-data.md)
- OracleStatement interface [4.5.5.2](Oracle-extensions.md)
- OracleTypes class [4.5.5.7](Oracle-extensions.md)
- OracleXAConnection class [32.2.2](distributed-transactions.md)
- OracleXADataSource class [32.2.1](distributed-transactions.md)
- OracleXAResource class [32.2.3](distributed-transactions.md)
- OracleXid class [32.2.5](distributed-transactions.md)
- ORAData interface
  - additional uses [13.3.8](Oracle-object-types.md)
  - reading data [13.3.7](Oracle-object-types.md)
  - writing data [13.3.7](Oracle-object-types.md)
- orai18n.jar file [19.1](globalization-support.md)
- outer joins, JDBC escape syntax [A.4.5](JDBC-reference-information.md)

------------------------------------------------------------------------

## P

- password, specifying [2.3.2](JDBC-getting-started.md)
- PDA [18.2](JDBC-Rowsets.md)
- performance enhancements, standard vs. Oracle [3.1.4](JDBC-standards-support.md)
- performance extensions
  - defining column types [21.2.3](performance-extensions.md)
- performance optimization [C.2](JDBC-coding-tips.md)
- Personal Digital Assistant (PDA) [18.2](JDBC-Rowsets.md)
- PL/SQL
  - stored procedures [2.12.1](JDBC-getting-started.md)
- PL/SQL Associative Arrays [4.7](Oracle-extensions.md)
- prefetching rows [21.2](performance-extensions.md)
  - suggested default [21.2.2](performance-extensions.md)
- prepare a distributed transaction branch [32.2.4](distributed-transactions.md)
- put() method
  - for Properties object [8.1.9](data-sources-and-URLs.md)

------------------------------------------------------------------------

## R

- RAW class [4.3.1](Oracle-extensions.md)
- recover (distributed transactions) [32.2.4](distributed-transactions.md)
- REF CURSORs [4.5.2](Oracle-extensions.md)
- refetching rows into a result set [17.5](resultset.md)
- registerConnectionInitializationCallback [28.6.3.2](application-continuity.md)
- Remote Method Invocation (RMI) [18.2](JDBC-Rowsets.md)
- resource managers [32.1.2](distributed-transactions.md)
- result set
  - auto-commit mode [C.2.1](JDBC-coding-tips.md)
  - metadata [4.5.5.6](Oracle-extensions.md)
  - Oracle extensions [11.3](accessing-and-manipulating-Oracle-data.md)
  - using getOracleObject() method [11.4.2](accessing-and-manipulating-Oracle-data.md)
- result set, processing [2.3.5](JDBC-getting-started.md)
- result set enhancements
  - downgrade rules [17.2](resultset.md)
  - fetch size [17.4](resultset.md)
  - limitations [17.2](resultset.md)
  - Oracle scrollability requirements [17.1](resultset.md)
  - Oracle updatability requirements [17.1](resultset.md)
  - refetching rows [17.5](resultset.md)
  - summary of visibility of changes [17.6.2](resultset.md)
  - visibility vs. detection of external changes [17.6.1](resultset.md)
- result set fetch size [17.4](resultset.md)
- Result Set Holdability [3.2.4](JDBC-standards-support.md)
- result set object
  - closing [2.3.6](JDBC-getting-started.md)
- Retrieval of Auto-Generated Keys [3.2.2](JDBC-standards-support.md)
- return types
  - for getXXX() methods [11.4.4.1](accessing-and-manipulating-Oracle-data.md)
  - getObject() method [11.4.3](accessing-and-manipulating-Oracle-data.md)
  - getOracleObject() method [11.4.3](accessing-and-manipulating-Oracle-data.md)
- return values
  - casting [11.4.5](accessing-and-manipulating-Oracle-data.md)
- RMI [18.2](JDBC-Rowsets.md)
- roll back a distributed transaction branch [32.2.4](distributed-transactions.md)
- roll back changes to database [2.3.8](JDBC-getting-started.md)
- ROWID, use for result set updates [17.1](resultset.md)
- ROWID class
  - defined [4.5.1](Oracle-extensions.md)
- row prefetching
  - and data streams [12.7.3](Java-streams-in-JDBC.md)
- RowSet
  - events and event listeners [18.1.2](JDBC-Rowsets.md)
  - overview [18.1](JDBC-Rowsets.md)
  - properties [18.1.1](JDBC-Rowsets.md)
  - traversing [18.1.4](JDBC-Rowsets.md)

------------------------------------------------------------------------

## S

- savepoints
  - transaction [3.2.1](JDBC-standards-support.md)
- scalar functions, JDBC escape syntax [A.4.2](JDBC-reference-information.md)
- SCAN
  - backward compatibility [31.4](single-client-access-name.md)
  - configuring the database [31.2](single-client-access-name.md)
  - connection load balancing [31.3](single-client-access-name.md)
  - maximum availability architecture environment [31.5](single-client-access-name.md)
  - Oracle connection manager [31.6](single-client-access-name.md)
  - overview [31.1](single-client-access-name.md)
  - version [31.4](single-client-access-name.md)
- Schema Naming [4.2.4](Oracle-extensions.md)
- scripts, authenticating users in [9.10](client-side-security.md)
- scrollable result sets
  - fetch direction [17.4.2](resultset.md)
  - implementation of scroll-sensitivity [17.6.3](resultset.md)
  - refetching rows [17.5](resultset.md)
  - visibility vs. detection of external changes [17.6.1](resultset.md)
- scroll-sensitive result sets
  - limitations [17.2](resultset.md)
- security
  - authentication [9.4](client-side-security.md)
  - Oracle Advanced Security support [9.3](client-side-security.md)
- server-side internal driver
  - connection to database [7.2](server-side-internal-driver.md)
- server-side Thin driver, overview [1.1](introducing-JDBC.md)
- session context
  - for KPRB driver [7.3](server-side-internal-driver.md)
- setBytes() limitations, using streams to avoid [12.7.2](Java-streams-in-JDBC.md)
- setCursorName() method [A.5.1](JDBC-reference-information.md)
- setDisableStmtCaching() method [20.2.3](statement-and-resultset-caching.md)
- setEscapeProcessing() method [A.4](JDBC-reference-information.md)
- setFixedCHAR() method [11.4.7.2](accessing-and-manipulating-Oracle-data.md)
- setNull() [11.2.3](accessing-and-manipulating-Oracle-data.md)
- setObejct() method [11.4.6](accessing-and-manipulating-Oracle-data.md)
- setObject() method
  - for STRUCT objects [13.2.4](Oracle-object-types.md)
- setOracleObject() method [11.4.6](accessing-and-manipulating-Oracle-data.md)
- setString() limitations, using streams to avoid [12.7.2](Java-streams-in-JDBC.md)
- setXXX() methods, for specific data types [11.4.7](accessing-and-manipulating-Oracle-data.md)
- Solaris
  - shared libraries [32.5.1](distributed-transactions.md)
- specifiers
  - database [8.2](data-sources-and-URLs.md)
- SQL
  - data converting to Java data types [11.2](accessing-and-manipulating-Oracle-data.md)
  - types, constants for [4.5.5.7](Oracle-extensions.md)
- SQLData interface
  - advantages [13.3.2](Oracle-object-types.md)
  - reading data from Oracle objects [13.3.5](Oracle-object-types.md)
  - writing data from Oracle objects [13.3.5](Oracle-object-types.md)
- SQL engine
  - relation to the KPRB driver [7.1](server-side-internal-driver.md)
- SQL syntax (Oracle) [A.4](JDBC-reference-information.md)
- SQLWarning class, limitations [A.5.5](JDBC-reference-information.md)
- start a distributed transaction branch [32.2.4](distributed-transactions.md)
- statement.cancel() [E.1.4](JDBC-troubleshooting.md)
- Statement caching
  - explicit
    - definition of [20.1.3](statement-and-resultset-caching.md)
  - implicit
    - definition of [20.1.2](statement-and-resultset-caching.md)
    - Least Recently Used (LRU) algorithm [20.1.2](statement-and-resultset-caching.md)
- Statement object
  - closing [2.3.6](JDBC-getting-started.md)
- statements
  - Oracle extensions [11.3](accessing-and-manipulating-Oracle-data.md)
- stopping
  - statement execution [E.1.4](JDBC-troubleshooting.md)
- stored procedures
  - Java [2.12.2](JDBC-getting-started.md)
  - PL/SQL [2.12.1](JDBC-getting-started.md)
- stream data [12](Java-streams-in-JDBC.md)
  - CHAR columns [12.3](Java-streams-in-JDBC.md)
  - closing [12.6](Java-streams-in-JDBC.md)
  - example [12.2.4](Java-streams-in-JDBC.md)
  - external files [12.4](Java-streams-in-JDBC.md)
  - LOBs [12.4](Java-streams-in-JDBC.md)
  - LONG columns [12.2.1](Java-streams-in-JDBC.md)
  - LONG RAW columns [12.2.1](Java-streams-in-JDBC.md)
  - multiple columns [12.5](Java-streams-in-JDBC.md)
  - precautions [12.7.1](Java-streams-in-JDBC.md)
  - RAW columns [12.3](Java-streams-in-JDBC.md)
  - row prefetching [12.7.3](Java-streams-in-JDBC.md)
  - use to avoid setBytes() and setString() limitations [12.7.2](Java-streams-in-JDBC.md)
  - VARCHAR columns [12.3](Java-streams-in-JDBC.md)
- stream data column
  - bypassing [12.5](Java-streams-in-JDBC.md)
- STRUCT class [4.3.1](Oracle-extensions.md)
- STRUCT object
  - retrieving [13.2.2](Oracle-object-types.md)
  - retrieving attributes as oracle.sql types [13.2.2](Oracle-object-types.md)
- SYS.ANYDATA [4.5.4](Oracle-extensions.md)
- SYS.ANYTYPE [4.5.4](Oracle-extensions.md)

------------------------------------------------------------------------

## T

- TAF, definition of [30.1](transparent-application-failover.md)
- TCP/IP protocol [8.2.4](data-sources-and-URLs.md)
- testing
  - for NULL values [11.2.3](accessing-and-manipulating-Oracle-data.md)
- Thin driver
  - overview [1.1](introducing-JDBC.md)
  - server-side, overview [1.1](introducing-JDBC.md)
- time and date literals, JDBC escape syntax [A.4.1](JDBC-reference-information.md)
- trace facility [E.2.1](JDBC-troubleshooting.md)
- trace parameters
  - client-side [E.2.1.1](JDBC-troubleshooting.md)
  - server-side [E.2.1.2](JDBC-troubleshooting.md)
- transaction branch [32.1.1](distributed-transactions.md)
- transaction branch ID component [32.2.5](distributed-transactions.md)
- transaction context
  - for KPRB driver [7.3](server-side-internal-driver.md)
- transaction guard [27.1](transaction-guard.md), [28](application-continuity.md)
  - at-most-once execution [27.1](transaction-guard.md)
  - logical transaction identifier [27.1](transaction-guard.md)
- transaction IDs (distributed transactions) [32.1.3](distributed-transactions.md)
- transaction managers [32.1.2](distributed-transactions.md)
- transactions
  - switching between local and global [32.1.4](distributed-transactions.md)
- transaction savepoints
- Transparent Application Failover (TAF), definition of [30.1](transparent-application-failover.md)
- TTC error messages, listed [D.4](JDBC-error-messages.md)
- type map [11.4.1](accessing-and-manipulating-Oracle-data.md)
  - adding entries [13.3.4.2](Oracle-object-types.md)
  - and STRUCTs [13.3.4.4](Oracle-object-types.md)
  - creating a new map [13.3.4.3](Oracle-object-types.md)
  - used with arrays [16.4.2.4](Oracle-collections.md)
  - using with arrays [16.5](Oracle-collections.md)
- type map (SQL to Java) [13.3.1](Oracle-object-types.md)
- type maps
  - relationship to database connection [7.2](server-side-internal-driver.md)

------------------------------------------------------------------------

## U

- unicode data [4.4.2](Oracle-extensions.md)
- unregisterConnectionInitializationCallback method [28.6.3.3](application-continuity.md)
- updatable result sets
  - limitations [17.2](resultset.md)
  - refetching rows [17.5](resultset.md)
  - update conflicts [17.3](resultset.md)
- update batching (standard model)
  - adding to batch [21.1.2.2](performance-extensions.md)
  - clearing the batch [21.1.2.6](performance-extensions.md)
  - committing changes [21.1.2.5](performance-extensions.md)
  - error handling [21.1.2.8](performance-extensions.md)
  - example [21.1.2.7](performance-extensions.md)
  - executing the batch [21.1.2.3](performance-extensions.md)
  - intermixing batched and non-batched [21.1.2.9](performance-extensions.md)
  - overview [21.1.2](performance-extensions.md)
  - update counts [21.1.2.7](performance-extensions.md)
  - update counts upon error [21.1.2.8](performance-extensions.md)
- update conflicts in result sets [17.3](resultset.md)
- update counts
  - standard update batching [21.1.2.7](performance-extensions.md)
  - upon error (standard batching) [21.1.2.8](performance-extensions.md)
- URLs
  - for KPRB driver [7.2](server-side-internal-driver.md)
- userid, specifying [2.3.2](JDBC-getting-started.md)

------------------------------------------------------------------------

## W

- WebRowSet [18.4](JDBC-Rowsets.md)
- window, scroll-sensitive result sets [17.6.3](resultset.md)

------------------------------------------------------------------------

## X

- XA
  - connection implementation [32.2.2](distributed-transactions.md)
  - connections (definition) [32.1.3](distributed-transactions.md)
  - data source implementation [32.2.1](distributed-transactions.md)
  - data sources (definition) [32.1.3](distributed-transactions.md)
  - definition [32.1.1](distributed-transactions.md)
  - error handling [32.3.3](distributed-transactions.md)
  - example of implementation [32.4](distributed-transactions.md)
  - exception classes [32.3.1](distributed-transactions.md)
  - Oracle optimizations [32.3.4](distributed-transactions.md)
  - Oracle transaction ID implementation [32.2.5](distributed-transactions.md)
  - resource implementation [32.2.3](distributed-transactions.md)
  - resources (definition) [32.1.3](distributed-transactions.md)
  - transaction ID interface [32.2.5](distributed-transactions.md)
