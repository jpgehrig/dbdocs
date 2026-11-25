This property specifies the parameters for the SQL statement or stored procedure.

### Declaration

    // C#
    public OracleParameterCollection Parameters {get;}

### Property Value

`OracleParameterCollection`

### Implements

`IDbCommand`

### Remarks

Default value = an empty collection

The number of the parameters in the collection must be equal to the number of parameter placeholders within the command text, or an error is raised.

If the command text does not contain any parameter tokens (such as,`:1`,`:2`), the values in the `Parameters` property are ignored.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommand Class](OracleCommandClass.md)

- [OracleCommand Members](OracleCommandMembers.md)
