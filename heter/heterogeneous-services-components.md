Heterogeneous Services in Oracle Database consists of a transaction service and a SQL service.

- Transaction Service
  The transaction service component of the Heterogeneous Services component enables non-Oracle systems to be integrated into Oracle Database transactions and sessions.
- SQL Service
  The structured query language (SQL) service handles the processing of all SQL-related operations.

**Parent topic:** [The Role of the Heterogeneous Services Component](heterogeneous-services-role.md)

### Transaction Service

The transaction service component of the Heterogeneous Services component enables non-Oracle systems to be integrated into Oracle Database transactions and sessions.

When you access a non-Oracle system for the first time using a database link within your Oracle user session, you transparently set up an authenticated session in the non-Oracle system. At the end of your Oracle user session, the authenticated session in the non-Oracle database system is closed.

Additionally, one or more non-Oracle systems can participate in an Oracle distributed transaction. When an application commits a transaction, Oracle's two-phase commit protocol accesses the non-Oracle database system to transparently coordinate the distributed transaction. Even in those cases where the non-Oracle system does not support all aspects of Oracle two-phase commit protocol, Oracle can (with some limitations) support distributed transactions with the non-Oracle system.

**Parent topic:** Heterogeneous Services Components

### SQL Service

The structured query language (SQL) service handles the processing of all SQL-related operations.

The work done by the SQL service includes:

- Mapping Oracle internal SQL-related calls to the Heterogeneous Services driver application programing interface (API). This API is then mapped by the driver to the client API of the non-Oracle system.

- Translating SQL statements from Oracle's SQL dialect to the SQL dialect of the non-Oracle system.

- Translating queries that reference Oracle data dictionary tables to queries that extract the necessary information from the non-Oracle system's data dictionary.

- Converting data from non-Oracle system data types to Oracle data types and back.

- Compensating for missing functionality of the non-Oracle system by issuing multiple queries to get the necessary data and doing postprocessing to get the desired results.

**Parent topic:** Heterogeneous Services Components
