This method converts the supplied string to an `OracleDate` structure.

### Declaration

    // C#
    public explicit operator OracleDate (string dateStr);

### Parameters

- `dateStr`

  A string representation of an Oracle `DATE`.

### Return Value

The returned `OracleDate` structure contains the date and time in the string `dateStr`.

### Exceptions

`ArgumentNullException` - The `dateStr` is null.

`ArgumentException` - This exception is thrown if any of the following conditions exist:

- The `dateStr` is an invalid string representation of an Oracle `DATE`.

- The `dateStr` is not in the date format specified by the thread's `OracleGlobalization`.`DateFormat` property, which represents the Oracle `NLS_DATE_FORMAT` parameter.

### Remarks

The names and abbreviations used for months and days are in the language specified by the `DateLanguage` and `Calendar` properties of the thread's `OracleGlobalization` object. If any of the thread's globalization properties are set to null or an empty string, the client computer's settings are used.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class OracleDateSample
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
        info.DateFormat = "MON DD YY";
        OracleGlobalization.SetThreadInfo(info);

        // Prints "DEC 01 99"
        Console.WriteLine(date.ToString());
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDate Structure](OracleDateStructure.md)

- [OracleDate Members](DateMembers.md)

- "[OracleGlobalization Class](OracleGlobalizationClass.md)"

- "[Globalization Support](featGlobal.md)"
