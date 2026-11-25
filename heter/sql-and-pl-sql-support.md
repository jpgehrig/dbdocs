SQL statements are translated and data types are mapped according to capabilities. PL/SQL calls are mapped to non-Oracle system stored procedures.

With SQL statements, if functionality is missing at the remote system, then either a simpler query is issued or the statement is broken up into multiple queries. Then, the desired results are obtained by postprocessing in the Oracle database.

Even though Heterogeneous Services can, for the most part, incorporate non-Oracle systems into Oracle distributed sessions, there are several limitations to this. Some of the generic limitations are:

- There is no support for `CONNECT BY` clauses in SQL statements.

- `ROWID` support is limited; consult individual gateway documentation for more details. The Oracle Universal `ROWID` data type is not supported in any gateway that uses Heterogeneous Services.

- Large objects (LOBs), abstract data types (ADTs), and reference data types (REFs) are not supported.

- Remote packages are not supported.

- Remote stored procedures can have `out` arguments of type `REF CURSOR` but not `in` or `in-out` objects.

- Oracle Heterogeneous Services agents do not support shared database links.

  **Note:**

  In addition to these generic limitations, each gateway can have additional limitations. See the gateway documentation for individual gateways for a complete list of limitations of the product.

**Parent topic:** [Features of Oracle Database Gateways](oracle-database-gateways-features.md)
