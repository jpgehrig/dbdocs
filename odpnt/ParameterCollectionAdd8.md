This method adds an `OracleParameter` object to the collection using the supplied name, database type, and size.

### Declaration

    // C#
    public OracleParameter Add(string name, OracleDbType dbType, int size);

### Parameters

- `name `

  The parameter name.

- `dbType`

  The data type of the `OracleParameter`.

- `size`

  The size of `OracleParameter`.

### Return Value

The newly created `OracleParameter` object which was added to the collection.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class AddSample
    {
      static void Main()
      {
        OracleCommand cmd = new OracleCommand();

        // Add parameter to the OracleParameterCollection
        OracleParameter prm = cmd.Parameters.Add(
          "MyParam", OracleDbType.Varchar2, 10);

        // Prints "cmd.Parameters.Count = 1"
        Console.WriteLine("cmd.Parameters.Count = " + cmd.Parameters.Count);

        prm.Dispose();
        cmd.Dispose();
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleParameterCollection Class](OracleParameterCollectionClass.md)

- [OracleParameterCollection Members](ParameterCollectionMembers.md)
