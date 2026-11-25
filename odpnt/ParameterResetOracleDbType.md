This method resets the type associated with the parameter so that it can infer its type from the value passed in the parameter.

### Declaration

    // C#
    public override void ResetOracleDbType();

### Remarks

If an application does not set the `DbType` or `OracleDbType` properties of an `OracleParameter` object, then these values are inferred from the value set by the application to that `OracleParameter` object. Calling the `ResetOracleDbType` method resets these properties so that `OracleParameter` can again infer its type from the value passed into the `OracleParameter`. Calling this method affects both the `DbType` and `OracleDbType` properties of the `OracleParameter` object.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameter Members](ParameterMembers.md)
