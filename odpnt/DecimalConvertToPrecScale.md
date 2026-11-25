This method returns a new `OracleDecimal` structure with a new precision and scale.

### Declaration

    // C#
    public static OracleDecimal ConvertToPrecScale(OracleDecimal val
        int precision, int scale);


### Parameters

- `val`

  An `OracleDecimal` structure.

- `precision`

  The precision. Range of precision is 1 to 38.

- `scale`

  The number of digits to the right of the decimal point. Range of scale is -84 to 127.

### Return Value

A new `OracleDecimal` structure.

### Remarks

If the supplied `OracleDecimal` has a null value, the returned `OracleDecimal` has a null value.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Types;

    class ConvertToPrecScaleSample
    {
      static void Main(string[] args)
      {
        OracleDecimal dec1 = new OracleDecimal(555.6666);

        // Set the precision of od to 5 and scale to 2
        OracleDecimal dec2 = OracleDecimal.ConvertToPrecScale(dec1,5,2);

        // Prints 555.67
        Console.WriteLine(dec2.ToString());

        // Set the precision of od to 3 and scale to 0
        OracleDecimal dec3 = OracleDecimal.ConvertToPrecScale(dec1,3,0);

        // Prints 556
        Console.WriteLine(dec3.ToString());
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Structure](OracleDecimalStructure.md)
