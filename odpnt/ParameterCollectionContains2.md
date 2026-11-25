This method indicates whether or not an `OracleParameter` object exists in the collection using the supplied string.

### Declaration

    // C#
    public override bool Contains(string name);

### Parameters

- `name`

  The name of `OracleParameter` object.

### Return Value

Returns `true` if the collection contains the `OracleParameter` object with the specified parameter name; otherwise, returns `false`.

### Implements

`IDataParameterCollection`

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class ContainsSample
    {
      static void Main()
      {
        OracleCommand cmd = new OracleCommand();

        // Add parameter to the OracleParameterCollection
        OracleParameter prm = cmd.Parameters.Add("MyParam", OracleDbType.Decimal);

        // Check if the OracleParameterCollection contains "MyParam"
        bool bContains = cmd.Parameters.Contains("MyParam");

        // Prints "bContains = True"
        Console.WriteLine("bContains = " + bContains);

        // Check if the OracleParameterCollection contains "NoParam"
        bContains = cmd.Parameters.Contains("NoParam");

        // Prints "bContains = False"
        Console.WriteLine("bContains = " + bContains);

        prm.Dispose();
        cmd.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameterCollection Class](OracleParameterCollectionClass.md)

- [OracleParameterCollection Members](ParameterCollectionMembers.md)
