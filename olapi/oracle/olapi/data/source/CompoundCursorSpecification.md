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

- [Prev Class](CompoundCursorInfoSpecification.md)
- [Next Class](CursorInfoSpecification.md)

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

## Class CompoundCursorSpecification

- java.lang.Object

- - [oracle.olapi.data.source.CursorSpecification](CursorSpecification.md)

  - - oracle.olapi.data.source.CompoundCursorSpecification

<!-- -->

- All Implemented Interfaces:
  [CompoundCursorInfoSpecification](CompoundCursorInfoSpecification.md), [CursorInfoSpecification](CursorInfoSpecification.md)

  ------------------------------------------------------------------------



      public final class CompoundCursorSpecification
      extends CursorSpecification
      implements CompoundCursorInfoSpecification

  A `CursorSpecification` for a `Source` that has one or more outputs. A `CompoundCursorSpecification` has child `CursorSpecification` objects. It always has a base `ValueCursorSpecification` for the values of the elements of the `Source`. It also has a `CursorSpecification` for each of the outputs of the `Source`. With methods of a `CompoundCursorSpecification`, an application can get its base `ValueCursorSpecification` and the outputs.
  With other methods, an application can accept a `CursorSpecificationVisitor` or specify that the default fetch size be set on the children of the `CompoundCursorSpecification`. The fetch size is the number of elements that a `Cursor` retrieves during a single fetch from the data store. If a `CursorSpecification` is set to specify the fetch size for a `Cursor`, then an application can specify the value of the fetch size by calling the `setFetchSize` method on the `Cursor`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                 | Method and Description                                                                                                                                                                                                                                                                                                  |
    |-------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                                                | `acceptVisitor``(`[`CursorSpecificationVisitor`](CursorSpecificationVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitCompoundCursorSpecification` method of the specified `CursorSpecificationVisitor` and passes that method this `CompoundCursorSpecification` and the specified `context` object. |
    | `java.util.List`                                                  | `getOutputs``()`<br>Gets a `List` whose values are the outputs of this `CompoundCursorSpecification`.                                                                                                                                                                                                                   |
    | [`ValueCursorInfoSpecification`](ValueCursorInfoSpecification.md) | `getValue``()`<br>Gets the `ValueCursorSpecification` for this `CompoundCursorSpecification`.                                                                                                                                                                                                                           |
    | [`ValueCursorSpecification`](ValueCursorSpecification.md)         | `getValueCursorSpecification``()`<br>Gets the base `ValueCursorSpecification`, which is the `CursorSpecification` for the base `ValueCursor`, which has the values of the `Source` for the `CompoundCursorSpecification`.                                                                                               |
    | `void`                                                            | `specifyDefaultFetchSizeOnChildren``()`<br>Specifies that the default fetch size be set on the child `CursorSpecification` objects of the `CompoundCursorSpecification`.                                                                                                                                                |
    | `void`                                                            | `specifyDefaultFetchSizeOnChildren``(int defaultFetchSize)`<br>Specifies that the default fetch size be set on the child `CursorSpecification` objects of the `CompoundCursorSpecification` and supplies an initial value for the fetch size.                                                                           |

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

      Calls the `visitCompoundCursorSpecification` method of the specified `CursorSpecificationVisitor` and passes that method this `CompoundCursorSpecification` and the specified `context` object.
      Specified by:
      [`acceptVisitor`](CursorSpecification.md) in class [`CursorSpecification`](CursorSpecification.md)

      Parameters:
      `visitor` - A `CursorSpecificationVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitCompoundCursorSpecification` method.

    <!-- -->

    - #### getOutputs

          public final java.util.List getOutputs()

      Gets a `List` whose values are the outputs of this `CompoundCursorSpecification`.
      Specified by:
      [`getOutputs`](CompoundCursorInfoSpecification.md) in interface [`CompoundCursorInfoSpecification`](CompoundCursorInfoSpecification.md)

      Returns:
      A `List` with the outputs of the `CompoundCursorSpecification`.

    <!-- -->

    - #### getValueCursorSpecification

          public final ValueCursorSpecification getValueCursorSpecification()

      Gets the base `ValueCursorSpecification`, which is the `CursorSpecification` for the base `ValueCursor`, which has the values of the `Source` for the `CompoundCursorSpecification`.
      Returns:
      The base `ValueCursorSpecification` for the `CompoundCursorSpecification`.

    <!-- -->

    - #### getValue

          public final ValueCursorInfoSpecification getValue()

      Gets the `ValueCursorSpecification` for this `CompoundCursorSpecification`.
      Specified by:
      [`getValue`](CompoundCursorInfoSpecification.md) in interface [`CompoundCursorInfoSpecification`](CompoundCursorInfoSpecification.md)

      Returns:
      The `ValueCursorSpecification` for this `CompoundCursorSpecification`.

    <!-- -->

    - #### specifyDefaultFetchSizeOnChildren

          public final void specifyDefaultFetchSizeOnChildren()

      Specifies that the default fetch size be set on the child `CursorSpecification` objects of the `CompoundCursorSpecification`.

    <!-- -->

    - #### specifyDefaultFetchSizeOnChildren

          public final void specifyDefaultFetchSizeOnChildren(int defaultFetchSize)

      Specifies that the default fetch size be set on the child `CursorSpecification` objects of the `CompoundCursorSpecification` and supplies an initial value for the fetch size.
      Parameters:
      `defaultFetchSize` - The initial fetch size to set for the child `CursorSpecification` objects.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](CompoundCursorInfoSpecification.md)
- [Next Class](CursorInfoSpecification.md)

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
