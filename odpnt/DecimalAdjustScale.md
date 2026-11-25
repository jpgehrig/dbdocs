This method returns a new `OracleDecimal` with the specified number of digits and indicates whether or not to round or truncate the number if the scale is less than the original.

### Declaration

    // C#
    public static OracleDecimal AdjustScale(OracleDecimal val, int digits,
         bool fRound);

### Parameters

- `val`

  An `OracleDecimal`.

- `digits`

  The number of digits.

- `fRound`

  Indicates whether or not to round or truncate the number. Setting it to `true` rounds the number and setting it to `false` truncates the number.

### Return Value

An `OracleDecimal`.

### Remarks

If the supplied `OracleDecimal` has a null value, the returned `OracleDecimal` has a null value.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Types;

    class AdjustScaleSample
    {
      static void Main(string[] args)
      {
        OracleDecimal dec1 = new OracleDecimal(5.555);

        // Adjust Scale to 2 with rounding off
        OracleDecimal dec2 = OracleDecimal.AdjustScale(dec1, 2, true);

        // Prints 5.56
        Console.WriteLine(dec2.ToString());

        // Adjust Scale to 2 with truncation
        OracleDecimal dec3 = OracleDecimal.AdjustScale(dec1, 2, false);

        // Prints 5.55
        Console.WriteLine(dec3.ToString());
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
