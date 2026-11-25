This property will returns an `OracleLogicalTransaction` object for a recoverable error when using Transaction Guard.

### Declaration

    // C#
    public OracleLogicalTransaction OracleLogicalTransaction {get;}

### Property Value

An `OracleLogicalTransaction`.

### Remarks

`OracleLogicalTransaction` is non-null when both of the following conditions are met:

- Transaction Guard is enabled on the service

- The exception is a recoverable error

`OracleLogicalTransaction` can be used to determine the transaction outcome by looking at the two properties that it exposes: `Committed` and `UserCallCompleted`. If the outcome is not known, then `Committed` and `UserCallCompleted` will be set to null.

If the outcome of a recoverable error could not be determined by ODP.NET and the connection have not participated in a distributed transaction, then the `OracleLogicalTransactionId` property of the `OracleLogicalTransaction` object will be non-null and it can be used to determine the outcome by having the application explicitly call the `OracleLogicalTransaction.GetOutcome `static method, if the database/service is up.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleException Class](OracleExceptionClass.md)

- [OracleException Members](ExceptionMembers.md)

- [OracleLogicalTransaction Class](OracleLogicalTransactionClass.md)
