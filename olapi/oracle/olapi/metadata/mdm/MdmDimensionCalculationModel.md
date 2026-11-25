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

- [Prev Class](MdmDimensionality.md)
- [Next Class](MdmDimensionedObject.md)

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

## Class MdmDimensionCalculationModel

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmModel](MdmModel.md)

        - - oracle.olapi.metadata.mdm.MdmDimensionCalculationModel

<!-- -->

- All Implemented Interfaces:
  [Model](../../data/source/Model.md), [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public class MdmDimensionCalculationModel
      extends MdmModel

  An `MdmModel` that is associated with an `MdmPrimaryDimension`. Each `MdmAssignment` of the `MdmDimensionCalculationModel` has an expression that determines the values to associate with various dimension members. You can get or create an `MdmDimensionCalculationModel` by calling the [`findOrCreateDimCalcModel`](MdmPrimaryDimension.md) method of an `MdmPrimaryDimension`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                             | Method and Description                                                                                                                                                                                                                                         |
    |-------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                                                            | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmDimensionCalculationModel` method of the `MdmObjectVisitor` and passes that method this `MdmDimensionCalculationModel` and an `Object`. |
    | [`MdmAssignment`](MdmAssignment.md)                                           | `addCustomMember``(`[`MdmCustomMember`](MdmCustomMember.md)` member)`<br>Adds a custom dimension member to this `MdmDimensionCalculationModel`.                                                                                                                |
    | `void`                                                                        | `addExplicitDimension``(`[`MdmPrimaryDimension`](MdmPrimaryDimension.md)` dim)`<br>Adds an `MdmPrimaryDimension` to the list of explicit dimensions of the `MdmDimensionCalculationModel`.                                                                     |
    | `java.util.List`                                                              | `getAutoAssignments``()`<br>Gets the `Assignment` objects that Oracle OLAP automatically creates for the `MdmDimensionCalculationModel`.                                                                                                                       |
    | [`FundamentalMetadataObject`](../../data/source/FundamentalMetadataObject.md) | `getDataType``()`<br>Gets the `FundamentalMetadataObject` that represents the data type of the `MdmDimensionCalculationModel`.                                                                                                                                 |
    | `java.util.List`                                                              | `getExplicitDimensions``()`<br>Gets the `MdmPrimaryDimension` objects that are the explicit dimensions of the `MdmDimensionCalculationModel`.                                                                                                                  |
    | `java.lang.String`                                                            | `getIncludedAWModel``()`<br>Gets the name of the included OLAP DML analytic workspace model.                                                                                                                                                                   |
    | `java.util.List`                                                              | `getInputs``()`<br>Gets an empty `List` because an `MdmDimensionCalculationModel` does not have inputs.                                                                                                                                                        |
    | [`MdmPrimaryDimension`](MdmPrimaryDimension.md)                               | `getMdmDimension``()`<br>Gets the `MdmPrimaryDimension` for the `MdmDimensionCalculationModel`.                                                                                                                                                                |
    | [`MdmSource`](MdmSource.md)                                                   | `getMdmSource``()`<br>Gets the `MdmSource` for the `MdmDimensionCalculationModel`.                                                                                                                                                                             |
    | `java.util.List`                                                              | `getParentModels``()`<br>Gets an empty `List` because an `MdmDimensionCalculationModel` does not have any parent `MdmModel` objects.                                                                                                                           |
    | [`Source`](../../data/source/Source.md)                                       | `getType``()`<br>Gets the `Source` that represents the type of the `MdmDimensionCalculationModel`.                                                                                                                                                             |
    | `void`                                                                        | `removeExplicitDimension``(`[`MdmPrimaryDimension`](MdmPrimaryDimension.md)` dim)`<br>Removes an `MdmPrimaryDimension` from the explicit dimensions of the `MdmDimensionCalculationModel`.                                                                     |
    | `void`                                                                        | `setIncludedAWModel``(java.lang.String modelName)`<br>Specifies the name of the OLAP DML model to include in this `MdmDimensionCalculationModel`.                                                                                                              |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmModel](MdmModel.md)

      [`assign`](MdmModel.md)`, `[`findAssignment`](MdmModel.md)`, `[`findOrCreateAssignment`](MdmModel.md)`, `[`getDefaultPrecedence`](MdmModel.md)`, `[`getMdmAssignments`](MdmModel.md)`, `[`getOutputs`](MdmModel.md)`, `[`removeMdmAssignment`](MdmModel.md)`, `[`setDefaultPrecedence`](MdmModel.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmObject](MdmObject.md)

      [`addDescription`](MdmObject.md)`, `[`addObjectClassification`](MdmObject.md)`, `[`findOrCreateDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescriptions`](MdmObject.md)`, `[`getMetadataProvider`](MdmObject.md)`, `[`getObjectClassifications`](MdmObject.md)`, `[`getShortDescription`](MdmObject.md)`, `[`isClassifiedAs`](MdmObject.md)`, `[`removeDescription`](MdmObject.md)`, `[`removeObjectClassification`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setName`](MdmObject.md)`, `[`setShortDescription`](MdmObject.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getName`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.olapi.data.source.[Model](../../data/source/Model.md)

      [`assign`](../../data/source/Model.md)`, `[`assign`](../../data/source/Model.md)`, `[`assign`](../../data/source/Model.md)`, `[`assign`](../../data/source/Model.md)`, `[`assign`](../../data/source/Model.md)`, `[`assign`](../../data/source/Model.md)`, `[`createSolvedSource`](../../data/source/Model.md)`, `[`createSolvedSource`](../../data/source/Model.md)`, `[`getAssignments`](../../data/source/Model.md)`, `[`unassign`](../../data/source/Model.md)

<!-- -->

- - ### Method Detail

    - #### acceptVisitor

          public java.lang.Object acceptVisitor(MdmObjectVisitor visitor,
                                                java.lang.Object context)

      Calls the `visitMdmDimensionCalculationModel` method of the `MdmObjectVisitor` and passes that method this `MdmDimensionCalculationModel` and an `Object`.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmDimensionCalculationModel` method.

    <!-- -->

    - #### getMdmDimension

          public final MdmPrimaryDimension getMdmDimension()

      Gets the `MdmPrimaryDimension` for the `MdmDimensionCalculationModel`.
      Returns:
      The `MdmPrimaryDimension` for the `MdmDimensionCalculationModel`.

    <!-- -->

    - #### getMdmSource

          public final MdmSource getMdmSource()

      Gets the `MdmSource` for the `MdmDimensionCalculationModel`. The `MdmSource` for an `MdmDimensionCalculationModel` is an `MdmPrimaryDimension`.
      Specified by:
      [`getMdmSource`](MdmModel.md) in class [`MdmModel`](MdmModel.md)

      Returns:
      The `MdmSource` for the `MdmDimensionCalculationModel`.

    <!-- -->

    - #### getDataType

          public final FundamentalMetadataObject getDataType()

      Gets the `FundamentalMetadataObject` that represents the data type of the `MdmDimensionCalculationModel`.
      Returns:
      The `FundamentalMetadataObject` that represents the data type of `MdmDimensionCalculationModel`.

    <!-- -->

    - #### getType

          public final Source getType()

      Gets the `Source` that represents the type of the `MdmDimensionCalculationModel`.
      Specified by:
      [`getType`](../../data/source/Model.md) in interface [`Model`](../../data/source/Model.md)

      Specified by:
      [`getType`](MdmModel.md) in class [`MdmModel`](MdmModel.md)

      Returns:
      The `Source` that represents the type of `MdmDimensionCalculationModel`.

    <!-- -->

    - #### getInputs

          public final java.util.List getInputs()

      Gets an empty `List` because an `MdmDimensionCalculationModel` does not have inputs.
      Specified by:
      [`getInputs`](../../data/source/Model.md) in interface [`Model`](../../data/source/Model.md)

      Specified by:
      [`getInputs`](MdmModel.md) in class [`MdmModel`](MdmModel.md)

      Returns:
      An empty `List`.

    <!-- -->

    - #### getParentModels

          public final java.util.List getParentModels()

      Gets an empty `List` because an `MdmDimensionCalculationModel` does not have any parent `MdmModel` objects.
      Specified by:
      [`getParentModels`](../../data/source/Model.md) in interface [`Model`](../../data/source/Model.md)

      Specified by:
      [`getParentModels`](MdmModel.md) in class [`MdmModel`](MdmModel.md)

      Returns:
      An empty `List`.

    <!-- -->

    - #### getAutoAssignments

          public java.util.List getAutoAssignments()

      Gets the `Assignment` objects that Oracle OLAP automatically creates for the `MdmDimensionCalculationModel`. When you create a custom dimension member, Oracle OLAP automatically creates an `Assignment` of the appropriate data type.
      Returns:
      A `List` of the `Assignment` objects that Oracle OLAP automatically creates for the `MdmDimensionCalculationModel`.

    <!-- -->

    - #### addCustomMember

          public MdmAssignment addCustomMember(MdmCustomMember member)

      Adds a custom dimension member to this `MdmDimensionCalculationModel`.
      Parameters:
      `member` - The `MdmCustomMember` to add to the model.

      Returns:
      An `MdmAssignment` for the custom member.

    <!-- -->

    - #### getExplicitDimensions

          public final java.util.List getExplicitDimensions()

      Gets the `MdmPrimaryDimension` objects that are the explicit dimensions of the `MdmDimensionCalculationModel`. Assignments in an `MdmDimensionCalculationModel` can depend only on the explicit dimensions and on the owning dimension, which is returned by `getMdmDimension`) method.
      Returns:
      A `List` of the explicit `MdmPrimaryDimension` objects of the `MdmDimensionCalculationModel`.

    <!-- -->

    - #### addExplicitDimension

          public final void addExplicitDimension(MdmPrimaryDimension dim)

      Adds an `MdmPrimaryDimension` to the list of explicit dimensions of the `MdmDimensionCalculationModel`. Assignments in an `MdmDimensionCalculationModel` can depend only on the explicit dimensions and on the owning dimension, which is returned by `getMdmDimension`) method.
      Parameters:
      `dim` - The `MdmPrimaryDimension` to add to the `MdmDimensionCalculationModel`.

    <!-- -->

    - #### removeExplicitDimension

          public final void removeExplicitDimension(MdmPrimaryDimension dim)

      Removes an `MdmPrimaryDimension` from the explicit dimensions of the `MdmDimensionCalculationModel`. Assignments in an `MdmDimensionCalculationModel` can depend only on the explicit dimensions and on the owning dimension, which is returned by the `getMdmDimension` method.
      Parameters:
      `dim` - The `MdmPrimaryDimension` to remove from the `MdmDimensionCalculationModel`.

    <!-- -->

    - #### getIncludedAWModel

          public final java.lang.String getIncludedAWModel()

      Gets the name of the included OLAP DML analytic workspace model.
      Returns:
      A `String` that contains the name of the included OLAP DML analytic workspace model.

    <!-- -->

    - #### setIncludedAWModel

          public final void setIncludedAWModel(java.lang.String modelName)

      Specifies the name of the OLAP DML model to include in this `MdmDimensionCalculationModel`. Oracle OLAP uses the included model whenever it uses this `MdmDimensionCalculationModel`, such as when this `MdmDimensionCalculationModel` is contained by a `ModelCommand` in a `ConsistentSolveSpecification` for an `MdmCube`.
      The OLAP DML model is one that a user has created, using Analytic Workspace Manager or other method, such as the `BUILD` procedure of the PL/SQL `DBMS_CUBE` program. The OLAP DML model can include any sort of assignment statements that the user wants. With the included model, the user can do more complex OLAP DML model customizations than are otherwise available through the OLAP Java API.

      This method causes Oracle OLAP to issue an `INCLUDE` statement to an OLAP DML `MODEL` command to the analytic workspace model that this `MdmDimensionCalculationModel` represents. For more information on using OLAP DML commands, see *Oracle OLAP User's Guide* and *Oracle OLAP DML Reference*.

      Parameters:
      `modelName` - A `String` that contains the name of an OLAP DML model.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmDimensionality.md)
- [Next Class](MdmDimensionedObject.md)

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
