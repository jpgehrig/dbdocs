`OracleBinary` members are listed in the following tables:

### OracleBinary Constructors

`OracleBinary` constructors are listed in Table 14-1

Table 14-1 OracleBinary Constructors

| Constructor                               | Description                                             |
|:------------------------------------------|:--------------------------------------------------------|
| [OracleBinary Constructor](BinaryCtor.md) | Instantiates a new instance of `OracleBinary` structure |

### OracleBinary Static Fields

The `OracleBinary` static fields are listed in Table 14-2.

Table 14-2 OracleBinary Static Fields

| Field                 | Description                                                                                 |
|:----------------------|:--------------------------------------------------------------------------------------------|
| [Null](BinaryNull.md) | Represents a null value that can be assigned to an instance of the `OracleBinary` structure |

### OracleBinary Static Methods

The `OracleBinary` static methods are listed in Table 14-3.

Table 14-3 OracleBinary Static Methods

| Methods                                           | Description                                                                                 |
|:--------------------------------------------------|:--------------------------------------------------------------------------------------------|
| [Concat](BinaryConcat.md)                         | Returns the concatenation of two `OracleBinary` structures                                  |
| [Equals](BinaryEqualsStatic.md)                   | Determines if two `OracleBinary` values are equal (Overloaded)                              |
| [GetXsdType](BinaryGetXsdType.md)                 | Returns the XML Schema definition language (XSD) of the specified `XmlSchemaSet`            |
| [GreaterThan](BinaryGreaterThan.md)               | Determines if the first of two `OracleBinary` values is greater than the second             |
| [GreaterThanOrEqual](BinaryGreaterThanOrEqual.md) | Determines if the first of two `OracleBinary` values is greater than or equal to the second |
| [LessThan](BinaryLessThan.md)                     | Determines if the first of two `OracleBinary` values is less than the second                |
| [LessThanOrEqual](BinaryLessThanOrEqual.md)       | Determines if the first of two `OracleBinary` values is less than or equal to the second    |
| [NotEquals](BinaryNotEquals.md)                   | Determines if two `OracleBinary` values are not equal                                       |

### OracleBinary Static Operators

The `OracleBinary` static operators are listed in Table 14-4.

Table 14-4 OracleBinary Static Operators

| Operator                                     | Description                                                                                 |
|:---------------------------------------------|:--------------------------------------------------------------------------------------------|
| [operator +](BinaryoperatorPlus.md)          | Concatenates two `OracleBinary` values                                                      |
| [operator ==](Binaryoperatorequalsequals.md) | Determines if two `OracleBinary` values are equal                                           |
| [operator \>](BinaryoperatorGT.md)           | Determines if the first of two `OracleBinary` values is greater than the second             |
| [operator \>=](BinaryoperatorGTequals.md)    | Determines if the first of two `OracleBinary` values is greater than or equal to the second |
| [operator !=](BinaryoperatorNotEqual.md)     | Determines if two `OracleBinary` values are not equal                                       |
| [operator \<](BinaryoperatorLT.md)           | Determines if the first of two `OracleBinary` value is less than the second                 |
| [operator \<=](BinaryoperatorLTequals.md)    | Determines if the first of two `OracleBinary` value is less than or equal to the second     |

### OracleBinary Static Type Conversion Operators

The `OracleBinary` static type conversion operators are listed in Table 14-5.

Table 14-5 OracleBinary Static Type Conversion Operators

| Operator                                                                | Description                                               |
|:------------------------------------------------------------------------|:----------------------------------------------------------|
| [explicit operator byte\[ \]](Binaryexplicitoperatorbyte.md)            | Converts an instance value to a byte array                |
| [implicit operator OracleBinary](BinaryimplicitoperatorOracleBinary.md) | Converts an instance value to an `OracleBinary` structure |

### OracleBinary Properties

The `OracleBinary` properties are listed in Table 14-6.

Table 14-6 OracleBinary Properties

| Properties                | Description                                                                 |
|:--------------------------|:----------------------------------------------------------------------------|
| [IsNull](BinaryIsNull.md) | Indicates whether or not the current instance has a null value              |
| [Item](BinaryItem.md)     | Obtains the particular `byte` in an `OracleBinary` structure using an index |
| [Length](BinaryLength.md) | Returns the length of the binary data                                       |
| [Value](BinaryValue.md)   | Returns the binary data that is stored in an `OracleBinary` structure       |

### OracleBinary Instance Methods

The `OracleBinary` instance methods are listed in Table 14-7.

Table 14-7 OracleBinary Instance Methods

| Methods                             | Description                                                                                             |
|:------------------------------------|:--------------------------------------------------------------------------------------------------------|
| [CompareTo](BinaryCompareTo.md)     | Compares the current instance to an object and returns an integer that represents their relative values |
| [Equals](BinaryEquals.md)           | Determines if two objects contain the same binary data (Overloaded)                                     |
| [GetHashCode](BinaryGetHashCode.md) | Returns a hash code for the current instance                                                            |
| GetType                             | Inherited from `System.Object`                                                                          |
| [ToString](BinaryToString.md)       | Converts the current `OracleBinary` structure to a string                                               |

**See Also:**

- "[Oracle.DataAccess.Types and Oracle.ManagedDataAccess.Types Namespaces](intro003.md)"

- [OracleBinary Structure](OracleBinaryStructure.md)
