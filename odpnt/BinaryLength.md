This property returns the length of the binary data.

### Declaration

    // C#
    public int length {get;}

### Property Value

Length of the binary data.

### Exceptions

`OracleNullValueException` - The current instance has a null value.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Types;

    class LengthSample
    {
      static void Main(string[] args)
      {
        OracleBinary binary = new OracleBinary(new byte[] {1,2,3,4});

        // Prints the value 4
        Console.WriteLine(binary.Length);
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBinary Structure](OracleBinaryStructure.md)

- [OracleBinary Members](BinaryMembers.md)
