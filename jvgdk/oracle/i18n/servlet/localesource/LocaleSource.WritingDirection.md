Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- [Prev Class](LocaleSource.Parameter.md)
- [Next Class](UserInput.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.i18n.servlet.localesource

## Class LocaleSource.WritingDirection

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.servlet.localesource.LocaleSource.WritingDirection

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true)

  <!-- -->

  Enclosing class:
  [LocaleSource](LocaleSource.md)

  ------------------------------------------------------------------------



      public static class LocaleSource.WritingDirection
      extends Object
      implements Serializable

  The `LocaleSource.WritingDirection` class represents the writing direction of the locale.
  See Also:
  [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                      | Field and Description                                                                                    |
    |----------------------------------------|----------------------------------------------------------------------------------------------------------|
    | `static LocaleSource.WritingDirection` | `LTR`<br>`LocaleSource.WritingDirection` object that represents left-to-right display writing direction. |
    | `static LocaleSource.WritingDirection` | `RTL`<br>`LocaleSource.WritingDirection` object that represents right-to-left display writing direction. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                           | Method and Description                                                                                                                                                                                                             |
    |---------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                                                   | `equals``(`[`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` o)`<br>Returns `true` if the input object is equal to this object.                                                         |
    | `static LocaleSource.WritingDirection`                                                      | `getWritingDirection``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name)`<br>Returns `LocaleSource.WritingDirection` object from the input string that is either `LTR` or `RTL`. |
    | `int`                                                                                       | `hashCode``()`<br>Returns the hash value.                                                                                                                                                                                          |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `toString``()`<br>Returns `LTR` or `RTL` representing a display writing direction.                                                                                                                                                 |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Field Detail

    - #### LTR

          public static final LocaleSource.WritingDirection LTR

      `LocaleSource.WritingDirection` object that represents left-to-right display writing direction.

    <!-- -->

    - #### RTL

          public static final LocaleSource.WritingDirection RTL

      `LocaleSource.WritingDirection` object that represents right-to-left display writing direction.

  <!-- -->

  - ### Method Detail

    - #### getWritingDirection

          public static LocaleSource.WritingDirection getWritingDirection(String name)

      Returns `LocaleSource.WritingDirection` object from the input string that is either `LTR` or `RTL`.
      Parameters:
      `name` - a `String` object representing the display writing direction

      Returns:
      a `LocaleSource.WritingDirection` object representing the display writing direction

    <!-- -->

    - #### toString

          public final String toString()

      Returns `LTR` or `RTL` representing a display writing direction.
      Overrides:
      [`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Returns:
      `LTR` for left-to-right writing direction or `RTL` for right-to-left writing direction

    <!-- -->

    - #### equals

          public boolean equals(Object o)

      Returns `true` if the input object is equal to this object.
      Overrides:
      [`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Parameters:
      `o` - an object to be compared

      Returns:
      boolean `true` if the input object is equal to this

    <!-- -->

    - #### hashCode

          public int hashCode()

      Returns the hash value.
      Overrides:
      [`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Returns:
      hash value

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database Globalization Development Kit Java API Reference
19c**
E96350-01

- [Prev Class](LocaleSource.Parameter.md)
- [Next Class](UserInput.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
