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

- [Prev Class](LocaleSource.md)
- [Next Class](LocaleSource.Parameter.md)

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

## Class LocaleSource.Alignment

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.servlet.localesource.LocaleSource.Alignment

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://docs.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true)

  <!-- -->

  Enclosing class:
  [LocaleSource](LocaleSource.md)

  ------------------------------------------------------------------------



      public static class LocaleSource.Alignment
      extends Object
      implements Serializable

  The `LocaleSource.Alignment` class represents the alignment of text elements.
  To set the text alignment in HTML, specify the attribute `align="left"` or `align="right"` in HTML tags. The value is effective, even if you switch the writing direction in HTML from `LTR` to `RTL`. As a result, you see text elements in opposite alignment in `RTL` mode. To avoid this issue, use this parameter value class to specify either `LocaleSource.Alignment.START` or `LocaleSource.Alignment.END` in place of the `left` or `right` attributes. GDK automatically detects the writing direction to return the appropriate alignment value.

  Note this class is a constant value class, so this will not determine the alignment.

  See Also:
  [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type               | Field and Description                                                                  |
    |---------------------------------|----------------------------------------------------------------------------------------|
    | `static LocaleSource.Alignment` | `END`<br>The `LocaleSource.Alignment` object that represents the ending alignment.     |
    | `static LocaleSource.Alignment` | `START`<br>The `LocaleSource.Alignment` object that represents the starting alignment. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                           | Method and Description                                                                                                                                                                                                 |
    |---------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LocaleSource.Alignment`                                                                    | `getAlignment``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name)`<br>Returns `LocaleSource.Alignment` object from the input string that is either `START` or `END`. |
    | `int`                                                                                       | `hashCode``()`<br>Returns the hash value.                                                                                                                                                                              |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `toString``()`<br>Returns `START` or `END` representing a display writing direction.                                                                                                                                   |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Field Detail

    - #### START

          public static final LocaleSource.Alignment START

      The `LocaleSource.Alignment` object that represents the starting alignment. If the mode is left-to-right writing direction, `left` is returned; otherwise `right` is returned.

    <!-- -->

    - #### END

          public static final LocaleSource.Alignment END

      The `LocaleSource.Alignment` object that represents the ending alignment. If the mode is left-to-right writing direction, `right` is returned; otherwise `left` is returned.

  <!-- -->

  - ### Method Detail

    - #### getAlignment

          public LocaleSource.Alignment getAlignment(String name)

      Returns `LocaleSource.Alignment` object from the input string that is either `START` or `END`.
      Parameters:
      `name` - a `String` object representing the alignment

      Returns:
      a `LocaleSource.Alignment` object representing the text alignment

    <!-- -->

    - #### toString

          public String toString()

      Returns `START` or `END` representing a display writing direction.
      Overrides:
      [`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--) in class [`Object`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      Returns:
      `START` for starting text alignment or `END` for ending text alignment

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

- [Prev Class](LocaleSource.md)
- [Next Class](LocaleSource.Parameter.md)

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
