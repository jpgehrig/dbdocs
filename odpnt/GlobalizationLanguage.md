This property specifies the default language of the database.

### Declaration

    // C#
    public string Language {get; set;}

### Property Value

The default language of the database.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

The default value is the `NLS_LANGUAGE` setting of the local computer.

`Language` is used for messages, day and month names, and sorting algorithms. It also determines `NLS_DATE_LANGUAGE` and `NLS_SORT` parameter values.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleGlobalization Class](OracleGlobalizationClass.md)

- [OracleGlobalization Members](GlobalizationMembers.md)
