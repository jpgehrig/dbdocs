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

- [Prev Class](Template.md)
- [Next Class](ValueCursorInfoSpecification.md)

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

## Class UnmatchedInputsException

- java.lang.Object

- - java.lang.Throwable

  - - java.lang.Exception

    - - java.lang.RuntimeException

      - - [oracle.olapi.OLAPIRuntimeException](../../OLAPIRuntimeException.md)

        - - oracle.olapi.data.source.UnmatchedInputsException

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [HasLocalizedMessage](../../HasLocalizedMessage.md)

  ------------------------------------------------------------------------



      public class UnmatchedInputsException
      extends OLAPIRuntimeException

  Indicates that an input of a `Source` does not have a matching `Source`. This `Exception` occurs, for example, when you try to create a `CursorManager` for a `Source` that has one or more unmatched inputs.
  See Also:
  [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                       |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------|
    | `java.util.List`  | `getUnmatchedInputIDs``()`<br>Gets a `List` of the unique identifiers of the `Source` objects that are the unmatched inputs. |

    - ### Methods inherited from class oracle.olapi.[OLAPIRuntimeException](../../OLAPIRuntimeException.md)

      [`getLocalizedMessage`](../../OLAPIRuntimeException.md)`, `[`getLocalizedMessage`](../../OLAPIRuntimeException.md)`, `[`getParameters`](../../OLAPIRuntimeException.md)`, `[`toString`](../../OLAPIRuntimeException.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Throwable

      `addSuppressed, fillInStackTrace, getCause, getMessage, getStackTrace, getSuppressed, initCause, printStackTrace, printStackTrace, printStackTrace, setStackTrace`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getUnmatchedInputIDs

          public java.util.List getUnmatchedInputIDs()

      Gets a `List` of the unique identifiers of the `Source` objects that are the unmatched inputs.
      Returns:
      A `List` of the unique identifiers for the `Source` objects that are the unmatched inputs.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](Template.md)
- [Next Class](ValueCursorInfoSpecification.md)

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
