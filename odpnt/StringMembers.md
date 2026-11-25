`OracleString` members are listed in the following tables:

### OracleString Constructors

`OracleString` constructors are listed in Table 14-87

Table 14-87 OracleString Constructors

| Constructor                                 | Description                                                          |
|:--------------------------------------------|:---------------------------------------------------------------------|
| [OracleString Constructors](StringCtors.md) | Instantiates a new instance of `OracleString` structure (Overloaded) |

### OracleString Static Fields

The `OracleString` static fields are listed in Table 14-88.

Table 14-88 OracleString Static Fields

| Field                 | Description                                                                                 |
|:----------------------|:--------------------------------------------------------------------------------------------|
| [Null](StringNull.md) | Represents a null value that can be assigned to an instance of the `OracleString` structure |

### OracleString Static Methods

The `OracleString` static methods are listed in Table 14-89.

Table 14-89 OracleString Static Methods

| Methods                                           | Description                                                                                                    |
|:--------------------------------------------------|:---------------------------------------------------------------------------------------------------------------|
| [Concat](StringConcat.md)                         | Concatenates two `OracleString` instances and returns a new `OracleString` instance that represents the result |
| [Equals](StringEqualsStatic.md)                   | Determines if two `OracleString` values are equal (Overloaded)                                                 |
| [GreaterThan](StringGreaterThan.md)               | Determines whether or not the first of two `OracleString` values is greater than the second                    |
| [GreaterThanOrEqual](StringGreaterThanOrEqual.md) | Determines whether or not the first of two `OracleString` values is greater than or equal to the second        |
| [LessThan](StringLessThan.md)                     | Determines whether or not the first of two `OracleString` values is less than the second                       |
| [LessThanOrEqual](StringLessThanOrEqual.md)       | Determines whether or not the first of two `OracleString` values is less than or equal to the second           |
| [NotEquals](StringNotEquals.md)                   | Determines whether two `OracleString` values are not equal                                                     |

### OracleString Static Operators

The `OracleString` static operators are listed in Table 14-90.

Table 14-90 OracleString Static Operators

| Operator                                          | Description                                                                                 |
|:--------------------------------------------------|:--------------------------------------------------------------------------------------------|
| [operator +](StringoperatorPLUS.md)               | Concatenates two `OracleString` values                                                      |
| [operator ==](StringoperatorEQUAL_EQUAL.md)       | Determines if two `OracleString` values are equal                                           |
| [operator \>](StringoperatorGT.md)                | Determines if the first of two `OracleString` values is greater than the second             |
| [operator \>=](StringoperatorGTequals.md)         | Determines if the first of two `OracleString` values is greater than or equal to the second |
| [operator !=](StringoperatorEXCLAMATION_EQUAL.md) | Determines if the two `OracleString` values are not equal                                   |
| [operator \<](StringoperatorLT.md)                | Determines if the first of two `OracleString` values is less than the second                |
| [operator \<=](StringoperatorLTequals.md)         | Determines if two `OracleString` values are not equal                                       |

### OracleString Type Conversions

The `OracleString` type conversions are listed in Table 14-91.

Table 14-91 OracleString Type Conversions

| Operator                                                                | Description                                                  |
|:------------------------------------------------------------------------|:-------------------------------------------------------------|
| [explicit operator string](Stringexplicitoperatorstring.md)             | Converts the supplied `OracleString` to a `string` instance  |
| [implicit operator OracleString](StringimplicitoperatorOracleString.md) | Converts the supplied `string` to an `OracleString` instance |

### OracleString Properties

The `OracleString` properties are listed in Table 14-92.

Table 14-92 OracleString Properties

| Properties                              | Description                                                                       |
|:----------------------------------------|:----------------------------------------------------------------------------------|
| [IsCaseIgnored](StringIsCaseIgnored.md) | Indicates whether or not case should be ignored when performing string comparison |
| [IsNull](StringIsNull.md)               | Indicates whether or not the current instance has a null value                    |
| [Item](StringItem.md)                   | Obtains the particular character in an `OracleString` using an index.             |
| [Length](StringLength.md)               | Returns the length of the `OracleString`                                          |
| [Value](StringValue.md)                 | Returns the string data that is stored in the `OracleString` structure.           |

### OracleString Methods

The `OracleString` methods are listed in Table 14-93.

Table 14-93 OracleString Methods

| Methods                                           | Description                                                                                                                       |
|:--------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------|
| [Clone](StringClone.md)                           | Returns a copy of the current `OracleString` instance                                                                             |
| [CompareTo](StringCompareTo.md)                   | Compares the current `OracleString` instance to the supplied object, and returns an integer that represents their relative values |
| [Equals](StringEquals.md)                         | Determines whether or not an object has the same string value as the current `OracleString` structure (Overloaded)                |
| [GetHashCode](StringGetHashCode.md)               | Returns a hash code for the `OracleString` instance                                                                               |
| [GetNonUnicodeBytes](StringGetNonUnicodeBytes.md) | Returns an array of bytes, containing the contents of the `OracleString`, in the client character set format                      |
| GetType                                           | Inherited from `System.Object`                                                                                                    |
| [GetUnicodeBytes](StringGetUnicodeBytes.md)       | Returns an array of bytes, containing the contents of the `OracleString`, in Unicode format                                       |
| [ToString](StringToString.md)                     | Converts the current `OracleString` instance to a `string`                                                                        |

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleString Structure](OracleStringStructure.md)
