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

- [Prev Class](UTF8ValidationFilter.md)
- Next Class

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

## Class UTF8ValidationFilter.ValidationBehavior

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.text.UTF8ValidationFilter.ValidationBehavior

<!-- -->

- Enclosing class:
  [UTF8ValidationFilter](UTF8ValidationFilter.md)

  ------------------------------------------------------------------------



      public abstract static class UTF8ValidationFilter.ValidationBehavior
      extends Object

  The `ValidationBehavior` class is the class used to determine the behavior in case the conversion fails.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                                | Field and Description                                                                                                                                              |
    |--------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static UTF8ValidationFilter.ValidationBehavior` | `REPLACE`<br>The parameter indicating the UTF-8 validator replaces the invalid UTF-8 with the replacement character U+FFFD, or 0xef, 0xbf, 0xbd in UTF-8 encoding. |
    | `static UTF8ValidationFilter.ValidationBehavior` | `REPORT`<br>The parameter indicating the UTF-8 validator reports the error if any invalid UTF-8 sequences are found.                                               |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Field Detail

    - #### REPORT

          public static final UTF8ValidationFilter.ValidationBehavior REPORT

      The parameter indicating the UTF-8 validator reports the error if any invalid UTF-8 sequences are found.
      The error is `UTFDataFormatException`.

    <!-- -->

    - #### REPLACE

          public static final UTF8ValidationFilter.ValidationBehavior REPLACE

      The parameter indicating the UTF-8 validator replaces the invalid UTF-8 with the replacement character U+FFFD, or 0xef, 0xbf, 0xbd in UTF-8 encoding.

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

- [Prev Class](UTF8ValidationFilter.md)
- Next Class

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
