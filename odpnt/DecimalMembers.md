`OracleDecimal` members are listed in the following tables:

### OracleDecimal Constructors

`OracleDecimal` constructors are listed in Table 14-40

Table 14-40 OracleDecimal Constructors

| Constructor                                   | Description                                                           |
|:----------------------------------------------|:----------------------------------------------------------------------|
| [OracleDecimal Constructors](DecimalCtors.md) | Instantiates a new instance of `OracleDecimal` structure (Overloaded) |

### OracleDecimal Static Fields

The `OracleDecimal` static fields are listed in Table 14-41.

Table 14-41 OracleDecimal Static Fields

| Field                                  | Description                                                                                     |
|:---------------------------------------|:------------------------------------------------------------------------------------------------|
| [MaxPrecision](DecimalMaxPrecision.md) | A constant representing the maximum precision, which is 38                                      |
| [MaxScale](DecimalMaxScale.md)         | A constant representing the maximum scale, which is 127                                         |
| [MaxValue](DecimalMaxValue.md)         | A constant representing the maximum value for this structure, which is 9.9…9 x 10<sup>125</sup> |
| [MinScale](DecimalMinScale.md)         | A constant representing the minimum scale, which is -84                                         |
| [MinValue](DecimalMinValue.md)         | A constant representing the minimum value for this structure, which is -1.0 x 10<sup>130</sup>  |
| [NegativeOne](DecimalNegativeOne.md)   | A constant representing the negative one value                                                  |
| [Null](DecimalNull.md)                 | Represents a null value that can be assigned to an `OracleDecimal` instance                     |
| [One](DecimalOne.md)                   | A constant representing the positive one value                                                  |
| [Pi](DecimalPi.md)                     | A constant representing the numeric Pi value                                                    |
| [Zero](DecimalZero.md)                 | A constant representing the zero value                                                          |

### OracleDecimal Static (Comparison) Methods

The `OracleDecimal` static (comparison) methods are listed in Table 14-42.

Table 14-42 OracleDecimal Static (Comparison) Methods

| Methods                                            | Description                                                                                  |
|:---------------------------------------------------|:---------------------------------------------------------------------------------------------|
| [Equals](DecimalEquals.md)                         | Determines if two `OracleDecimal` values are equal (Overloaded)                              |
| [GreaterThan](DecimalGreaterThan.md)               | Determines if the first of two `OracleDecimal` values is greater than the second             |
| [GreaterThanOrEqual](DecimalGreaterThanOrEqual.md) | Determines if the first of two `OracleDecimal` values is greater than or equal to the second |
| [LessThan](DecimalLessThan.md)                     | Determines if the first of two `OracleDecimal` values is less than the second                |
| [LessThanOrEqual](DecimalLessThanOrEqual.md)       | Determines if the first of two `OracleDecimal` values is less than or equal to the second.   |
| [NotEquals](DecimalNotEqual.md)                    | Determines if two `OracleDecimal` values are not equal                                       |

### OracleDecimal Static (Manipulation) Methods

The `OracleDecimal` static (manipulation) methods are listed in Table 14-43.

Table 14-43 OracleDecimal Static (Manipulation) Methods

| Methods                                            | Description                                                                                                                                                                                |
|:---------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Abs](DecimalAbs.md)                               | Returns the absolute value of an `OracleDecimal`                                                                                                                                           |
| [Add](DecimalAdd.md)                               | Adds two `OracleDecimal` structures                                                                                                                                                        |
| [AdjustScale](DecimalAdjustScale.md)               | Returns a new `OracleDecimal` with the specified number of digits and indicates whether or not to round or truncate the number if the scale is less than original                          |
| [Ceiling](DecimalCeiling.md)                       | Returns a new `OracleDecimal` structure with its value set to the ceiling of an `OracleDecimal` structure                                                                                  |
| [ConvertToPrecScale](DecimalConvertToPrecScale.md) | Returns a new `OracleDecimal` structure with a new precision and scale                                                                                                                     |
| [Divide](DecimalDivide.md)                         | Divides one `OracleDecimal` value by another                                                                                                                                               |
| [Floor](DecimalFloor.md)                           | Returns a new `OracleDecimal` structure with its value set to the floor of an `OracleDecimal` structure                                                                                    |
| [Max](DecimalMax.md)                               | Returns the maximum value of the two supplied `OracleDecimal` structures                                                                                                                   |
| [Min](DecimalMin.md)                               | Returns the minimum value of the two supplied `OracleDecimal` structures                                                                                                                   |
| [Mod](DecimalMod.md)                               | Returns a new `OracleDecimal` structure with its value set to the modulus of two `OracleDecimal` structures                                                                                |
| [Multiply](DecimalMultiply.md)                     | Returns a new `OracleDecimal` structure with its value set to the result of multiplying two `OracleDecimal` structures                                                                     |
| [Negate](DecimalNegate.md)                         | Returns a new `OracleDecimal` structure with its value set to the negation of the supplied `OracleDecimal` structure                                                                       |
| [Parse](DecimalParse.md)                           | Converts a `string` to an `OracleDecimal`                                                                                                                                                  |
| [Round](DecimalRound.md)                           | Returns a new `OracleDecimal` structure with its value set to that of the supplied `OracleDecimal` structure and rounded off to the specified place                                        |
| [SetPrecision](DecimalSetPrecision.md)             | Returns a new `OracleDecimal` structure with a new specified precision.                                                                                                                    |
| [Shift](DecimalShift.md)                           | Returns a new `OracleDecimal` structure with its value set to that of the supplied `OracleDecimal` structure, and its decimal place shifted to the specified number of places to the right |
| [Sign](DecimalSign.md)                             | Determines the sign of an `OracleDecimal` structure                                                                                                                                        |
| [Sqrt](DecimalSqrt.md)                             | Returns a new `OracleDecimal` structure with its value set to the square root of the supplied `OracleDecimal` structure                                                                    |
| [Subtract](DecimalSubtract.md)                     | Returns a new `OracleDecimal` structure with its value set to result of subtracting one `OracleDecimal` structure from another                                                             |
| [Truncate](DecimalTruncate.md)                     | Truncates the `OracleDecimal` at a specified position                                                                                                                                      |

### OracleDecimal Static (Logarithmic) Methods

The `OracleDecimal` static (logarithmic) methods are listed in Table 14-44.

Table 14-44 OracleDecimal Static (Logarithmic) Methods

| Methods                       | Description                                                                                                                                    |
|:------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------|
| [Exp](DecimalExp.md)          | Returns a new `OracleDecimal` structure with its value set to e raised to the supplied power                                                   |
| [Log](DecimalLogOverloads.md) | Returns the supplied `OracleDecimal` structure with its value set to the logarithm of the supplied `OracleDecimal` structure (Overloaded)      |
| [Pow](DecimalPowOverloads.md) | Returns a new `OracleDecimal` structure with its value set to the supplied `OracleDecimal` structure raised to the supplied power (Overloaded) |

### OracleDecimal Static (Trigonometric) Methods

The `OracleDecimal` static (trigonometric) methods are listed in Table 14-45.

Table 14-45 OracleDecimal Static (Trigonometric) Methods

| Methods                  | Description                                                                                              |
|:-------------------------|:---------------------------------------------------------------------------------------------------------|
| [Acos](DecimalAcos.md)   | Returns an angle in radians whose cosine is the supplied `OracleDecimal` structure                       |
| [Asin](DecimalAsin.md)   | Returns an angle in radians whose sine is the supplied `OracleDecimal` structure                         |
| [Atan](DecimalAtan.md)   | Returns an angle in radians whose tangent is the supplied `OracleDecimal` structure                      |
| [Atan2](DecimalAtan2.md) | Returns an angle in radians whose tangent is the quotient of the two supplied `OracleDecimal` structures |
| [Cos](DecimalCos.md)     | Returns the cosine of the supplied angle in radians                                                      |
| [Sin](DecimalSin.md)     | Returns the sine of the supplied angle in radians                                                        |
| [Tan](DecimalTan.md)     | Returns the tangent of the supplied angle in radians                                                     |
| [Cosh](DecimalCosh.md)   | Returns the hyperbolic cosine of the supplied angle in radians                                           |
| [Sinh](DecimalSinh.md)   | Returns the hyperbolic sine of the supplied angle in radians                                             |
| [Tanh](DecimalTanh.md)   | Returns the hyperbolic tangent of the supplied angle in radians                                          |

### OracleDecimal Static (Comparison) Operators

The `OracleDecimal` static (comparison) operators are listed in Table 14-46.

Table 14-46 OracleDecimal Static (Comparison) Operators

| Operator                                             | Description                                                                                                  |
|:-----------------------------------------------------|:-------------------------------------------------------------------------------------------------------------|
| [operator +](DecimaloperatorPLUS.md)                 | Adds two `OracleDecimal` values                                                                              |
| [operator /](DecimaloperatorDV.md)` `                | Divides one `OracleDecimal` value by another                                                                 |
| [operator ==](DecimalEQUALTO_EQUALTO.md)             | Determines if the two `OracleDecimal` values are equal                                                       |
| [operator \>](DecimaloperatorGT.md)                  | Determines if the first of two `OracleDecimal` values is greater than the second                             |
| [operator \>=](DecimaloperatorGTequals.md)           | Determines if the first of two `OracleDecimal` values is greater than or equal to the second                 |
| [operator !=](DecimaloperatorEXCLAMATION_EQUALTO.md) | Determines if the two `OracleDecimal` values are not equal                                                   |
| [operator \<](DecimaloperatorLT.md)                  | Determines if the first of two `OracleDecimal` values is less than the second                                |
| [operator \<=](DecimaloperatorLTequals.md)           | Determines if the first of two `OracleDecimal` values is less than or equal to the second                    |
| [operator \*](DecimaloperatorML.md)                  | Multiplies two `OracleDecimal` structures                                                                    |
| [operator -](DecimaloperatorMinus1.md)               | Subtracts one `OracleDecimal` structure from another                                                         |
| [operator -](Decimaloperator2.md)                    | Negates an `OracleDecimal` structure                                                                         |
| [operator%](DecimaloperatorPERCENT.md)               | Returns a new `OracleDecimal` structure with its value set to the modulus of two `OracleDecimal` structures. |

### OracleDecimal Static Operators (Conversion from .NET Type to OracleDecimal)

The `OracleDecimal` static operators (Conversion from .NET Type to `OracleDecimal`) are listed in Table 14-47.

Table 14-47 OracleDecimal Static Operators (Conversion from .NET Type to OracleDecimal)

| Operator                                                                            | Description                                                             |
|:------------------------------------------------------------------------------------|:------------------------------------------------------------------------|
| [implicit operator OracleDecimal](DecimalimplicitoperatorOracleDecimalOverloads.md) | Converts an instance value to an `OracleDecimal` structure (Overloaded) |
| [explicit operator OracleDecimal](DecimalexplicitoperatorOracleDecimalOverloads.md) | Converts an instance value to an `OracleDecimal` structure (Overloaded) |

### OracleDecimal Static Operators (Conversion from OracleDecimal to .NET)

The `OracleDecimal` static operators (Conversion from `OracleDecimal` to .NET) are listed in Table 14-48.

Table 14-48 OracleDecimal Static Operators (Conversion from OracleDecimal to .NET)

| Operator                                                       | Description                                                       |
|:---------------------------------------------------------------|:------------------------------------------------------------------|
| [explicit operator byte](Decimalexplicitoperatorbyte.md)       | Returns the `byte` representation of the `OracleDecimal` value    |
| [explicit operator decimal](Decimalexplicitoperatordecimal.md) | Returns the `decimal` representation of the `OracleDecimal` value |
| [explicit operator double](Decimalexplicitoperatordouble.md)   | Returns the `double` representation of the `OracleDecimal` value  |
| [explicit operator short](Decimalexplicitoperatorshort.md)     | Returns the `short` representation of the `OracleDecimal` value   |
| [explicit operator int](Decimalexplicitoperatorint.md)         | Returns the `int` representation of the `OracleDecimal` value     |
| [explicit operator long](Decimalexplicitoperatorlong.md)       | Returns the `long` representation of the `OracleDecimal` value    |
| [explicit operator float](Decimalexplicitoperatorfloat.md)     | Returns the `float` representation of the `OracleDecimal` value   |

### OracleDecimal Properties

The `OracleDecimal` properties are listed in Table 14-49.

Table 14-49 OracleDecimal Properties

| Properties                         | Description                                                                        |
|:-----------------------------------|:-----------------------------------------------------------------------------------|
| [BinData](DecimalBinData.md)       | Returns a byte array that represents the Oracle `NUMBER` in Oracle internal format |
| [Format](DecimalFormat.md)         | Specifies the format for `ToString()`                                              |
| [IsInt](DecimalIsInt.md)           | Indicates whether or not the current instance is an integer                        |
| [IsNull](DecimalIsNull.md)         | Indicates whether or not the current instance has a null value                     |
| [IsPositive](DecimalIsPositive.md) | Indicates whether or not the current instance is greater than `0`                  |
| [IsZero](DecimalIsZero.md)         | Indicates whether or not the current instance has a `zero` value                   |
| [Value](DecimalValue.md)           | Returns a `decimal` value                                                          |

### OracleDecimal Instance Methods

The `OracleDecimal` instance methods are listed in Table 14-50.

Table 14-50 OracleDecimal Instance Methods

| Method                               | Description                                                                                                                                                     |
|:-------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [CompareTo](DecimalCompareTo.md)     | Compares the current instance to the supplied object and returns an integer that represents their relative values                                               |
| [Equals](DecimalEqualsInstance.md)   | Determines whether or not an object is an instance of `OracleDecimal`, and whether or not the value of the object is equal to the current instance (Overloaded) |
| [GetHashCode](DecimalGetHashCode.md) | Returns a hash code for the current instance                                                                                                                    |
| GetType                              | Inherited from `System.Object`                                                                                                                                  |
| [ToByte](DecimalToByte.md)           | Returns the `byte` representation of the current instance                                                                                                       |
| [ToDouble](DecimalToDouble.md)       | Returns the `double` representation of the current instance                                                                                                     |
| [ToInt16](DecimalToint16.md)         | Returns the `Int16` representation of the current instance                                                                                                      |
| [ToInt32](DecimalToInt32.md)         | Returns the `Int32` representation of the current instance                                                                                                      |
| [ToInt64](DecimalToint64.md)         | Returns the `Int64` representation of the current instance                                                                                                      |
| [ToSingle](DecimalToSingle.md)       | Returns the `Single` representation of the current instance                                                                                                     |
| [ToString](DecimalToString.md)       | Overloads `Object.ToString() `<br>Returns the `string` representation of the current instance                                                                   |

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleDecimal Structure](OracleDecimalStructure.md)
