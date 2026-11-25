- Object Replication Using Oracle Golden Gate

- Active Data Guard and Logical Standby Support for Objects

### 9.8.1 Object Replication Using Oracle Golden Gate

Beginning with Oracle Database 12c Release 12.1, Oracle supports Oracle Golden Gate for all object datatypes, except nested tables. Oracle supports object tables and columns of ADTs, REFs, VARRAYS, and ANYDATA. Oracle also supports type evolution and object inheritance. The only exception is nested table columns, object tables, and columns of ADTs with nested table attributes.

**See Also:**

For information about data types supported by Oracle Golden Gate, see Oracle Golden Gate Administration Guide.

### 9.8.2 Active Data Guard and Logical Standby Support for Objects

Beginning with Oracle Database release 12c, release 12.1, Oracle supports Active Data Guard and Logical Standby for Object Tables and column for all Object datatypes, including REFs, varrays, ANYDATA and object inheritance. The only exception is that Active Data Guard and Logical Standby is not supported for tables with top-level nested tables and ADTs with nested table attributes.

**See Also:**

Oracle Data Guard Concepts and Administration for information about data types supported by SQL Apply (logical standby)
