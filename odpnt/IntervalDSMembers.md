`OracleIntervalDS` members are listed in the following tables:

### OracleIntervalDS Constructors

`OracleIntervalDS` constructors are listed in Table 14-61

Table 14-61 OracleIntervalDS Constructors

| Constructor                                         | Description                                                              |
|:----------------------------------------------------|:-------------------------------------------------------------------------|
| [OracleIntervalDS Constructors](IntervalDSCtors.md) | Instantiates a new instance of `OracleIntervalDS` structure (Overloaded) |

### OracleIntervalDS Static Fields

The `OracleIntervalDS` static fields are listed in Table 14-62.

Table 14-62 OracleIntervalDS Static Fields

| Field                             | Description                                                                    |
|:----------------------------------|:-------------------------------------------------------------------------------|
| [MaxValue](IntervalDSMaxValue.md) | Represents the maximum valid time interval for an `OracleIntervalDS` structure |
| [MinValue](IntervalDSMinValue.md) | Represents the minimum valid time interval for an `OracleIntervalDS` structure |
| [Null](IntervalDSNull.md)         | Represents a null value that can be assigned to an `OracleIntervalDS` instance |
| [Zero](IntervalDSZero.md)         | Represents a zero value for an `OracleIntervalDS` structure                    |

### OracleIntervalDS Static Methods

The `OracleIntervalDS` static methods are listed in Table 14-63.

Table 14-63 OracleIntervalDS Static Methods

| Methods                                               | Description                                                                                                      |
|:------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------|
| [Equals](IntervalDSEqualsStatic.md)                   | Determines whether or not two `OracleIntervalDS` values are equal (Overloaded)                                   |
| [GreaterThan](IntervalDSGreaterThan.md)               | Determines whether or not one `OracleIntervalDS` value is greater than another                                   |
| [GreaterThanOrEqual](IntervalDSGreaterThanOrEqual.md) | Determines whether or not one `OracleIntervalDS` value is greater than or equal to another                       |
| [LessThan](IntervalDSLessThan.md)                     | Determines whether or not one `OracleIntervalDS` value is less than another                                      |
| [LessThanOrEqual](IntervalDSLessThanOrEqual.md)       | Determines whether or not one `OracleIntervalDS` value is less than or equal to another                          |
| [NotEquals](IntervalDSNotEquals.md)                   | Determines whether or not two `OracleIntervalDS` values are not equal                                            |
| [Parse](IntervalDSParse.md)                           | Returns an `OracleIntervalDS` structure and sets its value for time interval using a string                      |
| [SetPrecision](IntervalDSSetPrecision.md)             | Returns a new instance of an `OracleIntervalDS` with the specified day precision and fractional second precision |

### OracleIntervalDS Static Operators

The `OracleIntervalDS` static operators are listed in Table 14-64.

Table 14-64 OracleIntervalDS Static Operators

| Operator                                              | Description                                                                                |
|:------------------------------------------------------|:-------------------------------------------------------------------------------------------|
| [operator +](IntervalDSoperatorPLUS.md)               | Adds two `OracleIntervalDS` values                                                         |
| [operator ==](IntervalDSoperatorEQUAL_EQUAL.md)       | Determines whether or not two `OracleIntervalDS` values are equal                          |
| [operator \>](IntervalDSoperatorGT.md)                | Determines whether or not one `OracleIntervalDS` value is greater than another             |
| [operator \>=](IntervalDSoperatorGTequals.md)         | Determines whether or not one `OracleIntervalDS` value is greater than or equal to another |
| [operator !=](IntervalDSoperatorEXCLAMATION_EQUAL.md) | Determines whether or not two `OracleIntervalDS` values are not equal                      |
| [operator \<](IntervalDSoperatorLT.md)                | Determines whether or not one `OracleIntervalDS` value is less than another                |
| [operator \<=](IntervalDSoperatorLTequals.md)         | Determines whether or not one `OracleIntervalDS` value is less than or equal to another    |
| [operator -](IntervalDSoperatorMinus1.md)             | Subtracts one `OracleIntervalDS` value from another                                        |
| [operator -](IntervalDSoperatorNegates2.md)           | Negates an `OracleIntervalDS` structure                                                    |
| [operator \*](IntervalDSoperatorML.md)                | Multiplies an `OracleIntervalDS` value by a number                                         |
| [operator /](IntervalDSoperatorDV.md)                 | Divides an `OracleIntervalDS` value by a number                                            |

### OracleIntervalDS Type Conversions

The `OracleIntervalDS` type conversions are listed in Table 14-65.

Table 14-65 OracleIntervalDS Type Conversions

| Operator                                                                            | Description                                                        |
|:------------------------------------------------------------------------------------|:-------------------------------------------------------------------|
| [explicit operator TimeSpan](IntervalDSexplicitoperatorTimeSpan.md)                 | Converts an `OracleIntervalDS` structure to a `TimeSpan` structure |
| [explicit operator OracleIntervalDS](IntervalDSexplicitoperatorOracleIntervalDS.md) | Converts a string to an `OracleIntervalDS` structure               |
| [implicit operator OracleIntervalDS](IntervalDSimplicitoperatorOracleIntervalDS.md) | Converts a `TimeSpan` structure to an `OracleIntervalDS` structure |

### OracleIntervalDS Properties

The `OracleIntervalDS` properties are listed in Table 14-66.

Table 14-66 OracleIntervalDS Properties

| Properties                                | Description                                                                                                   |
|:------------------------------------------|:--------------------------------------------------------------------------------------------------------------|
| [BinData](IntervalDSBinData.md)           | Returns an array of bytes that represents the Oracle `INTERVAL` `DAY` `TO` `SECOND` in Oracle internal format |
| [Days](IntervalDSDays.md)                 | Gets the days component of an `OracleIntervalDS`                                                              |
| [Hours](IntervalDSHours.md)               | Gets the hours component of an `OracleIntervalDS`                                                             |
| [IsNull](IntervalDSIsNull.md)             | Indicates whether or not the current instance has a null value                                                |
| [Milliseconds](IntervalDSMilliseconds.md) | Gets the milliseconds component of an `OracleIntervalDS`                                                      |
| [Minutes](IntervalDSMinutes.md)           | Gets the minutes component of an `OracleIntervalDS`                                                           |
| [Nanoseconds](IntervalDSNanoseconds.md)   | Gets the nanoseconds component of an `OracleIntervalDS`                                                       |
| [Seconds](IntervalDSSeconds.md)           | Gets the seconds component of an `OracleIntervalDS`                                                           |
| [TotalDays](IntervalDSTotalDays.md)       | Returns the total number, in days, that represent the time period in the `OracleIntervalDS` structure         |
| [Value](IntervalDSValue.md)               | Specifies the time interval that is stored in the `OracleIntervalDS` structure                                |

### OracleIntervalDS Methods

The `OracleIntervalDS` methods are listed in Table 14-67.

Table 14-67 OracleIntervalDS Methods

| Methods                                 | Description                                                                                                                 |
|:----------------------------------------|:----------------------------------------------------------------------------------------------------------------------------|
| [CompareTo](IntervalDSCompareTo.md)     | Compares the current `OracleIntervalDS` instance to an object, and returns an integer that represents their relative values |
| [Equals](IntervalDSEquals.md)           | Determines whether or not the specified `object` has the same time interval as the current instance (Overloaded)            |
| [GetHashCode](IntervalDSGetHashCode.md) | Returns a hash code for the `OracleIntervalDS` instance                                                                     |
| GetType                                 | Inherited from `System.Object`                                                                                              |
| [ToString](IntervalDSToString.md)       | Converts the current `OracleIntervalDS` structure to a string                                                               |

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalDS Structure](OracleIntervalDSStructure.md)
