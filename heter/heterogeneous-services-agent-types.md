There are two types of Heterogeneous Services agents.

- Oracle Database Gateways
  An Oracle Database Gateway is a gateway that is designed for accessing a specific non-Oracle system.
- Oracle Database Gateway for ODBC Agent
  In addition to Oracle Database gateways for various non-Oracle database systems, there is the Oracle Database Gateway for ODBC agent.

**Parent topic:** [The Role of the Heterogeneous Services Component](heterogeneous-services-role.md)

### Oracle Database Gateways

An Oracle Database Gateway is a gateway that is designed for accessing a specific non-Oracle system.

Oracle provides gateways to access several commercially available non-Oracle systems. For example, an Oracle Database Gateway for Sybase is designed to access Sybase databases.

Using Oracle Database gateways, you can access data anywhere in a distributed database system without being required to know either the location of the data or how it is stored. When the results of your queries are returned to you by Oracle Database, they are presented to you as if the data stores from which they were queried all resided within a remote instance of an Oracle distributed database.

**Parent topic:** Types of Heterogeneous Services Agents

### Oracle Database Gateway for ODBC Agent

In addition to Oracle Database gateways for various non-Oracle database systems, there is the Oracle Database Gateway for ODBC agent.

The Oracle Database Gateway for ODBC agent contains only generic code. You are responsible for providing the necessary drivers. Oracle Database Gateway for ODBC enables you to use ODBC drivers to access non-Oracle systems that have an ODBC interface.

To access a specific non-Oracle system using Oracle Database Gateway for ODBC, you must configure an ODBC driver to the non-Oracle system. These drivers are not provided by Oracle. However, if the non-Oracle system supports the ODBC protocols, you can use Oracle Database Gateway for ODBC to access any non-Oracle system that can be accessed using an ODBC driver.

Oracle Database Gateway for ODBC has some limitations. Especially, when compared to a paticular target, the functionality and performance are limited.

**Parent topic:** Types of Heterogeneous Services Agents
