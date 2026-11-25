`OracleTimeStampTZ` members are listed in the following tables:

### OracleTimeStampTZ Constructors

`OracleTimeStampTZ` constructors are listed in Table 14-126

Table 14-126 OracleTimeStampTZ Constructors

| Constructor                                           | Description                                                               |
|:------------------------------------------------------|:--------------------------------------------------------------------------|
| [OracleTimeStampTZ Constructors](TimeStampTZCtors.md) | Instantiates a new instance of `OracleTimeStampTZ` structure (Overloaded) |

### OracleTimeStampTZ Static Fields

The `OracleTimeStampTZ` static fields are listed in Table 14-127.

Table 14-127 OracleTimeStampTZ Static Fields

| Field                              | Description                                                                                                                 |
|:-----------------------------------|:----------------------------------------------------------------------------------------------------------------------------|
| [MaxValue](TimeStampTZMaxValue.md) | Represents the maximum valid date for an `OracleTimeStampTZ` structure in UTC, which is December 31, 999923:59:59.999999999 |
| [MinValue](TimeStampTZMinValue.md) | Represents the minimum valid date for an `OracleTimeStampTZ` structure in UTC, which is January 1, -4712 0:0:0              |
| [Null](TimeStampTZNull.md)         | Represents a null value that can be assigned to an instance of the `OracleTimeStampTZ` structure                            |

### OracleTimeStampTZ Static Methods

The `OracleTimeStampTZ` static methods are listed in Table 14-128.

Table 14-128 OracleTimeStampTZ Static Methods

| Methods                                                | Description                                                                                          |
|:-------------------------------------------------------|:-----------------------------------------------------------------------------------------------------|
| [Equals](TimeStampTZEqualsStatic.md)                   | Determines if two `OracleTimeStampTZ` values are equal (Overloaded)                                  |
| [GetSysDate](TimeStampTZGetSysDate.md)                 | Gets an `OracleTimeStampTZ` structure that represents the current date and time                      |
| [GreaterThan](TimeStampTZGreaterThan.md)               | Determines if the first of two `OracleTimeStampTZ` values is greater than the second                 |
| [GreaterThanOrEqual](TimeStampTZGreaterThanOrEqual.md) | Determines if the first of two `OracleTimeStampTZ` values is greater than or equal to the second     |
| [LessThan](TimeStampTZLessThan.md)                     | Determines if the first of two `OracleTimeStampTZ` values is less than the second                    |
| [LessThanOrEqual](TimeStampTZLessThanOrEqual.md)       | Determines if the first of two `OracleTimeStampTZ` values is less than or equal to the second        |
| [NotEquals](TimeStampTZNotEquals.md)                   | Determines if two `OracleTimeStampTZ` values are not equal                                           |
| [Parse](TimeStampTZParse.md)                           | Gets an `OracleTimeStampTZ` structure and sets its value for date and time using the supplied string |
| [SetPrecision](TimeStampTZSetPrecision.md)             | Returns a new instance of an `OracleTimeStampTZ` with the specified fractional second precision      |

### OracleTimeStampTZ Static Operators

The `OracleTimeStampTZ` static operators are listed in Table 14-129.

Table 14-129 OracleTimeStampTZ Static Operators

| Operator                                           | Description                                                                                                                              |
|:---------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------|
| [operator +](TimeStampTZoperatorPLUSOverloads.md)  | Adds the supplied instance value to the supplied `OracleTimeStampTZ` and returns a new `OracleTimeStampTZ` structure (Overloaded)        |
| [operator ==](TimeStampTZoperatorEQUAL_EQUAL.md)   | Determines if two `OracleTimeStampTZ` values are equal                                                                                   |
| [operator \>](TimeStampTZoperatorGT.md)            | Determines if the first of two `OracleTimeStampTZ` values is greater than the second                                                     |
| [operator \>=](TimeStampTZoperatorGTequals.md)     | Determines if the first of two `OracleTimeStampTZ` values is greater than or equal to the second                                         |
| [operator !=](TimeStampTZEXCLAMATION_EQUAL.md)     | Determines if two `OracleTimeStampTZ` values are not equal                                                                               |
| [operator \<](TimeStampTZoperatorLT.md)            | Determines if the first of two `OracleTimeStampTZ` values is less than the second                                                        |
| [operator \<=](TimeStampTZLTequals.md)             | Determines if the first of two `OracleTimeStampTZ` values is less than or equal to the second                                            |
| [operator -](TimeStampTZoperatorMinusOverloads.md) | Subtracts the supplied instance value from the supplied `OracleTimeStampTZ` and returns a new `OracleTimeStampTZ` structure (Overloaded) |

### OracleTimeStampTZ Static Type Conversions

The `OracleTimeStampTZ` static type conversions are listed in Table 14-130.

Table 14-130 OracleTimeStampTZ Static Type Conversions

| Operator                                                                                        | Description                                                                 |
|:------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------|
| [explicit operator OracleTimeStampTZ](TimeStampTZexplicitoperatorOracleTimeStampOverloads.md)   | Converts an instance value to an `OracleTimeStampTZ` structure (Overloaded) |
| [implicit operator OracleTimeStampTZ](TimeStampTZimplicitoperatorOracleTimeStampTZOverloads.md) | Converts an instance value to an `OracleTimeStampTZ` structure (Overloaded) |
| [explicit operator DateTime](TimeStampTZexplicitoperatorDateTime.md)                            | Converts an `OracleTimeStampTZ` value to a `DateTime` structure             |

### OracleTimeStampTZ Properties

The `OracleTimeStampTZ` properties are listed in Table 14-131.

Table 14-131 OracleTimeStampTZ Properties

| Properties                               | Description                                                                                                    |
|:-----------------------------------------|:---------------------------------------------------------------------------------------------------------------|
| [BinData](TimeStampTZBinData.md)         | Returns an array of bytes that represents an Oracle `TIMESTAMP` `WITH` `TIME` `ZONE` in Oracle internal format |
| [Day](TimeStampTZDay.md)                 | Specifies the day component of an `OracleTimeStampTZ` in the current time zone                                 |
| [IsNull](TimeStampTZIsNull.md)           | Indicates whether or not the current instance has a null value                                                 |
| [Hour](TimeStampTZHour.md)               | Specifies the hour component of an `OracleTimeStampTZ` in the current time zone                                |
| [Millisecond](TimeStampTZMillisecond.md) | Specifies the millisecond component of an `OracleTimeStampTZ` in the current time zone                         |
| [Minute](TimeStampTZMinute.md)           | Specifies the minute component of an `OracleTimeStampTZ` in the current time zone                              |
| [Month](TimeStampTZMonth.md)             | Specifies the month component of an `OracleTimeStampTZ` in the current time zone                               |
| [Nanosecond](TimeStampTZNanosecond.md)   | Specifies the nanosecond component of an `OracleTimeStampTZ` in the current time zone                          |
| [Second](TimeStampTZSecond.md)           | Specifies the second component of an `OracleTimeStampTZ` in the current time zone                              |
| [TimeZone](TimeStampTZTimeZone.md)       | Returns the time zone of the `OracleTimeStampTZ` instance                                                      |
| [Value](TimeStampTZValue.md)             | Returns the date and time that is stored in the `OracleTimeStampTZ` structure in the current time zone         |
| [Year](TimeStampTZYear.md)               | Specifies the year component of an `OracleTimeStampTZ`                                                         |

### OracleTimeStampTZ Methods

The `OracleTimeStampTZ` methods are listed in Table 14-132.

Table 14-132 OracleTimeStampTZ Methods

| Methods                                                    | Description                                                                                                                    |
|:-----------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------|
| [AddDays](TimeStampTZAddDays.md)                           | Adds the supplied number of days to the current instance                                                                       |
| [AddHours](TimeStampTZAddHours.md)                         | Adds the supplied number of hours to the current instance                                                                      |
| [AddMilliseconds](TimeStampTZAddMilliseconds.md)           | Adds the supplied number of milliseconds to the current instance                                                               |
| [AddMinutes](TimeStampTZAddMinutes.md)                     | Adds the supplied number of minutes to the current instance                                                                    |
| [AddMonths](TimeStampTZAddMonths.md)                       | Adds the supplied number of months to the current instance                                                                     |
| [AddNanoseconds](TimeStampTZAddNanoseconds.md)             | Adds the supplied number of nanoseconds to the current instance                                                                |
| [AddSeconds](TimeStampTZAddSeconds.md)                     | Adds the supplied number of seconds to the current instance                                                                    |
| [AddYears](TimeStampTZAddYears.md)                         | Adds the supplied number of years to the current instance                                                                      |
| [CompareTo](TimeStampTZCompareTo.md)                       | Compares the current `OracleTimeStampTZ` instance to an object, and returns an integer that represents their relative values   |
| [Equals](TimeStampTZEquals.md)                             | Determines whether or not an object has the same date and time as the current `OracleTimeStampTZ` instance                     |
| [GetDaysBetween](TimeStampTZGetDaysBetween.md)             | Subtracts an `OracleTimeStampTZ` from the current instance and returns an `OracleIntervalDS` that represents the time interval |
| [GetHashCode](TimeStampTZGetHashCode.md)                   | Returns a hash code for the `OracleTimeStampTZ` instance                                                                       |
| [GetTimeZoneOffset](TimeStampTZGetTimeZoneOffset.md)       | Gets the time zone information in hours and minutes of the current `OracleTimeStampTZ`                                         |
| [GetYearsBetween](TimeStampTZGetYearsBetween.md)           | Subtracts an `OracleTimeStampTZ` from the current instance and returns an `OracleIntervalYM` that represents the time interval |
| GetType                                                    | Inherited from `System.Object`                                                                                                 |
| [ToLocalTime](TimeStampTZToLocalTime.md)                   | Converts the current `OracleTimeStampTZ` instance to local time                                                                |
| [ToOracleDate](TimeStampTZToOracleDate.md)                 | Converts the current `OracleTimeStampTZ` structure to an `OracleDate` structure                                                |
| [ToOracleTimeStampLTZ](TimeStampTZToOracleTimeStampLTZ.md) | Converts the current `OracleTimeStampTZ` structure to an `OracleTimeStampLTZ` structure                                        |
| [ToOracleTimeStamp](TimeStampTZToOracleTimeStamp.md)       | Converts the current `OracleTimeStampTZ` structure to an `OracleTimeStamp` structure                                           |
| [ToString](TimeStampTZToString.md)                         | Converts the current `OracleTimeStampTZ` structure to a string                                                                 |
| [ToUniversalTime](TimeStampTZToUniversalTime.md)           | Converts the current datetime to Coordinated Universal Time (UTC)                                                              |

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampTZ Structure](OracleTimeStampTZStructure.md)
