This constructor creates a new instance of the `OracleDecimal` structure with the supplied `string` value and number format.

### Declaration

    // C#
    public OracleDecimal(string numStr, string format);

### Parameters

- `numStr`

  The provided `string` value.

- `format`

  The provided number `format`.

### Exceptions

`ArgumentException` - The `numStr` parameter is an invalid string representation of an `OracleDecimal` or the `numStr` is not in the numeric format specified by `format`.

`ArgumentNullException` - The `numStr` parameter is null.

`OverFlowException` - The value of `numStr` parameter is greater than the maximum value or less than the minimum value of `OracleDecimal`.

### Remarks

If the numeric format includes decimal and group separators, then the provided string must use those characters defined by the `OracleGlobalization`.`NumericCharacters` of the thread.

If the numeric format includes the currency symbol, ISO currency symbol, or the dual currency symbol, then the provided string must use those symbols defined by the `OracleGlobalization.Currency`, `OracleGlobalization`.`ISOCurrency`, and `OracleGlobalization`.`DualCurrency` properties respectively.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class OracleDecimalSample
    {
      static void Main(string[] args)
      {
        // Set the nls parameters related to currency
        OracleGlobalization info = OracleGlobalization.GetClientInfo();
        info.Currency = "$";
        info.NumericCharacters = ".,";
        OracleGlobalization.SetThreadInfo(info);

        // Construct an OracleDecimal using a valid numeric format
        OracleDecimal dec = new OracleDecimal("$2,222.22","L9G999D99");

        // Print "$2,222.22"
        Console.WriteLine(dec.ToString());
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)

- "[OracleGlobalization Class](OracleGlobalizationClass.md)"

- "[Globalization Support](featGlobal.md)"
