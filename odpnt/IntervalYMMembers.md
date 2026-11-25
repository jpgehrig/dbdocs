`OracleIntervalYM` members are listed in the following tables:

### OracleIntervalYM Constructors

`OracleIntervalYM` constructors are listed in Table 14-74

Table 14-74 OracleIntervalYM Constructors

| Constructor                                         | Description                                                              |
|:----------------------------------------------------|:-------------------------------------------------------------------------|
| [OracleIntervalYM Constructors](IntervalYMCtors.md) | Instantiates a new instance of `OracleIntervalYM` structure (Overloaded) |

### OracleIntervalYM Static Fields

The `OracleIntervalYM` static fields are listed in Table 14-75.

Table 14-75 OracleIntervalYM Static Fields

| Field                             | Description                                                                    |
|:----------------------------------|:-------------------------------------------------------------------------------|
| [MaxValue](IntervalYMMaxValue.md) | Represents the maximum value for an `OracleIntervalYM` structure               |
| [MinValue](IntervalYMMinValue.md) | Represents the minimum value for an `OracleIntervalYM` structure               |
| [Null](IntervalYMNull.md)         | Represents a null value that can be assigned to an `OracleIntervalYM` instance |
| [Zero](IntervalYMZero.md)         | Represents a zero value for an `OracleIntervalYM` structure                    |

### OracleIntervalYM Static Methods

The `OracleIntervalYM` static methods are listed in Table 14-76.

Table 14-76 OracleIntervalYM Static Methods

| Methods                                               | Description                                                                                 |
|:------------------------------------------------------|:--------------------------------------------------------------------------------------------|
| [Equals](IntervalYMEqualsStatic.md)                   | Determines whether or not two `OracleIntervalYM` values are equal (Overloaded)              |
| [GreaterThan](IntervalYMGreaterThan.md)               | Determines whether or not one `OracleIntervalYM` value is greater than another              |
| [GreaterThanOrEqual](IntervalYMGreaterThanOrEqual.md) | Determines whether or not one `OracleIntervalYM` value is greater than or equal to another  |
| [LessThan](IntervalYMLessThan.md)                     | Determines whether or not one `OracleIntervalYM` value is less than another                 |
| [LessThanOrEqual](IntervalYMLessThanOrEqual.md)       | Determines whether or not one `OracleIntervalYM` value is less than or equal to another     |
| [NotEquals](IntervalYMNotEquals.md)                   | Determines whether two `OracleIntervalYM` values are not equal                              |
| [Parse](IntervalYMParse.md)                           | Returns an `OracleIntervalYM` structure and sets its value for time interval using a string |
| [SetPrecision](IntervalYMSetPrecision.md)             | Returns a new instance of an `OracleIntervalYM` with the specified year precision.          |

### OracleIntervalYM Static Operators

The `OracleIntervalYM` static operators are listed in Table 14-77.

Table 14-77 OracleIntervalYM Static Operators

| Operator                                              | Description                                                                                |
|:------------------------------------------------------|:-------------------------------------------------------------------------------------------|
| [operator +](IntervalYMoperatorPLUS.md)               | Adds two `OracleIntervalYM` values                                                         |
| [operator ==](IntervalYMoperatorEQUAL_EQUAL.md)       | Determines whether or not two `OracleIntervalYM` values are equal                          |
| [operator \>](IntervalYMoperatorGT.md)                | Determines whether or not one `OracleIntervalYM` value is greater than another             |
| [operator \>=](IntervalYMoperatorGTequals.md)         | Determines whether or not one `OracleIntervalYM` value is greater than or equal to another |
| [operator !=](IntervalYMoperatorEXCLAMATION_EQUAL.md) | Determines whether two `OracleIntervalYM` values are not equal                             |
| [operator \<](IntervalYMoperatorLT.md)                | Determines whether or not one `OracleIntervalYM` value is less than another                |
| [operator \<=](IntervalYMoperatorLTequals.md)         | Determines whether or not one `OracleIntervalYM` value is less than or equal to another    |
| [operator -](IntervalYMoperatorMinus1.md)             | Subtracts one `OracleIntervalYM` value from another                                        |
| [operator -](IntervalYMoperatorNegates2.md)           | Negates an `OracleIntervalYM` structure                                                    |
| [operator \*](IntervalYMoperatorML.md)                | Multiplies an `OracleIntervalYM` value by a number                                         |
| [operator /](IntervalYMoperatorDV.md)                 | Divides an `OracleIntervalYM` value by a number                                            |

### OracleIntervalYM Type Conversions

The `OracleIntervalYM` conversions are listed in Table 14-78.

Table 14-78 OracleIntervalYM Type Conversions

| Operator                                                                            | Description                                                      |
|:------------------------------------------------------------------------------------|:-----------------------------------------------------------------|
| [explicit operator long](IntervalYMexplicitoperatorlong.md)                         | Converts an `OracleIntervalYM` structure to a number             |
| [explicit operator OracleIntervalYM](IntervalYMexplicitoperatorOracleIntervalYM.md) | Converts a string to an `OracleIntervalYM` structure             |
| [implicit operator OracleIntervalYM](IntervalYMimplicitoperatorOracleIntervalYM.md) | Converts the number of months to an `OracleIntervalYM` structure |

### OracleIntervalYM Properties

The `OracleIntervalYM` properties are listed in Table 14-79.

Table 14-79 OracleIntervalYM Properties

| Properties                            | Description                                                                                                        |
|:--------------------------------------|:-------------------------------------------------------------------------------------------------------------------|
| [BinData](IntervalYMBinData.md)       | Returns an array of bytes that represents the Oracle `INTERVAL` `YEAR` `TO` `MONTH` in an Oracle internal format   |
| [IsNull](IntervalYMIsNull.md)         | Indicates whether or not the current instance has a null value                                                     |
| [Months](IntervalYMMonths.md)         | Gets the months component of an `OracleIntervalYM`                                                                 |
| [TotalYears](IntervalYMTotalYears.md) | Returns the total number, in years, that represents the period of time in the current `OracleIntervalYM` structure |
| [Value](IntervalYMValue.md)           | Specifies the total number of months that is stored in the `OracleIntervalYM` structure                            |
| [Years](IntervalYMYears.md)           | Gets the years component of an `OracleIntervalYM`                                                                  |

### OracleIntervalYM Methods

The `OracleIntervalYM` methods are listed in Table 14-80.

Table 14-80 OracleIntervalYM Methods

| Methods                                 | Description                                                                                                                           |
|:----------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------|
| [CompareTo](IntervalYMCompareTo.md)     | Compares the current `OracleIntervalYM` instance to the supplied object, and returns an integer that represents their relative values |
| [Equals](IntervalYMEquals.md)           | Determines whether or not the specified `object` has the same time interval as the current instance (Overloaded)                      |
| [GetHashCode](IntervalYMGetHashCode.md) | Returns a hash code for the `OracleIntervalYM` instance                                                                               |
| GetType                                 | Inherited from `System.Object`                                                                                                        |
| [ToString](IntervalYMToString.md)       | Converts the current `OracleIntervalYM` structure to a string                                                                         |

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleIntervalYM Structure](OracleIntervalYMStructure.md)
