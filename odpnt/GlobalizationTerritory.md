This property specifies the name of the territory.

### Declaration

    // C#
    public string Territory {get; set;}

### Property Value

A string that provides the name of the territory.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

The default value is the `NLS_TERRITORY` setting of the local computer.

Changing this property changes other globalization properties.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleGlobalization Class](OracleGlobalizationClass.md)

- [OracleGlobalization Members](GlobalizationMembers.md)

- [Oracle Database Globalization Support Guide](../nlspg/setting-up-globalization-support-environment.md).
