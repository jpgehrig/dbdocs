This property specifies whether the current operation producing this exception can succeed if retried.

### Declaration

    // C#
    public bool IsRecoverable {get;}

### Property Value

A `bool`.

### Remarks

When a database outage occurs, such as during a network failure, the session becomes unavailable and the client receives an error code. The client can have difficulty determining whether the in-flight operation committed or needs to be resubmitted. Oracle automatically determines whether an in-flight database operation can be recovered or not using the `IsRecoverable` property. If `IsRecoverable` returns true after an outage, then the application can retrieve the current operation status and complete the transaction. If `IsRecoverable` returns false, then the application can rollback the current operation and resubmit the transaction.

This property is often used in conjunction with Transaction Guard.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleException Class](OracleExceptionClass.md)

- [OracleException Members](ExceptionMembers.md)

- [Using Transaction Guard to Prevent Logical Corruption](featTG.md)
