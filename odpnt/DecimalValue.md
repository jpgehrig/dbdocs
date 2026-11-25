This method returns a `decimal` value.

### Declaration

    // C#
    public decimal Value {get;}

### Property Value

A `decimal` value.

### Exceptions

`OracleNullValueException` - The current instance has a null value.

`OverFlowException` - The `decimal` cannot represent the supplied `OracleDecimal` structure.

### Remarks

Precision can be lost when the `decimal` value is obtained from an `OracleDecimal`. See Remarks under "[OracleDecimal Structure](OracleDecimalStructure.md)" for further information.

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
