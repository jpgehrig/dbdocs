Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Real Application Security Java API Reference
Release 19c**
E96300-01

- [Prev Class](XSSessionManager.md)
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

oracle.security.xs

## Class XSSessionManagerException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - [oracle.security.xs.XSException](XSException.md)

      - - oracle.security.xs.XSSessionManagerException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class XSSessionManagerException
      extends XSException

  Exception thrown when the session manager is not working.
  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                  |
    |----------------------------------------------------------------------------------------------------------------------------------------------|
    | `XSSessionManagerException``(java.lang.String errorString)`<br>Creates a new XSSessionManagerException with the specified exception message. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                |
    |--------------------|---------------------------------------------------------------------------------------|
    | `java.lang.String` | `toString``()`<br>Returns a string representation of the `XSSessionManagerException`. |

    - ### Methods inherited from class oracle.security.xs.[XSException](XSException.md)

      [`getMessage`](XSException.md)`, `[`getMessage`](XSException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XSSessionManagerException

          public XSSessionManagerException(java.lang.String errorString)

      Creates a new XSSessionManagerException with the specified exception message.
      Parameters:
      `errorString` - the exception message

  <!-- -->

  - ### Method Detail

    - #### toString

          public java.lang.String toString()

      Returns a string representation of the `XSSessionManagerException`.
      Overrides:
      `toString` in class `java.lang.Throwable`

      Returns:
      a string representation of the `XSSessionManagerException`

Skip navigation links

- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database Real Application Security Java API Reference
Release 19c**
E96300-01

- [Prev Class](XSSessionManager.md)
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

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.
Copyright © 2016, 2019, Oracle and/or its affiliates. All rights reserved.
