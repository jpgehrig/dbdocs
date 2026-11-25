This method indicates whether or not the supplied object exists in the collection.

### Declaration

    // C#
    public override bool Contains(object obj)

### Parameters

- `obj`

  The object.

### Return Value

A `bool` that indicates whether or not the `OracleParameter` specified is inside the collection.

### Implements

`IList`

### Exceptions

`InvalidCastException` - The supplied `obj` is not an `OracleParameter` object.

### Remarks

Returns `true` if the collection contains the `OracleParameter` object; otherwise, returns `false`.

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
        OracleParameter prm1 = cmd.Parameters.Add("MyParam", OracleDbType.Decimal);

        // Check if the OracleParameterCollection contains prm1
        bool bContains = cmd.Parameters.Contains(prm1);

        // Prints "bContains = True"
        Console.WriteLine("bContains = " + bContains);

        OracleParameter prm2 = new OracleParameter();

        // Check if the OracleParameterCollection contains prm2
        bContains = cmd.Parameters.Contains(prm2);

        // Prints "bContains = False"
        Console.WriteLine("bContains = " + bContains);

        prm1.Dispose();
        prm2.Dispose();
        cmd.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameterCollection Class](OracleParameterCollectionClass.md)

- [OracleParameterCollection Members](ParameterCollectionMembers.md)
