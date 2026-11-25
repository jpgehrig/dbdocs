Oracle Database Provider for DRDA supports the use of native DB2 SQL clauses.

### 14.1 Overview of SQL Statement Support

Oracle Database Provider for DRDA transforms parts of the third-party native SQL statements before sending them for processing on the Oracle Database. In this release, Oracle Database Provider for DRDA is made compatible with Oracle Database Release 11g, which does not have a native understanding of many clauses not supported by Oracle's version of SQL because it does not support SQL Translation. When using SQL Translation, this affects the data and content of SQL requests received by the translator.

Because the Translator never gets the `WITH UR` clause, the translation of the statement and the subsequent result set may not be what the user expects.

For this reason, this release of Oracle Database Provider for DRDA encompasses some translations functions.

Example 14-1 Removing Clauses from SQL Statements

If a user enters the following SQL line on the client:

    SELECT * FROM EMPLOYEES WITH UR

Oracle Database Provider for DRDA strips out the clause `WITH UR`, so if the user is using a Translator, it receives the following line of SQL:

    SELECT * FROM EMPLOYEEES

### 14.2 SQL Clause Restrictions

There are some restrictions on SQL statements that are supported for conversion by Oracle Database Provider for DRDA.

When describing SQL statements, keep in mind the following notation.

- Use of `(..)`, parantheses, enclose the applicable SQL statement context. For example, `(SELECT)` means that the clause applies to a `SELECT` statement.

- Use of `{..}`, curly brackets, indicates an optional constant.

- Use of `<..>` indicates an optional variable.

SQL language restrictions are arranged in following groups.

- Internally Processed SQL Statements

- Removed SQL Clauses that Retain Semantic Effect

- Ignored SQL Clauses

- Translated SQL Clauses

**Related Topics**

- Internally Processed SQL Statements
- Removed SQL Clauses that Retain Semantic Effect
- Ignored SQL Clauses
- Translated SQL Clauses

#### 14.2.1 Internally Processed SQL Statements

The following clauses are processed internally.

    GRANT {ALL, BIND, COPY, EXECUTE, DROP, SET} ON PACKAGE <collid>.<pkgnam> TO <authid>

    GRANT {ALL, BIND, COPY, EXECUTE, DROP, SET} ON PACKAGE <collid>.<pkgnam> TO <authid> WITH GRANT OPTION

    GRANT {ALL, BIND, COPY, EXECUTE, DROP, SET} ON PROGRAM <collid>.<pkgnam> TO <authid>

    GRANT {ALL, BIND, COPY, EXECUTE, DROP, SET} ON PROGRAM <collid>.<pkgnam> TO <authid> WITH GRANT OPTION

    REVOKE {ALL, BIND, COPY, EXECUTE, DROP, SET} ON PACKAGE <collid>.<pkgnam> FROM <authid>

    REVOKE {ALL, BIND, COPY, EXECUTE, DROP, SET} ON PROGRAM <collid>.<pkgnam> FROM <authid>

    DROP PACKAGE <collid>.<pkgnam> VERSION <vsn>

    DROP PACKAGE <collid>.<pkgnam>

    FREE LOCATOR :H

    HOLD LOCATOR :H

#### 14.2.2 Removed SQL Clauses that Retain Semantic Effect

The following SQL clauses are removed from SQL statements. This should be noted because they have a semantic effect.

    (SELECT) FOR READ ONLY

    (SELECT) FOR FETCH ONLY

    (DECLARE) WITH HOLD

    (DECLARE) WITHOUT HOLD

    (DECLARE) WITH ROWSET POSITIONING

    (DECLARE) WITHOUT ROWSET POSITIONING

    (DECLARE) NO SCROLL

    (DECLARE) SCROLL

    (CALL) WITH RETURN CLIENT

    (CALL) WITH RETURN CALLER

    (CALL) <:hostvar> USING DESCRIPTOR <:hostvar>

    (SAVEPOINT) {UNIQUE} ON ROLLBACK RETAIN CURSORS

    (SAVEPOINT) ON ROLLBACK RETAIN LOCKS

    (INSERT) FOR <literal>|<bind-variable> ROWS

    (INSERT) FOR MULTIPLE ROWS

    (INSERT) NOT ATOMIC CONTINUE ON SQLEXCEPTION

#### 14.2.3 Ignored SQL Clauses

These clauses are removed and ignored during translation.

    WITH RR

    WITH RR USE AND KEEP {EXCLUSIVE|UPDATE|SHARE} LOCKS

    WITH RS

    WITH RS USE AND KEEP {EXCLUSIVE|UPDATE|SHARE} LOCKS

    WITH CS

    WITH CS KEEP LOCKS

    WITH UR

    WITH NC

#### 14.2.4 Translated SQL Clauses

The following SQL clauses are translated into an alternative syntax; this may have a semantic effect.

- The original clause `WHERE CURRENT OF <cursorname>` becomes `WHERE ROWID = :N`. `N` is a number.

- The original `=` becomes `'' IS NULL`.

- The original `!=` becomes `'' IS NOT NULL`.

### 14.3 Support for Special Registers

DB2 uses a concept known as special registers; they may be thought of as environment variables within a SQL context. Oracle Database provides limited native support for special registers.

#### 14.3.1 Retrieving Values from Special Registers

Example 14-2 Retrieving values from special registers

When a user enters the following statement on the client:

    SELECT CURRENT CLIENT_ACCTNG FROM SYSIBM.SYSDUMMY1;

Oracle Database Provider for DRDA parses the preceding statement, and replaces the clause `CURRENT CLIENT_ACCTNG` by the clause `SYS_CONTEXT('DRDAAS_CTX_NAME','CLIENT_ACCTNG')`, as follows:

    SELECT SYS_CONTEXT('DRDAAS_CTX_NAME','CLIENT_ACCTNG') FROM SYSIBM.SYSDUMMY1;

Therefore, if a translator expects a `CURRENT CLIENT_ACCTNG` clause, it will receive an altered query.

#### 14.3.2 Setting Special Registers

Example 14-3 Setting special registers

When a user enters the following statement on the client:

    SET CLIENT_ACCTNG = 'abc';

Oracle Database Provider for DRDA sets the value of the `CLIENT_ACCTNG` register to the string `abc` by replacing the clause `CLIENT_ACCTNG = 'abc'` by clause `SYS_CONTEXT('DRDAAS_CTX_NAME','CLIENT_ACCTNG')`, as follows:

    SET SYS_CONTEXT('DRDAAS_CTX_NAME','CLIENT_ACCTNG') = 'abc';

Therefore, if a translator expects a `CURRENT CLIENT_ACCTNG` clause, it will receive an altered statement.

#### 14.3.3 Special Registers Supported by Oracle Database Provider for DRDA

Oracle Database Provider for DRDA supports the following registers.

##### 14.3.3.1 APPLICATION ENCODING SCHEME

    CURRENT APPLICATION ENCODING SCHEME

##### Query

    SYS_CONTEXT('DRDAAS','APPLICATION_ENCODING_SCHEME')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.2 CLIENT_ACCTNG

    CURRENT CLIENT_ACCTNG CLIENT ACCTNG

##### Query

    SYS_CONTEXT('DRDAAS','CLIENT_ACCTNG')

##### Set

Updates `SYS_CONTEXT` and `CLIENT_INFO`

##### Semantics

Updates `CLIENT_INFO` in `V$SESSION`

##### Notes

See MVS and DDF Accounting Information, as defined by IBM and DB2, documented in the `DSNDQMDA` macro.

##### 14.3.3.3 CLIENT_APPLNAME

    CURRENT CLIENT_APPLNAME CLIENT APPLNAME

##### Query

    SYS_CONTEXT('DRDAAS','CLIENT_APPLNAME')

##### Set

Updates `SYS_CONTEXT` and `CLIENT_IDENTIFIER`

##### Semantics

Updates `CLIENT_IDENTIFIER` in `V$SESSION`

##### 14.3.3.4 CLIENT_PROGRAMID

    CURRENT CLIENT_PROGRAMID

##### Query

    SYS_CONTEXT('DRDAAS','CLIENT_PROGRAMID')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.5 CLIENT_USERID

    CURRENT CLIENT_USERID CLIENT USERID

##### Query

    SYS_CONTEXT('DRDAAS','CLIENT_USERID')

##### Set

Cannot be set

##### Semantics

Cannot be set

##### 14.3.3.6 CLIENT_WRKSTNNAME

    CURRENT CLIENT_WRKSTNNAME CLIENT WRKSTNNAME

##### Query

    SYS_CONTEXT('DRDAAS','CLIENT_WRKSTNNAME')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.7 DATE

    CURRENT DATE CURRENT_DATE

##### Query

    CURRENT DATE

##### Set

Cannot be set

##### Semantics

Cannot be set

##### 14.3.3.8 DBPARTITIONNUM

    CURRENT DBPARTITIONNUM

##### Query

    SYS_CONTEXT('DRDAAS','DBPARTITIONNUM')

##### Set

Cannot be set

##### Semantics

Cannot be set

##### 14.3.3.9 DEBUG MODE

    CURRENT DEBUG MODE

##### Query

    SYS_CONTEXT('DRDAAS','DEBUG_MODE')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.10 DECFLOAT ROUNDING MODE

    CURRENT DECFLOAT ROUNDING MODE

##### Query

    SYS_CONTEXT('DRDAAS','DECFLOAT_ROUNDING_MODE')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.11 DEFAULT TRANSFORM GROUP

    CURRENT DEFAULT TRANSFORM GROUP

##### Query

    SYS_CONTEXT('DRDAAS','DEFAULT_TRANSFORM_GROUP')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.12 DEGREE

    CURRENT     DEGREE

##### Query

    SYS_CONTEXT('DRDAAS','DEGREE')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.13 EXPLAIN MODE

    CURRENT EXPLAIN MODE

##### Query

    SYS_CONTEXT('DRDAAS','EXPLAIN_MODE')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.14 EXPLAIN SNAPSHOT

    CURRENT EXPLAIN SNAPSHOT

##### Query

    SYS_CONTEXT('DRDAAS','EXPLAIN_SNAPSHOT')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.15 FEDERATED ASYNCHRONY

    CURRENT FEDERATED ASYNCHRONY

##### Query

    SYS_CONTEXT('DRDAAS','FEDERATED_ASYNCHRONY')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.16 IMPLICIT XMLPARSE OPTION

    CURRENT IMPLICIT XMLPARSE OPTION

##### Query

    SYS_CONTEXT('DRDAAS','IMPLICIT_XMLPARSE_OPTION')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.17 ISOLATION

    CURRENT ISOLATION

##### Query

    SYS_CONTEXT('DRDAAS','ISOLATION')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.18 LOCK TIMEOUT

    CURRENT LOCK TIMEOUT

##### Query

    SYS_CONTEXT('DRDAAS','LOCK_TIMEOUT')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.19 LOCALE LC_TYPE

    CURRENT LOCALE LC_TYPE CURRENT_LC_TYPE

##### Query

    SYS_CONTEXT('DRDAAS','LC_TYPE')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.20 MAINTAINED TABLE TYPES FOR OPTIMIZATION

    CURRENT MAINTAINED TABLE TYPES FOR OPTIMIZATION

##### Query

    SYS_CONTEXT('DRDAAS','MAINTAINED_TYPES')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.21 MEMBER

    CURRENT MEMBER

##### Query

    SYS_CONTEXT('DRDAAS','MEMBER')

##### Set

Cannot be set

##### Semantics

Cannot be set

##### 14.3.3.22 OPTIMIZATION HINT

    CURRENT OPTIMIZATION HINT

##### Query

    SYS_CONTEXT('DRDAAS','OPTIMIZATION_HINT')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.23 PACKAGE PATH

    CURRENT PACKAGE PATH

##### Query

    SYS_CONTEXT('DRDAAS','PACKAGE_PATH')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.24 PACKAGESET

    CURRENT PACKAGESET

##### Query

    SYS_CONTEXT('DRDAAS','PACKAGESET')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.25 PATH

    CURRENT PATH CURRENT_PATH CURRENT FUNCTION PATH

##### Query

    SYS_CONTEXT('DRDAAS','PATH')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.26 PRECISION

    CURRENT PRECISION

##### Query

    SYS_CONTEXT('DRDAAS','PRECISION')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.27 QUERY ACCELERATION

    CURRENT QUERY ACCELERATION

##### Query

    SYS_CONTEXT('DRDAAS','QUERY_ACCELERATION')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.28 QUERY OPTIMIZATION

    CURRENT QUERY OPTIMIZATION

##### Query

    SYS_CONTEXT('DRDAAS','QUERY_OPTIMIZATION')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.29 REFRESH AGE

    CURRENT REFRESH AGE

##### Query

    SYS_CONTEXT('DRDAAS','REFRESH_AGE')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.30 ROUTINE VERSION

    CURRENT ROUTINE VERSION

##### Query

    SYS_CONTEXT('DRDAAS','ROUTINE_VERSION')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.31 RULES

    CURRENT RULES

##### Query

    SYS_CONTEXT('DRDAAS','RULES')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.32 SCHEMA

    CURRENT SCHEMA CURRENT_SCHEMA

##### Query

    SYS_CONTEXT('USERENV','CURRENT_SCHEMA')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.33 SERVER

    CURRENT SERVER CURRENT_SERVER

##### Query

    SYS_CONTEXT('DRDAAS','SERVER')

##### Set

Cannot be set

##### Semantics

Cannot be set

##### 14.3.3.34 SQL_CCFLAGS

    CURRENT SQL_CCFLAGS

##### Query

    SYS_CONTEXT('DRDAAS','SQL_CCFLAGS')

##### Set

Updates `SYS_CONTEXT`

##### Semantics

No effect

##### 14.3.3.35 SQLID

    CURRENT SQLID USER

##### Query

    USER

##### Set

Updates `SYS_CONTEXT``('DRDAAS', 'CURRENT_SQLID')`

##### Semantics

No effect

##### 14.3.3.36 TIMESTAMP

    CURRENT TIMESTAMP CURRENT_TIMESTAMP

##### Query

    CURRENT TIMESTAMP

##### Set

Cannot be set

##### Semantics

Cannot be set

##### 14.3.3.37 USER

    CURRENT USER CURRENT_USER

##### Query

    USER

##### Set

Cannot be set

##### Semantics

Cannot be set

##### 14.3.3.38 SESSION_USER

    SESSION_USER

##### Query

    USER

##### Set

Cannot be set

##### Semantics

Cannot be set

##### 14.3.3.39 SYSTEM_USER

    SYSTE_USER

##### Query

    USER

##### Set

Cannot be set

##### Semantics

Cannot be set

##### 14.3.3.40 ENCRYPTION PASSWORD

    ENCRYPTION PASSWORD

##### Query

Cannot be queried

##### Set

Updates `SYS_CONTEXT('DRDAAS','ENCRYPTION_PASSWORD')`

##### Semantics

No effect
