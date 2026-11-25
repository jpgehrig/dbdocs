ODP.NET globalization support enables applications to manipulate culture-sensitive data appropriately. This feature ensures proper string format, date, time, monetary, numeric, sort order, and calendar conventions depending on the Oracle globalization settings.

**Note:**

- ODP.NET, Managed Driver and ODP.NET Core are not `NLS_LANG` sensitive. They are only .NET locale sensitive.

- ODP.NET, Managed Driver and ODP.NET Core do not support thread-based globalization.

**See Also:**

"[OracleGlobalization Class](OracleGlobalizationClass.md)"

This section includes the following:

- Globalization Settings

- Globalization-Sensitive Operations

### Globalization Settings

An `OracleGlobalization` object can be used to represent the following:

- Client Globalization Settings

- Session Globalization Settings

- Thread-Based Globalization Settings

#### Client Globalization Settings

Client globalization settings are derived from the Oracle globalization setting (`NLS_LANG`) in the Windows registry of the local computer. The client globalization parameter settings are read-only and remain constant throughout the lifetime of the application. These settings can be obtained by calling the `OracleGlobalization.GetClientInfo` static method.

The following example retrieves the client globalization settings:

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class ClientGlobalizationSample
    {
      static void Main()
      {
        OracleGlobalization ClientGlob = OracleGlobalization.GetClientInfo();

        Console.WriteLine("Client machine language: " + ClientGlob.Language);
        Console.WriteLine("Client characterset: " + ClientGlob.ClientCharacterSet);
      }
    }

The properties of the `OracleGlobalization` object provide the Oracle globalization value settings.

#### Session Globalization Settings

Session globalization parameters are initially identical to client globalization settings. Unlike client settings, session globalization settings can be updated. However, they can be obtained only after establishing a connection against the database. The session globalization settings can be obtained by calling the `GetSessionInfo` method on the `OracleConnection` object. Invoking this method returns an instance of an `OracleGlobalization` class whose properties represent the globalization settings of the session.

When the `OracleConnection` object establishes a connection, it implicitly opens a session whose globalization parameters are initialized with those values specified by the client computer's Oracle globalization (or (NLS)) registry settings. The session settings can be updated and can change during its lifetime.

The following example changes the date format setting on the session:

    // C#

    using System;
    using Oracle.DataAccess.Client;

    class SessionGlobalizationSample
    {
      static void Main()
      {
        OracleConnection con = new OracleConnection();

        con.ConnectionString = "User Id=scott;Password=tiger;Data Source=oracle;";
        con.Open();

        OracleGlobalization SessionGlob = con.GetSessionInfo();

        // SetSessionInfo updates the Session with the new value
        SessionGlob.DateFormat = "YYYY/MM/DD";
        con.SetSessionInfo(SessionGlob);
        Console.WriteLine("Date Format successfully changed for the session");

        // Close and Dispose OracleConnection object
        con.Close();
        con.Dispose();
      }
    }

#### Thread-Based Globalization Settings

Thread-based globalization parameter settings are specific to each thread. Initially, these settings are identical to the client globalization parameters, but they can be changed as specified by the application. When ODP.NET Types are converted to and from strings, the thread-based globalization parameters are used, if applicable.

Thread-based globalization parameter settings are obtained by invoking the `GetThreadInfo` static method of the `OracleGlobalization` class. The `SetThreadInfo` static method of the `OracleGlobalization` class can be called to set the thread's globalization settings.

ODP.NET classes and structures rely solely on the `OracleGlobalization` settings when manipulating culture-sensitive data. They do not use .NET thread culture information. If the application uses only .NET types, `OracleGlobalization` settings have no effect. However, when conversions are made between ODP.NET types and .NET types, `OracleGlobalization` settings are used where applicable.

**Note:**

Changes to the `System.Threading.Thread. CurrentThread.CurrentCulture` property do not impact the `OracleGlobalization` settings of the thread or the session, or the reverse.

The following example shows how the thread's globalization settings are used by the ODP.NET Types:

    // C#

    using System;
    using Oracle.DataAccess.Types;
    using Oracle.DataAccess.Client;

    class ThreadBasedGlobalizationSample
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

The `OracleGlobalization` object validates property changes made to it. If an invalid value is used to set a property, an exception is thrown. Note that changes made to the `Territory` and `Language` properties change other properties of the `OracleGlobalization` object implicitly.

**See Also:**

[Oracle Database Globalization Support Guide](../nlspg/index.md) for more information on the properties affected by `Territory` and `Language` globalization settings

### Globalization-Sensitive Operations

This section lists ODP.NET types and operations that are dependent on or sensitive to globalization settings.

#### Operations Dependent on Client Computer's Globalization Settings

The `OracleString` structure depends on the `OracleGlobalization` settings of the client computer. The client character set of the local computer is used when it converts a Unicode string to a `byte[]` in the `GetNonUnicode` method and when it converts a `byte[]` of ANSI characters to Unicode in the `OracleString` constructor that accepts a `byte[]`.

#### Operations Dependent on Thread Globalization Settings

The thread globalization settings are used by ODP.NET types whenever they are converted to and from .NET string types, where applicable. Specific thread globalization settings are used in most cases, depending on the ODP.NET type, by the following:

- The `ToString` method

- The `Parse` static method

- Constructors that accept .NET string data

- Conversion operators to and from .NET strings

For example, the `OracleDate` type uses the `DateFormat` property of the thread globalization settings when the `ToString` method is invoked on it. This returns a `DATE` as a string in the format specified by the thread's settings.

The thread globalization settings also affect data that is retrieved into the `DataSet` as a string using Safe Type Mapping. If the type is format-sensitive, the strings are always in the format specified by the thread globalization settings.

For example, `INTERVAL` `DAY` `TO` `SECOND` data is not affected by thread settings because no format is applicable for this type. However, the `DateFormat` and `NumericCharacters` properties can impact the string representation of `DATE` and `NUMBER` types, respectively, when they are retrieved as strings into the `DataSet` through Safe Type Mapping.

**See Also:**

- The remarks in [OracleGlobalization Class](OracleGlobalizationClass.md) for more details on the ODP.NET type methods that convert between ODP.NET types and .NET string types, and to identify which thread globalization settings are used for that particular method.

- [OracleDataAdapter Safe Type Mapping](featSafeType.md)

- [Oracle Data Provider for .NET Types Structures](types-structures.md)

#### Operations Sensitive to Session Globalization Parameters

Session globalization settings affect any data that is retrieved from or sent to the database as a string.

For example, if a `DATE` column is selected with the `TO_CHAR` function applied on it, the `DATE` column data will be a string in the date format specified by the `DateFormat` property of the session globalization settings. Transmitting data in the other direction, the string data that is to be inserted into the `DATE` column, must be in the format specified by the `DateFormat` property of the session globalization settings.

### ODP.NET Drivers Differences

ODP.NET drivers set the default session time zone differently. While the session time zone for unmanaged ODP.NET uses an hour offset, managed ODP.NET and ODP.NET Core use the region identifier for setting their respective session time zone. As a result, managed and Core ODP.NET is sensitive to daylight savings in scenarios where the timestamp LTZ values have to be converted from or to the session time zone.

There are two methods to resolve this difference if needed. For ODP.NET, Unmanaged Driver, the application explicitly sets the region identifier with the environment variable `ORA_SDTZ`. For example, `set ORA_SDTZ = <Region ID>`. If `ORA_SDTZ` variable is set, Oracle Client considers this value as the session time zone. The second method is to execute an alter session command to set the session time zone property to the region identifier.
