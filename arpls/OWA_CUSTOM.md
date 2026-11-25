## 228  OWA_CUSTOM

The `OWA_CUSTOM` package provides a Global PLSQL Agent Authorization callback function.

It is used when PLSQL Agent's authorization scheme is set to `GLOBAL` or `CUSTOM` when there is no overriding `OWA_CUSTOM` package.

**See Also:**

For more information about implementation of this package:

- [Oracle Fusion Middleware Administrator's Guide for Oracle HTTP Server](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/arpls&id=HSADM)

- [Oracle Fusion Middleware User's Guide for mod_plsql](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/arpls&id=YPMOD)

The chapter contains the following topics:

- Constants

- Summary of OWA_CUSTOM Subprograms

### 228.1 OWA_CUSTOM Constants

`OWA_CUSTOM` defines several constants to use when specifying parameter values.

- `dbms_server_timezone` `CONSTANT` `VARCHAR2(3)` `:= 'PST';`

- `dbms_server_gmtdiff` `CONSTANT` `NUMBER` `:= NULL`;

### 228.2 Summary of OWA_CUSTOM Subprograms

The `AUTHORIZE` function is the only subprogram in the `OWA_CUSTOM` package.

Table 228-1 OWA_CUSTOM Package Subprograms

| Subprogram         | Description                                                   |
|:-------------------|:--------------------------------------------------------------|
| AUTHORIZE Function | Provides a Global PLSQL Agent Authorization callback function |

#### 228.2.1 AUTHORIZE Function

This function is used when PLSQL Agent's authorization scheme is set to `GLOBAL` or `CUSTOM` when there is no overriding `OWA_CUSTOM` package.

##### Syntax

    OWA_CUSTOM.AUTHORIZE
      RETURN BOOLEAN;
