This appendix contains the following sections:

- Oracle Reserved Words

- Oracle Keywords

- PL/SQL Reserved Words

- Oracle Reserved Namespaces

This appendix lists words that have a special meaning to Oracle. Each word plays a specific role in the context in which it appears. For example, in an `INSERT` statement, the reserved word `INTO` introduces the tables to which rows will be added. But, in a `FETCH` or `SELECT` statement, the reserved word `INTO` introduces the output host variables to which column values will be assigned.

### B.1 Oracle Reserved Words

The following words are reserved by Oracle. That is, they have a special meaning to Oracle and so cannot be redefined. For this reason, you cannot use them to name database objects such as columns, tables, or indexes.

| Oracle Reserved Words | Oracle Reserved Words | Oracle Reserved Words | Oracle Reserved Words |
|:----------------------|:----------------------|:----------------------|:----------------------|
| ACCESS                | ELSE                  | MODIFY                | START                 |
| ADD                   | EXCLUSIVE             | NOAUDIT               | SELECT                |
| ALL                   | EXISTS                | NOCOMPRESS            | SESSION               |
| ALTER                 | FILE                  | NOT                   | SET                   |
| AND                   | FLOAT                 | NOTFOUND              | SHARE                 |
| ANY                   | FOR                   | NOWAIT                | SIZE                  |
| ARRAYLEN              | FROM                  | NULL                  | SMALLINT              |
| AS                    | GRANT                 | NUMBER                | SQLBUF                |
| ASC                   | GROUP                 | OF                    | SUCCESSFUL            |
| AUDIT                 | HAVING                | OFFLINE               | SYNONYM               |
| BETWEEN               | IDENTIFIED            | ON                    | SYSDATE               |
| BY                    | IMMEDIATE             | ONLINE                | TABLE                 |
| CHAR                  | IN                    | OPTION                | THEN                  |
| CHECK                 | INCREMENT             | OR                    | TO                    |
| CLUSTER               | INDEX                 | ORDER                 | TRIGGER               |
| COLUMN                | INITIAL               | PCTFREE               | UID                   |
| COMMENT               | INSERT                | PRIOR                 | UNION                 |
| COMPRESS              | INTEGER               | PRIVILEGES            | UNIQUE                |
| CONNECT               | INTERSECT             | PUBLIC                | UPDATE                |
| CREATE                | INTO                  | RAW                   | USER                  |
| CURRENT               | IS                    | RENAME                | VALIDATE              |
| DATE                  | LEVEL                 | RESOURCE              | VALUES                |
| DECIMAL               | LIKE                  | REVOKE                | VARCHAR               |
| DEFAULT               | LOCK                  | ROW                   | VARCHAR2              |
| DELETE                | LONG                  | ROWID                 | VIEW                  |
| DESC                  | MAXEXTENTS            | ROWLABEL              | WHENEVER              |
| DISTINCT              | MINUS                 | ROWNUM                | WHERE                 |
| DROP                  | MODE                  | ROWS                  | WITH                  |

### B.2 Oracle Keywords

The following words also have a special meaning to Oracle but are not reserved words and so can be redefined. However, some might eventually become reserved words.

| Oracle Keywords | Oracle Keywords | Oracle Keywords | Oracle Keywords |
|:----------------|:----------------|:----------------|:----------------|
| ADMIN           | CURSOR          | FOUND           | MOUNT           |
| AFTER           | CYCLE           | FUNCTION        | NEXT            |
| ALLOCATE        | DATABASE        | GO              | NEW             |
| ANALYZE         | DATAFILE        | GOTO            | NOARCHIVELOG    |
| ARCHIVE         | DBA             | GROUPS          | NOCACHE         |
| ARCHIVELOG      | DEC             | INCLUDING       | NOCYCLE         |
| AUTHORIZATION   | DECLARE         | INDICATOR       | NOMAXVALUE      |
| AVG             | DISABLE         | INITRANS        | NOMINVALUE      |
| BACKUP          | DISMOUNT        | INSTANCE        | NONE            |
| BEGIN           | DOUBLE          | INT             | NOORDER         |
| BECOME          | DUMP            | KEY             | NORESETLOGS     |
| BEFORE          | EACH            | LANGUAGE        | NORMAL          |
| BLOCK           | ENABLE          | LAYER           | NOSORT          |
| BODY            | END             | LINK            | NUMERIC         |
| CACHE           | ESCAPE          | LISTS           | OFF             |
| CANCEL          | EVENTS          | LOGFILE         | OLD             |
| CASCADE         | EXCEPT          | MANAGE          | ONLY            |
| CHANGE          | EXCEPTIONS      | MANUAL          | OPEN            |
| CHARACTER       | EXEC            | MAX             | OPTIMAL         |
| CHECKPOINT      | EXPLAIN         | MAXDATAFILES    | OWN             |
| CLOSE           | EXECUTE         | MAXINSTANCES    | PACKAGE         |
| COBOL           | EXTENT          | MAXLOGFILES     | PARALLEL        |
| COMMIT          | EXTERNALLY      | MAXLOGHISTORY   | PCTINCREASE     |
| COMPILE         | FETCH           | MAXLOGMEMBERS   | PCTUSED         |
| CONSTRAINT      | FLUSH           | MAXTRANS        | PLAN            |
| CONSTRAINTS     | FREELIST        | MAXVALUE        | PLI             |
| CONTENTS        | FREELISTS       | MIN             | PRECISION       |
| CONTINUE        | FORCE           | MINEXTENTS      | PRIMARY         |
| CONTROLFILE     | FOREIGN         | MINVALUE        | PRIVATE         |
| COUNT           | FORTRAN         | MODULE          | PROCEDURE       |
| PROFILE         | SAVEPOINT       | SQLSTATE        | TRACING         |
| QUOTA           | SCHEMA          | STATEMENT_ID    | TRANSACTION     |
| READ            | SCN             | STATISTICS      | TRIGGERS        |
| REAL            | SECTION         | STOP            | TRUNCATE        |
| RECOVER         | SEGMENT         | STORAGE         | UNDER           |
| REFERENCES      | SEQUENCE        | SUM             | UNLIMITED       |
| REFERENCING     | SHARED          | SWITCH          | UNTIL           |
| RESETLOGS       | SNAPSHOT        | SYSTEM          | USE             |
| RESTRICTED      | SOME            | TABLES          | USING           |
| REUSE           | SORT            | TABLESPACE      | WHEN            |
| ROLE            | SQL             | TEMPORARY       | WRITE           |
| ROLES           | SQLCODE         | THREAD          | WORK            |
| ROLLBACK        | SQLERROR        | TIME            |                 |

### B.3 PL/SQL Reserved Words

The following PL/SQL keywords may require special treatment when used in embedded SQL statements.

- ABORT
- ACCEPT
- ACCESS
- ADD
- ALL
- ALTER
- AND
- ANY
- ARRAY
- ARRAYLEN
- AS
- ASC
- ASSERT
- ASSIGN
- AT
- AUTHORIZATION
- AVG
- BASE_TABLE
- BEGIN
- BETWEEN
- BINARY_INTEGER
- BODY
- BOOLEAN
- BY
- CASE
- CHAR_BASE
- CHAR
- CHECK
- CLOSE
- CLUSTER
- CLUSTERS
- COLAUTH
- COLUMNS
- COMMIT
- COMPRESS
- CONNECT
- CONSTANT
- COUNT
- CRASH
- CREATE
- CURRENT
- CURRVAL
- CURSOR
- DATA_BASE
- DATABASE
- DATE
- DBA
- DEBUGOFF
- DEBUGON
- DECLARE
- DEFAULT
- DEFINITION
- DELAY
- DELETE
- DELTA
- DESC
- DIGITS
- DISPOSE
- DISTINCT
- DO
- DROP
- ELSE
- ELSIF
- END
- ENTRY
- EXCEPTION_INIT
- EXCEPTION
- EXISTS
- EXIT
- FALSE
- FETCH
- FLOAT
- FOR
- FORM
- FROM
- FUNCTION
- GENERIC
- GOTO
- GRANT
- GROUP
- HAVING
- IDENTIFIED
- IF
- IN
- INDEX
- INDEXES
- INDICATOR
- INSERT
- INTEGER
- INTERSECT
- INTO
- IS
- LEVEL
- LIKE
- LIMITED
- LOOP
- MAX
- MIN
- MINUS
- MLSLABEL
- MOD
- MODE
- NATURAL
- NEW
- NEXTVAL
- NOCOMPRESS
- NOT
- NULL
- NUMBER_BASE
- NUMBER
- OF
- ON
- OPEN
- OPTION
- OR
- ORDER
- OTHERS
- OUT
- PACKAGE
- PARTITION
- PCTFREE
- POSITIVE
- PRAGMA
- PRIOR
- PRIVATE
- PROCEDURE
- PUBLIC
- RAISE
- RANGE
- REAL
- RECORD
- RELEASE
- REMR
- RENAME
- RESOURCE
- RETURN
- REVERSE
- REVOKE
- ROLLBACK
- ROWID
- ROWLABEL
- ROWNUM
- ROWTYPE
- RUN
- SAVEPOINT
- SCHEMA
- SEPARATE
- SET
- SIZE
- SMALLINT
- SELECT
- SPACE
- SQL
- SQLCODE
- SQLERRM
- START
- STATEMENT
- STDDEV
- SUBTYPE
- SUM
- TABAUTH
- TABLE
- TABLES
- TASK
- TERMINATE
- THEN
- TO
- TRUE
- TYPE
- UNION
- UNIQUE
- UPDATE
- USE
- VALUES
- VARCHAR
- VARCHAR2
- VARIANCE
- VIEW
- VIEWS
- WHEN
- WHERE
- WHILE
- WITH
- WORK
- XOR

### B.4 Oracle Reserved Namespaces

Table B-1 contains a list of namespaces that are reserved by Oracle. The initial characters of function names in Oracle libraries are restricted to the character strings in this list. Because of potential name conflicts, use function names that do not begin with these characters.

For example, the SQL\*Net Transparent Network Service functions all begin with the characters "NS," so you need to avoid naming functions that begin with "NS."

Table B-1 Oracle Reserved Namespaces

| Namespace                                   | Library                                                   |
|:--------------------------------------------|:----------------------------------------------------------|
| O                                           | OCI functions                                             |
| S                                           | function names from SQLLIB and system-dependent libraries |
| XA                                          | external functions for XA applications only               |
| GEN KP L NA NC ND NL NM NR NS NT NZ TTC UPI | Internal functions                                        |
