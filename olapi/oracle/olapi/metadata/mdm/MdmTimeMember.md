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

- [Prev Class](MdmTimeDimension.md)
- [Next Class](MdmValueHierarchy.md)

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

## Class MdmTimeMember

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - oracle.olapi.metadata.mdm.MdmTimeMember

<!-- -->

- All Implemented Interfaces:
  [MdmMember](MdmMember.md), [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public class MdmTimeMember
      extends MdmSource
      implements MdmMember

  An object that represents a custom member of an `MdmTimeDimension`. You can create a custom member of the dimension with methods of an `MdmCustomObjectFactory` or with the convenience methods of an `MdmTimeDimension`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                                                                                                                                                                                          |
    |-------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                              | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmTimeMember` method of the `MdmObjectVisitor` and passes that method the `MdmTimeMember` and an `Object`. |
    | `java.util.Date`                                | `getEndDate``()`<br>Gets the end date of the time period that the `MdmTimeMember` represents.                                                                                                                                   |
    | [`MdmLevel`](MdmLevel.md)                       | `getLevel``()`<br>Gets the `MdmLevel` of which the `MdmTimeMember` is a member.                                                                                                                                                 |
    | `int`                                           | `getLevelDepth``()`<br>Gets the depth in the hierarchy of the level of which the `MdmTimeMember` is a member.                                                                                                                   |
    | `java.lang.String`                              | `getLocalValue``()`<br>Gets the local value of the `MdmTimeMember`.                                                                                                                                                             |
    | [`MdmPrimaryDimension`](MdmPrimaryDimension.md) | `getOwnerDimension``()`<br>Gets the `MdmPrimaryDimension` of which the `MdmTimeMember` is a member.                                                                                                                             |
    | [`MdmLevel`](MdmLevel.md)                       | `getParentLevel``()`<br>Gets the `MdmLevel` of which the parent of the `MdmTimeMember` is a member.                                                                                                                             |
    | `java.lang.String`                              | `getParentLocalValue``()`<br>Gets the local value of the parent of the `MdmTimeMember`.                                                                                                                                         |
    | `java.lang.String`                              | `getParentValue``()`<br>Gets the unique value of the parent of the `MdmTimeMember`.                                                                                                                                             |
    | `int`                                           | `getPrecedence``()`<br>Gets the precedence of the `MdmTimeMember`.                                                                                                                                                              |
    | [`MdmTimeDimension`](MdmTimeDimension.md)       | `getTimeDimension``()`<br>Gets the `MdmTimeDimension` of which the `MdmTimeMember` is a member.                                                                                                                                 |
    | `int`                                           | `getTimeSpan``()`<br>Gets the number of time periods that is the time span of the time period that the `MdmTimeMember` represents.                                                                                              |
    | [`MetadataObject`](../MetadataObject.md)        | `getType``()`<br>Gets the type of this `MdmTimeMember`, which is the type of the `Source` for the member.                                                                                                                       |
    | `java.lang.String`                              | `getValue``()`<br>Gets the unique value of the `MdmTimeMember`.                                                                                                                                                                 |
    | [`MdmValueHierarchy`](MdmValueHierarchy.md)     | `getValueHierarchy``()`<br>Gets the `MdmValueHierarchy` of which the `MdmTimeMember` is a member.                                                                                                                               |
    | `void`                                          | `setEndDate``(java.util.Date endDate)`<br>Specifies an end date for the time period that the `MdmTimeMember` represents.                                                                                                        |
    | `void`                                          | `setLevel``(`[`MdmLevel`](MdmLevel.md)` level)`<br>Specifies the `MdmLevel` to which you want to add the `MdmTimeMember` as a member.                                                                                           |
    | `void`                                          | `setParentLevel``(`[`MdmLevel`](MdmLevel.md)` parentLevel)`<br>Specifies an `MdmLevel` for the parent of the `MdmTimeMember`.                                                                                                   |
    | `void`                                          | `setParentLocalValue``(java.lang.String parentLocal)`<br>Specifies a local value for the parent of the `MdmTimeMember`.                                                                                                         |
    | `void`                                          | `setPrecedence``(int precedence)`<br>Specifies a precedence for the `MdmTimeMember`, with the higher integer value indicating a higher precedence.                                                                              |
    | `void`                                          | `setTimeSpan``(int timeSpan)`<br>Specifies a time span for the time period that the `MdmTimeMember` represents.                                                                                                                 |
    | `void`                                          | `setValueHierarchy``(`[`MdmValueHierarchy`](MdmValueHierarchy.md)` valueHier)`<br>Specifies the `MdmValueHierarchy` to which you want to add the `MdmTimeMember` as a member.                                                   |

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

      Calls the `visitMdmTimeMember` method of the `MdmObjectVisitor` and passes that method the `MdmTimeMember` and an `Object`.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmTimeMember` method.

    <!-- -->

    - #### getEndDate

          public java.util.Date getEndDate()

      Gets the end date of the time period that the `MdmTimeMember` represents.
      Returns:
      A `Date` that represents the end date of the time period for the `MdmTimeMember`.

    <!-- -->

    - #### getTimeSpan

          public int getTimeSpan()

      Gets the number of time periods that is the time span of the time period that the `MdmTimeMember` represents.
      Returns:
      An integer that represents the time span of the time period for the `MdmTimeMember`.

    <!-- -->

    - #### getPrecedence

          public int getPrecedence()

      Gets the precedence of the `MdmTimeMember`.
      Specified by:
      [`getPrecedence`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      An integer that specifies the precedence of the `MdmTimeMember`.

    <!-- -->

    - #### setPrecedence

          public void setPrecedence(int precedence)

      Specifies a precedence for the `MdmTimeMember`, with the higher integer value indicating a higher precedence.
      Parameters:
      `precedence` - An integer that specifies the precedence for the `MdmTimeMember`.

    <!-- -->

    - #### setEndDate

          public void setEndDate(java.util.Date endDate)

      Specifies an end date for the time period that the `MdmTimeMember` represents.
      Parameters:
      `endDate` - A `Date` that specifies the end date that you want the `MdmTimeMember` to have.

    <!-- -->

    - #### setTimeSpan

          public void setTimeSpan(int timeSpan)

      Specifies a time span for the time period that the `MdmTimeMember` represents.
      Parameters:
      `timeSpan` - An `int` that specifies the number of time periods that you want the time span of the `MdmTimeMember` to be.

    <!-- -->

    - #### getOwnerDimension

          public MdmPrimaryDimension getOwnerDimension()

      Gets the `MdmPrimaryDimension` of which the `MdmTimeMember` is a member.
      Specified by:
      [`getOwnerDimension`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      The `MdmPrimaryDimension` of which the `MdmTimeMember` is a member.

    <!-- -->

    - #### getValue

          public java.lang.String getValue()

      Gets the unique value of the `MdmTimeMember`.
      Specified by:
      [`getValue`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      A `String` that contains the unique value of the `MdmTimeMember`.

    <!-- -->

    - #### getLocalValue

          public java.lang.String getLocalValue()

      Gets the local value of the `MdmTimeMember`.
      Specified by:
      [`getLocalValue`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      A `String` that contains the local value of the `MdmTimeMember`.

    <!-- -->

    - #### getLevel

          public MdmLevel getLevel()

      Gets the `MdmLevel` of which the `MdmTimeMember` is a member.
      Specified by:
      [`getLevel`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      The `MdmLevel` of which the `MdmTimeMember` is a member.

    <!-- -->

    - #### setLevel

          public void setLevel(MdmLevel level)

      Specifies the `MdmLevel` to which you want to add the `MdmTimeMember` as a member.
      Parameters:
      `level` - The `MdmLevel` to which you want to add the `MdmTimeMember` as a member.

    <!-- -->

    - #### getValueHierarchy

          public MdmValueHierarchy getValueHierarchy()

      Gets the `MdmValueHierarchy` of which the `MdmTimeMember` is a member.
      Returns:
      The `MdmValueHierarchy` of which the `MdmTimeMember` is a member.

    <!-- -->

    - #### setValueHierarchy

          public void setValueHierarchy(MdmValueHierarchy valueHier)

      Specifies the `MdmValueHierarchy` to which you want to add the `MdmTimeMember` as a member.
      Parameters:
      `valueHier` - The `MdmValueHierarchy` to which you want to add the `MdmTimeMember` as a member.

    <!-- -->

    - #### getLevelDepth

          public int getLevelDepth()

      Gets the depth in the hierarchy of the level of which the `MdmTimeMember` is a member.
      Specified by:
      [`getLevelDepth`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      An integer that identifies the depth in the hierarchy of the level of which the `MdmTimeMember` is a member.

    <!-- -->

    - #### getParentValue

          public java.lang.String getParentValue()

      Gets the unique value of the parent of the `MdmTimeMember`.
      Specified by:
      [`getParentValue`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      A `String` that contains the unique value of the parent of the `MdmTimeMember`.

    <!-- -->

    - #### getParentLocalValue

          public java.lang.String getParentLocalValue()

      Gets the local value of the parent of the `MdmTimeMember`.
      Specified by:
      [`getParentLocalValue`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      A `String` that contains the local value of the parent of the `MdmTimeMember`.

    <!-- -->

    - #### setParentLocalValue

          public void setParentLocalValue(java.lang.String parentLocal)

      Specifies a local value for the parent of the `MdmTimeMember`.
      Parameters:
      `parentLocal` - A `String` that contains the local value that you want the parent of the `MdmTimeMember` to have.

    <!-- -->

    - #### getParentLevel

          public MdmLevel getParentLevel()

      Gets the `MdmLevel` of which the parent of the `MdmTimeMember` is a member.
      Specified by:
      [`getParentLevel`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      The `MdmLevel` of which the parent of the `MdmTimeMember` is a member.

    <!-- -->

    - #### setParentLevel

          public void setParentLevel(MdmLevel parentLevel)

      Specifies an `MdmLevel` for the parent of the `MdmTimeMember`.
      Parameters:
      `parentLevel` - The `MdmLevel` that you want to specify for the parent of the `MdmTimeMember`.

    <!-- -->

    - #### getTimeDimension

          public final MdmTimeDimension getTimeDimension()

      Gets the `MdmTimeDimension` of which the `MdmTimeMember` is a member.
      Returns:
      The `MdmTimeDimension` of which the `MdmTimeMember` is a member.

    <!-- -->

    - #### getType

          public MetadataObject getType()

      Gets the type of this `MdmTimeMember`, which is the type of the `Source` for the member.
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

- [Prev Class](MdmTimeDimension.md)
- [Next Class](MdmValueHierarchy.md)

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
