Overrides `ValueType`

This method converts the current `OracleDate` structure to a `string`.

### Declaration

    // C#
    public override string ToString();

### Return Value

A string.

### Remarks

The returned value is a string representation of the `OracleDate` in the format specified by the thread's `OracleGlobalization`.`DateFormat` property. The names and abbreviations used for months and days are in the language specified by the thread's `OracleGlobalization`.`DateLanguage` and `OracleGlobalization.Calendar` properties. If any of the thread's globalization properties are set to null or an empty string, the client computer's settings are used.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class ToStringSample
    {
      static void Main(string[] args)
      {
        // Set the thread's DateFormat to a specific format
        OracleGlobalization info = OracleGlobalization.GetClientInfo();
        info.DateFormat = "YYYY-MON-DD";
        OracleGlobalization.SetThreadInfo(info);

        // Construct OracleDate from a string using the DateFormat specified
        OracleDate date = (OracleDate)"1999-DEC-01";

        // Set a different DateFormat on the thread for ToString()
        info.DateFormat = "YYYY/MM/DD";
        OracleGlobalization.SetThreadInfo(info);

        // Prints "1999/12/01"
        Console.WriteLine(date.ToString());
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDate Structure](OracleDateStructure.md)

- [OracleDate Members](DateMembers.md)

- "[OracleGlobalization Class](OracleGlobalizationClass.md)"

- "[Globalization Support](featGlobal.md)"
