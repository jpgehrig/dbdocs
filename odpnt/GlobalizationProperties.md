The `OracleGlobalization` properties are listed in Table 10-5.

Table 10-5 OracleGlobalization Properties

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

**See Also:**

- "[Oracle.DataAccess.Client and Oracle.ManagedDataAccess.Client Namespaces](intro003.md)"

- [OracleGlobalization Class](OracleGlobalizationClass.md)

- [OracleGlobalization Members](GlobalizationMembers.md)
