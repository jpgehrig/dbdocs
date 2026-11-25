DB2 DSN sub-command `BIND PACKAGE` has several options that are used when Oracle binds a client application' package.

Further details on the `BIND PACKAGE` sub-command are part of the following volume: DB2® 10 for z/OS® Command Reference (SC19-2972-05).

### CONCURRENTACCESSRESOLUTION

Always implements `WAITFOROUTCOME` semantics; this is fundamental to how Oracle does data locking, and cannot be changed.

### CURRENTDATA

Supports `YES` semantics.

### DBPROTOCOL

Supports `DRDA` semantics.

### DEFER/NODEFER

Supports `NODEFER` semantics.

### DYNAMICRULES

Supports `RUN` semantics.

Default qualifier usage applies for each statement, as defined by DB2's rules. This is equivalent to `SET CURRENT SQLID` for a `STATIC` or `DYNAMIC SQL` statement. However, Oracle restricts object access authorization to the current logon id, and not the package owner's id. To control object access, the logon must be handled either through an explicit access grant (object grants, or role grants), or through a stored procedure that imposes object access authorization.

### ENABLE/DISABLE

Supports `ENABLE` semantics.

### EXTENDEDINDICATOR

Supports `NO` semantics.

### ISOLATION

Supports `CS` semantics.

Oracle, and therefore Oracle Database Provider for DRDA, do not support most isolation modes. Oracles data isolation mode may be described as a compromise between CS and RR. This cannot be changed because it is fundamental to how Oracle implements data integrity management. While the value is ignored, it is stored with the package definition for future processing.

### KEEPDYNAMIC

Supports `YES` semantics.

### OWNER

Authorization id must be a valid Oracle userid.

### QUALIFIER

Qualifier name should be a valid schema name within Oracle.

### RELEASE

Implements `COMMIT` semantics.

When using DRDA, the release of resources is performed at different level. At Commit/Rollback, the semantics of the cursor or statement may request a release of cursor and object locks. Other resources, such as the package itself, are retained until the session ends, and are only then de-allocated. This behaviors is specified largely by the client at runtime, rather than by the server.

### REOPT

Implements `AUTO` semantics.

Oracle, by default, automatically evaluates execution plans based on statement and host variables; both `STATIC` or `DYNAMIC` statements receive the same treatment.

### ROUNDING

Implements `HALFEVEN` semantics.

### VALIDATE

Implements `RUN` semantics.

This option is ignored because Oracle Database Provider for DRDA does not perform validation of `STATIC SQL` statements.
