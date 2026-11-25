This property obtains the particular `byte` in an `OracleBinary` structure using an index.

### Declaration

    // C#
    public byte this[int index] {get;}

### Property Value

A byte in the specified index.

### Exceptions

`OracleNullValueException` - The current instance has a null value.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Types;

    class ItemSample
    {
      static void Main(string[] args)
      {
        OracleBinary binary = new OracleBinary(new byte[] {1,2,3,4});

        // Prints the value 4
        Console.WriteLine(binary[binary.Length - 1]);
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBinary Structure](OracleBinaryStructure.md)

- [OracleBinary Members](BinaryMembers.md)
