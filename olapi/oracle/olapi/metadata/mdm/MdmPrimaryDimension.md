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

- [Prev Class](MdmOrganizationalSchema.md)
- [Next Class](MdmQuery.md)

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

## Class MdmPrimaryDimension

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - [oracle.olapi.metadata.mdm.MdmDimension](MdmDimension.md)

          - - oracle.olapi.metadata.mdm.MdmPrimaryDimension

<!-- -->

- All Implemented Interfaces:
  [MdmMemberListMapOwner](MdmMemberListMapOwner.md), [MdmQuery](MdmQuery.md), [MdmViewColumnOwner](MdmViewColumnOwner.md), [MetadataObject](../MetadataObject.md), [Buildable](../../syntax/Buildable.md)

  <!-- -->

  Direct Known Subclasses:
  [MdmMeasureDimension](MdmMeasureDimension.md), [MdmStandardDimension](MdmStandardDimension.md), [MdmTimeDimension](MdmTimeDimension.md)

  ------------------------------------------------------------------------



      public abstract class MdmPrimaryDimension
      extends MdmDimension
      implements MdmMemberListMapOwner, MdmViewColumnOwner, MdmQuery, Buildable

  The base class for objects that represent an Oracle OLAP dimension. An `MdmPrimaryDimension` has one or more components that are subclasses of `MdmSubDimension`.
  The concrete subclasses of the abstract `MdmPrimaryDimension` class represent dimensions that have different characteristics. An `MdmStandardDimension` typically has members that represent such things as products, customers, distribution channels, and so on. An `MdmTimeDimension` has members that represent time periods. An `MdmMeasureDimension` has members that are `MdmMeasure` objects.

  The `MdmHierarchy` components of an `MdmPrimaryDimension` represent organizations of the members of the dimension. An Oracle OLAP dimension can be a simple, nonhierarchical set of members, or it can organize members into one or more hierarchies. A hierarchy can have parent-child relationships organized by levels or by values. For example, a dimension of time periods might be organized into two hierarchies, one organized by calendar year time periods and the other organized by fiscal year time periods. Both hierarchies are organized by levels for year, quarter, month, and day time periods. Each of those hierarchies is represented by an `MdmLevelHierarchy`, which is a concrete subclass of the abstract `MdmHierarchy` class. Those `MdmLevelHierarchy` objects are the components of the `MdmTimeDimension`.

  Some the methods of an `MdmPrimaryDimension` return `MdmAttribute` objects that have members that are related to members of one or more of the components of the dimension. For example, the `getLocalValueAttribute` method returns an `MdmAttribute` that relates the unique value of a member of a component of the `MdmPrimaryDimension` to its corresponding local value. A unique value specifies a hierarchy, a level of the hierarchy, and the value of a member in that level, as in the following example from an `MdmLevelHierarchy` that represents products organized into levels by the type of product.

       PRODUCT_PRIMARY::ITEM::ENVY STD

  The parts of the unique value are separated by a value separation string. The value separation string in the preceding example is `::`, the double colons. The local value of that unique value is `ENVY STD`.
  An application can create a concrete instance of an `MdmPrimaryDimension` by calling the appropriate method of an `MdmDatabaseSchema`. It can also get existing `MdmPrimaryDimension` objects from the `MdmDatabaseSchema` or an `MdmDimensionedObject`. It gets the `MdmMeasureDimension` for a schema by calling the `getMeasureDimension` method of an `MdmDatabaseSchema`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                         | Method and Description                                                                                                                                                                                                                                |
    |-------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                    | `addDimensionLevel``(`[`MdmDimensionLevel`](MdmDimensionLevel.md)` level)`<br>Adds an `MdmDimensionLevel` to the `List` of `MdmDimensionLevel` objects associated with the `MdmPrimaryDimension`.                                                     |
    | `void`                                                                                    | `addHierarchy``(`[`MdmHierarchy`](MdmHierarchy.md)` hierarchy)`<br>Adds an `MdmHierarchy` to the `List` of `MdmHierarchy` objects associated with the `MdmPrimaryDimension`.                                                                          |
    | `void`                                                                                    | `addModel``(`[`MdmDimensionCalculationModel`](MdmDimensionCalculationModel.md)` model)`<br>Adds an `MdmDimensionCalculationModel` to the `List` of `MdmDimensionCalculationModel` objects associated with the `MdmPrimaryDimension`.                  |
    | [`AWPrimaryDimensionOrganization`](../deployment/AWPrimaryDimensionOrganization.md)       | `findOrCreateAWPrimaryDimensionOrganization``(`[`AW`](../deployment/AW.md)` aw)`<br>Gets the `AWPrimaryDimensionOrganization` for the `MdmPrimaryDimension` or creates a new `AWPrimaryDimensionOrganization` if one does not already exist.          |
    | [`MdmBaseAttribute`](MdmBaseAttribute.md)                                                 | `findOrCreateBaseAttribute``(java.lang.String publicName)`<br>Gets the specified `MdmBaseAttribute` or, if it does not already exist, creates a new one for the `MdmPrimaryDimension`.                                                                |
    | [`MdmDimensionCalculationModel`](MdmDimensionCalculationModel.md)                         | `findOrCreateDimCalcModel``(java.lang.String publicName)`<br>Gets the specified `MdmDimensionCalculationModel` or, if it does not already exist, creates a new one for the `MdmPrimaryDimension`.                                                     |
    | [`MdmDimensionLevel`](MdmDimensionLevel.md)                                               | `findOrCreateDimensionLevel``(java.lang.String publicName)`<br>Gets the specified `MdmDimensionLevel` or, if it does not already exist, creates a new one for the `MdmPrimaryDimension`.                                                              |
    | [`MdmLevelHierarchy`](MdmLevelHierarchy.md)                                               | `findOrCreateLevelHierarchy``(java.lang.String publicName)`<br>Gets the specified `MdmLevelHierarchy` or, if it does not already exist, creates a new one for the `MdmPrimaryDimension`.                                                              |
    | [`MdmCustomMember`](MdmCustomMember.md)                                                   | `findOrCreateMdmCustomMember``(java.lang.String memberName)`<br>Gets the specified `MdmCustomMember` of the dimension or, if the custom member does not already exist, creates a new one.                                                             |
    | [`MemberListMap`](../mapping/MemberListMap.md)                                            | `findOrCreateMemberListMap``()`<br>Gets the `MemberListMap` for the `MdmPrimaryDimension` or, if one does not already exist, creates a new one.                                                                                                       |
    | [`RolapPrimaryDimensionOrganization`](../deployment/RolapPrimaryDimensionOrganization.md) | `findOrCreateRolapPrimaryDimensionOrganization``()`<br>Gets the `RolapPrimaryDimensionOrganization` for the `MdmPrimaryDimension` or creates a new `RolapPrimaryDimensionOrganization` if one does not already exist.                                 |
    | [`MdmValueHierarchy`](MdmValueHierarchy.md)                                               | `findOrCreateValueHierarchy``(java.lang.String publicName)`<br>Gets the specified `MdmValueHierarchy` or, if it does not already exist, creates a new one for the `MdmPrimaryDimension`.                                                              |
    | [`MdmAttribute`](MdmAttribute.md)                                                         | `getAncestorsAttribute``()`<br>Gets the ancestors attribute for the `MdmPrimaryDimension`.                                                                                                                                                            |
    | `java.util.List`                                                                          | `getAttributes``()`<br>Gets a `List` of the `MdmAttribute` objects associated with the `MdmPrimaryDimension`.                                                                                                                                         |
    | [`MdmDimensionCalculationModel`](MdmDimensionCalculationModel.md)                         | `getDefaultCalcModel``()`<br>Gets the default `MdmDimensionCalculationModel` specified for the `MdmPrimaryDimension`.                                                                                                                                 |
    | [`MdmHierarchy`](MdmHierarchy.md)                                                         | `getDefaultHierarchy``()`<br>Gets the default component of the `MdmPrimaryDimension`.                                                                                                                                                                 |
    | `java.util.List`                                                                          | `getDimensionLevels``()`<br>Gets the `List` of the `MdmDimensionLevel` objects that are associated with the `MdmPrimaryDimension`.                                                                                                                    |
    | [`MdmViewColumn`](MdmViewColumn.md)                                                       | `getETDimensionOrderColumn``()`<br>Gets the dimension order column of the ET (Embedded Totals) view that is associated with the `MdmPrimaryDimension`.                                                                                                |
    | [`MdmViewColumn`](MdmViewColumn.md)                                                       | `getETHierarchyOrderColumn``()`<br>Gets the hierarchy order column of the ET (Embedded Totals) view that is associated with the `MdmPrimaryDimension`.                                                                                                |
    | [`MdmViewColumn`](MdmViewColumn.md)                                                       | `getETKeyColumn``()`<br>Gets the key column of the ET (Embedded Totals) view that is associated with the `MdmPrimaryDimension`.                                                                                                                       |
    | [`MdmViewColumn`](MdmViewColumn.md)                                                       | `getETLevelNameColumn``()`<br>Gets the level name column of the ET (Embedded Totals) view that is associated with the `MdmPrimaryDimension`.                                                                                                          |
    | [`MdmViewColumn`](MdmViewColumn.md)                                                       | `getETLocalValueColumn``()`<br>Gets the local value column of the ET (Embedded Totals) view that is associated with the `MdmPrimaryDimension`.                                                                                                        |
    | [`MdmViewColumn`](MdmViewColumn.md)                                                       | `getETMemberTypeColumn``()`<br>Gets the member type column of the ET (Embedded Totals) view that is associated with the `MdmPrimaryDimension`.                                                                                                        |
    | `java.lang.String`                                                                        | `getETViewName``()`<br>Gets the name of the ET (Embedded Totals) view that is associated with the `MdmPrimaryDimension`.                                                                                                                              |
    | `java.util.List`                                                                          | `getHierarchies``()`<br>Gets a `List` that contains the components of the `MdmPrimaryDimension`, which are `MdmHierarchy` objects.                                                                                                                    |
    | [`MdmHierarchy`](MdmHierarchy.md)                                                         | `getHierarchy``(java.lang.String name)`<br>Gets the specified `MdmHierarchy` component of the `MdmPrimaryDimension`.                                                                                                                                  |
    | [`MdmAttribute`](MdmAttribute.md)                                                         | `getHierarchyAttribute``()`<br>Gets the `MdmAttribute` that relates a hierarchy to each member of the `MdmPrimaryDimension`.                                                                                                                          |
    | [`MdmAttribute`](MdmAttribute.md)                                                         | `getIsCustomMemberAttribute``()`<br>Gets the `MdmAttribute` that, for each member of the `MdmPrimaryDimension`, indicates whether that member is a custom member.                                                                                     |
    | [`MdmAttribute`](MdmAttribute.md)                                                         | `getLevelAttribute``()`<br>Gets the `MdmAttribute` that relates the level of the hierarchy that a member of the hierarchy is in to each member of the `MdmPrimaryDimension`.                                                                          |
    | [`MdmAttribute`](MdmAttribute.md)                                                         | `getLevelDepthAttribute``()`<br>Gets the `MdmAttribute` that relates the depth of the level of the hierarchy that a member of the hierarchy is in to each member of the `MdmPrimaryDimension`.                                                        |
    | [`MdmAttribute`](MdmAttribute.md)                                                         | `getLocalValueAttribute``()`<br>Gets the `MdmAttribute` that relates a local value to each member of the `MdmPrimaryDimension`.                                                                                                                       |
    | `java.util.List`                                                                          | `getMdmCustomMembers``()`<br>Gets the `MdmCustomMember` objects that are associated with the `MdmPrimaryDimension`.                                                                                                                                   |
    | [`MemberListMap`](../mapping/MemberListMap.md)                                            | `getMemberListMap``()`<br>Gets the `MemberListMap` that is associated with the `MdmPrimaryDimension`.                                                                                                                                                 |
    | `java.util.List`                                                                          | `getModels``()`<br>Gets the `List` of the `MdmDimensionCalculationModel` objects that are associated with the `MdmPrimaryDimension`.                                                                                                                  |
    | `java.lang.String`                                                                        | `getNamespace``()`<br>Gets the namespace of this `MdmPrimaryDimension`.                                                                                                                                                                               |
    | [`PrimaryDimensionOrganization`](../deployment/PrimaryDimensionOrganization.md)           | `getOrganization``()`<br>Gets the organization object for the `MdmPrimaryDimension`, which specifies whether the dimension is deployed in an analytic workspace or in a relational OLAP organization.                                                 |
    | [`MdmSchema`](MdmSchema.md)                                                               | `getOwner``()`<br>Gets the `MdmDatabaseSchema` that owns this `MdmPrimaryDimension`.                                                                                                                                                                  |
    | [`MdmAttribute`](MdmAttribute.md)                                                         | `getParentAttribute``()`<br>Gets the parent attribute for the `MdmPrimaryDimension`.                                                                                                                                                                  |
    | `java.util.List`                                                                          | `getPersistentLanguages``()`<br>Gets the languages in which descriptions are available of this `MdmPrimaryDimension` and the objects owned by it.                                                                                                     |
    | [`Query`](../../syntax/Query.md)                                                          | `getQuery``()`<br>Gets the `Query` that is associated with the `MdmPrimaryDimension`.                                                                                                                                                                 |
    | [`MdmQueryColumn`](MdmQueryColumn.md)                                                     | `getQueryColumn``(java.lang.String name)`<br>Gets the specified `MdmQueryColumn`.                                                                                                                                                                     |
    | `java.util.List<`[`MdmQueryColumn`](MdmQueryColumn.md)`>`                                 | `getQueryColumns``()`<br>Gets the `MdmQueryColumn` objects that are associated with this `MdmPrimaryDimension`.                                                                                                                                       |
    | `java.lang.String`                                                                        | `getQueryName``()`<br>Gets the identifier of this `MdmPrimaryDimension`.                                                                                                                                                                              |
    | [`MdmAttribute`](MdmAttribute.md)                                                         | `getShortValueDescriptionAttribute``()`<br>Gets the `MdmAttribute` that relates a short description to each member of the `MdmPrimaryDimension`.                                                                                                      |
    | [`MetadataObject`](../MetadataObject.md)                                                  | `getType``()`<br>Gets the OLAP Java API String data type.                                                                                                                                                                                             |
    | [`MdmAttribute`](MdmAttribute.md)                                                         | `getValueDescriptionAttribute``()`<br>Gets the `MdmAttribute` that relates a long description to each member `MdmPrimaryDimension`.                                                                                                                   |
    | [`MdmAttribute`](MdmAttribute.md)                                                         | `getValueLineageAttribute``()`<br>Gets the `MdmAttribute` that relates a lineage to each member of the `MdmPrimaryDimension`.                                                                                                                         |
    | `java.lang.String`                                                                        | `getValueSeparationString``()`<br>Gets the `String` that separates the hierarchy, level, and local value parts of the unique value of a member of the `MdmPrimaryDimension`.                                                                          |
    | `void`                                                                                    | `removeAttribute``(`[`MdmAttribute`](MdmAttribute.md)` attr)`<br>Removes the specified `MdmAttribute` from the attributes of this `MdmPrimaryDimension`.                                                                                              |
    | `void`                                                                                    | `removeDimensionLevel``(`[`MdmDimensionLevel`](MdmDimensionLevel.md)` level)`<br>Removes an `MdmDimensionLevel` from the `List` of `MdmDimensionLevel` objects associated with the `MdmPrimaryDimension`.                                             |
    | `void`                                                                                    | `removeHierarchy``(`[`MdmHierarchy`](MdmHierarchy.md)` hierarchy)`<br>Removes an `MdmHierarchy` from the components of the `MdmPrimaryDimension`.                                                                                                     |
    | `void`                                                                                    | `removeMdmCustomMember``(`[`MdmCustomMember`](MdmCustomMember.md)` member)`<br>Removes an `MdmCustomMember` from the `MdmPrimaryDimension`.                                                                                                           |
    | `void`                                                                                    | `removeModel``(`[`MdmDimensionCalculationModel`](MdmDimensionCalculationModel.md)` model)`<br>Removes an `MdmDimensionCalculationModel` from the `List` of `MdmDimensionCalculationModel` objects that are associated with the `MdmPrimaryDimension`. |
    | `void`                                                                                    | `setDefaultCalcModel``(`[`MdmDimensionCalculationModel`](MdmDimensionCalculationModel.md)` model)`<br>Specifies an `MdmDimensionCalculationModel` as the default for the `MdmPrimaryDimension`.                                                       |
    | `void`                                                                                    | `setDefaultHierarchy``(`[`MdmHierarchy`](MdmHierarchy.md)` hierarchy)`<br>Specifies a default hierarchy for the `MdmPrimaryDimension`.                                                                                                                |
    | `void`                                                                                    | `setETViewName``(java.lang.String name)`<br>Specifies a name for the ET (Embedded Totals) view that is associated with the `MdmPrimaryDimension`.                                                                                                     |
    | `void`                                                                                    | `setMemberListMap``(`[`MemberListMap`](../mapping/MemberListMap.md)` map)`<br>Specifies the `MemberListMap` to associate with the `MdmPrimaryDimension`.                                                                                              |
    | `void`                                                                                    | `setOwner``(`[`MdmDatabaseSchema`](MdmDatabaseSchema.md)` owner)`<br>Specifies an `MdmDatabaseSchema` as the owner of this `MdmPrimaryDimension`.                                                                                                     |
    | `void`                                                                                    | `setShortValueDescriptionAttribute``(`[`MdmAttribute`](MdmAttribute.md)` attr)`<br>Specifes an `MdmAttribute` that contains short descriptions for the members of the `MdmPrimaryDimension`.                                                          |
    | `void`                                                                                    | `setValueDescriptionAttribute``(`[`MdmAttribute`](MdmAttribute.md)` attr)`<br>Specifes an `MdmAttribute` that contains long descriptions for the members of the `MdmPrimaryDimension`.                                                                |
    | `void`                                                                                    | `setValueSeparationString``(java.lang.String sep)`<br>Specifies a `String` that separates the hierarchy, level, and local value parts of the unique value of a member of the `MdmPrimaryDimension`.                                                   |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmDimension](MdmDimension.md)

      [`getCardinality`](MdmDimension.md)`, `[`getCustomOrder`](MdmDimension.md)`, `[`getPluralDescription`](MdmDimension.md)`, `[`getPrimaryDimension`](MdmDimension.md)`, `[`getShortPluralDescription`](MdmDimension.md)`, `[`setCardinality`](MdmDimension.md)`, `[`setCustomOrder`](MdmDimension.md)`, `[`setPluralDescription`](MdmDimension.md)`, `[`setShortPluralDescription`](MdmDimension.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmSource](MdmSource.md)

      [`getDataType`](MdmSource.md)`, `[`getSource`](MdmSource.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmObject](MdmObject.md)

      [`acceptVisitor`](MdmObject.md)`, `[`addDescription`](MdmObject.md)`, `[`addObjectClassification`](MdmObject.md)`, `[`findOrCreateDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescription`](MdmObject.md)`, `[`getDescriptions`](MdmObject.md)`, `[`getMetadataProvider`](MdmObject.md)`, `[`getObjectClassifications`](MdmObject.md)`, `[`getShortDescription`](MdmObject.md)`, `[`isClassifiedAs`](MdmObject.md)`, `[`removeDescription`](MdmObject.md)`, `[`removeObjectClassification`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setDescription`](MdmObject.md)`, `[`setName`](MdmObject.md)`, `[`setShortDescription`](MdmObject.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getName`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getAncestorsAttribute

          public MdmAttribute getAncestorsAttribute()
                                             throws oracle.express.mdm.MetadataNotFoundException

      Gets the ancestors attribute for the `MdmPrimaryDimension`. The ancestors attribute relates each member of an `MdmHierarchy` to the ancestors of the member in the hierarchy. For example, the ancestors for a month in a time hierarchy might be quarter and year.
      Returns:
      The `MdmAttribute` that is the ancestors attribute of the `MdmPrimaryDimension`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### getHierarchies

          public final java.util.List getHierarchies()

      Gets a `List` that contains the components of the `MdmPrimaryDimension`, which are `MdmHierarchy` objects.
      Returns:
      A `List` that contains the components of the `MdmPrimaryDimension`.

    <!-- -->

    - #### getHierarchy

          public final MdmHierarchy getHierarchy(java.lang.String name)

      Gets the specified `MdmHierarchy` component of the `MdmPrimaryDimension`.
      Parameters:
      `name` - A `String` that contains the name of the `MdmHierarchy` to get.

      Returns:
      The `MdmHierarchy` that has the specified name.

    <!-- -->

    - #### getDefaultHierarchy

          public MdmHierarchy getDefaultHierarchy()

      Gets the default component of the `MdmPrimaryDimension`.
      Returns:
      The `MdmHierarchy` that is the default component of the `MdmPrimaryDimension`.

    <!-- -->

    - #### getParentAttribute

          public MdmAttribute getParentAttribute()
                                          throws oracle.express.mdm.MetadataNotFoundException

      Gets the parent attribute for the `MdmPrimaryDimension`. The parent attribute relates each member of the `MdmHierarchy` to the parent of the member in the hierarchy.
      Returns:
      The `MdmAttribute` that is the parent attribute of the `MdmPrimaryDimension`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### getShortValueDescriptionAttribute

          public final MdmAttribute getShortValueDescriptionAttribute()
                                                               throws oracle.express.mdm.MetadataNotFoundException

      Gets the `MdmAttribute` that relates a short description to each member of the `MdmPrimaryDimension`.
      Returns:
      The `MdmAttribute` that relates a short description to each member `MdmPrimaryDimension`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### getValueDescriptionAttribute

          public final MdmAttribute getValueDescriptionAttribute()
                                                          throws oracle.express.mdm.MetadataNotFoundException

      Gets the `MdmAttribute` that relates a long description to each member `MdmPrimaryDimension`.
      Returns:
      The `MdmAttribute` that relates a long description to each member of the components of the `MdmPrimaryDimension`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### getLevelAttribute

          public final MdmAttribute getLevelAttribute()

      Gets the `MdmAttribute` that relates the level of the hierarchy that a member of the hierarchy is in to each member of the `MdmPrimaryDimension`.
      Returns:
      The `MdmAttribute` that relates a level of a hierarchy to each member of the `MdmPrimaryDimension`.

    <!-- -->

    - #### getLevelDepthAttribute

          public final MdmAttribute getLevelDepthAttribute()

      Gets the `MdmAttribute` that relates the depth of the level of the hierarchy that a member of the hierarchy is in to each member of the `MdmPrimaryDimension`.
      Returns:
      The `MdmAttribute` that relates the depth of a level in a hierarchy to each member of the `MdmPrimaryDimension`.

    <!-- -->

    - #### getLocalValueAttribute

          public final MdmAttribute getLocalValueAttribute()
                                                    throws oracle.express.mdm.MetadataNotFoundException

      Gets the `MdmAttribute` that relates a local value to each member of the `MdmPrimaryDimension`.
      Returns:
      The `MdmAttribute` that relates a local value to each member of the `MdmPrimaryDimension`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### getHierarchyAttribute

          public final MdmAttribute getHierarchyAttribute()
                                                   throws oracle.express.mdm.MetadataNotFoundException

      Gets the `MdmAttribute` that relates a hierarchy to each member of the `MdmPrimaryDimension`.
      Returns:
      The `MdmAttribute` that relates a hierarchy to each member of the `MdmPrimaryDimension`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### getIsCustomMemberAttribute

          public final MdmAttribute getIsCustomMemberAttribute()
                                                        throws oracle.express.mdm.MetadataNotFoundException

      Gets the `MdmAttribute` that, for each member of the `MdmPrimaryDimension`, indicates whether that member is a custom member.
      Returns:
      The `MdmAttribute` that, for each member of the of the `MdmPrimaryDimension`, indicates whether that member is a custom member.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### getValueLineageAttribute

          public final MdmAttribute getValueLineageAttribute()
                                                      throws oracle.express.mdm.MetadataNotFoundException

      Gets the `MdmAttribute` that relates a lineage to each member of the `MdmPrimaryDimension`. The lineage is useful for display purposes.
      The lineage associated with a dimension member provides the ancestors of the member in the hierarchy. The ancestor member values are in brackets and are separated by periods. For example, the value lineage attribute value associated with item ENVY EXE of the Product dimension is the following.

             [TOTAL].[HRD].[LTPC].[ENVY EXE]

      The ancestor attribute returned by the `getAncestorAttribute` method associates each ancestor individually. The ancestor attribute values associated with item ENVY EXE are the following.

            PRODUCT_PRIMARY::TOTAL_PRODUCT::TOTAL
            PRODUCT_PRIMARY::CLASS::HRD
            PRODUCT_PRIMARY::FAMILY::LTPC
            PRODUCT_PRIMARY::ITEM::ENVY EXE

      Returns:
      The `MdmAttribute` that relates a lineage to each member of the `MdmPrimaryDimension`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### getValueSeparationString

          public final java.lang.String getValueSeparationString()

      Gets the `String` that separates the hierarchy, level, and local value parts of the unique value of a member of the `MdmPrimaryDimension`.
      Returns:
      The value separation string for the parts of a unique value of a member of the `MdmPrimaryDimension`.

    <!-- -->

    - #### getNamespace

          public final java.lang.String getNamespace()

      Gets the namespace of this `MdmPrimaryDimension`. For information on namespaces, see [Using Namespaces](MdmMetadataProvider.md) in the description of `MdmMetadataProvider`.
      Returns:
      A `String` that contains the namespace of this `MdmPrimaryDimension`.

    <!-- -->

    - #### setDefaultHierarchy

          public void setDefaultHierarchy(MdmHierarchy hierarchy)

      Specifies a default hierarchy for the `MdmPrimaryDimension`.
      Parameters:
      `hierarchy` - The `MdmHierarchy` to set as the default hierarchy for the `MdmPrimaryDimension`.

    <!-- -->

    - #### addHierarchy

          public void addHierarchy(MdmHierarchy hierarchy)

      Adds an `MdmHierarchy` to the `List` of `MdmHierarchy` objects associated with the `MdmPrimaryDimension`.
      Parameters:
      `hierarchy` - The `MdmHierarchy` to add to the dimension.

    <!-- -->

    - #### removeHierarchy

          public void removeHierarchy(MdmHierarchy hierarchy)

      Removes an `MdmHierarchy` from the components of the `MdmPrimaryDimension`.
      Parameters:
      `hierarchy` - The `MdmHierarchy` to remove from the `MdmPrimaryDimension`

    <!-- -->

    - #### setShortValueDescriptionAttribute

          public final void setShortValueDescriptionAttribute(MdmAttribute attr)

      Specifes an `MdmAttribute` that contains short descriptions for the members of the `MdmPrimaryDimension`.
      Parameters:
      `attr` - An `MdmAttribute` that relates short descriptions to members of the `MdmPrimaryDimension`.

    <!-- -->

    - #### setValueDescriptionAttribute

          public final void setValueDescriptionAttribute(MdmAttribute attr)

      Specifes an `MdmAttribute` that contains long descriptions for the members of the `MdmPrimaryDimension`.
      Parameters:
      `attr` - An `MdmAttribute` that relates long descriptions to members of the `MdmPrimaryDimension`.

    <!-- -->

    - #### setValueSeparationString

          public final void setValueSeparationString(java.lang.String sep)

      Specifies a `String` that separates the hierarchy, level, and local value parts of the unique value of a member of the `MdmPrimaryDimension`.
      Parameters:
      `sep` - The `String` to use as the value separation string for the parts of a unique value of a member of the `MdmPrimaryDimension`.

    <!-- -->

    - #### addDimensionLevel

          public final void addDimensionLevel(MdmDimensionLevel level)

      Adds an `MdmDimensionLevel` to the `List` of `MdmDimensionLevel` objects associated with the `MdmPrimaryDimension`.
      Parameters:
      `level` - The `MdmDimensionLevel` to add to the list of `MdmDimensionLevel` objects of the `MdmPrimaryDimension`.

    <!-- -->

    - #### removeDimensionLevel

          public final void removeDimensionLevel(MdmDimensionLevel level)

      Removes an `MdmDimensionLevel` from the `List` of `MdmDimensionLevel` objects associated with the `MdmPrimaryDimension`.
      Parameters:
      `level` - The `MdmDimensionLevel` to remove from the list of `MdmDimensionLevel` objects of the `MdmPrimaryDimension`.

    <!-- -->

    - #### getDimensionLevels

          public final java.util.List getDimensionLevels()

      Gets the `List` of the `MdmDimensionLevel` objects that are associated with the `MdmPrimaryDimension`.
      Returns:
      A `List` of the `MdmDimensionLevel` objects of the `MdmPrimaryDimension`.

    <!-- -->

    - #### addModel

          public final void addModel(MdmDimensionCalculationModel model)

      Adds an `MdmDimensionCalculationModel` to the `List` of `MdmDimensionCalculationModel` objects associated with the `MdmPrimaryDimension`.
      Parameters:
      `model` - The `MdmDimensionCalculationModel` to add to the list of `MdmDimensionCalculationModel` objects of the `MdmPrimaryDimension`.

    <!-- -->

    - #### removeModel

          public final void removeModel(MdmDimensionCalculationModel model)

      Removes an `MdmDimensionCalculationModel` from the `List` of `MdmDimensionCalculationModel` objects that are associated with the `MdmPrimaryDimension`.
      Parameters:
      `model` - The `MdmDimensionCalculationModel` to remove from the list of `MdmDimensionCalculationModel` objects of the `MdmPrimaryDimension`.

    <!-- -->

    - #### getModels

          public final java.util.List getModels()

      Gets the `List` of the `MdmDimensionCalculationModel` objects that are associated with the `MdmPrimaryDimension`.
      Returns:
      A `List` of the `MdmDimensionCalculationModel` objects of the `MdmPrimaryDimension`.

    <!-- -->

    - #### getDefaultCalcModel

          public final MdmDimensionCalculationModel getDefaultCalcModel()

      Gets the default `MdmDimensionCalculationModel` specified for the `MdmPrimaryDimension`.
      Returns:
      The default `MdmDimensionCalculationModel` for the `MdmPrimaryDimension`.

    <!-- -->

    - #### setDefaultCalcModel

          public final void setDefaultCalcModel(MdmDimensionCalculationModel model)

      Specifies an `MdmDimensionCalculationModel` as the default for the `MdmPrimaryDimension`.
      Parameters:
      `model` - The `MdmDimensionCalculationModel` to specify as the default for the dimension.

    <!-- -->

    - #### getOwner

          public final MdmSchema getOwner()

      Gets the `MdmDatabaseSchema` that owns this `MdmPrimaryDimension`.
      Overrides:
      [`getOwner`](../BaseMetadataObject.md) in class [`BaseMetadataObject`](../BaseMetadataObject.md)

      Returns:
      The `MdmDatabaseSchema` that owns this `MdmPrimaryDimension`.

    <!-- -->

    - #### setOwner

          public final void setOwner(MdmDatabaseSchema owner)

      Specifies an `MdmDatabaseSchema` as the owner of this `MdmPrimaryDimension`.
      Parameters:
      `owner` - The `MdmDatabaseSchema` to specify as the owner of this `MdmPrimaryDimension`.

    <!-- -->

    - #### getMemberListMap

          public final MemberListMap getMemberListMap()

      Gets the `MemberListMap` that is associated with the `MdmPrimaryDimension`. With this method you can get the `MemberListMap` of the dimension if one exists without creating a new `MemberListMap`.
      Specified by:
      [`getMemberListMap`](MdmMemberListMapOwner.md) in interface [`MdmMemberListMapOwner`](MdmMemberListMapOwner.md)

      Returns:
      The `MemberListMap` associated with the `MdmPrimaryDimension`.

    <!-- -->

    - #### setMemberListMap

          public final void setMemberListMap(MemberListMap map)

      Specifies the `MemberListMap` to associate with the `MdmPrimaryDimension`.
      Parameters:
      `map` - The `MemberListMap` to associate with the `MdmPrimaryDimension`.

    <!-- -->

    - #### getAttributes

          public java.util.List getAttributes()

      Gets a `List` of the `MdmAttribute` objects associated with the `MdmPrimaryDimension`.
      Specified by:
      [`getAttributes`](MdmDimension.md) in class [`MdmDimension`](MdmDimension.md)

      Returns:
      A `List` of the `MdmAttribute` objects for the `MdmPrimaryDimension`.

      See Also:
      [`MdmAttribute`](MdmAttribute.md)

    <!-- -->

    - #### removeAttribute

          public void removeAttribute(MdmAttribute attr)

      Removes the specified `MdmAttribute` from the attributes of this `MdmPrimaryDimension`.
      Specified by:
      [`removeAttribute`](MdmDimension.md) in class [`MdmDimension`](MdmDimension.md)

      Parameters:
      `attr` - The `MdmAttribute` to remove from this `MdmPrimaryDimension`.

    <!-- -->

    - #### getOrganization

          public final PrimaryDimensionOrganization getOrganization()

      Gets the organization object for the `MdmPrimaryDimension`, which specifies whether the dimension is deployed in an analytic workspace or in a relational OLAP organization.

    <!-- -->

    - #### findOrCreateAWPrimaryDimensionOrganization

          public final AWPrimaryDimensionOrganization findOrCreateAWPrimaryDimensionOrganization(AW aw)

      Gets the `AWPrimaryDimensionOrganization` for the `MdmPrimaryDimension` or creates a new `AWPrimaryDimensionOrganization` if one does not already exist.
      Parameters:
      `aw` - The `AW` object to associate with the `AWPrimaryDimensionOrganization`.

      Returns:
      The new or existing `AWPrimaryDimensionOrganization` for the `MdmPrimaryDimension`.

    <!-- -->

    - #### findOrCreateRolapPrimaryDimensionOrganization

          public final RolapPrimaryDimensionOrganization findOrCreateRolapPrimaryDimensionOrganization()

      Gets the `RolapPrimaryDimensionOrganization` for the `MdmPrimaryDimension` or creates a new `RolapPrimaryDimensionOrganization` if one does not already exist.
      Returns:
      The new or existing `RolapPrimaryDimensionOrganization` for the `MdmPrimaryDimension`.

    <!-- -->

    - #### getETViewName

          public final java.lang.String getETViewName()

      Gets the name of the ET (Embedded Totals) view that is associated with the `MdmPrimaryDimension`.
      Returns:
      A `String` that contains the name of the ET view.

    <!-- -->

    - #### setETViewName

          public final void setETViewName(java.lang.String name)

      Specifies a name for the ET (Embedded Totals) view that is associated with the `MdmPrimaryDimension`.
      Parameters:
      `name` - A `String` that contains the name for the ET view.

    <!-- -->

    - #### getETKeyColumn

          public final MdmViewColumn getETKeyColumn()

      Gets the key column of the ET (Embedded Totals) view that is associated with the `MdmPrimaryDimension`.
      Returns:
      An `MdmViewColumn` that represents the key column of the ET view.

    <!-- -->

    - #### getETLocalValueColumn

          public final MdmViewColumn getETLocalValueColumn()

      Gets the local value column of the ET (Embedded Totals) view that is associated with the `MdmPrimaryDimension`.
      Returns:
      An `MdmViewColumn` that represents the local value column of the ET view.

    <!-- -->

    - #### getETLevelNameColumn

          public final MdmViewColumn getETLevelNameColumn()

      Gets the level name column of the ET (Embedded Totals) view that is associated with the `MdmPrimaryDimension`.
      Returns:
      An `MdmViewColumn` that represents the level name column of the ET view.

    <!-- -->

    - #### getETMemberTypeColumn

          public final MdmViewColumn getETMemberTypeColumn()

      Gets the member type column of the ET (Embedded Totals) view that is associated with the `MdmPrimaryDimension`.
      Returns:
      An `MdmViewColumn` that represents the member type column of the ET view.

    <!-- -->

    - #### getETDimensionOrderColumn

          public final MdmViewColumn getETDimensionOrderColumn()

      Gets the dimension order column of the ET (Embedded Totals) view that is associated with the `MdmPrimaryDimension`.
      Returns:
      An `MdmViewColumn` that represents the dimension order column of the ET view.

    <!-- -->

    - #### getETHierarchyOrderColumn

          public final MdmViewColumn getETHierarchyOrderColumn()

      Gets the hierarchy order column of the ET (Embedded Totals) view that is associated with the `MdmPrimaryDimension`.
      Returns:
      An `MdmViewColumn` that represents the hierarchy order column of the ET view.

    <!-- -->

    - #### getQuery

          public final Query getQuery()

      Gets the `Query` that is associated with the `MdmPrimaryDimension`.
      Specified by:
      [`getQuery`](MdmQuery.md) in interface [`MdmQuery`](MdmQuery.md)

      Returns:
      The `Query` associated with the `MdmPrimaryDimension`.

    <!-- -->

    - #### getQueryColumns

          public final java.util.List<MdmQueryColumn> getQueryColumns()

      Gets the `MdmQueryColumn` objects that are associated with this `MdmPrimaryDimension`.
      Specified by:
      [`getQueryColumns`](MdmQuery.md) in interface [`MdmQuery`](MdmQuery.md)

      Returns:
      A `List` of the `MdmQueryColumn` objects associated with this `MdmPrimaryDimension`.

    <!-- -->

    - #### getQueryName

          public final java.lang.String getQueryName()

      Gets the identifier of this `MdmPrimaryDimension`.
      Specified by:
      [`getQueryName`](MdmQuery.md) in interface [`MdmQuery`](MdmQuery.md)

      Returns:
      A `String` that contains the identifier of this `MdmPrimaryDimension`.

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

    <!-- -->

    - #### getType

          public MetadataObject getType()

      Gets the OLAP Java API String data type. An `MdmPrimaryDimension` has String values.
      Specified by:
      [`getType`](MdmSource.md) in class [`MdmSource`](MdmSource.md)

      Returns:
      A `MetadataObject` that represents the OLAP Java API String data type.

    <!-- -->

    - #### findOrCreateLevelHierarchy

          public MdmLevelHierarchy findOrCreateLevelHierarchy(java.lang.String publicName)

      Gets the specified `MdmLevelHierarchy` or, if it does not already exist, creates a new one for the `MdmPrimaryDimension`.
      Parameters:
      `publicName` - A `String` that contains the name of the `MdmLevelHierarchy` to get or create.

      Returns:
      The specified `MdmLevelHierarchy` or a new one with the specified name.

    <!-- -->

    - #### findOrCreateValueHierarchy

          public MdmValueHierarchy findOrCreateValueHierarchy(java.lang.String publicName)

      Gets the specified `MdmValueHierarchy` or, if it does not already exist, creates a new one for the `MdmPrimaryDimension`.
      Parameters:
      `publicName` - A `String` that contains the name of the `MdmValueHierarchy` to get or create.

      Returns:
      The specified `MdmValueHierarchy` or a new one with the specified name.

    <!-- -->

    - #### findOrCreateDimensionLevel

          public MdmDimensionLevel findOrCreateDimensionLevel(java.lang.String publicName)

      Gets the specified `MdmDimensionLevel` or, if it does not already exist, creates a new one for the `MdmPrimaryDimension`.
      Parameters:
      `publicName` - A `String` that contains the name of the `MdmDimensionLevel` to get or create.

      Returns:
      The specified `MdmDimensionLevel` or a new one with the specified name.

    <!-- -->

    - #### findOrCreateDimCalcModel

          public MdmDimensionCalculationModel findOrCreateDimCalcModel(java.lang.String publicName)

      Gets the specified `MdmDimensionCalculationModel` or, if it does not already exist, creates a new one for the `MdmPrimaryDimension`.
      Parameters:
      `publicName` - A `String` that contains the name of the `MdmDimensionCalculationModel` to get or create.

      Returns:
      The specified `MdmDimensionCalculationModel` or a new one with the specified name.

    <!-- -->

    - #### findOrCreateBaseAttribute

          public MdmBaseAttribute findOrCreateBaseAttribute(java.lang.String publicName)

      Gets the specified `MdmBaseAttribute` or, if it does not already exist, creates a new one for the `MdmPrimaryDimension`. The public name of the `MdmBaseAttribute` is the `String` returned by the `getName` method of the `MdmBaseAttribute`. An application specifies the role of an `MdmBaseAttribute` with methods like `setValueDescriptionAttribute`.
      Parameters:
      `publicName` - A `String` that contains the name of the `MdmBaseAttribute` to get or create.

      Returns:
      The specified `MdmBaseAttribute` or a new one with the specified name.

    <!-- -->

    - #### findOrCreateMemberListMap

          public MemberListMap findOrCreateMemberListMap()

      Gets the `MemberListMap` for the `MdmPrimaryDimension` or, if one does not already exist, creates a new one.
      Specified by:
      [`findOrCreateMemberListMap`](MdmMemberListMapOwner.md) in interface [`MdmMemberListMapOwner`](MdmMemberListMapOwner.md)

      Returns:
      The `MemberListMap` for the `MdmPrimaryDimension`.

    <!-- -->

    - #### getPersistentLanguages

          public java.util.List getPersistentLanguages()

      Gets the languages in which descriptions are available of this `MdmPrimaryDimension` and the objects owned by it. The languages include those available for `AttributeMap` objects that are owned by `DimensionMap` objects that are owned directly or indirectly by the `MdmPrimaryDimension`.
      Returns:
      A `List` of `String` objects that contain the names of NLS languages.

    <!-- -->

    - #### getMdmCustomMembers

          public final java.util.List getMdmCustomMembers()

      Gets the `MdmCustomMember` objects that are associated with the `MdmPrimaryDimension`.
      Returns:
      A `List` of the `MdmCustomMember` objects that are associated with the `MdmPrimaryDimension`.

    <!-- -->

    - #### findOrCreateMdmCustomMember

          public MdmCustomMember findOrCreateMdmCustomMember(java.lang.String memberName)

      Gets the specified `MdmCustomMember` of the dimension or, if the custom member does not already exist, creates a new one.
      Parameters:
      `memberName` - A `String` that contains the name of and existing custom member or a name for the new custom member.

      Returns:
      The new or existing `MdmCustomMember`.

    <!-- -->

    - #### removeMdmCustomMember

          public final void removeMdmCustomMember(MdmCustomMember member)

      Removes an `MdmCustomMember` from the `MdmPrimaryDimension`.
      Parameters:
      `member` - The `MdmCustomMember` to remove from the `MdmPrimaryDimension`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmOrganizationalSchema.md)
- [Next Class](MdmQuery.md)

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
