This method gets an `OracleDate` structure and sets its value for date and time using the supplied string.

### Declaration

    // C#
    public static OracleDate Parse (string dateStr);

### Parameters

- `dateStr`

  A string that represents an Oracle `DATE`.

### Return Value

An `OracleDate` structure.

### Exceptions

`ArgumentException` - The `dateStr` is an invalid string representation of an Oracle `DATE` or the `dateStr` is not in the date format specified by the thread's `OracleGlobalization`.`DateFormat` property, which represents the Oracle `NLS_DATE_FORMAT` parameter.

`ArgumentNullException` - The `dateStr` is null.

### Remarks

The names and abbreviations used for months and days are in the language specified by the `DateLanguage` and `Calendar` properties of the thread's `OracleGlobalization` object. If any of the thread's globalization properties are set to null or an empty string, the client computer's settings are used.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Types;
    using Oracle.DataAccess.Client;

    class ParseSample
    {
      static void Main(string[] args)
      {
        // Set the thread's DateFormat for the OracleDate constructor
        OracleGlobalization info = OracleGlobalization.GetClientInfo();
        info.DateFormat = "YYYY-MON-DD";
        OracleGlobalization.SetThreadInfo(info);

        // Construct OracleDate from a string using the DateFormat specified
        OracleDate date = OracleDate.Parse("1999-DEC-01");

        // Set a different DateFormat on the thread for ToString()
        info.DateFormat = "MM-DD-YY";
        OracleGlobalization.SetThreadInfo(info);

        // Print "12-01-1999"
        Console.WriteLine(date.ToString());
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDate Structure](OracleDateStructure.md)

- [OracleDate Members](DateMembers.md)

- "[OracleGlobalization Class](OracleGlobalizationClass.md)"

- "[Globalization Support](featGlobal.md)"

- [Oracle Database SQL Language Reference](../sqlrf/Format-Models.md) for further information on datetime format elements
