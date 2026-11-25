Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- [Prev Class](CharacterValidationReader.md)
- [Next Class](OraCollator.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.i18n.text

## Class OraCollationKey

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.text.OraCollationKey

<!-- -->

- All Implemented Interfaces:
  [Comparable](http://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)

  ------------------------------------------------------------------------



      public class OraCollationKey
      extends Object
      implements Comparable

  The `OraCollationKey` class represents a `String` object under control of a specific `OraCollator` object. This construct is used to store a sorting order under a certain sorting rule and to be compared when needed.
  Since:
  Oracle 10.1.0.2

  See Also:
  [`OraCollator`](OraCollator.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `protected int`   | `primIdx`             |
    | `protected int`   | `secIdx`              |
    | `protected int`   | `terIdx`              |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                           | Method and Description                                                                                                                                                                                             |
    |---------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                                                                       | `compareTo``(`[`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` o)`<br>Compares this `OraCollationKey` object with the specified `Object` object.                       |
    | `int`                                                                                       | `compareTo``(OraCollationKey target)`<br>Compare this `OraCollationKey` object to the target `OraCollationKey` object.                                                                                             |
    | `boolean`                                                                                   | `equals``(`[`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` target)`<br>Determines if this `OraCollationKey` object and the target `OraCollationKey` object are equal. |
    | `int`                                                                                       | `getNextMonoKeys``(byte[] keyArray)`                                                                                                                                                                               |
    | `int[]`                                                                                     | `getNextMultiKeys``(byte[] keyArray)`                                                                                                                                                                              |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getSourceString``()`<br>Returns the source `String` object that this `OraCollationKey` object represents.                                                                                                         |
    | `int`                                                                                       | `hashCode``()`<br>Creates a hash code for this `OraCollationKey` object; the value is calculated on the key, not the source string.                                                                                |
    | `byte[]`                                                                                    | `toByteArray``()`<br>Converts the `OraCollationKey` object to a sequence of bytes.                                                                                                                                 |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Field Detail

    - #### primIdx

          protected int primIdx

    <!-- -->

    - #### secIdx

          protected int secIdx

    <!-- -->

    - #### terIdx

          protected int terIdx

  <!-- -->

  - ### Method Detail

    - #### compareTo

          public int compareTo(OraCollationKey target)

      Compare this `OraCollationKey` object to the target `OraCollationKey` object. The collation rules of the `OraCollator` object that created these keys are applied. `OraCollationKey` objects created by different `OraCollator` objects cannot be compared.
      Parameters:
      `target` - the target `OraCollationKey`

      Returns:
      `OraCollator.GREATER`, `OraCollator.LESS`, or `OraCollator.EQUAL`

      See Also:
      [`OraCollator.compare(java.lang.Object, java.lang.Object)`](OraCollator.md)

    <!-- -->

    - #### compareTo

          public int compareTo(Object o)

      Compares this `OraCollationKey` object with the specified `Object` object.
      Specified by:
      [`compareTo`](http://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true#compareTo-T-) in interface [`Comparable`](http://docs.oracle.com/javase/8/docs/api/java/lang/Comparable.html?is-external=true)

      Parameters:
      `o` - the `Object` object to which the `OraCollationKey` object is compared

      Returns:
      `OraCollator.GREATER`, `OraCollator.LESS`, or `OraCollator.EQUAL`

    <!-- -->

    - #### equals

          public boolean equals(Object target)

      Determines if this `OraCollationKey` object and the target `OraCollationKey` object are equal.
      Overrides:
      [`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Parameters:
      `target` - the `OraCollationKey` object to which this `OraCollationKey` object is compared

      Returns:
      `ture` if the two are equal; `false` otherwise

    <!-- -->

    - #### hashCode

          public int hashCode()

      Creates a hash code for this `OraCollationKey` object; the value is calculated on the key, not the source string.
      Overrides:
      [`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Returns:
      the hash value

    <!-- -->

    - #### getSourceString

          public String getSourceString()

      Returns the source `String` object that this `OraCollationKey` object represents.
      Returns:
      the source `String` object

    <!-- -->

    - #### toByteArray

          public byte[] toByteArray()

      Converts the `OraCollationKey` object to a sequence of bytes.
      Returns:
      a byte array representation of the `OraCollationKey` object

    <!-- -->

    - #### getNextMultiKeys

          public int[] getNextMultiKeys(byte[] keyArray)

    <!-- -->

    - #### getNextMonoKeys

          public int getNextMonoKeys(byte[] keyArray)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- [Prev Class](CharacterValidationReader.md)
- [Next Class](OraCollator.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
