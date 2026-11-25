## 3 PL/SQL Data Types

Every PL/SQL constant, variable, parameter, and function return value has a data type that determines its storage format and its valid values and operations.

This chapter explains scalar data types, which store values with no internal components.

A scalar data type can have subtypes. A subtype is a data type that is a subset of another data type, which is its base type. A subtype has the same valid operations as its base type. A data type and its subtypes comprise a data type family.

PL/SQL predefines many types and subtypes in the package `STANDARD` and lets you define your own subtypes.

The PL/SQL scalar data types are:

- The SQL data types

- `BOOLEAN`

- `PLS_INTEGER`

- `BINARY_INTEGER`

- `REF` `CURSOR`

- User-defined subtypes

### Topics

- [SQL Data Types](sql-data-types.md)

- [BOOLEAN Data Type](boolean-data-type.md)

- [PLS_INTEGER and BINARY_INTEGER Data Types](pls_integer-and-binary_integer-data-types.md)

- [SIMPLE_INTEGER Subtype of PLS_INTEGER](pls_integer-and-binary_integer-data-types.md)

- [User-Defined PL/SQL Subtypes](user-defined-pl-sql-subtypes.md)

**See Also:**

- "[PL/SQL Collections and Records](plsql-collections-and-records.md)" for information about composite data types

- "[Cursor Variables](cursor-variables.md)" for information about `REF` `CURSOR`

- "[CREATE TYPE Statement](CREATE-TYPE-statement.md)" for information about creating schema-level user-defined data types

- "[PL/SQL Predefined Data Types](plsql-predefined-data-types.md)" for the predefined PL/SQL data types and subtypes, grouped by data type family
