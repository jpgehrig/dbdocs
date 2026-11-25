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

- [Prev Class](MdmStandardDimension.md)
- [Next Class](MdmSubDimension.md)

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

## Class MdmStandardMember

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - oracle.olapi.metadata.mdm.MdmStandardMember

<!-- -->

- All Implemented Interfaces:
  [MdmMember](MdmMember.md), [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public class MdmStandardMember
      extends MdmSource
      implements MdmMember

  An object that represents a custom member of an `MdmStandardDimension`. You can create a custom member of the dimension with methods of the `MdmStandardDimension`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                 | Method and Description                                                                                                                                                                                                                   |
    |---------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                                | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmStandardMember` method of the `MdmObjectVisitor` and passes that method the `MdmStandardMember` and the `Object`. |
    | [`MdmLevel`](MdmLevel.md)                         | `getLevel``()`<br>Gets the `MdmLevel` of which the `MdmStandardMember` is a member.                                                                                                                                                      |
    | `int`                                             | `getLevelDepth``()`<br>Gets the depth in the hierarchy of the level of which the `MdmStandardMember` is a member.                                                                                                                        |
    | `java.lang.String`                                | `getLocalValue``()`<br>Gets the local value of the `MdmStandardMember`.                                                                                                                                                                  |
    | [`MdmPrimaryDimension`](MdmPrimaryDimension.md)   | `getOwnerDimension``()`<br>Gets the `MdmPrimaryDimension` of which the `MdmStandardMember` is a member.                                                                                                                                  |
    | [`MdmLevel`](MdmLevel.md)                         | `getParentLevel``()`<br>Gets the `MdmLevel` of which the parent of the `MdmStandardMember` is a member.                                                                                                                                  |
    | `java.lang.String`                                | `getParentLocalValue``()`<br>Gets the local value of the parent of the `MdmStandardMember`.                                                                                                                                              |
    | `java.lang.String`                                | `getParentValue``()`<br>Gets the unique value of the parent of the `MdmStandardMember`.                                                                                                                                                  |
    | `int`                                             | `getPrecedence``()`<br>Gets the precedence of the `MdmStandardMember`.                                                                                                                                                                   |
    | [`MdmStandardDimension`](MdmStandardDimension.md) | `getStandardDimension``()`<br>Gets the `MdmStandardDimension` of which the `MdmStandardMember` is a member.                                                                                                                              |
    | [`MetadataObject`](../MetadataObject.md)          | `getType``()`<br>Gets the type of this `MdmStandardMember`, which is the type of the `Source` for the member.                                                                                                                            |
    | `java.lang.String`                                | `getValue``()`<br>Gets the unique value of the `MdmStandardMember`.                                                                                                                                                                      |
    | [`MdmValueHierarchy`](MdmValueHierarchy.md)       | `getValueHierarchy``()`<br>Gets the `MdmValueHierarchy` of which the `MdmStandardMember` is a member.                                                                                                                                    |
    | `void`                                            | `setLevel``(`[`MdmLevel`](MdmLevel.md)` level)`<br>Specifies the `MdmLevel` to which you want to add the `MdmStandardMember` as a member.                                                                                                |
    | `void`                                            | `setParentLevel``(`[`MdmLevel`](MdmLevel.md)` parentLevel)`<br>Specifies an `MdmLevel` for the parent of the `MdmStandardMember`.                                                                                                        |
    | `void`                                            | `setParentLocalValue``(java.lang.String parentLocal)`<br>Specifies a local value for the parent of the `MdmStandardMember`.                                                                                                              |
    | `void`                                            | `setPrecedence``(int precedence)`<br>Specifies a precedence for the `MdmStandardMember`, with the higher integer value indicating a higher precedence.                                                                                   |
    | `void`                                            | `setValueHierarchy``(`[`MdmValueHierarchy`](MdmValueHierarchy.md)` valueHier)`<br>Specifies the `MdmValueHierarchy` to which you want to add the `MdmStandardMember` as a member.                                                        |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmSource](MdmSource.md)

      [`getDataType`](MdmSource.md)`, `[`getSource`](MdmSource.md)

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

    - ### Methods inherited from interface oracle.olapi.metadata.mdm.[MdmMember](MdmMember.md)

      [`getDataType`](MdmMember.md)`, `[`getDescription`](MdmMember.md)`, `[`getShortDescription`](MdmMember.md)`, `[`getSource`](MdmMember.md)

<!-- -->

- - ### Method Detail

    - #### acceptVisitor

          public java.lang.Object acceptVisitor(MdmObjectVisitor visitor,
                                                java.lang.Object context)

      Calls the `visitMdmStandardMember` method of the `MdmObjectVisitor` and passes that method the `MdmStandardMember` and the `Object`.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmStandardMember` method.

    <!-- -->

    - #### getPrecedence

          public int getPrecedence()

      Gets the precedence of the `MdmStandardMember`.
      Specified by:
      [`getPrecedence`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      An integer that specifies the precedence of the `MdmStandardMember`.

    <!-- -->

    - #### setPrecedence

          public void setPrecedence(int precedence)

      Specifies a precedence for the `MdmStandardMember`, with the higher integer value indicating a higher precedence.
      Parameters:
      `precedence` - An integer that specifies the precedence for the `MdmStandardMember`.

    <!-- -->

    - #### getOwnerDimension

          public MdmPrimaryDimension getOwnerDimension()

      Gets the `MdmPrimaryDimension` of which the `MdmStandardMember` is a member.
      Specified by:
      [`getOwnerDimension`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      The `MdmPrimaryDimension` of which the `MdmStandardMember` is a member.

    <!-- -->

    - #### getValue

          public java.lang.String getValue()

      Gets the unique value of the `MdmStandardMember`.
      Specified by:
      [`getValue`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      A `String` that contains the unique value of the `MdmStandardMember`.

    <!-- -->

    - #### getLocalValue

          public java.lang.String getLocalValue()

      Gets the local value of the `MdmStandardMember`.
      Specified by:
      [`getLocalValue`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      A `String` that contains the local value of the `MdmStandardMember`.

    <!-- -->

    - #### getLevel

          public MdmLevel getLevel()

      Gets the `MdmLevel` of which the `MdmStandardMember` is a member.
      Specified by:
      [`getLevel`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      The `MdmLevel` of which the `MdmStandardMember` is a member.

    <!-- -->

    - #### setLevel

          public void setLevel(MdmLevel level)

      Specifies the `MdmLevel` to which you want to add the `MdmStandardMember` as a member.
      Parameters:
      `level` - The `MdmLevel` to which you want to add the `MdmStandardMember` as a member.

    <!-- -->

    - #### getValueHierarchy

          public MdmValueHierarchy getValueHierarchy()

      Gets the `MdmValueHierarchy` of which the `MdmStandardMember` is a member.
      Returns:
      The `MdmValueHierarchy` of which the `MdmStandardMember` is a member.

    <!-- -->

    - #### setValueHierarchy

          public void setValueHierarchy(MdmValueHierarchy valueHier)

      Specifies the `MdmValueHierarchy` to which you want to add the `MdmStandardMember` as a member.
      Parameters:
      `valueHier` - The `MdmValueHierarchy` to which you want to add the `MdmStandardMember` as a member.

    <!-- -->

    - #### getLevelDepth

          public int getLevelDepth()

      Gets the depth in the hierarchy of the level of which the `MdmStandardMember` is a member.
      Specified by:
      [`getLevelDepth`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      An integer that identifies the depth in the hierarchy of the level of which the `MdmStandardMember` is a member.

    <!-- -->

    - #### getParentValue

          public java.lang.String getParentValue()

      Gets the unique value of the parent of the `MdmStandardMember`.
      Specified by:
      [`getParentValue`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      A `String` that contains the unique value of the parent of the `MdmStandardMember`.

    <!-- -->

    - #### getParentLocalValue

          public java.lang.String getParentLocalValue()

      Gets the local value of the parent of the `MdmStandardMember`.
      Specified by:
      [`getParentLocalValue`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      A `String` that contains the local value of the parent of the `MdmStandardMember`.

    <!-- -->

    - #### setParentLocalValue

          public void setParentLocalValue(java.lang.String parentLocal)

      Specifies a local value for the parent of the `MdmStandardMember`.
      Parameters:
      `parentLocal` - A `String` that contains the local value that you want the parent of the `MdmStandardMember` to have.

    <!-- -->

    - #### getParentLevel

          public MdmLevel getParentLevel()

      Gets the `MdmLevel` of which the parent of the `MdmStandardMember` is a member.
      Specified by:
      [`getParentLevel`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      The `MdmLevel` of which the parent of the `MdmStandardMember` is a member.

    <!-- -->

    - #### setParentLevel

          public void setParentLevel(MdmLevel parentLevel)

      Specifies an `MdmLevel` for the parent of the `MdmStandardMember`.
      Parameters:
      `parentLevel` - The `MdmLevel` that you want to specify for the parent of the `MdmStandardMember`.

    <!-- -->

    - #### getStandardDimension

          public final MdmStandardDimension getStandardDimension()

      Gets the `MdmStandardDimension` of which the `MdmStandardMember` is a member.
      Returns:
      The `MdmStandardDimension` of which the `MdmStandardMember` is a member.

    <!-- -->

    - #### getType

          public MetadataObject getType()

      Gets the type of this `MdmStandardMember`, which is the type of the `Source` for the member.
      Specified by:
      [`getType`](MdmSource.md) in class [`MdmSource`](MdmSource.md)

      Returns:
      A `MetadataObject` that represents the type of this custom dimension member.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmStandardDimension.md)
- [Next Class](MdmSubDimension.md)

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
