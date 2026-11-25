`OracleTimeStampLTZ` members are listed in the following tables:

### OracleTimeStampLTZ Constructors

`OracleTimeStampLTZ` constructors are listed in Table 14-113

Table 14-113 OracleTimeStampLTZConstructors

| Constructor                                             | Description                                                                |
|:--------------------------------------------------------|:---------------------------------------------------------------------------|
| [OracleTimeStampLTZ Constructors](TimeStampLTZCtors.md) | Instantiates a new instance of `OracleTimeStampLTZ` structure (Overloaded) |

### OracleTimeStampLTZ Static Fields

The `OracleTimeStampLTZ` static fields are listed in Table 14-114.

Table 14-114 OracleTimeStampLTZ Static Fields

| Field                                | Description                                                                                                            |
|:-------------------------------------|:-----------------------------------------------------------------------------------------------------------------------|
| [MaxValue](TimeStampLTZMaxvValue.md) | Represents the maximum valid date for an `OracleTimeStampLTZ `structure, which is December 31, 9999 23:59:59.999999999 |
| [MinValue](TimeStampLTZMinValue.md)  | Represents the minimum valid date for an `OracleTimeStampLTZ `structure, which is January 1, -4712 0:0:0               |
| [Null](TimeStampLTZNull.md)` `       | Represents a null value that can be assigned to an instance of the `OracleTimeStampLTZ `structure                      |

### OracleTimeStampLTZ Static Methods

The `OracleTimeStampLTZ` static methods are listed in Table 14-115.

Table 14-115 OracleTimeStampLTZ Static Methods

| Methods                                                         | Description                                                                                           |
|:----------------------------------------------------------------|:------------------------------------------------------------------------------------------------------|
| [Equals](TimeStampLTZEqualsStatic.md)                           | Determines if two `OracleTimeStampLTZ` values are equal (Overloaded)                                  |
| [GetLocalTimeZoneName](TimeStampLTZGetLocalTimeZoneName.md)     | Gets the client's local time zone name                                                                |
| [GetLocalTimeZoneOffset](TimeStampLTZGetLocalTimeZoneOffset.md) | Gets the client's local time zone offset relative to UTC                                              |
| [GetSysDate](TimeStampLTZGetSysDate.md)` `                      | Gets an `OracleTimeStampLTZ` structure that represents the current date and time                      |
| [GreaterThan](TimeStampLTZGreaterThan.md)                       | Determines if the first of two `OracleTimeStampLTZ` values is greater than the second                 |
| [GreaterThanOrEqual](TimeStampLTZGreaterThanOrEquals.md)        | Determines if the first of two `OracleTimeStampLTZ` values is greater than or equal to the second     |
| [LessThan](TimeStampLTZLessThan.md)                             | Determines if the first of two `OracleTimeStampLTZ` values is less than the second                    |
| [LessThanOrEqual](TimeStampLTZLessThanOrEquals.md)              | Determines if the first of two `OracleTimeStampLTZ` values is less than or equal to the second        |
| [NotEquals](TimeStampLTZNotEquals.md)                           | Determines if two `OracleTimeStampLTZ` values are not equal                                           |
| [Parse](TimeStampLTZParse.md)` `                                | Gets an `OracleTimeStampLTZ` structure and sets its value for date and time using the supplied string |
| [SetPrecision](TimeStampLTZSetPrecision.md)                     | Returns a new instance of an `OracleTimeStampLTZ` with the specified fractional second precision      |

### OracleTimeStampLTZ Static Operators

The `OracleTimeStampLTZ` static operators are listed in Table 14-116.

Table 14-116 OracleTimeStampLTZ Static Operators

| Operator                                                   | Description                                                                                                                                |
|:-----------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------|
| [operator +](TimeStampLTZoperatorPLUSOverloads.md)` `      | Adds the supplied instance value to the supplied `OracleTimeStampLTZ` and returns a new `OracleTimeStampLTZ` structure (Overloaded)        |
| [operator ==](TimeStampLTZoperatorEQUAL_EQUAL.md)` `       | Determines if two `OracleTimeStampLTZ` values are equal                                                                                    |
| [operator \>](TimeStampLTZoperatorGT.md)` `                | Determines if the first of two `OracleTimeStampLTZ` values is greater than the second                                                      |
| [operator \>=](TimeStampLTZoperatorGTequals.md)` `         | Determines if the first of two `OracleTimeStampLTZ` values is greater than or equal to the second                                          |
| [operator !=](TimeStampLTZoperatorEXCLAMATION_EQUAL.md)` ` | Determines if two `OracleTimeStampLTZ` values are not equal                                                                                |
| [operator \<](TimeStampLTZoperatorLT.md)` `                | Determines if the first of two `OracleTimeStampLTZ` values is less than the second                                                         |
| [operator \<=](TimeStampLTZoperatorLTequals.md)` `         | Determines if the first of two `OracleTimeStampLTZ` values is less than or equal to the second                                             |
| [operator -](TimeStampLTZoepratorMinusOverloads.md)        | Subtracts the supplied instance value from the supplied `OracleTimeStampLTZ` and returns a new `OracleTimeStampLTZ` structure (Overloaded) |

### OracleTimeStampLTZ Static Type Conversions

The `OracleTimeStampLTZ` static type conversions are listed in Table 14-117.

Table 14-117 OracleTimeStampLTZ Static Type Conversions

| Operator                                                                                           | Description                                                                  |
|:---------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------|
| [explicit operator OracleTimeStampLTZ](TimeStampLTZexplicitoperatorOracleTimeStampLTZOverloads.md) | Converts an instance value to an `OracleTimeStampLTZ` structure (Overloaded) |
| [implicit operator OracleTimeStampLTZ](TimeStampLTZimplicitoperatorOracleTimeStampLTZOverloads.md) | Converts an instance value to an `OracleTimeStampLTZ` structure (Overloaded) |
| [explicit operator DateTime](TimeStampLTZexplicitoperatorDateTime.md)                              | Converts an `OracleTimeStampLTZ` value to a `DateTime` structure             |

### OracleTimeStampLTZ Properties

The `OracleTimeStampLTZ` properties are listed in Table 14-118.

Table 14-118 OracleTimeStampLTZ Properties

| Properties                                | Description                                                                                                            |
|:------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------|
| [BinData](TimeStampLTZBinData.md)         | Returns an array of bytes that represents an `Oracle TIMESTAMP`` WITH`` LOCAL`` TIME`` ZONE` in Oracle internal format |
| [Day](TimeStampLTZDay.md)                 | Specifies the `day` component of an `OracleTimeStampLTZ`                                                               |
| [IsNull](TimeStampLTZIsNull.md)           | Indicates whether or not the `OracleTimeStampLTZ` instance has a null value                                            |
| [Hour](TimeStampLTZHour.md)               | Specifies the hour component of an `OracleTimeStampLTZ`                                                                |
| [Millisecond](TimeStampLTZMillisecond.md) | Specifies the millisecond component of an `OracleTimeStampLTZ`                                                         |
| [Minute](TimeStampLTZMinute.md)           | Specifies the minute component of an `OracleTimeStampLTZ`                                                              |
| [Month](TimeStampLTZMonth.md)             | Specifies the month component of an `OracleTimeStampLTZ`                                                               |
| [Nanosecond](TimeStampLTZNanosecond.md)   | Specifies the nanosecond component of an `OracleTimeStampLTZ`                                                          |
| [Second](TimeStampLTZSecond.md)           | Specifies the second component of an `OracleTimeStampLTZ`                                                              |
| [Value](TimeStampLTZValue.md)             | Specifies the date and time that is stored in the `OracleTimeStampLTZ` structure                                       |
| [Year](TimeStampLTZYear.md)               | Specifies the year component of an `OracleTimeStampLTZ`                                                                |

### OracleTimeStampLTZ Methods

The `OracleTimeStampLTZ` methods are listed in Table 14-119.

Table 14-119 OracleTimeStampLTZ Methods

| Methods                                                   | Description                                                                                                                  |
|:----------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------|
| [AddDays](TimeStampLTZAddDays.md)                         | Adds the supplied number of days to the current instance                                                                     |
| [AddHours](TimeStampLTZAddHours.md)                       | Adds the supplied number of hours to the current instance                                                                    |
| [AddMilliseconds](TimeStampLTZAddMilliseconds.md)         | Adds the supplied number of milliseconds to the current instance                                                             |
| [AddMinutes](TimeStampLTZAddMinutes.md)                   | Adds the supplied number of minutes to the current instance                                                                  |
| [AddMonths](TimeStampLTZAddMonths.md)                     | Adds the supplied number of months to the current instance                                                                   |
| [AddNanoseconds](TimeStampLTZAddNanoseconds.md)           | Adds the supplied number of nanoseconds to the current instance                                                              |
| [AddSeconds](TimeStampLTZAddSeconds.md)                   | Adds the supplied number of seconds to the current instance                                                                  |
| [AddYears](TimeStampLTZAddYears.md)                       | Adds the supplied number of years to the current instance                                                                    |
| [CompareTo](TimeStampLTZCompareTo.md)                     | Compares the current `OracleTimeStampLTZ` instance to an object and returns an integer that represents their relative values |
| [Equals](TimeStampLTZEquals.md)                           | Determines whether or not an object has the same date and time as the current `OracleTimeStampLTZ` instance (Overloaded)     |
| [GetHashCode](TimeStampLTZGetHashCode.md)                 | Returns a hash code for the `OracleTimeStampLTZ` instance                                                                    |
| [GetDaysBetween](TimeStampLTZGetDaysBetween.md)           | Subtracts an `OracleTimeStampLTZ` from the current instance and returns an `OracleIntervalDS` that represents the difference |
| [GetYearsBetween](TimeStampLTZGetYearsBetween.md)         | Subtracts an `OracleTimeStampLTZ` from the current instance and returns an `OracleIntervalYM` that represents the difference |
| GetType                                                   | Inherited from `System.Object`                                                                                               |
| [ToOracleDate](TimeStampLTZToOracleDate.md)               | Converts the current `OracleTimeStampLTZ` structure to an `OracleDate` structure                                             |
| [ToOracleTimeStamp](TimeStampLTZToOracleTimeStamp.md)     | Converts the current `OracleTimeStampLTZ` structure to an `OracleTimeStamp` structure                                        |
| [ToOracleTimeStampTZ](TimeStampLTZToOracleTimeStampTZ.md) | Converts the current `OracleTimeStampLTZ` structure to an `OracleTimeStampTZ` structure                                      |
| [ToString](TimeStampLTZToString.md)                       | Converts the current `OracleTimeStampLTZ` structure to a string                                                              |
| [ToUniversalTime](TimeStampLTZToUniversalTime.md)         | Converts the current local time to Coordinated Universal Time (UTC)                                                          |

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleTimeStampLTZ Structure](OracleTimeStampLTZStructure.md)
