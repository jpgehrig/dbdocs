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

- [Prev Class](CharEntityReference.md)
- [Next Class](MimeUtility.md)

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

oracle.i18n.net

## Class CharEntityReference.Form

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.net.CharEntityReference.Form

<!-- -->

- Enclosing class:
  [CharEntityReference](CharEntityReference.md)

  ------------------------------------------------------------------------



      public static class CharEntityReference.Form
      extends Object

  Form parameter class that specifies the escaped form.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                 | Field and Description                                                                                                                             |
    |-----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static CharEntityReference.Form` | `DECIMAL_NUMBER`<br>Constant value used to specify the escaped values in decimal number form; used for all data, for example, `&#12345;`.         |
    | `static CharEntityReference.Form` | `HEXADECIMAL_NUMBER`<br>Constant value used to specify the escaped values in hexadecimal number form; used for all data, for example, `&#x1235;`. |
    | `static CharEntityReference.Form` | `NAMED`<br>Constant value used to specify the escaped values in a registered named entity, for example, `&lt;`.                                   |
    | `static CharEntityReference.Form` | `NAMED_DECIMAL_NUMBER`<br>Constant value used to specify the escaped values in a named character entity, if the entity is registered.             |
    | `static CharEntityReference.Form` | `NAMED_HEXADECIMAL_NUMBER`<br>Constant value used to specify the escaped values in a named character entity, if the entity is registered.         |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Field Detail

    - #### NAMED

          public static final CharEntityReference.Form NAMED

      Constant value used to specify the escaped values in a registered named entity, for example, `&lt;`.

    <!-- -->

    - #### DECIMAL_NUMBER

          public static final CharEntityReference.Form DECIMAL_NUMBER

      Constant value used to specify the escaped values in decimal number form; used for all data, for example, `&#12345;`.

    <!-- -->

    - #### HEXADECIMAL_NUMBER

          public static final CharEntityReference.Form HEXADECIMAL_NUMBER

      Constant value used to specify the escaped values in hexadecimal number form; used for all data, for example, `&#x1235;`.

    <!-- -->

    - #### NAMED_HEXADECIMAL_NUMBER

          public static final CharEntityReference.Form NAMED_HEXADECIMAL_NUMBER

      Constant value used to specify the escaped values in a named character entity, if the entity is registered. Otherwise, the `HEXADECIMAL_NUMBER` form is used.

    <!-- -->

    - #### NAMED_DECIMAL_NUMBER

          public static final CharEntityReference.Form NAMED_DECIMAL_NUMBER

      Constant value used to specify the escaped values in a named character entity, if the entity is registered. Otherwise, the `DECIMAL_NUMBER` form is used.

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

- [Prev Class](CharEntityReference.md)
- [Next Class](MimeUtility.md)

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
