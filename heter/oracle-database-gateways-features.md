This chapter describes the major features provided by Oracle Database gateways.

**Note:**

These features may not be available in all Heterogeneous Services gateways. Not only must there be generic support for these features, which Heterogeneous Services provides, but there must also be support added to the driver for them. Consult the appropriate gateway documentation to determine if a particular feature is supported for your gateway.

- [SQL and PL/SQL Support](sql-and-pl-sql-support.md)
  SQL statements are translated and data types are mapped according to capabilities. PL/SQL calls are mapped to non-Oracle system stored procedures.
- [Heterogeneous Replication](heterogeneous-replication.md)
  Data can be replicated between a non-Oracle system and Oracle Database using materialized views.
- [Passthrough SQL](passthrough-sql.md)
  The passthrough SQL feature enables you to send a statement directly to a non-Oracle system without first being interpreted by Oracle Database.
- [Result Set Support](result-set-support.md)
  Various relational databases enable stored procedures to return result sets (one or more sets of rows).
- [Data Dictionary Translations](data-dictionary-translations.md)
  A data dictionary is a collection of information about the database objects that were created by various users of the system.
- [Date-Time Data Types](date-time-data-types.md)
  Heterogeneous Services generic code supports Oracle date-time data types in SQL and stored procedures. Heterogeneous Services does not support these data types in data dictionary translations or queries involving data dictionary translations.
- [Two-Phase Commit Protocol](two-phase-commit-protocol.md)
  Heterogeneous Services provides the infrastructure to implement the two-phase commit protocol.
- [Piecewise LONG Data Type](piecewise-long-data-type.md)
  The gateways now manage the data piecewise between the agent and Oracle Database, eliminating the large memory and network bandwidth requirements.
- [SQL\*Plus DESCRIBE Command](sql-plus-describe-command.md)
  You can describe non-Oracle system objects using the SQL\*Plus `DESCRIBE` command.
- [Constraints on SQL in a Distributed Environment](distributed-environment_sql_constraints.md)
  This section explains some of the constraints on SQL in a distributed environment.
- [Oracle's Optimizer and Heterogeneous Services](optimizer-and-heterogeneous-services.md)
  Oracle's optimizer can be used with Heterogeneous Services.
