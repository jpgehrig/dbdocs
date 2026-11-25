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

- [Prev Class](MdmDimensionedObject.md)
- [Next Class](MdmDimensionMemberInfo.md)

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

## Class MdmDimensionLevel

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - [oracle.olapi.metadata.mdm.MdmDimension](MdmDimension.md)

          - - [oracle.olapi.metadata.mdm.MdmSubDimension](MdmSubDimension.md)

            - - oracle.olapi.metadata.mdm.MdmDimensionLevel

<!-- -->

- All Implemented Interfaces:
  [MdmMemberListMapOwner](MdmMemberListMapOwner.md), [MdmViewColumnOwner](MdmViewColumnOwner.md), [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public class MdmDimensionLevel
      extends MdmSubDimension
      implements MdmMemberListMapOwner, MdmViewColumnOwner

  A component of an `MdmPrimaryDimension` that represents a subset of members of the dimension. Any dimension member can be in at most one `MdmDimensionLevel`. An application creates an `MdmDimensionLevel` with the [`findOrCreateDimensionLevel`](MdmPrimaryDimension.md) method of an `MdmPrimaryDimension`.
  The members of an `MdmDimensionLevel` are specified by an associated [`MemberListMap`](../mapping/MemberListMap.md). The key `Expression` for the `MemberListMap` is typically a `ColumnExpression` that specifies a column in a relational table.

  An `MdmDimensionLevel` can be associated with zero, one, or more `MdmHierarchyLevel` objects. An `MdmHierarchyLevel` is associated with only one `MdmDimensionLevel`. The members of an `MdmHierarchyLevel` are some or all of the members of the `MdmDimensionLevel`. A member of an `MdmDimensionLevel` need not be a member of any `MdmHierarchyLevel`. Therefore, an `MdmDimensionLevel` can contain more members than an associated `MdmHierarchyLevel`.

  An `MdmDimensionLevel` has a type that indicates the type of values in the level. The static constant fields contain the possible type values. By default the level type is `LEVEL_TYPE_STANDARD`. For an `MdmDimensionLevel` of an `MdmTimeDimension`, you can specify one of the other level types by using the `setLevelType` method.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                          |
    |---------------------------|--------------------------------------------------------------------------------|
    | `static java.lang.String` | `LEVEL_TYPE_DAY`<br>A constant that specifies a level type of `DAY`.           |
    | `static java.lang.String` | `LEVEL_TYPE_HALFYEAR`<br>A constant that specifies a level type of `HALFYEAR`. |
    | `static java.lang.String` | `LEVEL_TYPE_HOUR`<br>A constant that specifies a level type of `HOUR`.         |
    | `static java.lang.String` | `LEVEL_TYPE_MINUTE`<br>A constant that specifies a level type of `MINUTE`.     |
    | `static java.lang.String` | `LEVEL_TYPE_MONTH`<br>A constant that specifies a level type of `MONTH`.       |
    | `static java.lang.String` | `LEVEL_TYPE_QUARTER`<br>A constant that specifies a level type of `QUARTER`.   |
    | `static java.lang.String` | `LEVEL_TYPE_SECOND`<br>A constant that specifies a level type of `SECOND`.     |
    | `static java.lang.String` | `LEVEL_TYPE_STANDARD`<br>A constant that specifies a level type of `STANDARD`. |
    | `static java.lang.String` | `LEVEL_TYPE_WEEK`<br>A constant that specifies a level type of `WEEK`.         |
    | `static java.lang.String` | `LEVEL_TYPE_YEAR`<br>A constant that specifies a level type of `YEAR`.         |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                             | Method and Description                                                                                                                                                                                                                                                |
    |---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                                            | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmDimensionLevel` method of the specified `MdmObjectVisitor` and passes that method this `MdmDimensionLevel` and the specified `context` object. |
    | `void`                                                        | `addUniqueKeyAttribute``(`[`MdmBaseAttribute`](MdmBaseAttribute.md)` attr)`<br>Adds a unique key attribute to the list of them that are associated with this `MdmDimensionLevel`.                                                                                     |
    | [`MemberListMap`](../mapping/MemberListMap.md)                | `findOrCreateMemberListMap``()`<br>Gets the `MemberListMap` that is associated with this `MdmDimensionLevel` or creates a new `MemberListMap` if one does not already exist.                                                                                          |
    | [`MdmViewColumn`](MdmViewColumn.md)                           | `getETViewLevelKeyColumn``()`<br>Gets the `MdmViewColumn` that represents the key column of the embedded totals view associated with the `MdmDimensionLevel`.                                                                                                         |
    | [`MdmViewColumn`](MdmViewColumn.md)                           | `getETViewLocalValueColumn``()`<br>Gets the `MdmViewColumn` that represents the local value column of the embedded totals view associated with the `MdmDimensionLevel`.                                                                                               |
    | `java.lang.String`                                            | `getLevelType``()`<br>Gets the type of information that this `MdmDimensionLevel` represents.                                                                                                                                                                          |
    | [`MemberListMap`](../mapping/MemberListMap.md)                | `getMemberListMap``()`<br>Gets the `MemberListMap` associated with the `MdmDimensionLevel`.                                                                                                                                                                           |
    | `java.util.List<`[`MdmBaseAttribute`](MdmBaseAttribute.md)`>` | `getUniqueKeyAttributes``()`<br>Gets a list of the unique key attributes that are associated with this `MdmDimensionLevel`.                                                                                                                                           |
    | `void`                                                        | `removeUniqueKeyAttribute``(`[`MdmBaseAttribute`](MdmBaseAttribute.md)` attr)`<br>Removes a unique key attribute from the list of them that are associated with this `MdmDimensionLevel`.                                                                             |
    | `void`                                                        | `setLevelType``(java.lang.String levelType)`<br>Specifies the type of information that this `MdmDimensionLevel` represents.                                                                                                                                           |
    | `void`                                                        | `setMemberListMap``(`[`MemberListMap`](../mapping/MemberListMap.md)` map)`<br>Specifies the `MemberListMap` to associate with the `MdmDimensionLevel`.                                                                                                                |

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

- - ### Field Detail

    - #### LEVEL_TYPE_STANDARD

          public static final java.lang.String LEVEL_TYPE_STANDARD

      A constant that specifies a level type of `STANDARD`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVEL_TYPE_YEAR

          public static final java.lang.String LEVEL_TYPE_YEAR

      A constant that specifies a level type of `YEAR`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVEL_TYPE_HALFYEAR

          public static final java.lang.String LEVEL_TYPE_HALFYEAR

      A constant that specifies a level type of `HALFYEAR`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVEL_TYPE_QUARTER

          public static final java.lang.String LEVEL_TYPE_QUARTER

      A constant that specifies a level type of `QUARTER`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVEL_TYPE_MONTH

          public static final java.lang.String LEVEL_TYPE_MONTH

      A constant that specifies a level type of `MONTH`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVEL_TYPE_WEEK

          public static final java.lang.String LEVEL_TYPE_WEEK

      A constant that specifies a level type of `WEEK`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVEL_TYPE_DAY

          public static final java.lang.String LEVEL_TYPE_DAY

      A constant that specifies a level type of `DAY`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVEL_TYPE_HOUR

          public static final java.lang.String LEVEL_TYPE_HOUR

      A constant that specifies a level type of `HOUR`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVEL_TYPE_MINUTE

          public static final java.lang.String LEVEL_TYPE_MINUTE

      A constant that specifies a level type of `MINUTE`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVEL_TYPE_SECOND

          public static final java.lang.String LEVEL_TYPE_SECOND

      A constant that specifies a level type of `SECOND`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### acceptVisitor

          public java.lang.Object acceptVisitor(MdmObjectVisitor visitor,
                                                java.lang.Object context)

      Calls the `visitMdmDimensionLevel` method of the specified `MdmObjectVisitor` and passes that method this `MdmDimensionLevel` and the specified `context` object.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An implementation of the `Mdm11_ObjectVisitor` interface.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmDimensionLevel` method.

    <!-- -->

    - #### getUniqueKeyAttributes

          public final java.util.List<MdmBaseAttribute> getUniqueKeyAttributes()

      Gets a list of the unique key attributes that are associated with this `MdmDimensionLevel`.
      Returns:
      A `List` of the unique key attributes associated with this `MdmDimensionLevel`.

    <!-- -->

    - #### addUniqueKeyAttribute

          public final void addUniqueKeyAttribute(MdmBaseAttribute attr)

      Adds a unique key attribute to the list of them that are associated with this `MdmDimensionLevel`.
      Parameters:
      `attr` - The `MdmBaseAttribute` to add to the `List` of unique key attributes of this `MdmDimensionLevel`.

    <!-- -->

    - #### removeUniqueKeyAttribute

          public final void removeUniqueKeyAttribute(MdmBaseAttribute attr)

      Removes a unique key attribute from the list of them that are associated with this `MdmDimensionLevel`.
      Parameters:
      `attr` - The `MdmBaseAttribute` to remove from the `List` of unique key attributes of this `MdmDimensionLevel`.

    <!-- -->

    - #### getLevelType

          public java.lang.String getLevelType()
                                        throws oracle.express.mdm.MetadataNotFoundException

      Gets the type of information that this `MdmDimensionLevel` represents. For an `MdmDimensionLevel` associated with an `MdmTimeDimension`, the possible level type values are `YEAR`, `HALFYEAR`, `QUARTER`, `MONTH`, `WEEK`, `DAY`, `HOUR`, `MINUTE`, `SECOND`, and `STANDARD`. For an `MdmDimensionLevel` associated with any other subclass of `MdmPrimaryDimension`, the level type is `STANDARD`.
      Returns:
      A `String` indicating the type of information in the level.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### setLevelType

          public void setLevelType(java.lang.String levelType)
                            throws MdmInvalidValueException

      Specifies the type of information that this `MdmDimensionLevel` represents. For an `MdmTimeDimension`, the possible `levelType` values are `YEAR`, `HALFYEAR`, `QUARTER`, `MONTH`, `WEEK`, `DAY`, `HOUR`, `MINUTE`, `SECOND`, and `STANDARD`. For an `MdmStandardDimension` or `MdmMeasureDimension`, the level type is `STANDARD`.
      Parameters:
      `levelType` - A `String` indicating the type of the information in this level.

      Throws:
      [`MdmInvalidValueException`](MdmInvalidValueException.md)

    <!-- -->

    - #### getMemberListMap

          public final MemberListMap getMemberListMap()

      Gets the `MemberListMap` associated with the `MdmDimensionLevel`.
      Specified by:
      [`getMemberListMap`](MdmMemberListMapOwner.md) in interface [`MdmMemberListMapOwner`](MdmMemberListMapOwner.md)

      Returns:
      The `MemberListMap` for the `MdmDimensionLevel`.

    <!-- -->

    - #### setMemberListMap

          public final void setMemberListMap(MemberListMap map)

      Specifies the `MemberListMap` to associate with the `MdmDimensionLevel`.
      Parameters:
      `map` - The `MemberListMap` to associate with the `MdmDimensionLevel`.

    <!-- -->

    - #### getETViewLevelKeyColumn

          public final MdmViewColumn getETViewLevelKeyColumn()

      Gets the `MdmViewColumn` that represents the key column of the embedded totals view associated with the `MdmDimensionLevel`.
      Returns:
      An `MdmViewColumn` that represents the key column of the embedded totals view.

    <!-- -->

    - #### getETViewLocalValueColumn

          public final MdmViewColumn getETViewLocalValueColumn()

      Gets the `MdmViewColumn` that represents the local value column of the embedded totals view associated with the `MdmDimensionLevel`.
      Returns:
      An `MdmViewColumn` that represents the local value column of the embedded totals view.

    <!-- -->

    - #### findOrCreateMemberListMap

          public MemberListMap findOrCreateMemberListMap()

      Gets the `MemberListMap` that is associated with this `MdmDimensionLevel` or creates a new `MemberListMap` if one does not already exist.
      Specified by:
      [`findOrCreateMemberListMap`](MdmMemberListMapOwner.md) in interface [`MdmMemberListMapOwner`](MdmMemberListMapOwner.md)

      Returns:
      The `MemberListMap` associated with this `MdmDimensionLevel`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmDimensionedObject.md)
- [Next Class](MdmDimensionMemberInfo.md)

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
