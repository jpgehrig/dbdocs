Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEDataSource.md)
- Next Class

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.io

## Class NFEIOException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - oracle.spatial.network.nfe.io.NFEIOException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class NFEIOException
      extends java.lang.Exception

  Base exception for NFE.
  See Also:
  [Serialized Form](../../../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                          |
    |-------------------|----------------------------------------------------------------|
    | `static int`      | `CATALOG_ALREADY_EXISTS`<br>Catalog already exists error code. |
    | `static int`      | `DUPLICATE_LAYER`<br>Duplicate layer error code.               |
    | `static int`      | `GENERAL_ERROR`<br>General error code.                         |
    | `static int`      | `INVALID_COLUMN_NAME`<br>Invalid column name error code.       |
    | `static int`      | `INVALID_SQL_NAME`<br>Invalid SQL Name error code.             |
    | `static int`      | `TABLE_ALREADY_EXISTS`<br>Table already exists error code.     |
    | `static int`      | `WRONG_TABLE_NAME`<br>Wrong table name error code.             |
    | `static int`      | `WS_ALREADY_EXISTS`<br>Workspace already exists error code.    |
    | `static int`      | `WS_NOT_LEAF`<br>Not leaf workspace error code.                |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                  |
    |------------------------------------------------------------------------------|
    | `NFEIOException``()`                                                         |
    | `NFEIOException``(java.lang.String message)`                                 |
    | `NFEIOException``(java.lang.String message, int errorCode)`                  |
    | `NFEIOException``(java.lang.String message, java.lang.Throwable throwable)`  |
    | `NFEIOException``(java.lang.Throwable throwable)`                            |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                |
    |--------------------|-----------------------------------------------------------------------|
    | `int`              | `getErrorCode``()`<br>Returns the error code.                         |
    | `java.lang.String` | `getErrorMsg``()`<br>Returns the error message.                       |
    | `void`             | `setErrorCode``(int errorCode)`<br>Sets the error code.               |
    | `void`             | `setErrorMsg``(java.lang.String errorMsg)`<br>Sets the error message. |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### GENERAL_ERROR

          public static int GENERAL_ERROR

      General error code.

    <!-- -->

    - #### DUPLICATE_LAYER

          public static int DUPLICATE_LAYER

      Duplicate layer error code.

    <!-- -->

    - #### TABLE_ALREADY_EXISTS

          public static int TABLE_ALREADY_EXISTS

      Table already exists error code.

    <!-- -->

    - #### WRONG_TABLE_NAME

          public static int WRONG_TABLE_NAME

      Wrong table name error code.

    <!-- -->

    - #### WS_ALREADY_EXISTS

          public static int WS_ALREADY_EXISTS

      Workspace already exists error code.

    <!-- -->

    - #### CATALOG_ALREADY_EXISTS

          public static int CATALOG_ALREADY_EXISTS

      Catalog already exists error code.

    <!-- -->

    - #### WS_NOT_LEAF

          public static int WS_NOT_LEAF

      Not leaf workspace error code.

    <!-- -->

    - #### INVALID_COLUMN_NAME

          public static int INVALID_COLUMN_NAME

      Invalid column name error code.

    <!-- -->

    - #### INVALID_SQL_NAME

          public static int INVALID_SQL_NAME

      Invalid SQL Name error code.

  <!-- -->

  - ### Constructor Detail

    - #### NFEIOException

          public NFEIOException()

    <!-- -->

    - #### NFEIOException

          public NFEIOException(java.lang.String message)

    <!-- -->

    - #### NFEIOException

          public NFEIOException(java.lang.Throwable throwable)

    <!-- -->

    - #### NFEIOException

          public NFEIOException(java.lang.String message,
                                java.lang.Throwable throwable)

    <!-- -->

    - #### NFEIOException

          public NFEIOException(java.lang.String message,
                                int errorCode)

  <!-- -->

  - ### Method Detail

    - #### getErrorCode

          public int getErrorCode()

      Returns the error code.
      Returns:
      one of the following constants: NFEIOException.GENERAL_ERROR, NFEIOException.DUPLICATE_LAYER, NFEIOException.TABLE_ALREADY_EXISTS, NFEIOException.WRONG_TABLE_NAME, NFEIOException.WS_ALREADY_EXISTS, NFEIOException.CATALOG_ALREADY_EXISTS, NFEIOException.WS_NOT_LEAF or NFEIOException.INVALID_COLUMN_NAME

    <!-- -->

    - #### setErrorCode

          public void setErrorCode(int errorCode)

      Sets the error code.
      Parameters:
      `errorCode` - error code

    <!-- -->

    - #### getErrorMsg

          public java.lang.String getErrorMsg()

      Returns the error message.
      Returns:
      error message

    <!-- -->

    - #### setErrorMsg

          public void setErrorMsg(java.lang.String errorMsg)

      Sets the error message.
      Parameters:
      `errorMsg` - error message

Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEDataSource.md)
- Next Class

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
