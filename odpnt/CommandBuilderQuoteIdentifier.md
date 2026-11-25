This method returns the correct quoted form of the provided unquoted identifier, with any embedded quotes in the identifier properly escaped.

### Declaration

    // C#
    public override string QuoteIdentifier(string unquotedIdentifier);

### Parameters

- `UnquotedIdentifier `

  An unquoted identifier string.

### Return Value

The quoted version of the identifier. Embedded quotes within the identifier are properly escaped.

### Exceptions

`ArgumentNullException` - The input parameter is null.

### Remarks

This method is independent of any `OracleConnection` or `OracleCommand` objects.

### Example

    // C#

    using System;
    using System.Data;
    using System.Data.Common;
    using Oracle.DataAccess.Client;

    class QuoteIdentifierSample
    {
      static void Main(string[] args)
      {
        OracleCommandBuilder builder = new OracleCommandBuilder();
        string quoteIdentifier = builder.QuoteIdentifier("US\"ER");

        //quoteIdentifier for "US\"ER" is (\"US\"\"ER\")
        Console.WriteLine("quoteIdentifier is {0}" , quoteIdentifier);
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommandBuilder Class](OracleCommandBuilderClass.md)

- [OracleCommandBuilder Members](CommandBuilderMembers.md)
