Overrides `Object`

This method converts the current `OracleTimeStamp` structure to a string.

### Declaration

    // C#
    public override string ToString();

### Return Value

A `string` that represents the same date and time as the current `OracleTimeStamp` structure.

### Remarks

The returned value is a string representation of an `OracleTimeStamp` in the format specified by the `OracleGlobalization`.`TimeStampFormat` property of the thread.

The names and abbreviations used for months and days are in the language specified by the `OracleGlobalization`'s `DateLanguage` and `Calendar` properties of the thread. If any of the thread's globalization properties are set to null or an empty string, the client computer's settings are used.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Types;
    using Oracle.DataAccess.Client;

    class ToStringSample
    {
      static void Main()
      {
        // Set the nls_timestamp_format for the OracleTimeStamp(string)
        // constructor
        OracleGlobalization info = OracleGlobalization.GetClientInfo();
        info.TimeStampFormat = "DD-MON-YYYY HH:MI:SS.FF AM";
        OracleGlobalization.SetThreadInfo(info);

        // construct OracleTimeStamp from a string using the format specified.
        OracleTimeStamp ts = new OracleTimeStamp("11-NOV-1999 11:02:33.444 AM");

        // Set the nls_timestamp_format for the ToString() method
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
