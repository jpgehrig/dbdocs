Overrides `Object`

This method converts the current `OracleTimeStampTZ` structure to a string.

### Declaration

    // C#
    public override string ToString();

### Return Value

A `string` that represents the same date and time as the current `OracleTimeStampTZ` structure.

### Remarks

The returned value is a string representation of an `OracleTimeStampTZ` in the format specified by the `OracleGlobalization`.`TimeStampTZFormat` property of the thread. The names and abbreviations used for months and days are in the language specified by the `OracleGlobalization`.`DateLanguage` and the `OracleGlobalization.Calendar` properties of the thread. If any of the thread's globalization properties are set to null or an empty string, the client computer's settings are used.

### Example

    // C#

    using System;
    using Oracle.DataAccess.Client;
    using Oracle.DataAccess.Types;

    class ToStringSample
    {
      static void Main()
      {
        // Set the nls parameters for the current thread
        OracleGlobalization info = OracleGlobalization.GetClientInfo();
        info.TimeZone = "US/Eastern";
        info.TimeStampFormat = "DD-MON-YYYY HH:MI:SS.FF AM";
        info.TimeStampTZFormat = "DD-MON-YYYY HH:MI:SS.FF AM TZR";
        OracleGlobalization.SetThreadInfo(info);

        // Create an OracleTimeStampTZ in US/Pacific time zone
        OracleTimeStampTZ tstz1=new OracleTimeStampTZ("11-NOV-1999 "+
          "11:02:33.444 AM US/Pacific");

        // Note that ToOracleTimeStampTZ uses the thread's time zone region,
        // "US/Eastern"
        OracleTimeStamp ts = new OracleTimeStamp("11-NOV-1999 11:02:33.444 AM");
        OracleTimeStampTZ tstz2 = ts.ToOracleTimeStampTZ();

        // Calculate the difference between tstz1 and tstz2
        OracleIntervalDS idsDiff = tstz1.GetDaysBetween(tstz2);

        // Prints "US/Pacific"
        Console.WriteLine("tstz1.TimeZone = " + tstz1.TimeZone);

        // Prints "US/Eastern"
        Console.WriteLine("tstz2.TimeZone = " + tstz2.TimeZone);

        // Prints 3
        Console.WriteLine("idsDiff.Hours = " + idsDiff.Hours);

        // Prints 0
        Console.WriteLine("idsDiff.Minutes = " + idsDiff.Minutes);
      }
    }

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)

- [OracleTimeStampTZ Members](TimeStampTZMembers.md)

- "[OracleGlobalization Class](OracleGlobalizationClass.md)"

- "[Globalization Support](featGlobal.md)"
