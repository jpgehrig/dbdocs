`OracleTimeStamp` members are listed in the following tables:

### OracleTimeStamp Constructors

`OracleTimeStamp` constructors are listed in Table 14-100

Table 14-100 OracleTimeStamp Constructors

| Constructor                                       | Description                                                             |
|:--------------------------------------------------|:------------------------------------------------------------------------|
| [OracleTimeStamp Constructors](TimeStampCtors.md) | Instantiates a new instance of `OracleTimeStamp` structure (Overloaded) |

### OracleTimeStamp Static Fields

The `OracleTimeStamp` static fields are listed in Table 14-101.

Table 14-101 OracleTimeStamp Static Fields

| Field                            | Description                                                                                                         |
|:---------------------------------|:--------------------------------------------------------------------------------------------------------------------|
| [MaxValue](TimeStampMaxValue.md) | Represents the maximum valid date for an `OracleTimeStamp` structure, which is December 31, 9999 23:59:59.999999999 |
| [MinValue](TimeStampMinValue.md) | Represents the minimum valid date for an `OracleTimeStamp` structure, which is January 1, -4712 0:0:0               |
| [Null](TimeStampNull.md)         | Represents a null value that can be assigned to an instance of the `OracleTimeStamp` structure                      |

### OracleTimeStamp Static Methods

The `OracleTimeStamp` static methods are listed in Table 14-102.

Table 14-102 OracleTimeStamp Static Methods

| Methods                                              | Description                                                                                    |
|:-----------------------------------------------------|:-----------------------------------------------------------------------------------------------|
| [Equals](TimeStampEqualsStatic.md)                   | Determines if two `OracleTimeStamp` values are equal (Overloaded)                              |
| [GreaterThan](TimeStampGreaterThan.md)               | Determines if the first of two `OracleTimeStamp` values is greater than the second             |
| [GreaterThanOrEqual](TimeStampGreaterThanOrEqual.md) | Determines if the first of two `OracleTimeStamp` values is greater than or equal to the second |
| [LessThan](TimeStampLessThan.md)                     | Determines if the first of two `OracleTimeStamp` values is less than the second                |
| [LessThanOrEqual](TimeStampLessThanOrEqual.md)       | Determines if the first of two `OracleTimeStamp` values is less than or equal to the second    |
| [NotEquals](TimeStampNotEquals.md)                   | Determines if two `OracleTimeStamp` values are not equal                                       |
| [GetSysDate](TimeStampGetSysDate.md)                 | Gets an `OracleTimeStamp` structure that represents the current date and time                  |
| [Parse](TimeStampParse.md)                           | Gets an `OracleTimeStamp` structure and sets its value using the supplied string               |
| [SetPrecision](TimeStampSetPrecision.md)             | Returns a new instance of an `OracleTimeStamp` with the specified fractional second precision  |

### OracleTimeStamp Static Operators

The `OracleTimeStamp` static operators are listed in Table 14-103.

Table 14-103 OracleTimeStamp Static Operators

| Operator                                             | Description                                                                                                                          |
|:-----------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------|
| [operator +](TimeStampoperatorPLUSOverloads.md)      | Adds the supplied instance value to the supplied `OracleTimeStamp` and returns a new `OracleTimeStamp` structure (Overloaded)        |
| [operator ==](TimeStampoperatorEQUAL_EQUAL.md)       | Determines if two `OracleTimeStamp` values are equal                                                                                 |
| [operator \>](TimeStampoperatorGT.md)                | Determines if the first of two `OracleTimeStamp` values is greater than the second                                                   |
| [operator \>=](TimeStampoperatorGTequals.md)         | Determines if the first of two `OracleTimeStamp` values is greater than or equal to the second                                       |
| [operator !=](TimeStampoperatorEXCLAMATION_EQUAL.md) | Determines if the two `OracleTimeStamp` values are not equal                                                                         |
| [operator \<](TimeStampoperatorLT.md)                | Determines if the first of two `OracleTimeStamp` values is less than the second                                                      |
| [operator \<=](TimeStampoperatorLTequals.md)         | Determines if the first of two `OracleTimeStamp` values is less than or equal to the second                                          |
| [operator -](TimeStampoperatorMinusOverloads.md)     | Subtracts the supplied instance value from the supplied `OracleTimeStamp` and returns a new `OracleTimeStamp` structure (Overloaded) |

### OracleTimeStamp Static Type Conversions

The `OracleTimeStamp` static type conversions are listed in Table 14-104.

Table 14-104 OracleTimeStamp Static Type Conversions

| Operator                                                                                  | Description                                                               |
|:------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------|
| [explicit operator OracleTimeStamp](TimeStampexplicitoperatorOracleTimeStampOverloads.md) | Converts an instance value to an `OracleTimeStamp` structure (Overloaded) |
| [implicit operator OracleTimeStamp](TimeStampimplicitoperatorOracleTimeStampOverloads.md) | Converts an instance value to an `OracleTimeStamp` structure (Overloaded) |
| [explicit operator DateTime](TimeStampexplicitoperatorDateTime.md)                        | Converts an `OracleTimeStamp` value to a `DateTime` structure             |

### OracleTimeStamp Properties

The `OracleTimeStamp` properties are listed in Table 14-105.

Table 14-105 OracleTimeStamp Properties

| Properties                             | Description                                                                               |
|:---------------------------------------|:------------------------------------------------------------------------------------------|
| [BinData](TimeStampBinData.md)         | Returns an array of bytes that represents an Oracle `TIMESTAMP` in Oracle internal format |
| [Day](TimeStampDay.md)                 | Specifies the day component of an `OracleTimeStamp`                                       |
| [IsNull](TimeStampIsNull.md)           | Indicates whether or not the `OracleTimeStamp` instance has a null value                  |
| [Hour](TimeStampHour.md)               | Specifies the hour component of an `OracleTimeStamp`                                      |
| [Millisecond](TimeStampMillisecond.md) | Specifies the millisecond component of an `OracleTimeStamp`                               |
| [Minute](TimeStampMinute.md)           | Specifies the minute component of an `OracleTimeStamp`                                    |
| [Month](TimeStampMonth.md)             | Specifies the month component of an `OracleTimeStamp`                                     |
| [Nanosecond](TimeStampNanosecond.md)   | Specifies the nanosecond component of an `OracleTimeStamp`                                |
| [Second](TimeStampSecond.md)           | Specifies the second component of an `OracleTimeStamp`                                    |
| [Value](TimeStampValue.md)             | Specifies the date and time that is stored in the `OracleTimeStamp` structure             |
| [Year](TimeStampYear.md)               | Specifies the year component of an `OracleTimeStamp`                                      |

### OracleTimeStamp Methods

The `OracleTimeStamp` methods are listed in Table 14-106.

Table 14-106 OracleTimeStamp Methods

| Methods                                                  | Description                                                                                                                                                                                          |
|:---------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [AddDays](TimeStampAddDays.md)                           | Adds the supplied number of days to the current instance                                                                                                                                             |
| [AddHours](TimeStampAddHours.md)                         | Adds the supplied number of hours to the current instance                                                                                                                                            |
| [AddMilliseconds](TimeStampAddMilliseconds.md)           | Adds the supplied number of milliseconds to the current instance                                                                                                                                     |
| [AddMinutes](TimeStampAddMinutes.md)                     | Adds the supplied number of minutes to the current instance                                                                                                                                          |
| [AddMonths](TimeStampAddMonths.md)                       | Adds the supplied number of months to the current instance                                                                                                                                           |
| [AddNanoseconds](TimeStampAddNanoseconds.md)             | Adds the supplied number of nanoseconds to the current instance                                                                                                                                      |
| [AddSeconds](TimeStampAddSeconds.md)                     | Adds the supplied number of seconds to the current instance                                                                                                                                          |
| [AddYears](TimeStampAddYears.md)                         | Adds the supplied number of years to the current instance                                                                                                                                            |
| [CompareTo](TimeStampCompareTo.md)                       | Compares the current `OracleTimeStamp` instance to an object, and returns an integer that represents their relative values                                                                           |
| [Equals](TimeStampEquals.md)                             | Determines whether or not an object has the same date and time as the current `OracleTimeStamp` instance (Overloaded)                                                                                |
| [GetHashCode](TimeStampGetHashCode.md)                   | Returns a hash code for the `OracleTimeStamp` instance                                                                                                                                               |
| [GetDaysBetween](TimeStampGetDaysBetween.md)             | Subtracts an `OracleTimeStamp` value from the current instance and returns an `OracleIntervalDS` that represents the time difference between the supplied `OracleTimeStamp` and the current instance |
| [GetYearsBetween](TimeStampGetYearsBetween.md)           | Subtracts `value1` from the current instance and returns an `OracleIntervalYM` that represents the difference between `value1` and the current instance using `OracleIntervalYM`                     |
| GetType                                                  | Inherited from `System.Object`                                                                                                                                                                       |
| [ToOracleDate](TimeStampToOracleDate.md)                 | Converts the current `OracleTimeStamp` structure to an `OracleDate` structure                                                                                                                        |
| [ToOracleTimeStampLTZ](TimeStampToOracleTimeStampLTZ.md) | Converts the current `OracleTimeStamp` structure to an `OracleTimeStampLTZ` structure                                                                                                                |
| [ToOracleTimeStampTZ](TimeStampToOracleTimeStampTZ.md)   | Converts the current `OracleTimeStamp` structure to an `OracleTimeStampTZ` structure                                                                                                                 |
| [ToString](TimeStampToString.md)                         | Converts the current `OracleTimeStamp` structure to a string                                                                                                                                         |

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStamp Structure](OracleTimeStampStructure.md)
