`OracleGlobalization` members are listed in the following tables.

### OracleGlobalization Static Methods

The `OracleGlobalization` static methods are listed in Table 10-1.

Table 10-1 OracleGlobalization Static Methods

| Name                                                    | Description                                                                                                                                                                                          |
|:--------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [GetClientInfo](GlobalizationGetClientInfoOverloads.md) | Returns an `OracleGlobalization` object that represents the Oracle globalization settings of the local computer (Overloaded)<br>Not Available in ODP.NET, Managed Driver and ODP.NET Core            |
| [GetThreadInfo](GlobalizationGetThreadInfoOverloads.md) | Returns or refreshes an `OracleGlobalization` instance that represents Oracle globalization settings of the current thread (Overloaded)<br>Not Available in ODP.NET, Managed Driver and ODP.NET Core |
| [SetThreadInfo](GlobalizationSetThreadInfo.md)          | Sets Oracle globalization parameters to the current thread<br>Not Available in ODP.NET, Managed Driver and ODP.NET Core                                                                              |

### OracleGlobalization Properties

The `OracleGlobalization` properties are listed in Table 10-2.

Table 10-2 OracleGlobalization Properties

| Name                                                                 | Description                                                                                                             |
|:---------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------|
| [Calendar](GlobalizationCalendar.md)                                 | Specifies the calendar system                                                                                           |
| [ClientCharacterSet](GlobalizationClientCharacterSet.md)             | Specifies a client character set<br>Not Available in ODP.NET, Managed Driver and ODP.NET Core                           |
| [Comparison](GlobalizationComparison.md)                             | Specifies a method of comparison for `WHERE` clauses and comparison in PL/SQL blocks                                    |
| [Currency](GlobalizationCurrency.md)                                 | Specifies the string to use as a local currency symbol for the L number format element                                  |
| [DateFormat](GlobalizationDateFormat.md)                             | Specifies the date format for Oracle `Date` type as a string                                                            |
| [DateLanguage](GlobalizationDateLanguage.md)                         | Specifies the language used to spell day and month names and date abbreviations                                         |
| [DualCurrency](GlobalizationDualCurrency.md)                         | Specifies the dual currency symbol, such as Euro, for the U number format element                                       |
| [ISOCurrency](GlobalizationISOCurrency.md)                           | Specifies the string to use as an international currency symbol for the C number format element                         |
| [Language](GlobalizationLanguage.md)                                 | Specifies the default language of the database                                                                          |
| [LengthSemantics](GlobalizationLengthSemantics.md)                   | Enables creation of `CHAR` and `VARCHAR2` columns using either byte or character (default) length semantics             |
| [NCharConversionException](GlobalizationNCharConversionException.md) | Determines whether or not data loss during an implicit or explicit character type conversion reports an error           |
| [NumericCharacters](GlobalizationNumericCharacters.md)               | Specifies the characters used for the decimal character and the group separator character for numeric values in strings |
| [Sort](GlobalizationSort.md)                                         | Specifies the collating sequence for `ORDER` by clause                                                                  |
| [Territory](GlobalizationTerritory.md)                               | Specifies the name of the territory                                                                                     |
| [TimeStampFormat](GlobalizationTimeStampFormat.md)                   | Specifies the string format for `TimeStamp` types                                                                       |
| [TimeStampTZFormat](GlobalizationTimeStampTZFormat.md)               | Specifies the string format for `TimeStampTZ` types                                                                     |
| [TimeZone](GlobalizationTimeZone.md)                                 | Specifies the time zone region name                                                                                     |

### OracleGlobalization Public Methods

`OracleGlobalization` public methods are listed in Table 10-3.

Table 10-3 OracleGlobalization Public Methods

| Public Method                      | Description                                              |
|:-----------------------------------|:---------------------------------------------------------|
| [Clone](GlobalizationClone.md)     | Creates a copy of an `OracleGlobalization` object        |
| [Dispose](GlobalizationDispose.md) | Releases any resources or memory allocated by the object |

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleGlobalization Class](OracleGlobalizationClass.md)

- OracleGlobalization Members
