This method creates a shallow copy of an `OracleParameter` object.

### Declaration

    // C#
    public object Clone();

### Return Value

An `OracleParameter` object.

### Implements

`ICloneable`

### Remarks

The cloned object has the same property values as that of the object being cloned.

### Example

    // C#

    using System;
    using System.Data;
    using Oracle.DataAccess.Client;

    class CloneSample
    {
      static void Main()
      {
        OracleParameter prm1 = new OracleParameter();

        // Prints "prm1.ParameterName = "
        Console.WriteLine("prm1.ParameterName = " + prm1.ParameterName);

        // Set the ParameterName before cloning
        prm1.ParameterName = "MyParam";

        // Clone the OracleParameter
        OracleParameter prm2 = (OracleParameter) prm1.Clone();

        // Prints "prm2.ParameterName = MyParam"
        Console.WriteLine("prm2.ParameterName = " + prm2.ParameterName);

        prm1.Dispose();
        prm2.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameter Class](OracleParameterClass.md)

- [OracleParameter Members](ParameterMembers.md)
