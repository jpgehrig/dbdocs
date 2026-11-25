This method refreshes the database schema information used to generate `INSERT`, `UPDATE`, or `DELETE` statements.

### Declaration

    // C#
    public override void RefreshSchema();

### Remarks

An application should call `RefreshSchema` whenever the `SelectCommand` value of the `OracleDataAdapter` object changes.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommandBuilder Class](OracleCommandBuilderClass.md)

- [OracleCommandBuilder Members](CommandBuilderMembers.md)
