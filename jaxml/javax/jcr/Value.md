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

- **[Prev Class](UnsupportedRepositoryOperationException.md)**
- **[Next Class](ValueFactory.md)**

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

## **Interface Value**

-

  ------------------------------------------------------------------------

  **
  **

      public interface Value

  **A generic holder for the value of a property. A `Value` object can be used without knowing the actual property type (`STRING`, `DOUBLE`, `BINARY` etc.).**
  **Any implementation of this interface must adhere to the following behavior:**

  - **A `Value` object can be read using type-specific `get` methods. These methods are divided into two groups:**
    - **The non-stream `get` methods `getString()`, `getDate()`, `getLong()`, `getDouble()` and `getBoolean()`.**
    - **`getStream()`.**
  - **Once a `Value` object has been read once using `getStream()`, all subsequent calls to `getStream()` will return the same `Stream` object. This may mean, for example, that the stream returned is fully or partially consumed. In order to get a fresh stream the `Value` object must be reacquired via [`Property.getValue()`](Property.md) or [`Property.getValues()`](Property.md).**
  - **Once a `Value` object has been read once using `getStream()`, any subsequent call to any of the non-stream `get` methods will throw an `IllegalStateException`. In order to successfully invoke a non-stream `get` method, the `Value` must be reacquired.**
  - **Once a `Value` object has been read once using a non-stream get method, any subsequent call to `getStream()` will throw an `IllegalStateException`. In order to successfully invoke `getStream()`, the `Value` must be reacquired.**

  **Two `Value` instances, `v1` and `v2`, are considered equal if and only if:**

  - **`v1.getType() == v2.getType()`, and,**
  - **`v1.getString().equals(v2.getString())`**

  **Actually comparing two `Value` instances by converting them to string form may not be practical in some cases (for example, if the values are very large binaries). Consequently, the above is intended as a normative definition of `Value` equality but not as a procedural test of equality. It is assumed that implementations will have efficient means of determining equality that conform with the above definition.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type     | Method and Description                                                    |
    |-----------------------|---------------------------------------------------------------------------|
    | `boolean`             | `getBoolean``()`<br>Returns a `Boolean` representation of this value.     |
    | `java.util.Calendar`  | `getDate``()`<br>Returns a `Calendar` representation of this value.       |
    | `double`              | `getDouble``()`<br>Returns a `double` representation of this value.       |
    | `long`                | `getLong``()`<br>Returns a `long` representation of this value.           |
    | `java.io.InputStream` | `getStream``()`<br>Returns an `InputStream` representation of this value. |
    | `java.lang.String`    | `getString``()`<br>Returns a `String` representation of this value.       |
    | `int`                 | `getType``()`<br>Returns the `type` of this `Value`.                      |

<!-- -->

- - ### Method Detail

    - #### getString

          java.lang.String getString()
                              throws ValueFormatException,
                                     java.lang.IllegalStateException,
                                     RepositoryException

      Returns a `String` representation of this value.
      If this value cannot be converted to a string, a `ValueFormatException` is thrown.

      If `getStream` has previously been called on this `Value` instance, an `IllegalStateException` is thrown. In this case a new `Value` instance must be acquired in order to successfully call `getString`.

      A `RepositoryException` is thrown if another error occurs.

      Returns:
      A `String` representation of the value of this property.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if conversion to a `String` is not possible.

      `java.lang.IllegalStateException` - if `getStream` has previously been called on this `Value` instance.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getStream

          java.io.InputStream getStream()
                                 throws java.lang.IllegalStateException,
                                        RepositoryException

      Returns an `InputStream` representation of this value. Uses the standard conversion to binary (see JCR specification)
      If a non-stream `get` method has previously been called on this `Value` instance, an `IllegalStateException` is thrown. In this case a new `Value` instance must be acquired in order to successfully call `getStream`.

      A `RepositoryException` is thrown if another error occurs.

      Returns:
      An `InputStream` representation of this value.

      Throws:
      `java.lang.IllegalStateException` - if a non-stream `get` method has previously been called on this `Value` instance.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getLong

          long getLong()
                throws java.lang.IllegalStateException,
                       RepositoryException

      Returns a `long` representation of this value.
      If this value cannot be converted to a `long`, a `ValueFormatException` is thrown.

      If `getStream` has previously been called on this `Value` instance, an `IllegalStateException` is thrown. In this case a new `Value` instance must be acquired in order to successfully call `getLong`.

      A `RepositoryException` is thrown if another error occurs.

      Returns:
      A `long` representation of this value.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if conversion to an `long` is not possible.

      `java.lang.IllegalStateException` - if `getStream` has previously been called on this `Value` instance.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getDouble

          double getDouble()
                    throws ValueFormatException,
                           java.lang.IllegalStateException,
                           RepositoryException

      Returns a `double` representation of this value.
      If this value cannot be converted to a `double`, a `ValueFormatException` is thrown.

      If `getStream` has previously been called on this `Value` instance, an `IllegalStateException` is thrown. In this case a new `Value` instance must be acquired in order to successfully call `getDouble`.

      A `RepositoryException` is thrown if another error occurs.

      Returns:
      A `double` representation of this value.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if conversion to a `double` is not possible.

      `java.lang.IllegalStateException` - if `getStream` has previously been called on this `Value` instance.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getDate

          java.util.Calendar getDate()
                              throws ValueFormatException,
                                     java.lang.IllegalStateException,
                                     RepositoryException

      Returns a `Calendar` representation of this value.
      The object returned is a copy of the stored value, so changes to it are not reflected in internal storage.

      If this value cannot be converted to a `Calendar`, a `ValueFormatException` is thrown.

      If `getStream` has previously been called on this `Value` instance, an `IllegalStateException` is thrown. In this case a new `Value` instance must be acquired in order to successfully call `getDate`.

      A `RepositoryException` is thrown if another error occurs.

      Returns:
      A `Calendar` representation of this value.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if conversion to a `Calendar` is not possible.

      `java.lang.IllegalStateException` - if `getStream` has previously been called on this `Value` instance.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getBoolean

          boolean getBoolean()
                      throws ValueFormatException,
                             java.lang.IllegalStateException,
                             RepositoryException

      Returns a `Boolean` representation of this value.
      If this value cannot be converted to a `Boolean`, a `ValueFormatException` is thrown.

      If `getStream` has previously been called on this `Value` instance, an `IllegalStateException` is thrown. In this case a new `Value` instance must be acquired in order to successfully call `getBoolean`.

      A `RepositoryException` is thrown if another error occurs.

      Returns:
      A `Boolean` representation of this value.

      Throws:
      [`ValueFormatException`](ValueFormatException.md) - if conversion to a `Boolean` is not possible.

      `java.lang.IllegalStateException` - if `getStream` has previously been called on this `Value` instance.

      [`RepositoryException`](RepositoryException.md) - if another error occurs.

    <!-- -->

    - #### getType

          int getType()

      Returns the `type` of this `Value`. One of:
      - `PropertyType.STRING`
      - `PropertyType.DATE`
      - `PropertyType.BINARY`
      - `PropertyType.DOUBLE`
      - `PropertyType.LONG`
      - `PropertyType.BOOLEAN`
      - `PropertyType.NAME`
      - `PropertyType.PATH`
      - `PropertyType.REFERENCE`

      See [`PropertyType`](PropertyType.md).
      The type returned is that which was set at property creation.

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

- **[Prev Class](UnsupportedRepositoryOperationException.md)**
- **[Next Class](ValueFactory.md)**

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
