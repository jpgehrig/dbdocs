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

- [Prev Class](ExternalUser.md)
- [Next Class](InvalidXSAttributeException.md)

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

## Class InvalidSessionException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - [oracle.security.xs.XSException](XSException.md)

      - - oracle.security.xs.InvalidSessionException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class InvalidSessionException
      extends XSException

  Exception thrown on any session operations when the session is not valid. A common case is that the session has been destroyed.
  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                               |
    |---------------------------------------------------------------------------|
    | `InvalidSessionException``()`                                             |
    | `InvalidSessionException``(java.lang.String e)`                           |
    | `InvalidSessionException``(java.lang.String msg, java.lang.Throwable t)`  |
    | `InvalidSessionException``(java.lang.Throwable t)`                        |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class oracle.security.xs.[XSException](XSException.md)

      [`getMessage`](XSException.md)`, `[`getMessage`](XSException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### InvalidSessionException

          public InvalidSessionException()

    <!-- -->

    - #### InvalidSessionException

          public InvalidSessionException(java.lang.String e)

    <!-- -->

    - #### InvalidSessionException

          public InvalidSessionException(java.lang.Throwable t)

    <!-- -->

    - #### InvalidSessionException

          public InvalidSessionException(java.lang.String msg,
                                         java.lang.Throwable t)

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

- [Prev Class](ExternalUser.md)
- [Next Class](InvalidXSAttributeException.md)

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
