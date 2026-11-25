The `OracleDecimal` structure represents an Oracle `NUMBER` in the database or any Oracle numeric value.

### Class Inheritance

`System.Object`

`  System.ValueType`

`    Oracle.DataAccess.Types.OracleDecimal`

### Declaration

    // C#
     public struct OracleDecimal : IComparable, INullable, IXmlSerializable

### Requirements

| Provider       | ODP.NET, Unmanaged Driver  | ODP.NET, Managed Driver           | ODP.NET Core                      |
|:---------------|:---------------------------|:----------------------------------|:----------------------------------|
| Assembly       | `Oracle.DataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    | `Oracle.ManagedDataAccess.dll`    |
| Namespace      | `Oracle.DataAccess.Client` | `Oracle.ManagedDataAccess.Client` | `Oracle.ManagedDataAccess.Client` |
| .NET Framework | 3.5, 4.5, 4.6, 4.7         | 4.5, 4.6, 4.7                     | 4.6.1 or higher                   |
| .NET Core      | \-                         | \-                                | 2.1 or higher                     |

### Thread Safety

All public static methods are thread-safe, although instance methods do not guarantee thread safety.

### Remarks

`OracleDecimal` can store up to 38 precision, while the .NET `Decimal` data type can only hold up to 28 precision. When accessing the `OracleDecimal.Value` property from an `OracleDecimal` that has a value greater than 28 precision, an exception is thrown. To retrieve the actual value of `OracleDecimal`, use the `OracleDecimal.ToString()` method. Another approach is to obtain the `OracleDecimal` value as a byte array in an internal Oracle `NUMBER` format through the `BinData` property.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Types;

    class OracleDecimalSample
    {
      static void Main(string[] args)
      {
        // Illustrates the range of OracleDecimal vs. .NET decimal
        OracleDecimal decimal1 = OracleDecimal.MinValue;
        OracleDecimal decimal2 = OracleDecimal.MaxValue;
        OracleDecimal decimal3 = new OracleDecimal(decimal.MinValue);
        OracleDecimal decimal4 = new OracleDecimal(decimal.MaxValue);

        // Print the ranges
        Console.WriteLine("OracleDecimal can range from\n{0}\nto\n{1}\n",
          decimal1, decimal2);
        Console.WriteLine(".NET decimal can range from\n{0}\nto\n{1}",
          decimal3, decimal4);
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Members](DecimalMembers.md)

- [OracleDecimal Constructors](DecimalCtors.md)

- [OracleDecimal Static Fields](DecimalStaticFields.md)

- [OracleDecimal Static (Comparison) Methods](DecimalStaticComparisonMethods.md)

- [OracleDecimal Static (Manipulation) Methods](DecimalStaticManipulationMethods.md)

- [OracleDecimal Static (Logarithmic) Methods](DecimalstaticLogarithmicMethods.md)

- [OracleDecimal Static (Trigonometric) Methods](DecimalStaticTrignometricMethods.md)

- [OracleDecimal Static (Comparison) Operators](DecimalStaticComparisonOperators.md)

- [OracleDecimal Static Operators (Conversion from .NET Type to OracleDecimal)](DecimalStaticOperatorsNetToDecimal.md)

- [OracleDecimal Static Operators (Conversion from OracleDecimal to .NET)](DecimalStaticOperatorsOracleDecimalToNet.md)

- [OracleDecimal Properties](DecimalProperties.md)

- [OracleDecimal Instance Methods](DecimalInstanceMethods.md)
