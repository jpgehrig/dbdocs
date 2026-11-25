This property specifies the `OracleTransaction` object in which the `OracleCommand` executes.

### Declaration

    // C#
    public OracleTransaction Transaction {set; get;}

### Property Value

`OracleTransaction`

### Implements

`IDbCommand`

### Remarks

Default value = `null`

`Transaction` returns a reference to the transaction object associated with the `OracleCommand` connection object. Thus the command is executed in whatever transaction context its connection is currently in.

**Note:**

When this property is accessed through an `IDbCommand` reference, its set accessor method is not operational.

### Remarks (.NET Stored Procedure)

Always returns `null`.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)
