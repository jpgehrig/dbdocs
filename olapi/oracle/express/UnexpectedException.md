Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](TaskInterruptedException.md)
- Next Class

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

oracle.express

## Class UnexpectedException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - [oracle.olapi.OLAPIRuntimeException](../olapi/OLAPIRuntimeException.md)

        - - oracle.express.UnexpectedException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](../olapi/HasLocalizedMessage.md)

  ------------------------------------------------------------------------



      public class UnexpectedException
      extends OLAPIRuntimeException

  Indicates that you have called a method that requires the internal OLAP API client code to request information from Oracle OLAP, and the results that were returned do not conform to the expectations of the OLAP API client code.
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Method Summary

    - ### Methods inherited from class oracle.olapi.[OLAPIRuntimeException](../olapi/OLAPIRuntimeException.md)

      [`getLocalizedMessage`](../olapi/OLAPIRuntimeException.md)`, `[`getLocalizedMessage`](../olapi/OLAPIRuntimeException.md)`, `[`getParameters`](../olapi/OLAPIRuntimeException.md)`, `[`toString`](../olapi/OLAPIRuntimeException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](TaskInterruptedException.md)
- Next Class

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
