This method returns a new `OracleDecimal` structure with a new specified precision.

### Declaration

    // C#
    public static OracleDecimal SetPrecision(OracleDecimal val, int precision);

### Parameters

- `val`

  An `OracleDecimal` structure.

- `precision`

  The specified precision. Range of precision is 1 to 38.

### Return Value

An `OracleDecimal` structure.

### Remarks

The returned `OracleDecimal` is rounded off if the specified precision is smaller than the precision of `val`.

If `val` has a null value, the returned `OracleDecimal` has a null value.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Types;

    class SetPrecisionSample
    {
      static void Main(string[] args)
      {
        OracleDecimal dec1 = new OracleDecimal(555.6666);

        // Set the precision of dec1 to 3
        OracleDecimal dec2 = OracleDecimal.SetPrecision(dec1, 3);

        // Prints 556
        Console.WriteLine(dec2.ToString());

        // Set the precision of dec1 to 4
        OracleDecimal dec3 = OracleDecimal.SetPrecision(dec1, 4);

        // Prints 555.7
        Console.WriteLine(dec3.ToString());
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)""[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
