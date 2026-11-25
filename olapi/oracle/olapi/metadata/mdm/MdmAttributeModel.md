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

- [Prev Class](MdmAttribute.md)
- [Next Class](MdmBaseAttribute.md)

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

## Class MdmAttributeModel

- oracle.olapi.metadata.mdm.MdmAttributeModel

<!-- -->

-

  ------------------------------------------------------------------------



      public class MdmAttributeModel

  An `MdmDimensionedObjectModel` that represents an `MdmAttribute`. This class is for use by an OLAP Java API application that is running in a 10*g* metadata reader mode. Do not use this class in an 11*g* application.
  Unlike an `MdmMeasureModel`, an `MdmAttributeModel` does not inherit the `Assignment` objects of the `MdmDimensionCalculationModel` for the `MdmDimension` for which the `MdmAttribute` has values.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                 | Method and Description                                                                                                                                                                                                                  |
    |---------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                                | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmAttributeModel` method of an `MdmObjectVisitor` and passes that method this `MdmAttributeModel` and an `Object`. |
    | `java.util.List`                                  | `getAutoAssignments``()`<br>Gets the `Assignment` objects that Oracle OLAP automatically creates for the `MdmAttributeModel`.                                                                                                           |
    | [`MdmAttribute`](MdmAttribute.md)                 | `getMdmAttribute``()`<br>Gets the `MdmAttribute` for the `MdmAttributeModel`.                                                                                                                                                           |
    | [`MdmDimensionedObject`](MdmDimensionedObject.md) | `getMdmDimensionedObject``()`<br>Gets the `MdmDimensionedObject` for the `MdmAttributeModel`.                                                                                                                                           |
    | `java.util.List`                                  | `getParentModels``()`<br>Gets an empty `List` because an `MdmAttributeModel` does not have any parent `MdmModel` objects.                                                                                                               |
    | `void`                                            | `setMdmAttribute``(`[`MdmAttribute`](MdmAttribute.md)` attribute)`<br>Specifies the `MdmAttribute` with which to associate the `MdmAttributeModel`.                                                                                     |

<!-- -->

- - ### Method Detail

    - #### acceptVisitor

          public java.lang.Object acceptVisitor(MdmObjectVisitor visitor,
                                                java.lang.Object context)

      Calls the `visitMdmAttributeModel` method of an `MdmObjectVisitor` and passes that method this `MdmAttributeModel` and an `Object`.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmAttributeModel` method.

    <!-- -->

    - #### getMdmAttribute

          public final MdmAttribute getMdmAttribute()

      Gets the `MdmAttribute` for the `MdmAttributeModel`.
      Returns:
      The `MdmAttribute` for the `MdmAttributeModel`.

    <!-- -->

    - #### getMdmDimensionedObject

          public final MdmDimensionedObject getMdmDimensionedObject()

      Gets the `MdmDimensionedObject` for the `MdmAttributeModel`. The `MdmDimensionedObject` for an `MdmAttributeModel` is an `MdmAttribute`.
      Returns:
      The `MdmDimensionedObject` for the `MdmAttributeModel`.

    <!-- -->

    - #### getParentModels

          public final java.util.List getParentModels()

      Gets an empty `List` because an `MdmAttributeModel` does not have any parent `MdmModel` objects.
      Specified by:
      [`getParentModels`](MdmModel.md) in class [`MdmModel`](MdmModel.md)

      Returns:
      A empty `List`.

    <!-- -->

    - #### setMdmAttribute

          public final void setMdmAttribute(MdmAttribute attribute)

      Specifies the `MdmAttribute` with which to associate the `MdmAttributeModel`.
      Parameters:
      `attribute` - The `MdmAttribute` with which to associate the `MdmAttributeModel`.

    <!-- -->

    - #### getAutoAssignments

          public java.util.List getAutoAssignments()

      Gets the `Assignment` objects that Oracle OLAP automatically creates for the `MdmAttributeModel`.
      Returns:
      A `List` of the `Assignment` objects that Oracle OLAP automatically creates for the `MdmAttributeModel`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmAttribute.md)
- [Next Class](MdmBaseAttribute.md)

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
