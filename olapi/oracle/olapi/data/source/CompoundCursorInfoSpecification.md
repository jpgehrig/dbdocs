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

- [Prev Class](BuildWarningsException.md)
- [Next Class](CompoundCursorSpecification.md)

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

## Interface CompoundCursorInfoSpecification

- All Superinterfaces:
  [CursorInfoSpecification](CursorInfoSpecification.md)

  <!-- -->

  All Known Implementing Classes:
  [CompoundCursorSpecification](CompoundCursorSpecification.md)

  ------------------------------------------------------------------------



      public interface CompoundCursorInfoSpecification
      extends CursorInfoSpecification

  A `CursorInfoSpecification` for a `Cursor` for a `Source` that has one or more outputs.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                 | Method and Description                                                                                                                                                                                             |
    |-------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.util.List`                                                  | `getOutputs``()`<br>Gets a `List` whose values are the outputs of this `CompoundCursorInfoSpecification`.                                                                                                          |
    | [`ValueCursorInfoSpecification`](ValueCursorInfoSpecification.md) | `getValue``()`<br>Gets the base `ValueCursorInfoSpecification`, which is the `CursorInfoSpecification` for the base `ValueCursor`, which has the values of the `Source` for the `CompoundCursorInfoSpecification`. |

    - ### Methods inherited from interface oracle.olapi.data.source.[CursorInfoSpecification](CursorInfoSpecification.md)

      [`getSource`](CursorInfoSpecification.md)`, `[`isParentEndCalculationSpecified`](CursorInfoSpecification.md)`, `[`isParentStartCalculationSpecified`](CursorInfoSpecification.md)`, `[`setParentEndCalculationSpecified`](CursorInfoSpecification.md)`, `[`setParentStartCalculationSpecified`](CursorInfoSpecification.md)

<!-- -->

- - ### Method Detail

    - #### getOutputs

          java.util.List getOutputs()

      Gets a `List` whose values are the outputs of this `CompoundCursorInfoSpecification`.
      Returns:
      A `List` with the outputs of the `CompoundCursorInfoSpecification`.

    <!-- -->

    - #### getValue

          ValueCursorInfoSpecification getValue()

      Gets the base `ValueCursorInfoSpecification`, which is the `CursorInfoSpecification` for the base `ValueCursor`, which has the values of the `Source` for the `CompoundCursorInfoSpecification`.
      Returns:
      The base `ValueCursorInfoSpecification` for the `CompoundCursorInfoSpecification`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](BuildWarningsException.md)
- [Next Class](CompoundCursorSpecification.md)

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
