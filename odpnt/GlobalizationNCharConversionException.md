This property determines whether or not data loss during an implicit or explicit character type conversion reports an error.

### Declaration

    // C#
    public bool NCharConversionException {get; set;}

### Property Value

A string that indicates whether or not a character type conversion causes an error message.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

The default value of `NLS_NCHAR_CONV_EXCP` is `False`, unless it is overridden by a setting in the `INIT.ORA` file.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleGlobalization Class](OracleGlobalizationClass.md)

- [OracleGlobalization Members](GlobalizationMembers.md)
