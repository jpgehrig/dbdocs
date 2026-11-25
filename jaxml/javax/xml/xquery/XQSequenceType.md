Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XQSequence.md)**
- **[Next Class](XQStackTraceElement.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**javax.xml.xquery**

## **Interface XQSequenceType**

- **All Known Subinterfaces:**
  **[XQItemType](XQItemType.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XQSequenceType

  **The `XQSequenceType` interface represents a sequence type as [*XQuery 1.0: An XML Query language*](http://www.w3.org/TR/xquery). The `XQSequenceType` is the base interface for the `XQItemType` interface and contains an occurence indicator.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static int`      | `OCC_EMPTY`           |
    | `static int`      | `OCC_EXACTLY_ONE`     |
    | `static int`      | `OCC_ONE_OR_MORE`     |
    | `static int`      | `OCC_ZERO_OR_MORE`    |
    | `static int`      | `OCC_ZERO_OR_ONE`     |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type             | Method and Description                                                                                        |
    |-------------------------------|---------------------------------------------------------------------------------------------------------------|
    | `boolean`                     | `equals``(java.lang.Object o)`<br>Compares the specified object with this sequence type for equality.         |
    | `int`                         | `getItemOccurrence``()`<br>Returns the occurrence indicator for the sequence type.                            |
    | [`XQItemType`](XQItemType.md) | `getItemType``()`<br>Returns the type of the item in the sequence type.                                       |
    | `int`                         | `hashCode``()`<br>Returns a hash code consistent with the definition of the equals method.                    |
    | `java.lang.String`            | `toString``()`<br>Returns a human-readable implementation-defined string representation of the sequence type. |

<!-- -->

- - ### Field Detail

    - #### OCC_ZERO_OR_ONE

          static final int OCC_ZERO_OR_ONE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### OCC_EXACTLY_ONE

          static final int OCC_EXACTLY_ONE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### OCC_ZERO_OR_MORE

          static final int OCC_ZERO_OR_MORE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### OCC_ONE_OR_MORE

          static final int OCC_ONE_OR_MORE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### OCC_EMPTY

          static final int OCC_EMPTY

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getItemType

          XQItemType getItemType()

      Returns the type of the item in the sequence type.
      Returns:
      `XQItemType` representing the item type in the sequence. `null` is returned in case of an empty sequence.

    <!-- -->

    - #### getItemOccurrence

          int getItemOccurrence()

      Returns the occurrence indicator for the sequence type. One of:
      | Description  | Value              |
      |--------------|--------------------|
      | Zero or one  | `OCC_ZERO_OR_ONE`  |
      | Exactly one  | `OCC_EXACTLY_ONE`  |
      | Zero or more | `OCC_ZERO_OR_MORE` |
      | One or more  | `OCC_ONE_OR_MORE`  |
      | Empty        | `OCC_EMPTY`        |


      Returns:
      `int` indicating the occurrence indicator

    <!-- -->

    - #### toString

          java.lang.String toString()

      Returns a human-readable implementation-defined string representation of the sequence type.
      Overrides:
      `toString` in class `java.lang.Object`

      Returns:
      a `String` representation of the sequence type

    <!-- -->

    - #### equals

          boolean equals(java.lang.Object o)

      Compares the specified object with this sequence type for equality. The result is `true` only if the argument is a sequence type object which represents the same XQuery sequence type.

      In order to comply with the general contract of `equals` and `hashCode` across different implementations the following algorithm must be used. Return `true` if and only if both objects are `XQsequenceType` and:
      - `getItemOccurrence()` is equal
      - if not `OCC_EMPTY`, `getItemType()` is equal

      Overrides:
      `equals` in class `java.lang.Object`

      Parameters:
      `o` - an `XQItemType` object representing an XQuery sequence type

      Returns:
      `true` if the input item type object represents the same XQuery sequence type, `false` otherwise

    <!-- -->

    - #### hashCode

          int hashCode()

      Returns a hash code consistent with the definition of the equals method.

      In order to comply with the general contract of `equals` and `hashCode` across different implementations the following algorithm must be used:
            int hashCode;
            if (getItemOccurrence() == XQSequenceType.OCC_EMPTY)
            {
              hashCode = 1;
            }
            else
            {
              hashCode = getItemOccurrence()*31 + getItemType().hashCode();
            }


      Overrides:
      `hashCode` in class `java.lang.Object`

      Returns:
      hash code for this item type

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XQSequence.md)**
- **[Next Class](XQStackTraceElement.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
