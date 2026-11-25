This method compares the current instance to an object and returns an integer that represents their relative values

### Declaration

    // C#
    public int CompareTo(object obj);

### Parameters

- `obj`

  The object being compared.

### Return Value

The method returns a number that is:

- Less than zero: if the current `OracleBinary` instance value is less than `obj`.

- Zero: if the current `OracleBinary` instance and `obj` values have the same binary data.

- Greater than zero: if the current `OracleBinary` instance value is greater than `obj`.

### Implements

`IComparable`

### Exceptions

`ArgumentException` - The parameter is not of type `OracleBinary`.

### Remarks

The following rules apply to the behavior of this method.

- The comparison must be between `OracleBinary`s. For example, comparing an `OracleBinary` instance with an `OracleTimeStamp` instance is not allowed. When an `OracleBinary` is compared with a different type, an `ArgumentException` is thrown.

- Any `OracleBinary` that has a value is greater than an `OracleBinary` that has a null value.

- Two `OracleBinary`s that contain a null value are equal.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Types;

    class CompareToSample
    {
      static void Main(string[] args)
      {
        OracleBinary binary1 = new OracleBinary(new byte[] {1,2,3});
        OracleBinary binary2 = new OracleBinary(new byte[] {1,2,3,4});

        // Compare
        if (binary1.CompareTo(binary2) == 0)
          Console.WriteLine("binary1 is the same as binary2");
        else
          Console.WriteLine("binary1 is different from binary2");
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBinary Structure](OracleBinaryStructure.md)

- [OracleBinary Members](BinaryMembers.md)
