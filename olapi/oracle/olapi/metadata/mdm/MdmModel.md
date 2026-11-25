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

- [Prev Class](MdmMetadataProvider.md)
- [Next Class](MdmMultiValuedAttribute.md)

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

## Class MdmModel

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - oracle.olapi.metadata.mdm.MdmModel

<!-- -->

- All Implemented Interfaces:
  [Model](../../data/source/Model.md), [MetadataObject](../MetadataObject.md)

  <!-- -->

  Direct Known Subclasses:
  [MdmDimensionCalculationModel](MdmDimensionCalculationModel.md)

  ------------------------------------------------------------------------



      public abstract class MdmModel
      extends MdmObject
      implements Model

  A `Model` that assigns values for `MdmDimension` members. The values and the `MdmDimension` members are specified by the `MdmAssignment` objects of the `MdmModel`. Each `MdmAssignment` contains an `Expression` that specifies the value to use for the dimension member that is associated with the `MdmAssignment`.
  When an `MdmModel` is an instance of an `MdmDimensionCalculationModel` for an `MdmPrimaryDimension`, it persists on the server. You can use it in a `ModelCommand` in a build process or in a `ConsistentSolveSpecification` for an `MdmCube`.

  See Also:
  [`MdmAssignment`](MdmAssignment.md), [`AggregationFunctionExpression`](../../syntax/AggregationFunctionExpression.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                         |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `MdmModel``(`[`MdmMetadataProvider`](MdmMetadataProvider.md)` metadataProvider)`<br>Creates an `MdmModel` for MDM metadata objects provided by the specified `MdmMetadataProvider`. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                  | Method and Description                                                                                                                                                                                                                               |
    |----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`MdmAssignment`](MdmAssignment.md)                | `assign``(java.lang.String lhs, `[`Expression`](../../syntax/Expression.md)` rhs)`<br>Gets the existing `MdmAssignment`, or creates a new one, for a dimension member and assigns the value of the `Expression` as the measure value for the member. |
    | [`MdmAssignment`](MdmAssignment.md)                | `findAssignment``(java.lang.String lhs)`<br>Gets the existing `MdmAssignment` for a dimension member.                                                                                                                                                |
    | [`MdmAssignment`](MdmAssignment.md)                | `findOrCreateAssignment``(java.lang.String lhs)`<br>Gets the existing `MdmAssignment`, or creates a new one, for a dimension member.                                                                                                                 |
    | `int`                                              | `getDefaultPrecedence``()`<br>Gets the default precedence value for the `MdmModel`.                                                                                                                                                                  |
    | `abstract java.util.List`                          | `getInputs``()`<br>Gets the `Source` objects that are the inputs of the `MdmModel`.                                                                                                                                                                  |
    | `java.util.List`                                   | `getMdmAssignments``()`<br>Gets the `MdmAssignment` objects that are associated with this `MdmModel`.                                                                                                                                                |
    | `abstract `[`MdmSource`](MdmSource.md)             | `getMdmSource``()`<br>Gets the `MdmSource` for the `MdmModel`.                                                                                                                                                                                       |
    | `java.util.List`                                   | `getOutputs``()`<br>Returns an empty `List` because an `MdmModel` does not have outputs.                                                                                                                                                             |
    | `abstract java.util.List`                          | `getParentModels``()`<br>Gets the `MdmModel` objects that are the parents of the `MdmModel`.                                                                                                                                                         |
    | `abstract `[`Source`](../../data/source/Source.md) | `getType``()`<br>Gets the `Source` that is the type of the `MdmModel`.                                                                                                                                                                               |
    | `void`                                             | `removeMdmAssignment``(`[`MdmAssignment`](MdmAssignment.md)` assignment)`<br>Deletes the specified `MdmAssignment` from the list of `MdmAssignment` objects that are associated with this `MdmModel`.                                                |
    | `void`                                             | `setDefaultPrecedence``(int precedence)`<br>Specifies the default precedence, which is the precedence value for `Assignment` objects that are created by methods that do not specify a value.                                                        |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmObject](MdmObject.md)

      [`acceptVisitor`](MdmObject.md)`, `[`addDescription`](MdmObject.md)`, `[`addObjectClassification`](MdmObject.md)`, `[`findOrCreateDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescriptions`](MdmObject.md)`, `[`getMetadataProvider`](MdmObject.md)`, `[`getObjectClassifications`](MdmObject.md)`, `[`getShortDescription`](MdmObject.md)`, `[`isClassifiedAs`](MdmObject.md)`, `[`removeDescription`](MdmObject.md)`, `[`removeObjectClassification`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setName`](MdmObject.md)`, `[`setShortDescription`](MdmObject.md)

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

- - ### Constructor Detail

    - #### MdmModel

          public MdmModel(MdmMetadataProvider metadataProvider)

      Creates an `MdmModel` for MDM metadata objects provided by the specified `MdmMetadataProvider`.
      Parameters:
      `metadataProvider` - The `MdmMetadataProvider` to use in creating the `MdmModel`.

  <!-- -->

  - ### Method Detail

    - #### getMdmSource

          public abstract MdmSource getMdmSource()

      Gets the `MdmSource` for the `MdmModel`.
      Returns:
      The `MdmSource` for the `MdmModel`.

    <!-- -->

    - #### getType

          public abstract Source getType()

      Gets the `Source` that is the type of the `MdmModel`.
      Specified by:
      [`getType`](../../data/source/Model.md) in interface [`Model`](../../data/source/Model.md)

      Returns:
      The `Source` that is the type of the `MdmModel`.

    <!-- -->

    - #### getInputs

          public abstract java.util.List getInputs()

      Gets the `Source` objects that are the inputs of the `MdmModel`.
      Specified by:
      [`getInputs`](../../data/source/Model.md) in interface [`Model`](../../data/source/Model.md)

      Returns:
      A `List` of the `Source` objects that are the inputs of the `MdmModel`.

    <!-- -->

    - #### getOutputs

          public final java.util.List getOutputs()

      Returns an empty `List` because an `MdmModel` does not have outputs. A `CustomModel` can have outputs.
      Specified by:
      [`getOutputs`](../../data/source/Model.md) in interface [`Model`](../../data/source/Model.md)

      Returns:
      An empty `List`.

    <!-- -->

    - #### getParentModels

          public abstract java.util.List getParentModels()

      Gets the `MdmModel` objects that are the parents of the `MdmModel`.
      Specified by:
      [`getParentModels`](../../data/source/Model.md) in interface [`Model`](../../data/source/Model.md)

      Returns:
      A `List` of the `MdmModel` objects that are the parents of the `MdmModel`.

    <!-- -->

    - #### getDefaultPrecedence

          public int getDefaultPrecedence()

      Gets the default precedence value for the `MdmModel`.
      Specified by:
      [`getDefaultPrecedence`](../../data/source/Model.md) in interface [`Model`](../../data/source/Model.md)

      Returns:
      An integer that represents the precedence for `Assignment` objects that are created by methods that do not specify a precedence value.

    <!-- -->

    - #### setDefaultPrecedence

          public void setDefaultPrecedence(int precedence)

      Specifies the default precedence, which is the precedence value for `Assignment` objects that are created by methods that do not specify a value.
      Specified by:
      [`setDefaultPrecedence`](../../data/source/Model.md) in interface [`Model`](../../data/source/Model.md)

      Parameters:
      `precedence` - The integer value to set as the default precedence.

    <!-- -->

    - #### findAssignment

          public final MdmAssignment findAssignment(java.lang.String lhs)

      Gets the existing `MdmAssignment` for a dimension member.
      Parameters:
      `lhs` - A `String` that contains the local value of the dimension member for the assignment.

      Returns:
      The `MdmAssignment` for the specified dimension member or `null` if no assignment exists for the member.

    <!-- -->

    - #### findOrCreateAssignment

          public final MdmAssignment findOrCreateAssignment(java.lang.String lhs)

      Gets the existing `MdmAssignment`, or creates a new one, for a dimension member.
      Parameters:
      `lhs` - A `String` that contains the local value of the dimension member for the assignment.

      Returns:
      The specified `MdmAssignment` or a new `MdmAssignment`.

    <!-- -->

    - #### assign

          public final MdmAssignment assign(java.lang.String lhs,
                                            Expression rhs)

      Gets the existing `MdmAssignment`, or creates a new one, for a dimension member and assigns the value of the `Expression` as the measure value for the member.
      Parameters:
      `lhs` - A `String` that contains the local value of the dimension member for the assignment.

      `rhs` - An `Expression` that specifies the value to assign to a measure for the member.

      Returns:
      An `MdmAssignment` that represents the assigment of a value to a measure for a dimension member.

    <!-- -->

    - #### removeMdmAssignment

          public final void removeMdmAssignment(MdmAssignment assignment)

      Deletes the specified `MdmAssignment` from the list of `MdmAssignment` objects that are associated with this `MdmModel`.
      Parameters:
      `assignment` - The `MdmAssignment` to remove.

    <!-- -->

    - #### getMdmAssignments

          public final java.util.List getMdmAssignments()

      Gets the `MdmAssignment` objects that are associated with this `MdmModel`.
      Returns:
      A `List` of the `MdmAssignment` objects of this `MdmModel`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmMetadataProvider.md)
- [Next Class](MdmMultiValuedAttribute.md)

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
