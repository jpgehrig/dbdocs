`OracleBoolean` members are listed in the following tables:

### OracleBoolean Constructors

`OracleBoolean` constructors are listed in Table 14-14

Table 14-14 OracleBoolean Constructors

| Constructor                                   | Description                                                           |
|:----------------------------------------------|:----------------------------------------------------------------------|
| [OracleBoolean Constructors](BooleanCtors.md) | Instantiates a new instance of `OracleBoolean` structure (Overloaded) |

### OracleBoolean Static Fields

The `OracleBoolean` static fields are listed in Table 14-15.

Table 14-15 OracleBoolean Static Fields

| Field                    | Description                                                                  |
|:-------------------------|:-----------------------------------------------------------------------------|
| [False](BooleanFalse.md) | Represents a false value that can be assigned to an `OracleBoolean` instance |
| [Null](BooleanNull.md)   | Represents a null value that can be assigned to an `OracleBoolean` instance  |
| [One](BooleanOne.md)     | Indicates a constant representing the positive one value                     |
| [True](BooleanTrue.md)   | Represents a true value that can be assigned to an `OracleBoolean` instance  |
| [Zero](BooleanZero.md)   | Indicates a constant representing the zero value                             |

### OracleBoolean Static Methods

`OracleBoolean` static methods are listed in Table 14-16

Table 14-16 OracleBoolean Static Methods

| Methods                                              | Description                                                                                              |
|:-----------------------------------------------------|:---------------------------------------------------------------------------------------------------------|
| [And](BooleanAnd.md)                                 | Returns the result of bitwise `AND` operation of two `OracleBoolean` instances                           |
| [Equals](BooleanEquals.md)                           | Determines whether or not the two `OracleBoolean` values are equal                                       |
| [GreaterThan](BooleanGreaterThan.md)                 | Determines whether or not the first of two `OracleBoolean` values is greater than the second             |
| [GreaterThanOrEquals](BooleanGreaterThanOrEquals.md) | Determines whether or not the first of two `OracleBoolean` values is greater than or equal to the second |
| [LessThan](BooleanLessThan.md)                       | Determines whether or not the first of two `OracleBoolean` values is less than the second                |
| [LessThanOrEquals](BooleanLessThanOrEquals.md)       | Determines whether or not the first of two `OracleBoolean` values is less than or equal to the second    |
| [NotEquals](BooleanNotEquals.md)                     | Determines whether or not two `OracleBoolean` values are not equal                                       |
| [OnesComplement](BooleanOnesComplement.md)           | Returns the result of a one's complement operation on the specified `OracleBoolean` value                |
| [Or](BooleanOr.md)                                   | Returns the result of bitwise `OR` operation of two `OracleBoolean` instances                            |
| [Parse](BooleanParse.md)                             | Returns an `OracleBoolean` structure and sets its value using a `string`                                 |
| [Xor](BooleanXor.md)                                 | Returns the result of a bitwise exclusive `OR` operation of two `OracleBoolean` instances                |

### OracleBoolean Static Operators

The `OracleBoolean` static operators are listed in Table 14-17.

Table 14-17 OracleBoolean Static Operators

| Field                                         | Description                                                                                              |
|:----------------------------------------------|:---------------------------------------------------------------------------------------------------------|
| [operator \>](BooleanoperatorGT.md)           | Determines whether or not the first of two `OracleBoolean` values is greater than the second             |
| [operator \>=](BooleanoperatorGTequals.md)    | Determines whether or not the first of two `OracleBoolean` values is greater than or equal to the second |
| [operator \<](BooleanoperatorLT.md)           | Determines whether or not the first of two `OracleBoolean` values is less than the second                |
| [operator \<=](BooleanoperatorLTequals.md)    | Dtermines whether or not the first of two `OracleBoolean` values is less than or equal to the second     |
| [operator ==](Booleanoperatorequalsequals.md) | Indicates whether or not the two `OracleBoolean` instances are equal                                     |
| [operator !=](BooleanoperatorNotEqual.md)     | Determines whether or not two `OracleBoolean` values are not equal                                       |
| [operator !](BooleanoperatorNot.md)           | Determines the result of a `NOT` operation on a `OracleBoolean`                                          |
| [operator ~](BooleanoperatorTILDE.md)         | Returns the result of a one's complement operation on the specified `OracleBoolean` value                |
| [operator false](Booleanoperatorfalse.md)     | Determines whether or not the specified `OracleBoolean` value is false                                   |
| [operator true](Booleanoperatortrue.md)       | Determines whether or not the specified `OracleBoolean` value is true                                    |
| [operator &](BooleanoperatorAMP.md)           | Returns the result of bitwise `AND` operation of two `OracleBoolean` instances                           |
| [operator \|](BooleanoperatorPIPE.md)         | Returns the result of bitwise `OR` operation of two `OracleBoolean` instances                            |
| [operator ^](BooleanoperatorCARET.md)         | Returns the result of bitwise exclusive `OR` operation of two `OracleBoolean` instances                  |

### The OracleBoolean Static Type conversions

The `OracleBoolean` static type conversions are listed in Table 14-18

Table 14-18 OracleBoolean Static Type Conversions

| Field                                                                               | Description                                                       |
|:------------------------------------------------------------------------------------|:------------------------------------------------------------------|
| [implicit operator OracleBoolean](BooleanimpilictoperatorOracleBoolean.md)          | Returns the `OracleBoolean` representation of a boolean value     |
| [explicit operator bool](Booleanexpilictoperatorbool.md)                            | Returns the boolean representation of the `OracleBoolean` value   |
| [explicit operator OracleBoolean](BooleanexpilictoperatorOracleBooleanOverloads.md) | Converts a structure to an `OracleBoolean` structure (Overloaded) |

### OracleBoolean Properties

The `OracleBoolean` properties are listed in [Table 14-25](BooleanProperties.md).

Table 14-19 OracleBoolean Properties

| Properties                       | Description                                                         |
|:---------------------------------|:--------------------------------------------------------------------|
| [ByteValue](BooleanByteValue.md) | Returns a `byte` that represents the `OracleBoolean` structure      |
| [IsFalse](BooleanIsFalse.md)     | Indicates whether or not the value of the current instance is false |
| [IsNull](BooleanIsNull.md)       | Indicates whether or not the current instance has a null value      |
| [IsTrue](BooleanIsTrue.md)       | Indicates whether or not the value of the current instance is true  |
| [Value](BooleanValue.md)         | Returns a boolean value that represents the current instance        |

### OracleBoolean Instance Methods

The `OracleBoolean` instance methods are listed in Table 14-20.

Table 14-20 OracleBoolean Instance Methods

| Method                               | Description                                                                                                                                        |
|:-------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------|
| [CompareTo](BooleanCompareTo.md)     | Compares the current instance to the supplied object and returns an integer that represents their relative values                                  |
| [Equals](BooleanInstanceEquals.md)   | Determines whether or not an object is an instance of `OracleBoolean`, and whether or not the value of the object is equal to the current instance |
| [GetHashCode](BooleanGetHashCode.md) | Returns a hash code for the current instance                                                                                                       |
| [ToString](BooleanToString.md)       | Returns the `string` representation of the current instance                                                                                        |

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBoolean Structure](OracleBooleanStructure.md)
