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

- [Prev Class](OraDecimalFormatSymbols.md)
- [Next Class](OraNumberFormat.md)

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

## Class OraNormalizer

- [java.lang.Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - oracle.i18n.text.OraNormalizer

<!-- -->

-

  ------------------------------------------------------------------------



      public class OraNormalizer
      extends Object

  The `OraNormalizer` class is a class used for normalizing strings following the Unicode Standard. Unicode characters may have different canonical formats. Before you can accurately compare characters, you must call the methods in this class to make sure that they are in the same canonical format. For more information regarding Unicode Normalization and the Unicode Standard, please refer to Technical Report 15 at www.unicode.org.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                         |
    |-------------------|-----------------------------------------------------------------------------------------------|
    | `static int`      | `CANONICAL_DECOMP`<br>Canonical decompose the string and then canonical sort the string.      |
    | `static int`      | `COMPATIBILITY_DECOMP`<br>Compatible decompose the string and then canonical sort the string. |
    | `static int`      | `NFC`<br>Canonical decomposition then composition.                                            |
    | `static int`      | `NFD`<br>Canonical decomposition.                                                             |
    | `static int`      | `NFKC`<br>Compatibility decomposition then composition canonical sort the string.             |
    | `static int`      | `NFKD`<br>Compatibility decomposition.                                                        |
    | `static int`      | `NO_DECOMP`<br>Canonical sort the string.                                                     |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                           | Method and Description                                                                                                                                               |
    |---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                      | `canonicalSort``(char[] sequence)`<br>This method takes a char\[\] and performs canonical sort on the sequence.                                                      |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `compose``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sequence)`<br>This is the normalization method.             |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `decompose``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sequence, int mode)`<br>This is the normalization method. |
    | `static OraNormalizer`                                                                      | `getInstance``()`<br>Returns a shared `OraNormalizer` instance to the user.                                                                                          |
    | [`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `normalize``(`[`String`](http://docs.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sequence, int mode)`<br>This is the normalization method. |

    - ### Methods inherited from class java.lang.[Object](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone--)`, `[`equals`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#equals-java.lang.Object-)`, `[`finalize`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize--)`, `[`getClass`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass--)`, `[`hashCode`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode--)`, `[`notify`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify--)`, `[`notifyAll`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll--)`, `[`toString`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait--)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-)`, `[`wait`](http://docs.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait-long-int-)

<!-- -->

- - ### Field Detail

    - #### NO_DECOMP

          public static final int NO_DECOMP

      Canonical sort the string.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CANONICAL_DECOMP

          public static final int CANONICAL_DECOMP

      Canonical decompose the string and then canonical sort the string.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### COMPATIBILITY_DECOMP

          public static final int COMPATIBILITY_DECOMP

      Compatible decompose the string and then canonical sort the string.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NFD

          public static final int NFD

      Canonical decomposition.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NFC

          public static final int NFC

      Canonical decomposition then composition.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NFKD

          public static final int NFKD

      Compatibility decomposition.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NFKC

          public static final int NFKC

      Compatibility decomposition then composition canonical sort the string.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getInstance

          public static OraNormalizer getInstance()

      Returns a shared `OraNormalizer` instance to the user.
      Returns:
      an `OraNormalizer` instance

    <!-- -->

    - #### canonicalSort

          public void canonicalSort(char[] sequence)

      This method takes a char\[\] and performs canonical sort on the sequence. The character string before and after this operation is considered equivalent by the Unicode Standard.
      Parameters:
      `sequence` - a string to sort

    <!-- -->

    - #### compose

          public String compose(String sequence)

      This is the normalization method. It normalizes by composing the Unicode characters after which it performs a canonical sort on the string.
      Parameters:
      `sequence` - a string to compose

      Returns:
      the composed string

    <!-- -->

    - #### decompose

          public String decompose(String sequence,
                                  int mode)

      This is the normalization method. It normalizes by decomposing the Unicode characters after which it performs a canonical sort on the string.
      Parameters:
      `sequence` - a string to compose

      `mode` - decomposed mode; options are `NO_DECOMPOSITION`, `CANONICAL_DECOMPOSITION`, and `COMPATIBLE_DECOMPOSITION`

      Returns:
      the decomposed string

    <!-- -->

    - #### normalize

          public String normalize(String sequence,
                                  int mode)

      This is the normalization method. It normalizes by decomposing the Unicode character after which it performs a canonical sort on the string.
      Parameters:
      `sequence` - a string to compose

      `mode` - decomposed mode; options are `NFD, NFC, NFKD, NFKC`

      Returns:
      the normalized string

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

- [Prev Class](OraDecimalFormatSymbols.md)
- [Next Class](OraNumberFormat.md)

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
