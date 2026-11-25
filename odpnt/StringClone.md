This method creates a copy of an `OracleString` instance.

### Declaration

    // C#
    public OracleString Clone();

### Return Value

An `OracleString` structure.

### Remarks

The cloned object has the same property values as that of the object being cloned.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Types;

    class CloneSample
    {
      static void Main()
      {
        OracleString str1 = new OracleString("aAaAa");
        OracleString str2 = str1.Clone();

        // The OracleStrings are same; Prints 0
        Console.WriteLine(str1.CompareTo(str2));
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleString Structure](OracleStringStructure.md)

- [OracleString Members](StringMembers.md)
