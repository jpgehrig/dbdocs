This property specifies the minimum number of seconds that the command is allowed to execute before terminating with an exception.

### Declaration

    // C#
    public override int CommandTimeout {get; set;}

### Property Value

`int`

### Implements

`IDbCommand.CommandTimeout`

### Exceptions

`InvalidArgument` - The specified value is less than 0.

### Remarks

Default is `0` seconds, which enforces no time limit.

When the specified timeout value expires before a command execution finishes, ODP.NET will begin the process of canceling the command. If cancellation is successful, then an exception is thrown with the message `ORA-01013: user requested cancel of current operation`. Other possible exceptions thrown after a command timeout expiration occurs include` ORA-00936` and `ORA-00604`. If the command is executed in time without any errors, then no exceptions are thrown.

ODP.NET does not guarantee a command will be cancelled at the exact moment the timeout value is reached. The timeout value is the minimum time to allow a command to complete before the cancellation process begins. It is possible for commands to complete after the timeout value expires.

In a situation where multiple `OracleCommand` objects use the same connection, the timeout expiration on one of the `OracleCommand` objects may terminate any of the executions on the single connection. To make the timeout expiration of a `OracleCommand` cancel only its own command execution, simply use one `OracleCommand` for each connection if that `OracleCommand` sets the `CommandTimeout` property to a value greater than `0`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)

- [`http://msdn.microsoft.com/library`](http://msdn.microsoft.com/library) for detailed information about this Microsoft .NET Framework feature
