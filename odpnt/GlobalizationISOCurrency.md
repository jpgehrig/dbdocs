This property specifies the string to use as an international currency symbol for the C number format element.

### Declaration

    // C#
    public string ISOCurrency {get; set;}

### Property Value

The string used as an international currency symbol.

### Exceptions

`ObjectDisposedException` - The object is already disposed.

### Remarks

The default value is the `NLS_ISO_CURRENCY` setting of the local computer.

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleGlobalization Class](OracleGlobalizationClass.md)

- [OracleGlobalization Members](GlobalizationMembers.md)

- [Oracle Database SQL Language Reference](../sqlrf/Format-Models.md) for further information on the C number format element
