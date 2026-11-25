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

- [Prev Class](MdmMeasureDimension.md)
- [Next Class](MdmMember.md)

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

oracle.olapi.metadata.mdm

## Class MdmMeasureModel

- oracle.olapi.metadata.mdm.MdmMeasureModel

<!-- -->

-

  ------------------------------------------------------------------------



      public class MdmMeasureModel

  An `MdmDimensionedObjectModel` that represents an `MdmMeasure`. This class is for use by an OLAP Java API application that is running in a 10*g* metadata reader mode. Do not use this class in an 11*g* application.
  For each of the dimensions of its associated `MdmMeasure`, an `MdmMeasureModel` inherits the `Assignment` objects of the `MdmDimensionCalculationModel` of the appropriate data type.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                 | Method and Description                                                                                                                                                                                                             |
    |---------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                                | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmMeasureModel` method of an `MdmObjectVisitor` and passes that method the `MdmMeasureModel` and an `Object`. |
    | `java.util.List`                                  | `getAutoAssignments``()`<br>Gets an empty `List` because Oracle OLAP does not automatically create `Assignment` objects for an `MdmMeasureModel`.                                                                                  |
    | [`MdmDimensionedObject`](MdmDimensionedObject.md) | `getMdmDimensionedObject``()`<br>Gets the `MdmDimensionedObject` for the `MdmMeasureModel`.                                                                                                                                        |
    | [`MdmMeasure`](MdmMeasure.md)                     | `getMdmMeasure``()`<br>Gets the `MdmMeasure` for the `MdmMeasureModel`.                                                                                                                                                            |
    | `java.util.List`                                  | `getParentModels``()`<br>Gets the `MdmDimensionCalculationModel` objects that are the parent `Model` objects for the `MdmMeasureModel`.                                                                                            |
    | `void`                                            | `setMdmMeasure``(`[`MdmMeasure`](MdmMeasure.md)` measure)`<br>Specifies the `MdmMeasure` with which to associate the `MdmMeasureModel`.                                                                                            |

<!-- -->

- - ### Method Detail

    - #### acceptVisitor

          public java.lang.Object acceptVisitor(MdmObjectVisitor visitor,
                                                java.lang.Object context)

      Calls the `visitMdmMeasureModel` method of an `MdmObjectVisitor` and passes that method the `MdmMeasureModel` and an `Object`.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmMeasureModel` method.

    <!-- -->

    - #### getMdmMeasure

          public final MdmMeasure getMdmMeasure()

      Gets the `MdmMeasure` for the `MdmMeasureModel`.
      Returns:
      The `MdmMeasure` for the `MdmMeasureModel`.

    <!-- -->

    - #### getMdmDimensionedObject

          public final MdmDimensionedObject getMdmDimensionedObject()

      Gets the `MdmDimensionedObject` for the `MdmMeasureModel`. The `MdmDimensionedObject` for an `MdmMeasureModel` is an `MdmMeasure`.
      Returns:
      The `MdmDimensionedObject` for the `MdmMeasureModel`.

    <!-- -->

    - #### getAutoAssignments

          public java.util.List getAutoAssignments()

      Gets an empty `List` because Oracle OLAP does not automatically create `Assignment` objects for an `MdmMeasureModel`.
      Returns:
      A empty `List`.

    <!-- -->

    - #### getParentModels

          public final java.util.List getParentModels()

      Gets the `MdmDimensionCalculationModel` objects that are the parent `Model` objects for the `MdmMeasureModel`. The parent `Model` objects are the `MdmDimensionCalculationModel` objects of the appropriate data type of each input of the `MdmMeasureModel`. The `MdmMeasureModel` inherits the `Assignment` objects of its parent `Model` objects.
      Specified by:
      [`getParentModels`](MdmModel.md) in class [`MdmModel`](MdmModel.md)

      Returns:
      A `List` that contains one `MdmDimensionCalculationModel` of the appropriate data type for each of the dimensions of the measure for which it is the model.

    <!-- -->

    - #### setMdmMeasure

          public final void setMdmMeasure(MdmMeasure measure)

      Specifies the `MdmMeasure` with which to associate the `MdmMeasureModel`.
      Parameters:
      `measure` - The `MdmMeasure` with which to associate the `MdmMeasureModel`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmMeasureDimension.md)
- [Next Class](MdmMember.md)

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
