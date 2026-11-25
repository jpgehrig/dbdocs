Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/CharacterWalker.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](CharacterSetWithConverter.md)
- [Next Class](CLOB.md)

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

## Class CharacterWalker

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.sql.CharacterWalker

<!-- -->

-

  ------------------------------------------------------------------------



      public final class CharacterWalker
      extends Object

  A CharacterWalker lets you walk through the characters that are represented as a sequence of bytes in some CharacterSet.
  A character set determines a 32 bit value for each character. The values from 0 to 64K are reserved for their Unicode interpretation. Otherwise the value has no particular significance. But values can be used to build up another sequence with a CharacterBuffer.

  See Also:
  [`CharacterSet`](CharacterSet.md), [`CharacterBuffer`](CharacterBuffer.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                           |
    |-----------------------------------------------------------------------------------------------------------------------|
    | `CharacterWalker``(`[`CharacterSet`](CharacterSet.md)` charSet, byte[] bytes, int offset, int count)`<br>Constructor. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                      |
    |-------------------|-------------------------------------------------------------------------------------------------------------|
    | `boolean`         | `hasMoreCharacters``()`<br>Reports whether there are more bytes waiting to be converted.                    |
    | `int`             | `nextCharacter``()`<br>Returns the next character in the sequence and advances the CharacterWalker over it. |

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`equals`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals_java_lang_Object_)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

<!-- -->

- - ### Constructor Detail

    - #### CharacterWalker

          public CharacterWalker(CharacterSet charSet,
                                 byte[] bytes,
                                 int offset,
                                 int count)

      Constructor.
      Parameters:
      `charSet` - the CharacterSet to be used in interpreting the bytes.

      `bytes` - the byte array containing the data to be interpreted.

      `offset` - the index in bytes of the first byte to be interpreted.

      `count` - the number of bytes to be interpreted.

  <!-- -->

  - ### Method Detail

    - #### nextCharacter

          public int nextCharacter()
                            throws NoSuchElementException

      Returns the next character in the sequence and advances the CharacterWalker over it.
      Returns:
      the 32 bit representation of the next character

      Throws:
      [`NoSuchElementException`](http://download.oracle.com/javase/8/docs/api/java/util/NoSuchElementException.html?is-external=true) - if the walker has already returned the last character or the sequence is ill-formed. That is, the next bytes are somehow not allowed in the given representation

    <!-- -->

    - #### hasMoreCharacters

          public boolean hasMoreCharacters()

      Reports whether there are more bytes waiting to be converted. Note that even if hasMoreCharacters returns true, it's possible for nextCharacter to throw an exception because the bytes aren't well-formed.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/CharacterWalker.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](CharacterSetWithConverter.md)
- [Next Class](CLOB.md)

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
