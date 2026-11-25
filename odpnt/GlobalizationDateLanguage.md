This property specifies the language used to spell names of days and months, and date abbreviations (for example: a.m., p.m., AD, BC).

### Declaration

    // C#
    public string DateLanguage {get; set;}

### Property Value

A string specifying the language.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

The default value is the `NLS_DATE_LANGUAGE` setting of the local computer.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleGlobalization Class](OracleGlobalizationClass.md)

- [OracleGlobalization Members](GlobalizationMembers.md)
