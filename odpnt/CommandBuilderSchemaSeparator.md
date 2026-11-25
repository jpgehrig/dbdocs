This property specifies the character to be used for the separator between the schema identifier and other identifiers.

### Declaration

    // C#
    public override string SchemaSeparator {get; set; }

### Property Value

The character to be used as the schema separator.

### Exceptions

`NotSupportedException` - The input value is not a dot (`.`).

### Remarks

The default schema separator is a dot (`.`). The only acceptable value for this property is a dot (`.`).

This property is independent of any `OracleConnection` or `OracleCommand` objects.

### Example

    // C#

    using System;
    using System.Data;
    using System.Data.Common;
    using Oracle.DataAccess.Client;

    class SchemaSeperatorSample
    {
      static void Main(string[] args)
      {
        try
        {
          OracleCommandBuilder cmdBuilder = new OracleCommandBuilder();

          //schemaSeparator is dot(.)
          Console.WriteLine("schemaSeparator is {0}",
                                cmdBuilder.SchemaSeparator);

          //set the schemaseparator, only '.' is allowed.
          cmdBuilder.SchemaSeparator = ".";

          // the only acceptable value for this property is a dot (.)
          // Hence the following line will throw NotSupportedException
          cmdBuilder.SchemaSeparator = "!";
        }
        catch (Exception ex)
        {
          Console.WriteLine(ex.Message);
          Console.WriteLine(ex.StackTrace);
        }
      }
    }

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleCommandBuilder Class](OracleCommandBuilderClass.md)

- [OracleCommandBuilder Members](CommandBuilderMembers.md)
