This property indicates whether or not `CHAR` and `VARCHAR2` columns use byte or character (default) length semantics.

### Declaration

    // C#
    public string LengthSemantics {get; set;}

### Property Value

A string that indicates either byte or character length semantics.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

The default value is the `NLS_LENGTH_SEMANTICS` setting of the local computer.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleGlobalization Class](OracleGlobalizationClass.md)

- [OracleGlobalization Members](GlobalizationMembers.md)
