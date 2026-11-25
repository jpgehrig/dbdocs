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

- [Prev Class](MdmDimensionMemberInfo.md)
- [Next Class](MdmHierarchyLevel.md)

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

## Class MdmHierarchy

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - [oracle.olapi.metadata.mdm.MdmDimension](MdmDimension.md)

          - - [oracle.olapi.metadata.mdm.MdmSubDimension](MdmSubDimension.md)

            - - oracle.olapi.metadata.mdm.MdmHierarchy

<!-- -->

- All Implemented Interfaces:
  [MdmQuery](MdmQuery.md), [MdmViewColumnOwner](MdmViewColumnOwner.md), [MetadataObject](../MetadataObject.md)

  <!-- -->

  Direct Known Subclasses:
  [MdmLevelHierarchy](MdmLevelHierarchy.md), [MdmValueHierarchy](MdmValueHierarchy.md)

  ------------------------------------------------------------------------



      public abstract class MdmHierarchy
      extends MdmSubDimension
      implements MdmViewColumnOwner, MdmQuery

  An `MdmSubDimension` that represents members of an Oracle OLAP dimension that are organized either hierarchically or nonhierarchically. An `MdmHierarchy` is a component of an `MdmPrimaryDimension`.
  A hierarchical organization is defined by parent-child relationships between the members of the hierarchy. If the parent-child relationships are defined by levels, then the `MdmHierarchy` is an `MdmLevelHierarchy`, which has a component `MdmLevel` object for each level. If the parent-child relationships are defined by values and not by levels, then the `MdmHierarchy` is an `MdmValueHierarchy`.

  A nonhierarchical `MdmHierarchy` is one that is not organized by parent-child relationships. It is represented by an `MdmLevelHierarchy` that has only one level.

  `MdmAttribute` objects record the parent-child relationships among the members of an `MdmHierarchy` You use the `getParentAttribute` and `getAncestorsAttribute` methods to get the `MdmAttribute` objects that relate parents to children and ancestors to descendents, respectively.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                | Method and Description                                                                                                                                 |
    |------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`MdmAttribute`](MdmAttribute.md)                                | `getAncestorsAttribute``()`<br>Gets the ancestors attribute for this `MdmHierarchy`.                                                                   |
    | `abstract `[`MdmDimensionMemberInfo`](MdmDimensionMemberInfo.md) | `getDefaultMember``()`<br>Gets the `MdmDimensionMemberInfo` that is associated with the default member of this `MdmHierarchy`.                         |
    | [`MdmQueryColumn`](MdmQueryColumn.md)                            | `getETDepthColumn``()`<br>Gets the `MdmQueryColumn` that represents the depth column of the embedded totals view associated with the `MdmHierarchy`.   |
    | [`MdmQueryColumn`](MdmQueryColumn.md)                            | `getETParentColumn``()`<br>Gets the `MdmQueryColumn` that represents the parent column of the embedded totals view associated with the `MdmHierarchy`. |
    | `java.lang.String`                                               | `getETViewName``()`<br>Gets the name of the ET (Embedded Totals) view associated with the `MdmHierarchy`.                                              |
    | [`MdmAttribute`](MdmAttribute.md)                                | `getParentAttribute``()`<br>Gets the parent attribute for this `MdmHierarchy`.                                                                         |
    | [`Query`](../../syntax/Query.md)                                 | `getQuery``()`<br>Gets the `Query` that is associated with the `MdmHierarchy`.                                                                         |
    | [`MdmQueryColumn`](MdmQueryColumn.md)                            | `getQueryColumn``(java.lang.String name)`<br>Gets the specified `MdmQueryColumn`.                                                                      |
    | `java.util.List<`[`MdmQueryColumn`](MdmQueryColumn.md)`>`        | `getQueryColumns``()`<br>Gets the `MdmQueryColumn` objects that are associated with the `MdmHierarchy`.                                                |
    | `java.lang.String`                                               | `getQueryName``()`<br>Gets the identifier of the `MdmHierarchy`.                                                                                       |
    | `boolean`                                                        | `isDefaultHierarchy``()`<br>Indicates whether this `MdmHierarchy` is the default component of an `MdmPrimaryDimension`.                                |
    | `abstract void`                                                  | `setDefaultMember``(`[`MdmDimensionMemberInfo`](MdmDimensionMemberInfo.md)` defaultMember)`<br>Specifies a default member for this `MdmHierarchy`.     |
    | `void`                                                           | `setETViewName``(java.lang.String name)`<br>Specifies the ET (Embedded Totals) view to associate with the `MdmHierarchy`.                              |

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

      [`acceptVisitor`](MdmObject.md)`, `[`addDescription`](MdmObject.md)`, `[`addObjectClassification`](MdmObject.md)`, `[`findOrCreateDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescriptions`](MdmObject.md)`, `[`getMetadataProvider`](MdmObject.md)`, `[`getObjectClassifications`](MdmObject.md)`, `[`getShortDescription`](MdmObject.md)`, `[`isClassifiedAs`](MdmObject.md)`, `[`removeDescription`](MdmObject.md)`, `[`removeObjectClassification`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setName`](MdmObject.md)`, `[`setShortDescription`](MdmObject.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getName`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getAncestorsAttribute

          public MdmAttribute getAncestorsAttribute()
                                             throws oracle.express.mdm.MetadataNotFoundException

      Gets the ancestors attribute for this `MdmHierarchy`. The ancestors attribute relates each member of this `MdmHierarchy` to the members that are the ancestors of it in the hierarchy. For example, the ancestors for a given day in a time hierarchy might be month, quarter, and year.
      Returns:
      The `MdmAttribute` that is the ancestors attribute of this `MdmHierarchy`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### getParentAttribute

          public MdmAttribute getParentAttribute()
                                          throws oracle.express.mdm.MetadataNotFoundException

      Gets the parent attribute for this `MdmHierarchy`. The parent attribute relates each member of this `MdmHierarchy` to the parent of it.
      Returns:
      The `MdmAttribute` that is the parent attribute of this `MdmHierarchy`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### getDefaultMember

          public abstract MdmDimensionMemberInfo getDefaultMember()
                                                           throws oracle.express.mdm.MetadataNotFoundException

      Gets the `MdmDimensionMemberInfo` that is associated with the default member of this `MdmHierarchy`. You can get the value of the default member by calling the `getLocalValue` or `getUniqueValue` method of the `MdmDimensionMemberInfo`.
      Returns:
      An `MdmDimensionMemberInfo` for the default member of this `MdmHierarchy`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### setDefaultMember

          public abstract void setDefaultMember(MdmDimensionMemberInfo defaultMember)
                                         throws oracle.express.mdm.MetadataNotFoundException,
                                                MdmInvalidValueException

      Specifies a default member for this `MdmHierarchy`.
      Parameters:
      `defaultMember` - The `MdmDimensionMemberInfo` that is associated with the dimension member that you want as the default member for this `MdmHierarchy`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

      [`MdmInvalidValueException`](MdmInvalidValueException.md)

    <!-- -->

    - #### isDefaultHierarchy

          public final boolean isDefaultHierarchy()

      Indicates whether this `MdmHierarchy` is the default component of an `MdmPrimaryDimension`.
      Returns:
      A `boolean` that is `true` if this is the default hierarchy or `false` if it is not.

    <!-- -->

    - #### getETViewName

          public final java.lang.String getETViewName()

      Gets the name of the ET (Embedded Totals) view associated with the `MdmHierarchy`.
      Returns:
      A `String` that contains the name of the ET view associated with the `MdmHierarchy`.

    <!-- -->

    - #### setETViewName

          public final void setETViewName(java.lang.String name)

      Specifies the ET (Embedded Totals) view to associate with the `MdmHierarchy`.
      Parameters:
      `name` - A `String` that contains the name of the ET view to associate with the `MdmHierarchy`.

    <!-- -->

    - #### getETParentColumn

          public final MdmQueryColumn getETParentColumn()

      Gets the `MdmQueryColumn` that represents the parent column of the embedded totals view associated with the `MdmHierarchy`.
      Returns:
      An `MdmQueryColumn` that represents the parent column of the embedded totals view.

    <!-- -->

    - #### getETDepthColumn

          public final MdmQueryColumn getETDepthColumn()

      Gets the `MdmQueryColumn` that represents the depth column of the embedded totals view associated with the `MdmHierarchy`.
      Returns:
      An `MdmQueryColumn` that represents the depth column of the embedded totals view.

    <!-- -->

    - #### getQuery

          public final Query getQuery()

      Gets the `Query` that is associated with the `MdmHierarchy`.
      Specified by:
      [`getQuery`](MdmQuery.md) in interface [`MdmQuery`](MdmQuery.md)

      Returns:
      The `Query` associated with the `MdmHierarchy`.

    <!-- -->

    - #### getQueryName

          public final java.lang.String getQueryName()

      Gets the identifier of the `MdmHierarchy`.
      Specified by:
      [`getQueryName`](MdmQuery.md) in interface [`MdmQuery`](MdmQuery.md)

      Returns:
      A `String` that contains the identifier of the `MdmHierarchy` object.

    <!-- -->

    - #### getQueryColumns

          public java.util.List<MdmQueryColumn> getQueryColumns()

      Gets the `MdmQueryColumn` objects that are associated with the `MdmHierarchy`.
      Specified by:
      [`getQueryColumns`](MdmQuery.md) in interface [`MdmQuery`](MdmQuery.md)

      Returns:
      A `List` of the `MdmQueryColumn` objects associated with the `MdmHierarchy`.

    <!-- -->

    - #### getQueryColumn

          public MdmQueryColumn getQueryColumn(java.lang.String name)

      Gets the specified `MdmQueryColumn`.
      Specified by:
      [`getQueryColumn`](MdmQuery.md) in interface [`MdmQuery`](MdmQuery.md)

      Parameters:
      `name` - A `String` that contains the name of an `MdmQueryColumn`.

      Returns:
      The `MdmQueryColumn` that has the specified name.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmDimensionMemberInfo.md)
- [Next Class](MdmHierarchyLevel.md)

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
