Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XStream Java API Reference
19c**
E96285-02

- [Prev Class](RowLCR.md)
- [Next Class](XStreamIn.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

oracle.streams

## Class StreamsException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - oracle.streams.StreamsException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class StreamsException
      extends java.lang.Exception

  The StreamsException class provides information about Oracle Streams errors. Each StreamsException may have the following information:
  - A string describing the error. This is used as the Java Exception message, available through the method getMesage().
  - An integer error code that is specific to Oracle Streams or underlying Oracle database, available via the method getErrorCode().

  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                               |
    |-------------------------------------------------------------------------------------------------------------------------------------------|
    | `StreamsException``(java.lang.String message)`<br>Constructs a StreamsException object with message only.                                 |
    | `StreamsException``(java.lang.String message, int errorCode)`<br>Constructs a StreamsException object with message and error code.        |
    | `StreamsException``(java.lang.String message, java.lang.Throwable cause)`<br>Constructs a StreamsException object with message and cause. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                     |
    |-------------------|------------------------------------------------------------|
    | `int`             | `getErrorCode``()`<br>Gets the Oracle-specific error code. |

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### StreamsException

          public StreamsException(java.lang.String message)

      Constructs a StreamsException object with message only.
      Parameters:
      `message` - A string describing the error.

    <!-- -->

    - #### StreamsException

          public StreamsException(java.lang.String message,
                                  int errorCode)

      Constructs a StreamsException object with message and error code.
      Parameters:
      `message` - A string describing the error.

      `errorCode` - An integer error code.

    <!-- -->

    - #### StreamsException

          public StreamsException(java.lang.String message,
                                  java.lang.Throwable cause)

      Constructs a StreamsException object with message and cause.
      Parameters:
      `message` - A string describing the error.

      `cause` - The cause of this StreamsException.

  <!-- -->

  - ### Method Detail

    - #### getErrorCode

          public int getErrorCode()

      Gets the Oracle-specific error code.
      This method is used to obtain an Oracle Streams error code or a database internal error code.
      Returns:
      An integer identifies the Oracle Streams specific error.

Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XStream Java API Reference
19c**
E96285-02

- [Prev Class](RowLCR.md)
- [Next Class](XStreamIn.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

Copyright © 2001, 2019, Oracle and/or its affiliates. All Rights Reserved.
