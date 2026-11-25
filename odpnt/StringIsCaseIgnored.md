This property indicates whether or not case should be ignored when performing string comparison.

### Declaration

    //C#
    public bool IsCaseIgnored {get;set;}

### Property Value

Returns `true` if string comparison must ignore case; otherwise `false`.

### Remarks

Default value is `true`.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Types;

    class IsCaseIgnoredSample
    {
      static void Main()
      {
        OracleString string1 = new OracleString("aAaAa");
        OracleString string2 = new OracleString("AaAaA");

        // Ignore case for comparisons
        string1.IsCaseIgnored = true;
        string2.IsCaseIgnored = true;

        // Same; Prints 0
        Console.WriteLine(string1.CompareTo(string2));

        // Make comparisons case sensitive
        // Note that IsCaseIgnored must be set to false for both
        //   OracleStrings; otherwise an exception is thrown
        string1.IsCaseIgnored = false;
        string2.IsCaseIgnored = false;

        // Different; Prints nonzero value
        Console.WriteLine(string1.CompareTo(string2));
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleString Structure](OracleStringStructure.md)

- [OracleString Members](StringMembers.md)
