This static method returns an `OracleTimeStampTZ` structure and sets its value for date and time using the supplied string.

### Declaration

    // C#
    public static OracleTimeStampTZ Parse(string tsStr);

### Parameters

- `tsStr`

  A string that represents an Oracle `TIMESTAMP` `WITH` `TIME` `ZONE`.

### Return Value

An `OracleTimeStampTZ` structure.

### Exceptions

`ArgumentException` - The `tsStr` is an invalid string representation of an Oracle `TIMESTAMP` `WITH` `TIME` `ZONE` or the `tsStr` is not in the timestamp format specified by the `OracleGlobalization`.`TimeStampTZFormat` property of the thread, which represents the Oracle `NLS_TIMESTAMP_TZ_FORMAT` parameter.

`ArgumentNullException` - The `tsStr` value is null.

### Remarks

The names and abbreviations used for months and days are in the language specified by the `DateLanguage` and `Calendar` properties of the thread's `OracleGlobalization` object. If any of the thread's globalization properties are set to null or an empty string, the client computer's settings are used.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class ParseSample
    {
      static void Main()
      {
        // Set the nls_timestamp_tz_format for the Parse() method
        OracleGlobalization info = OracleGlobalization.GetClientInfo();
        info.TimeStampTZFormat = "DD-MON-YYYY HH:MI:SS.FF AM TZR";
        OracleGlobalization.SetThreadInfo(info);

        // construct OracleTimeStampTZ from a string using the format specified.
        OracleTimeStampTZ tstz = OracleTimeStampTZ.Parse("11-NOV-1999 " +
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
