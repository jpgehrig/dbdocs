Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](FundamentalMetadataProvider.md)
- [Next Class](LiteralQualification.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.olapi.data.source

## Class IncorrectDataValueException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - [oracle.olapi.OLAPIRuntimeException](../../OLAPIRuntimeException.md)

        - - oracle.olapi.data.source.IncorrectDataValueException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](../../HasLocalizedMessage.md)

  ------------------------------------------------------------------------



      public class IncorrectDataValueException
      extends OLAPIRuntimeException

  Indicates that the data value is incorrect for the attempted operation. For example, the `DataProvider.createListSource(String[] elements)` method takes an array of `String` values. If an element of the `elements` array is `null`, then the method throws this exception.
  See Also:
  [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Method Summary

    - ### Methods inherited from class oracle.olapi.[OLAPIRuntimeException](../../OLAPIRuntimeException.md)

      [`getLocalizedMessage`](../../OLAPIRuntimeException.md)`, `[`getLocalizedMessage`](../../OLAPIRuntimeException.md)`, `[`getParameters`](../../OLAPIRuntimeException.md)`, `[`toString`](../../OLAPIRuntimeException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](FundamentalMetadataProvider.md)
- [Next Class](LiteralQualification.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
