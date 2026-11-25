This method removes all the `OracleParameter` objects from the collection.

### Declaration

    // C#
    public override void Clear();

### Implements

`IList`

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class ClearSample
    {
      static void Main()
      {
        OracleCommand cmd = new OracleCommand();

        // Add parameter to the OracleParameterCollection
        OracleParameter prm = cmd.Parameters.Add("MyParam", OracleDbType.Decimal);

        // Prints "cmd.Parameters.Count = 1"
        Console.WriteLine("cmd.Parameters.Count = " + cmd.Parameters.Count);

        // Clear all parameters in the OracleParameterCollection
        cmd.Parameters.Clear();

        // Prints "cmd.Parameters.Count = 0"
        Console.WriteLine("cmd.Parameters.Count = " + cmd.Parameters.Count);

        prm.Dispose();
        cmd.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameterCollection Class](OracleParameterCollectionClass.md)

- [OracleParameterCollection Members](ParameterCollectionMembers.md)
