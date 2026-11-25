This property specifies the calendar system.

### Declaration

    // C#
    public string Calendar {get; set;}

### Property Value

A string representing the `Calendar`.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

The default value is the `NLS_CALENDAR` setting of the local computer. This value is the same regardless of whether or not the `OracleGlobalization` object represents the settings of the client, thread, or session.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleGlobalization Class](OracleGlobalizationClass.md)

- [OracleGlobalization Members](GlobalizationMembers.md)
