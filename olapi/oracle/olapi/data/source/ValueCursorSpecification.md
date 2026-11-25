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

- [Prev Class](ValueCursorInfoSpecification.md)
- Next Class

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

## Class ValueCursorSpecification

- java.lang.Object

- - [oracle.olapi.data.source.CursorSpecification](CursorSpecification.md)

  - - oracle.olapi.data.source.ValueCursorSpecification

<!-- -->

- All Implemented Interfaces:
  [CursorInfoSpecification](CursorInfoSpecification.md), [ValueCursorInfoSpecification](ValueCursorInfoSpecification.md)

  ------------------------------------------------------------------------



      public final class ValueCursorSpecification
      extends CursorSpecification
      implements ValueCursorInfoSpecification

  A `CursorSpecification` for the values of a `Source`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                                                                                                            |
    |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object` | `acceptVisitor``(`[`CursorSpecificationVisitor`](CursorSpecificationVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitValueCursorSpecification` method of the specified `CursorSpecificationVisitor` and passes that method this `ValueCursorSpecification` and the specified context `Object`. |

    - ### Methods inherited from class oracle.olapi.data.source.[CursorSpecification](CursorSpecification.md)

      [`getDefaultFetchSize`](CursorSpecification.md)`, `[`getSource`](CursorSpecification.md)`, `[`getTransaction`](CursorSpecification.md)`, `[`isExtentCalculationSpecified`](CursorSpecification.md)`, `[`isParentEndCalculationSpecified`](CursorSpecification.md)`, `[`isParentStartCalculationSpecified`](CursorSpecification.md)`, `[`setDefaultFetchSize`](CursorSpecification.md)`, `[`setExtentCalculationSpecified`](CursorSpecification.md)`, `[`setParentEndCalculationSpecified`](CursorSpecification.md)`, `[`setParentStartCalculationSpecified`](CursorSpecification.md)`, `[`setTransaction`](CursorSpecification.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.olapi.data.source.[CursorInfoSpecification](CursorInfoSpecification.md)

      [`getSource`](CursorInfoSpecification.md)`, `[`isParentEndCalculationSpecified`](CursorInfoSpecification.md)`, `[`isParentStartCalculationSpecified`](CursorInfoSpecification.md)`, `[`setParentEndCalculationSpecified`](CursorInfoSpecification.md)`, `[`setParentStartCalculationSpecified`](CursorInfoSpecification.md)

<!-- -->

- - ### Method Detail

    - #### acceptVisitor

          public final java.lang.Object acceptVisitor(CursorSpecificationVisitor visitor,
                                                      java.lang.Object context)

      Calls the `visitValueCursorSpecification` method of the specified `CursorSpecificationVisitor` and passes that method this `ValueCursorSpecification` and the specified context `Object`.
      Specified by:
      [`acceptVisitor`](CursorSpecification.md) in class [`CursorSpecification`](CursorSpecification.md)

      Parameters:
      `visitor` - A `CursorSpecificationVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitValueCursorSpecification` method.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](ValueCursorInfoSpecification.md)
- Next Class

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
