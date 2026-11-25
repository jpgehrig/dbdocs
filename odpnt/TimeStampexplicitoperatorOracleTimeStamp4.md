This static type conversion operator converts the supplied string to an `OracleTimeStamp` structure.

### Declaration

    // C#
    public static explicit operator OracleTimeStamp(string tsStr);

### Parameters

- `tsStr`

  A string representation of an Oracle `TIMESTAMP`.

### Return Value

An `OracleTimeStamp`.

### Exceptions

`ArgumentException` - The `tsStr` is an invalid string representation of an Oracle `TIMESTAMP` or the `tsStr` is not in the timestamp format specified by the thread's `OracleGlobalization`.`TimeStampFormat` property, which represents the Oracle `NLS_TIMESTAMP_FORMAT` parameter.

### Remarks

The names and abbreviations used for months and days are in the language specified by the `DateLanguage` and `Calendar` properties of the thread's `OracleGlobalization` object. If any of the thread's globalization properties are set to null or an empty string, the client computer's settings are used.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Types;
    using Oracle.DataAccess.Client;

    class OracleTimeStampSample
    {
      static void Main()
      {
        // Set the nls_timestamp_format for the explicit
        // operator OracleTimeStamp(string)
        OracleGlobalization info = OracleGlobalization.GetClientInfo();
        info.TimeStampFormat = "DD-MON-YYYY HH:MI:SS.FF AM";
        OracleGlobalization.SetThreadInfo(info);

        // construct OracleTimeStamp from a string using the format specified.
        OracleTimeStamp ts = new OracleTimeStamp("11-NOV-1999 11:02:33.444 AM");

        // Set the nls_timestamp_format for the ToString method
        info.TimeStampFormat = "YYYY-MON-DD HH:MI:SS.FF AM";
        OracleGlobalization.SetThreadInfo(info);

        // Prints "1999-NOV-11 11:02:33.444000000 AM"
        Console.WriteLine(ts.ToString());
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStamp Structure](OracleTimeStampStructure.md)

- [OracleTimeStamp Members](TimeStampMembers.md)

- "[OracleGlobalization Class](OracleGlobalizationClass.md)"

- "[Globalization Support](featGlobal.md)"

- [Oracle Database SQL Language Reference](../sqlrf/Format-Models.md) for further information on datetime format elements
