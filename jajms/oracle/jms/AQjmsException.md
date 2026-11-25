Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- [Prev Class](AQjmsDestinationProperty.md)
- [Next Class](AQjmsFactory.md)

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

oracle.jms

## Class AQjmsException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - [javax.jms.JMSException](../../javax/jms/JMSException.md)

      - - oracle.jms.AQjmsException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class AQjmsException
      extends JMSException

  This is an Oracle class which extends `javax.jms.JMSException` and adds Oracle® Database Advanced Queuing extensions.
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                |
    |-------------------|-----------------------------------------------------------------------|
    | `int`             | `getErrorNumber``()`<br>Gets the Oracle error code for the exception. |

    - ### Methods inherited from class javax.jms.[JMSException](../../javax/jms/JMSException.md)

      [`getErrorCode`](../../javax/jms/JMSException.md)`, `[`getLinkedException`](../../javax/jms/JMSException.md)`, `[`setLinkedException`](../../javax/jms/JMSException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getLocalizedMessage, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getErrorNumber

          public int getErrorNumber()

      Gets the Oracle error code for the exception.
      **Important:** This method will be deprecated in a future release. Use `getErrorCode()` instead.

      Returns:
      the error code

      See Also:
      [`JMSException.getErrorCode()`](../../javax/jms/JMSException.md)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- [Prev Class](AQjmsDestinationProperty.md)
- [Next Class](AQjmsFactory.md)

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

Copyright © 2001, 2019, Oracle and/or its affiliates. All rights reserved.
