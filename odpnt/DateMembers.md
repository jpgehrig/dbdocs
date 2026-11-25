`OracleDate` members are listed in the following tables:

### OracleDate Constructors

`OracleDate` constructors are listed in Table 14-27

Table 14-27 OracleDate Constructors

| Constructor                             | Description                                                        |
|:----------------------------------------|:-------------------------------------------------------------------|
| [OracleDate Constructors](DateCtors.md) | Instantiates a new instance of `OracleDate` structure (Overloaded) |

### OracleDate Static Fields

The `OracleDate` static fields are listed in Table 14-28.

Table 14-28 OracleDate Static Fields

| Field                       | Description                                                                                          |
|:----------------------------|:-----------------------------------------------------------------------------------------------------|
| [MaxValue](DateMaxValue.md) | Represents the maximum valid date for an `OracleDate` structure, which is December 31, 9999 23:59:59 |
| [MinValue](DateMinValue.md) | Represents the minimum valid date for an `OracleDate` structure, which is January 1, -4712 0:0:0     |
| [Null](DateNull.md)         | Represents a null value that can be assigned to the value of an `OracleDate` structure instance      |

### OracleDate Static Methods

The `OracleDate` static methods are listed in Table 14-29.

Table 14-29 OracleDate Static Methods

| Methods                                         | Description                                                                               |
|:------------------------------------------------|:------------------------------------------------------------------------------------------|
| [Equals](DateEqualsStatic.md)                   | Determines if two `OracleDate` values are equal (Overloaded)                              |
| [GreaterThan](DateGreaterThan.md)               | Determines if the first of two `OracleDate` values is greater than the second             |
| [GreaterThanOrEqual](DateGreaterThanOrEqual.md) | Determines if the first of two `OracleDate` values is greater than or equal to the second |
| [LessThan](DateLessThan.md)                     | Determines if the first of two `OracleDate` values is less than the second                |
| [LessThanOrEqual](DateLessThanOrEqual.md)       | Determines if the first of two `OracleDate` values is less than or equal to the second    |
| [NotEquals](DateNotEquals.md)                   | Determines if two `OracleDate` values are not equal                                       |
| [GetSysDate](DateGetSysDate.md)                 | Returns an `OracleDate` structure that represents the current date and time               |
| [Parse](DateParse.md)                           | Returns an `OracleDate` structure and sets its value using a string                       |

### OracleDate Static Operators

The `OracleDate` static operators are listed in Table 14-30.

Table 14-30 OracleDate Static Operators

| Operator                                   | Description                                                                               |
|:-------------------------------------------|:------------------------------------------------------------------------------------------|
| [operator ==](Dateoperatorequalsequals.md) | Determines if two `OracleDate` values are the same                                        |
| [operator \>](DateoperatorGT.md)           | Determines if the first of two `OracleDate` values is greater than the second             |
| [operator \>=](DateoperatorGTequals.md)    | Determines if the first of two `OracleDate` values is greater than or equal to the second |
| [operator !=](DateoperatorNotEqual.md)     | Determines if the two `OracleDate` values are not equal                                   |
| [operator \<](DateoperatorLT.md)           | Determines if the first of two `OracleDate` values is less than the second                |
| [operator \<=](DateoperatorLTequals.md)    | Determines if the first of two `OracleDate` values is less than or equal to the second    |

### OracleDate Static Type Conversions

The `OracleDate` static type conversions are listed in Table 14-31.

Table 14-31 OracleDate Static Type Conversions

| Operator                                                                   | Description                                                    |
|:---------------------------------------------------------------------------|:---------------------------------------------------------------|
| [explicit operator DateTime](DateexplicitoperatorDateTime.md)              | Converts a structure to a `DateTime` structure                 |
| [explicit operator OracleDate](DateexpilictoperatorOracleDateOverloads.md) | Converts a structure to an `OracleDate` structure (Overloaded) |

### OracleDate Properties

The `OracleDate` properties are listed in Table 14-32.

Table 14-32 OracleDate Properties

| Properties                | Description                                                                       |
|:--------------------------|:----------------------------------------------------------------------------------|
| [BinData](DateBinData.md) | Gets an array of bytes that represents an Oracle `DATE` in Oracle internal format |
| [Day](DateDay.md)         | Gets the day component of an `OracleDate` method                                  |
| [IsNull](DateIsNull.md)   | Indicates whether or not the current instance has a null value                    |
| [Hour](DateHour.md)       | Gets the `hour` component of an `OracleDate`                                      |
| [Minute](DateMinute.md)   | Gets the minute component of an `OracleDate`                                      |
| [Month](DateMonth.md)     | Gets the `month` component of an `OracleDate`                                     |
| [Second](DateSecond.md)   | Gets the `second` component of an `OracleDate`                                    |
| [Value](DateValue.md)     | Gets the date and time that is stored in the `OracleDate` structure               |
| [Year](DateYear.md)       | Gets the `year` component of an `OracleDate`                                      |

### OracleDate Methods

The `OracleDate` methods are listed in Table 14-33.

Table 14-33 OracleDate Methods

| Methods                                       | Description                                                                                                           |
|:----------------------------------------------|:----------------------------------------------------------------------------------------------------------------------|
| [CompareTo](DateCompareTo.md)                 | Compares the current `OracleDate` instance to an object, and returns an integer that represents their relative values |
| [Equals](DateEquals.md)                       | Determines whether or not an object has the same date and time as the current `OracleDate` instance (Overloaded)      |
| [GetHashCode](DateGetHashCode.md)             | Returns a hash code for the `OracleDate` instance                                                                     |
| [GetDaysBetween](DateGetDaysBetween.md)       | Calculates the number of days between the current `OracleDate` instance and an `OracleDate` structure                 |
| GetType                                       | Inherited from `System.Object`                                                                                        |
| [ToOracleTimeStamp](DateToOracleTimeStamp.md) | Converts the current `OracleDate` structure to an `OracleTimeStamp` structure                                         |
| [ToString](DateToString.md)                   | Converts the current `OracleDate` structure to a `string`                                                             |

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDate Structure](OracleDateStructure.md)
