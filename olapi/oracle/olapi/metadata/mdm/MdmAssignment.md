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

- [Prev Class](Mdm11_ObjectVisitor.md)
- [Next Class](MdmAttribute.md)

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

## Class MdmAssignment

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - oracle.olapi.metadata.mdm.MdmAssignment

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public class MdmAssignment
      extends MdmObject

  An object that represents an expression, the value of which is assigned as a measure value for a dimension member as specified by an `MdmModel`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                          | Method and Description                                                                                                                                                                                                           |
    |--------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                         | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmAssignment` method of the `MdmObjectVisitor` and passes that method this `MdmAssignment` and an `Object`. |
    | [`MdmCustomMember`](MdmCustomMember.md)    | `getCustomMember``()`<br>Gets the `MdmCustomMember` that is associated with this `MdmAssignment`.                                                                                                                                |
    | [`MdmModel`](MdmModel.md)                  | `getMdmModel``()`<br>Gets the `MdmModel` that owns this `MdmAssignment`.                                                                                                                                                         |
    | [`Expression`](../../syntax/Expression.md) | `getMemberExpression``()`<br>Gets the `Expression` specified by this `MdmAssignment`.                                                                                                                                            |
    | `void`                                     | `setCustomMember``(`[`MdmCustomMember`](MdmCustomMember.md)` member)`<br>Specifies an `MdmCustomMember` to associate with this `MdmAssignment`.                                                                                  |
    | `void`                                     | `setMemberExpression``(`[`Expression`](../../syntax/Expression.md)` exp)`<br>Specifies an `Expression` for this `MdmAssignment`.                                                                                                 |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmObject](MdmObject.md)

      [`addDescription`](MdmObject.md)`, `[`addObjectClassification`](MdmObject.md)`, `[`findOrCreateDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescriptions`](MdmObject.md)`, `[`getMetadataProvider`](MdmObject.md)`, `[`getObjectClassifications`](MdmObject.md)`, `[`getShortDescription`](MdmObject.md)`, `[`isClassifiedAs`](MdmObject.md)`, `[`removeDescription`](MdmObject.md)`, `[`removeObjectClassification`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setName`](MdmObject.md)`, `[`setShortDescription`](MdmObject.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getName`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getMdmModel

          public MdmModel getMdmModel()

      Gets the `MdmModel` that owns this `MdmAssignment`.
      Returns:
      The `MdmModel` that owns this `MdmAssignment`.

    <!-- -->

    - #### getMemberExpression

          public Expression getMemberExpression()

      Gets the `Expression` specified by this `MdmAssignment`.
      Returns:
      The `Expression` specified by this `MdmAssignment`.

    <!-- -->

    - #### setMemberExpression

          public void setMemberExpression(Expression exp)

      Specifies an `Expression` for this `MdmAssignment`.
      Parameters:
      `exp` - The `Expression` for this `MdmAssignment`.

    <!-- -->

    - #### getCustomMember

          public MdmCustomMember getCustomMember()

      Gets the `MdmCustomMember` that is associated with this `MdmAssignment`.
      Returns:
      The `MdmCustomMember` associated with this `MdmAssignment`.

    <!-- -->

    - #### setCustomMember

          public void setCustomMember(MdmCustomMember member)

      Specifies an `MdmCustomMember` to associate with this `MdmAssignment`.
      Parameters:
      `member` - The `MdmCustomMember` for this `MdmAssignment`.

    <!-- -->

    - #### acceptVisitor

          public java.lang.Object acceptVisitor(MdmObjectVisitor visitor,
                                                java.lang.Object context)

      Calls the `visitMdmAssignment` method of the `MdmObjectVisitor` and passes that method this `MdmAssignment` and an `Object`.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor` that implements the `Mdm11_ObjectVisitor` interface.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmAssignment` method.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](Mdm11_ObjectVisitor.md)
- [Next Class](MdmAttribute.md)

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
