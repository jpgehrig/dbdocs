Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../CharacterSet.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

## Uses of Class oracle.sql.CharacterSet

- **Packages that use [CharacterSet](../CharacterSet.md)**

  | Package    | Description                                                                       |
  |------------|-----------------------------------------------------------------------------------|
  | oracle.sql | A package of classes that represent java SQL types and Oracle specific SQL types. |

- - ### Uses of [CharacterSet](../CharacterSet.md) in [oracle.sql](../package-summary.md)

    **Subclasses of [CharacterSet](../CharacterSet.md) in [oracle.sql](../package-summary.md)**

    | Modifier and Type | Class and Description                                                                                                                                              |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `class `          | [`CharacterSetWithConverter`](../CharacterSetWithConverter.md)<br>This is an abstract base class that all character sets that use CharacterConverter are based on. |

    **Fields in [oracle.sql](../package-summary.md) declared as [CharacterSet](../CharacterSet.md)**

    | Modifier and Type                             | Field and Description                 |
    |-----------------------------------------------|---------------------------------------|
    | `static `[`CharacterSet`](../CharacterSet.md) | CHAR.[`DEFAULT_CHARSET`](../CHAR.md)  |
    | `static `[`CharacterSet`](../CharacterSet.md) | CHAR.[`DEFAULT_CHARSET`](../CHAR.md)  |

    **Methods in [oracle.sql](../package-summary.md) that return [CharacterSet](../CharacterSet.md)**

    | Modifier and Type                             | Method and Description                                                |
    |-----------------------------------------------|-----------------------------------------------------------------------|
    | `static `[`CharacterSet`](../CharacterSet.md) | CharacterSet.[`make`](../CharacterSet.md)`(int oracleId)`<br>Factory. |
    | `static `[`CharacterSet`](../CharacterSet.md) | CharacterSet.[`make`](../CharacterSet.md)`(int oracleId)`<br>Factory. |

    **Methods in [oracle.sql](../package-summary.md) with parameters of type [CharacterSet](../CharacterSet.md)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                         |
    |--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract byte[]`  | CharacterSet.[`convert`](../CharacterSet.md)`(`[`CharacterSet`](../CharacterSet.md)` from, byte[] source, int offset, int count)`<br>Converts bytes in some representation to oracleId representation.         |
    | `byte[]`           | CharacterSetWithConverter.[`convert`](../CharacterSetWithConverter.md)`(`[`CharacterSet`](../CharacterSet.md)` from, byte[] source, int offset, int count)`                                                    |
    | `byte[]`           | CharacterSetWithConverter.[`convert`](../CharacterSetWithConverter.md)`(`[`CharacterSet`](../CharacterSet.md)` from, byte[] source, int offset, int count)`                                                    |
    | `abstract byte[]`  | CharacterSet.[`convert`](../CharacterSet.md)`(`[`CharacterSet`](../CharacterSet.md)` from, byte[] source, int offset, int count)`<br>Converts bytes in some representation to oracleId representation.         |
    | `byte[]`           | CharacterSet.[`convertUnshared`](../CharacterSet.md)`(`[`CharacterSet`](../CharacterSet.md)` from, byte[] source, int offset, int count)`<br>Converts bytes in some representation to oracleId representation. |
    | `byte[]`           | CharacterSet.[`convertUnshared`](../CharacterSet.md)`(`[`CharacterSet`](../CharacterSet.md)` from, byte[] source, int offset, int count)`<br>Converts bytes in some representation to oracleId representation. |
    | `abstract boolean` | CharacterSet.[`isConvertibleFrom`](../CharacterSet.md)`(`[`CharacterSet`](../CharacterSet.md)` source)`<br>Are conversions supported.                                                                          |
    | `boolean`          | CharacterSetWithConverter.[`isConvertibleFrom`](../CharacterSetWithConverter.md)`(`[`CharacterSet`](../CharacterSet.md)` source)`                                                                              |
    | `boolean`          | CharacterSetWithConverter.[`isConvertibleFrom`](../CharacterSetWithConverter.md)`(`[`CharacterSet`](../CharacterSet.md)` source)`                                                                              |
    | `abstract boolean` | CharacterSet.[`isConvertibleFrom`](../CharacterSet.md)`(`[`CharacterSet`](../CharacterSet.md)` source)`<br>Are conversions supported.                                                                          |
    | `abstract boolean` | CharacterSet.[`isLossyFrom`](../CharacterSet.md)`(`[`CharacterSet`](../CharacterSet.md)` from)`<br>A conversion looses information if the mapping is not invertible.                                           |
    | `boolean`          | CharacterSetWithConverter.[`isLossyFrom`](../CharacterSetWithConverter.md)`(`[`CharacterSet`](../CharacterSet.md)` from)`                                                                                      |
    | `boolean`          | CharacterSetWithConverter.[`isLossyFrom`](../CharacterSetWithConverter.md)`(`[`CharacterSet`](../CharacterSet.md)` from)`                                                                                      |
    | `abstract boolean` | CharacterSet.[`isLossyFrom`](../CharacterSet.md)`(`[`CharacterSet`](../CharacterSet.md)` from)`<br>A conversion looses information if the mapping is not invertible.                                           |

    **Constructors in [oracle.sql](../package-summary.md) with parameters of type [CharacterSet](../CharacterSet.md)**

    | Constructor and Description                                                                                                                                                                                       |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`CHAR`](../CHAR.md)`(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj, `[`CharacterSet`](../CharacterSet.md)` charSet)`<br>Construct a CHAR from an Object. |
    | [`CHAR`](../CHAR.md)`(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` obj, `[`CharacterSet`](../CharacterSet.md)` charSet)`<br>Construct a CHAR from an Object. |
    | [`CHAR`](../CHAR.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str, `[`CharacterSet`](../CharacterSet.md)` charSet)`<br>Constructor for CHAR.            |
    | [`CHAR`](../CHAR.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str, `[`CharacterSet`](../CharacterSet.md)` charSet)`<br>Constructor for CHAR.            |
    | [`CHAR`](../CHAR.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str, `[`CharacterSet`](../CharacterSet.md)` charSet, int len)`<br>Constructor for CHAR.   |
    | [`CHAR`](../CHAR.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str, `[`CharacterSet`](../CharacterSet.md)` charSet, int len)`<br>Constructor for CHAR.   |
    | [`CharacterBuffer`](../CharacterBuffer.md)`(`[`CharacterSet`](../CharacterSet.md)` charSet)`<br>Constructor.                                                                                                      |
    | [`CharacterBuffer`](../CharacterBuffer.md)`(`[`CharacterSet`](../CharacterSet.md)` charSet)`<br>Constructor.                                                                                                      |
    | [`CharacterWalker`](../CharacterWalker.md)`(`[`CharacterSet`](../CharacterSet.md)` charSet, byte[] bytes, int offset, int count)`<br>Constructor.                                                                 |
    | [`CharacterWalker`](../CharacterWalker.md)`(`[`CharacterSet`](../CharacterSet.md)` charSet, byte[] bytes, int offset, int count)`<br>Constructor.                                                                 |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../CharacterSet.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
