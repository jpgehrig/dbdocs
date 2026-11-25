This method removes the supplied `OracleParameter` from the collection.

### Declaration

    // C#
    public override void Remove(object obj);

### Parameters

- `obj`

  The specified object to remove.

### Implements

`IList`

### Exceptions

`InvalidCastException` - The supplied `obj` cannot be cast to an `OracleParameter` object.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class RemoveSample
    {
      static void Main()
      {
        OracleCommand cmd = new OracleCommand();

        // Add 2 parameters to the OracleParameterCollection
        OracleParameter prm1 = cmd.Parameters.Add("MyParam1", OracleDbType.Decimal);
        OracleParameter prm2 = cmd.Parameters.Add("MyParam2", OracleDbType.Decimal);

        // Prints "cmd.Parameters.Count = 2"
        Console.WriteLine("cmd.Parameters.Count = " + cmd.Parameters.Count);

        // Remove the 1st parameter from the OracleParameterCollection
        cmd.Parameters.Remove(prm1);

        // Prints "cmd.Parameters.Count = 1"
        Console.WriteLine("cmd.Parameters.Count = " + cmd.Parameters.Count);

        // Prints "cmd.Parameters[0].ParameterName = MyParam2"
        Console.WriteLine("cmd.Parameters[0].ParameterName = " +
          cmd.Parameters[0].ParameterName);

        prm1.Dispose();
        prm2.Dispose();
        cmd.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameterCollection Class](OracleParameterCollectionClass.md)

- [OracleParameterCollection Members](ParameterCollectionMembers.md)
