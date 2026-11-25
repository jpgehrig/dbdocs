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

- [Prev Class](MdmTimeMember.md)
- [Next Class](MdmViewColumn.md)

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

## Class MdmValueHierarchy

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - [oracle.olapi.metadata.mdm.MdmDimension](MdmDimension.md)

          - - [oracle.olapi.metadata.mdm.MdmSubDimension](MdmSubDimension.md)

            - - [oracle.olapi.metadata.mdm.MdmHierarchy](MdmHierarchy.md)

              - - oracle.olapi.metadata.mdm.MdmValueHierarchy

<!-- -->

- All Implemented Interfaces:
  [MdmQuery](MdmQuery.md), [MdmViewColumnOwner](MdmViewColumnOwner.md), [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public final class MdmValueHierarchy
      extends MdmHierarchy

  An `MdmHierarchy` that represents members of an Oracle OLAP dimension that are organized hierarchically by values rather than by levels. An application creates an `MdmValueHierarchy` with the [`findOrCreateValueHierarchy`](MdmPrimaryDimension.md) method of an `MdmPrimaryDimension`.
  The hierarchical organization is defined by parent-child relationships between the members of the `MdmValueHierarchy`. For example, the employee reporting structure of a company can be represented with parent-child relationships but without levels.

  To map an `MdmValueHierarchy` to a data source, you use a `SolvedValueHierarchyMap`. You specify the children of the hierarchy with the `setKeyExpression` method of the `SolvedValueHierarchyMap` and you specify the parents with the `setParentKeyExpression` method.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                  | Method and Description                                                                                                                                                                                                                                                |
    |--------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                                                 | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmValueHierarchy` method on the specified `MdmObjectVisitor` and passes that method this `MdmValueHierarchy` and the specified `context` object. |
    | [`SolvedValueHierarchyMap`](../mapping/SolvedValueHierarchyMap.md) | `findOrCreateSolvedValueHierarchyMap``()`<br>Gets the `SolvedValueHierarchyMap` that is contained by this `MdmValueHierarchy` or creates a new `SolvedValueHierarchyMap` if one does not already exist.                                                               |
    | [`MdmDimensionMemberInfo`](MdmDimensionMemberInfo.md)              | `getDefaultMember``()`<br>Gets the `MdmDimensionMemberInfo` that specifies the default member of this `MdmValueHierarchy`.                                                                                                                                            |
    | [`SolvedValueHierarchyMap`](../mapping/SolvedValueHierarchyMap.md) | `getSolvedHierarchyMap``()`<br>Gets the `SolvedValueHierarchyMap` that is contained by this `MdmValueHierarchy`.                                                                                                                                                      |
    | `void`                                                             | `setDefaultMember``(`[`MdmDimensionMemberInfo`](MdmDimensionMemberInfo.md)` defaultMember)`<br>Specifies a default member for this `MdmValueHierarchy`.                                                                                                               |
    | `void`                                                             | `setSolvedHierarchyMap``(`[`SolvedValueHierarchyMap`](../mapping/SolvedValueHierarchyMap.md)` map)`<br>Specifies a `SolvedValueHierarchyMap` for this `MdmValueHierarchy`.                                                                                            |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmHierarchy](MdmHierarchy.md)

      [`getAncestorsAttribute`](MdmHierarchy.md)`, `[`getETDepthColumn`](MdmHierarchy.md)`, `[`getETParentColumn`](MdmHierarchy.md)`, `[`getETViewName`](MdmHierarchy.md)`, `[`getParentAttribute`](MdmHierarchy.md)`, `[`getQuery`](MdmHierarchy.md)`, `[`getQueryColumn`](MdmHierarchy.md)`, `[`getQueryColumns`](MdmHierarchy.md)`, `[`getQueryName`](MdmHierarchy.md)`, `[`isDefaultHierarchy`](MdmHierarchy.md)`, `[`setETViewName`](MdmHierarchy.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmSubDimension](MdmSubDimension.md)

      [`addAttribute`](MdmSubDimension.md)`, `[`getAttributes`](MdmSubDimension.md)`, `[`removeAttribute`](MdmSubDimension.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmDimension](MdmDimension.md)

      [`getCardinality`](MdmDimension.md)`, `[`getCustomOrder`](MdmDimension.md)`, `[`getPluralDescription`](MdmDimension.md)`, `[`getPrimaryDimension`](MdmDimension.md)`, `[`getShortPluralDescription`](MdmDimension.md)`, `[`setCardinality`](MdmDimension.md)`, `[`setCustomOrder`](MdmDimension.md)`, `[`setPluralDescription`](MdmDimension.md)`, `[`setShortPluralDescription`](MdmDimension.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmSource](MdmSource.md)

      [`getDataType`](MdmSource.md)`, `[`getSource`](MdmSource.md)`, `[`getType`](MdmSource.md)

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

- - ### Method Detail

    - #### acceptVisitor

          public java.lang.Object acceptVisitor(MdmObjectVisitor visitor,
                                                java.lang.Object context)

      Calls the `visitMdmValueHierarchy` method on the specified `MdmObjectVisitor` and passes that method this `MdmValueHierarchy` and the specified `context` object.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmValueHierarchy` method.

    <!-- -->

    - #### getDefaultMember

          public MdmDimensionMemberInfo getDefaultMember()
                                                  throws oracle.express.mdm.MetadataNotFoundException

      Gets the `MdmDimensionMemberInfo` that specifies the default member of this `MdmValueHierarchy`. From the `MdmDimensionMemberInfo` you can get the value of the default member by calling its `getLocalValue` or `getUniqueValue` method.
      Specified by:
      [`getDefaultMember`](MdmHierarchy.md) in class [`MdmHierarchy`](MdmHierarchy.md)

      Returns:
      An `MdmDimensionMemberInfo` that has the default member of this `MdmValueHierarchy`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### setDefaultMember

          public void setDefaultMember(MdmDimensionMemberInfo defaultMember)
                                throws oracle.express.mdm.MetadataNotFoundException,
                                       MdmInvalidValueException

      Specifies a default member for this `MdmValueHierarchy`.
      Specified by:
      [`setDefaultMember`](MdmHierarchy.md) in class [`MdmHierarchy`](MdmHierarchy.md)

      Parameters:
      `defaultMember` - An `MdmDimensionMemberInfo` that has the value that you want the default member of this `MdmValueHierarchy` to have.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

      [`MdmInvalidValueException`](MdmInvalidValueException.md)

    <!-- -->

    - #### getSolvedHierarchyMap

          public final SolvedValueHierarchyMap getSolvedHierarchyMap()

      Gets the `SolvedValueHierarchyMap` that is contained by this `MdmValueHierarchy`.
      Returns:
      The `SolvedValueHierarchyMap` for this `MdmValueHierarchy`.

    <!-- -->

    - #### setSolvedHierarchyMap

          public final void setSolvedHierarchyMap(SolvedValueHierarchyMap map)

      Specifies a `SolvedValueHierarchyMap` for this `MdmValueHierarchy`.
      Parameters:
      `map` - The `SolvedValueHierarchyMap` for this `MdmValueHierarchy`.

    <!-- -->

    - #### findOrCreateSolvedValueHierarchyMap

          public SolvedValueHierarchyMap findOrCreateSolvedValueHierarchyMap()

      Gets the `SolvedValueHierarchyMap` that is contained by this `MdmValueHierarchy` or creates a new `SolvedValueHierarchyMap` if one does not already exist.
      Returns:
      The `SolvedValueHierarchyMap` for this `MdmValueHierarchy`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmTimeMember.md)
- [Next Class](MdmViewColumn.md)

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
