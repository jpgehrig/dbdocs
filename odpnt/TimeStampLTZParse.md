This static method creates an `OracleTimeStampLTZ` structure and sets its value using the supplied string.

### Declaration

    // C#
    public static OracleTimeStampLTZ Parse(string tsStr);

### Parameters

- `tsStr`

  A string that represents an Oracle `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE`.

### Return Value

An `OracleTimeStampLTZ` structure.

### Exceptions

`ArgumentException` - The `tsStr` parameter is an invalid string representation of an Oracle `TIMESTAMP` `WITH` `LOCAL` `TIME` `ZONE` or the `tsStr` is not in the timestamp format specified by the `OracleGlobalization`.`TimeStampFormat` property of the thread, which represents the Oracle `NLS_TIMESTAMP_FORMAT` parameter.

`ArgumentNullException` - The `tsStr` value is null.

### Remarks

The names and abbreviations used for months and days are in the language specified by the `DateLanguage` and `Calendar` properties of the thread's `OracleGlobalization` object. If any of the thread's globalization properties are set to null or an empty string, the client computer's settings are used.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Types;
    using Oracle.DataAccess.Client;

    class ParseSample
    {
      static void Main()
      {
        // Set the nls_timestamp_format for the Parse() method
        OracleGlobalization info = OracleGlobalization.GetClientInfo();
        info.TimeStampFormat = "DD-MON-YYYY HH:MI:SS.FF AM";
        OracleGlobalization.SetThreadInfo(info);

        // construct OracleTimeStampLTZ from a string using the format specified.
        OracleTimeStampLTZ ts =
          OracleTimeStampLTZ.Parse("11-NOV-1999 11:02:33.444 AM");

        // Set the nls_timestamp_format for the ToString() method
        info.TimeStampFormat = "YYYY-MON-DD HH:MI:SS.FF AM";
        OracleGlobalization.SetThreadInfo(info);

        // Prints "1999-NOV-11 11:02:33.444000000 AM"
        Console.WriteLine(ts.ToString());
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampLTZ Structure](OracleTimeStampLTZStructure.md)

- [OracleTimeStampLTZ Members](TimeStampLTZMembers.md)

- "[OracleGlobalization Class](OracleGlobalizationClass.md)"

- "[Globalization Support](featGlobal.md)"
