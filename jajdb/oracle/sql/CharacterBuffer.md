Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/CharacterBuffer.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](CHAR.md)
- [Next Class](CharacterSet.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

oracle.sql

## Class CharacterBuffer

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.sql.CharacterBuffer

<!-- -->

-

  ------------------------------------------------------------------------



      public final class CharacterBuffer
      extends Object

  This class allows the program to construct an array of bytes in some representation using the 32 bit values returned by a CharacterWalker.
  See Also:
  [`CharacterWalker`](CharacterWalker.md), [`CharacterSet`](CharacterSet.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                      |
    |----------------------------------------------------------------------------------|
    | `CharacterBuffer``(`[`CharacterSet`](CharacterSet.md)` charSet)`<br>Constructor. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                    |
    |-------------------|---------------------------------------------------------------------------|
    | `void`            | `append``(int c)`<br>Append the (posibly multi-byte) representation of c. |
    | `byte[]`          | `getBytes``()`<br>The accumulated data                                    |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### CharacterBuffer

          public CharacterBuffer(CharacterSet charSet)

      Constructor.
      Parameters:
      `charSet` - the CharacterSet in which the data is represented

  <!-- -->

  - ### Method Detail

    - #### append

          public void append(int c)
                      throws SQLException

      Append the (posibly multi-byte) representation of c.
      Parameters:
      `c` - a value in the 32 bit representation of characters of charSet.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if c is not a value in the 32 bit representation of charSet.

    <!-- -->

    - #### getBytes

          public byte[] getBytes()

      The accumulated data
      Returns:
      an array of bytes containing the representation of all characters that have been appended.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/CharacterBuffer.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](CHAR.md)
- [Next Class](CharacterSet.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

Copyright © 2008, 2022, Oracle and/or its affiliates.
