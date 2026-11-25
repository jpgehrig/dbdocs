Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](PropertyIterator.md)**
- **[Next Class](RangeIterator.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

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

**javax.jcr**

## **Class PropertyType**

- **java.lang.Object**

- - **javax.jcr.PropertyType**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public final class PropertyType
      extends java.lang.Object

  **The property types supported by the JCR standard.**
  **This interface defines following property types:**

  - **`STRING`**
  - **`BINARY`**
  - **`LONG`**
  - **`DOUBLE`**
  - **`DATE`**
  - **`BOOLEAN`**
  - **`NAME`**
  - **`PATH`**
  - **`REFERENCE`**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description |
    |---------------------------|-----------------------|
    | `static int`              | `BINARY`              |
    | `static int`              | `BOOLEAN`             |
    | `static int`              | `DATE`                |
    | `static int`              | `DOUBLE`              |
    | `static int`              | `LONG`                |
    | `static int`              | `NAME`                |
    | `static int`              | `PATH`                |
    | `static int`              | `REFERENCE`           |
    | `static int`              | `STRING`              |
    | `static java.lang.String` | `TYPENAME_BINARY`     |
    | `static java.lang.String` | `TYPENAME_BOOLEAN`    |
    | `static java.lang.String` | `TYPENAME_DATE`       |
    | `static java.lang.String` | `TYPENAME_DOUBLE`     |
    | `static java.lang.String` | `TYPENAME_LONG`       |
    | `static java.lang.String` | `TYPENAME_NAME`       |
    | `static java.lang.String` | `TYPENAME_PATH`       |
    | `static java.lang.String` | `TYPENAME_REFERENCE`  |
    | `static java.lang.String` | `TYPENAME_STRING`     |
    | `static java.lang.String` | `TYPENAME_UNDEFINED`  |
    | `static int`              | `UNDEFINED`           |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type         | Method and Description                                                                                              |
    |---------------------------|---------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `nameFromValue``(int type)`<br>Returns the name of the specified `type`, as used in serialization.                  |
    | `static int`              | `valueFromName``(java.lang.String name)`<br>Returns the numeric constant value of the type with the specified name. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### STRING

          public static final int STRING

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BINARY

          public static final int BINARY

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### LONG

          public static final int LONG

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DOUBLE

          public static final int DOUBLE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DATE

          public static final int DATE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### BOOLEAN

          public static final int BOOLEAN

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### NAME

          public static final int NAME

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### PATH

          public static final int PATH

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### REFERENCE

          public static final int REFERENCE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### UNDEFINED

          public static final int UNDEFINED

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPENAME_STRING

          public static final java.lang.String TYPENAME_STRING

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPENAME_BINARY

          public static final java.lang.String TYPENAME_BINARY

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPENAME_LONG

          public static final java.lang.String TYPENAME_LONG

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPENAME_DOUBLE

          public static final java.lang.String TYPENAME_DOUBLE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPENAME_DATE

          public static final java.lang.String TYPENAME_DATE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPENAME_BOOLEAN

          public static final java.lang.String TYPENAME_BOOLEAN

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPENAME_NAME

          public static final java.lang.String TYPENAME_NAME

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPENAME_PATH

          public static final java.lang.String TYPENAME_PATH

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPENAME_REFERENCE

          public static final java.lang.String TYPENAME_REFERENCE

      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### TYPENAME_UNDEFINED

          public static final java.lang.String TYPENAME_UNDEFINED

      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### nameFromValue

          public static java.lang.String nameFromValue(int type)

      Returns the name of the specified `type`, as used in serialization.
      Parameters:
      `type` - the property type

      Returns:
      the name of the specified `type`

      Throws:
      `java.lang.IllegalArgumentException` - if `type` is not a valid property type.

    <!-- -->

    - #### valueFromName

          public static int valueFromName(java.lang.String name)

      Returns the numeric constant value of the type with the specified name.
      Parameters:
      `name` - the name of the property type

      Returns:
      the numeric constant value

      Throws:
      `java.lang.IllegalArgumentException` - if `name` is not a valid property type name.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](PropertyIterator.md)**
- **[Next Class](RangeIterator.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

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

**Copyright © 2004-2005 Day Software Management AG. All Rights Reserved.**
