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

- **[Prev Class](Value.md)**
- **[Next Class](ValueFormatException.md)**

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

## **Interface ValueFactory**

-

  ------------------------------------------------------------------------

  **
  **

      public interface ValueFactory

  **The `ValueFactory` object provides methods for the creation Value objects that can then be used to set properties.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type   | Method and Description                                                                                                                                                 |
    |---------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Value`](Value.md) | `createValue``(boolean value)`<br>Returns a `Value` object of [`PropertyType.BOOLEAN`](PropertyType.md) with the specified `value`.                                    |
    | [`Value`](Value.md) | `createValue``(java.util.Calendar value)`<br>Returns a `Value` object of [`PropertyType.DATE`](PropertyType.md) with the specified `value`.                            |
    | [`Value`](Value.md) | `createValue``(double value)`<br>Returns a `Value` object of [`PropertyType.DOUBLE`](PropertyType.md) with the specified `value`.                                      |
    | [`Value`](Value.md) | `createValue``(java.io.InputStream value)`<br>Returns a `Value` object of `PropertyType.BINARY` with a value consisting of the content of the specified `InputStream`. |
    | [`Value`](Value.md) | `createValue``(long value)`<br>Returns a `Value` object of [`PropertyType.LONG`](PropertyType.md) with the specified `value`.                                          |
    | [`Value`](Value.md) | `createValue``(`[`Node`](Node.md)` value)`<br>Returns a `Value` object of [`PropertyType.REFERENCE`](PropertyType.md) that holds the UUID of the specified `Node`.     |
    | [`Value`](Value.md) | `createValue``(java.lang.String value)`<br>Returns a `Value` object of [`PropertyType.STRING`](PropertyType.md) with the specified `value`.                            |
    | [`Value`](Value.md) | `createValue``(java.lang.String value, int type)`<br>Returns a `Value` object of the [`PropertyType`](PropertyType.md) specified by `type` with the specified `value`. |

<!-- -->

- - ### Method Detail

    - #### createValue

          Value createValue(java.lang.String value)

      Returns a `Value` object of [`PropertyType.STRING`](PropertyType.md) with the specified `value`.
      Parameters:
      `value` - a `String`

      Returns:
      a `Value` of [`PropertyType.STRING`](PropertyType.md)

    <!-- -->

    - #### createValue

          Value createValue(java.lang.String value,
                            int type)
                     throws ValueFormatException

      Returns a `Value` object of the [`PropertyType`](PropertyType.md) specified by `type` with the specified `value`. A `ValueFormatException` is thrown if the specified `value` cannot be converted to the specifed `type`.
      Parameters:
      `value` - a `String`

      `type` - one of the constants defined in [`PropertyType`](PropertyType.md).

      Returns:
      a `Value` of [`PropertyType`](PropertyType.md) `type`.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if the specified `value` cannot be converted to the specifed `type`.

    <!-- -->

    - #### createValue

          Value createValue(long value)

      Returns a `Value` object of [`PropertyType.LONG`](PropertyType.md) with the specified `value`.
      Parameters:
      `value` - a `long`

      Returns:
      a `Value` of [`PropertyType.LONG`](PropertyType.md)

    <!-- -->

    - #### createValue

          Value createValue(double value)

      Returns a `Value` object of [`PropertyType.DOUBLE`](PropertyType.md) with the specified `value`.
      Parameters:
      `value` - a `double`

      Returns:
      a `Value` of [`PropertyType.DOUBLE`](PropertyType.md)

    <!-- -->

    - #### createValue

          Value createValue(boolean value)

      Returns a `Value` object of [`PropertyType.BOOLEAN`](PropertyType.md) with the specified `value`.
      Parameters:
      `value` - a `boolean`

      Returns:
      a `Value` of [`PropertyType.BOOLEAN`](PropertyType.md)

    <!-- -->

    - #### createValue

          Value createValue(java.util.Calendar value)

      Returns a `Value` object of [`PropertyType.DATE`](PropertyType.md) with the specified `value`.
      Parameters:
      `value` - a `Calendar`

      Returns:
      a `Value` of [`PropertyType.DATE`](PropertyType.md)

    <!-- -->

    - #### createValue

          Value createValue(java.io.InputStream value)

      Returns a `Value` object of `PropertyType.BINARY` with a value consisting of the content of the specified `InputStream`.
      Parameters:
      `value` - an `InputStream`

      Returns:
      a `Value` of [`PropertyType.BINARY`](PropertyType.md)

    <!-- -->

    - #### createValue

          Value createValue(Node value)
                     throws RepositoryException

      Returns a `Value` object of [`PropertyType.REFERENCE`](PropertyType.md) that holds the UUID of the specified `Node`. This `Value` object can then be used to set a property that will be a reference to that `Node`.
      A `RepositoryException` is thrown if the specified `Node` is not referencable, the current `Session` is no longer active, or another error occurs.

      Parameters:
      `value` - a `Node`

      Returns:
      a `Value` of [`PropertyType.REFERENCE`](PropertyType.md)

      Throws:
      [`RepositoryException`](RepositoryException.md) - if the specified `Node` is not referencable, the current `Session` is no longer active, or another error occurs.

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

- **[Prev Class](Value.md)**
- **[Next Class](ValueFormatException.md)**

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
