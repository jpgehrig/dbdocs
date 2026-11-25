## 270 UTL_IDENT

The `UTL_IDENT` package specifies which Database or client PL/SQL is running.

This chapter contains the following topics:

- Overview

- Security Model

- Constants

### 270.1 UTL_IDENT Overview

The `UTL_IDENT` package is intended for use for conditional compilation of PL/SQL packages that are supported by Oracle, TimesTen Database, and clients such as Oracle Forms.

### 270.2 UTL_IDENT Security Model

The `UTL_IDENT` package runs as the package owner `SYS`. The public synonym `UTL_IDENT`, and `EXECUTE` permission on this package is granted to `PUBLIC`.

### 270.3 UTL_IDENT Constants

The `UTL_IDENT` package defines several constants to use when specifying parameter values.

These constants are shown in the following table.

Table 270-1 UTL_IDENT Constants

| Constant           | Type      | Value        | Description                        |
|:-------------------|:----------|:-------------|:-----------------------------------|
| `IS_ORACLE_SERVER` | `BOOLEAN` | `TRUE/FALSE` | Stipulates if Oracle Server or not |
| `IS_ORACLE_CLIENT` | `BOOLEAN` | `TRUE/FALSE` | Stipulates if Oracle Client or not |
| `IS_TIMESTEN`      | `BOOLEAN` | `TRUE/FALSE` | Stipulates if TimesTen or not      |
| `IS_ORACLE_FORMS`  | `BOOLEAN` | `TRUE/FALSE` | Stipulates if Oracle Forms or not  |
