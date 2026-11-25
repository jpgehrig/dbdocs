This constructor creates a new instance of the `OracleDate` structure and sets its value using the supplied string.

### Declaration

    // C#
    public OracleDate (string dateStr);

### Parameters

- `dateStr`

  A string that represents an Oracle `DATE`.

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

    class OracleDateSample
    {
      static void Main(string[] args)
      {
        // Set the thread's DateFormat for the OracleDate constructor
        OracleGlobalization info = OracleGlobalization.GetClientInfo();
        info.DateFormat = "YYYY-MON-DD";
        OracleGlobalization.SetThreadInfo(info);

        // construct OracleDate from a string using the DateFormat specified.
        OracleDate date = new OracleDate("1999-DEC-01");

        // Set a different DateFormat for the thread
        info.DateFormat = "MM/DD/YYYY";
        OracleGlobalization.SetThreadInfo(info);

        // Print "12/01/1999"
        Console.WriteLine(date.ToString());
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDate Structure](OracleDateStructure.md)

- [OracleDate Members](DateMembers.md)

- "[OracleGlobalization Class](OracleGlobalizationClass.md)"

- [Oracle Database SQL Language Reference](../sqlrf/Format-Models.md) for further information on date format elements
