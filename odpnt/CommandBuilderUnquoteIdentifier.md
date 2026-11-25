This method returns the correct unquoted form of the provided quoted identifier, removing any escape notation for quotes embedded in the identifier.

### Declaration

    // C#
    public override string UnquoteIdentifier(string quotedIdentifier);

### Parameters

- `quotedIdentifier`

  The quoted string identifier.

### Return Value

The unquoted identifier, with escape notation for any embedded quotes removed.

### Exceptions

`ArgumentNullException` - The input parameter is null.

`ArgumentException` - The input parameter is empty.

### Remarks

This method is independent of any `OracleConnection` or `OracleCommand` objects.

### Example

    // C#

    using System;
    using System.Data;
    using System.Data.Common;
    using Oracle.DataAccess.Client;

    class UnQuoteIdentifierSample
    {
      static void Main(string[] args)
      {
        //create an OracleCommandBuilder object.
        OracleCommandBuilder builder = new OracleCommandBuilder();

        string identifier = "US\"ER";
        Console.WriteLine("Identifier is {0}", identifier);

        // quote the identifier
        string quoteIdentifier = builder.QuoteIdentifier(identifier);

        //quoteIdentifier of "US\"ER" is (\"US\"\"ER\")
        Console.WriteLine("QuotedIdentifier is {0}" , quoteIdentifier);
        string unquoteIdentifier = builder.UnquoteIdentifier(quoteIdentifier);

        //And its unquoteIdentifier is US\"ER
        Console.WriteLine("UnquotedIdentifier is {0}" , unquoteIdentifier);
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommandBuilder Class](OracleCommandBuilderClass.md)

- [OracleCommandBuilder Members](CommandBuilderMembers.md)
