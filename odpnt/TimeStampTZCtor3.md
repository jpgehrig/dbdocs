This constructor creates a new instance of the `OracleTimeStampTZ` structure and sets its value for date and time using the supplied string.

### Declaration

    // C#
    public OracleTimeStampTZ (string tsStr);

### Parameters

- `tsStr`

  A string that represents an Oracle `TIMESTAMP` `WITH` `TIME` `ZONE`.

### Exceptions

`ArgumentException` - The `tsStr` is an invalid string representation of an Oracle `TIMESTAMP` `WITH` `TIME` `ZONE` or the `tsStr` is not in the timestamp format specified by the `OracleGlobalization`.`TimeStampTZFormat` property of the thread.

`ArgumentNullException` - The `tsStr` value is null.

### Remarks

The names and abbreviations used for months and days are in the language specified by the `DateLanguage` and `Calendar` properties of the thread's `OracleGlobalization` object. If any of the thread's globalization properties are set to null or an empty string, the client computer's settings are used.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class OracleTimeStampTZSample
    {
      static void Main()
      {
        OracleGlobalization info = OracleGlobalization.GetClientInfo();
        info.TimeStampTZFormat = "DD-MON-YYYY HH:MI:SS.FF AM TZR";
        OracleGlobalization.SetThreadInfo(info);

        // construct OracleTimeStampTZ from a string using the format specified.
        OracleTimeStampTZ tstz = new OracleTimeStampTZ("11-NOV-1999" +
          "11:02:33.444 AM US/Pacific");

        // Set the nls_timestamp_tz_format for the ToString() method
        info.TimeStampTZFormat = "YYYY-MON-DD HH:MI:SS.FF AM TZR";
        OracleGlobalization.SetThreadInfo(info);

        // Prints "1999-NOV-11 11:02:33.444000000 AM US/Pacific"
        Console.WriteLine(tstz.ToString());
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)

- "[OracleGlobalization Class](OracleGlobalizationClass.md)"

- "[Globalization Support](featGlobal.md)"

- [Oracle Database SQL Language Reference](../sqlrf/Format-Models.md) for further information on date format elements
