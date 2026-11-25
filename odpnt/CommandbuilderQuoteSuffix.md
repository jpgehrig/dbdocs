This property specifies the ending character or characters used to specify database objects whose names contain special characters such as spaces or reserved words.

### Declaration

    // C#
    public override string QuoteSuffix {get; set;}

### Property Value

The ending character or characters to use. The default value is `"\""`.

### Remarks

This property is independent of any `OracleConnection` or `OracleCommand` objects.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommandBuilder Class](OracleCommandBuilderClass.md)

- [OracleCommandBuilder Members](CommandBuilderMembers.md)
