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

- [Prev Class](MdmInvalidValueException.md)
- [Next Class](MdmLevelHierarchy.md)

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

## Class MdmLevel

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - [oracle.olapi.metadata.mdm.MdmDimension](MdmDimension.md)

          - - [oracle.olapi.metadata.mdm.MdmSubDimension](MdmSubDimension.md)

            - - [oracle.olapi.metadata.mdm.MdmHierarchyLevel](MdmHierarchyLevel.md)

              - - oracle.olapi.metadata.mdm.MdmLevel

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------

  Deprecated. 
  As of Oracle 11g, Release 1 (11.1); replaced by [`MdmHierarchyLevel`](MdmHierarchyLevel.md).


      public class MdmLevel
      extends MdmHierarchyLevel

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                                                    |
    |---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `LEVELTYPE_DAY`<br>Deprecated. <br>As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.LEVEL_TYPE_DAY`](MdmDimensionLevel.md)            |
    | `static java.lang.String` | `LEVELTYPE_HALFYEAR`<br>Deprecated. <br>As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.LEVEL_TYPE_HALFYEAR`](MdmDimensionLevel.md). |
    | `static java.lang.String` | `LEVELTYPE_HOUR`<br>Deprecated. <br>As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.LEVEL_TYPE_HOUR`](MdmDimensionLevel.md)          |
    | `static java.lang.String` | `LEVELTYPE_MINUTE`<br>Deprecated. <br>As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.LEVEL_TYPE_MINUTE`](MdmDimensionLevel.md)      |
    | `static java.lang.String` | `LEVELTYPE_MONTH`<br>Deprecated. <br>As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.LEVEL_TYPE_MONTH`](MdmDimensionLevel.md)        |
    | `static java.lang.String` | `LEVELTYPE_QUARTER`<br>Deprecated. <br>As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.LEVEL_TYPE_QUARTER`](MdmDimensionLevel.md).   |
    | `static java.lang.String` | `LEVELTYPE_SECOND`<br>Deprecated. <br>As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.LEVEL_TYPE_SECOND`](MdmDimensionLevel.md)      |
    | `static java.lang.String` | `LEVELTYPE_STANDARD`<br>Deprecated. <br>As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.LEVEL_TYPE_STANDARD`](MdmDimensionLevel.md). |
    | `static java.lang.String` | `LEVELTYPE_WEEK`<br>Deprecated. <br>As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.LEVEL_TYPE_WEEK`](MdmDimensionLevel.md)          |
    | `static java.lang.String` | `LEVELTYPE_YEAR`<br>Deprecated. <br>As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.LEVEL_TYPE_YEAR`](MdmDimensionLevel.md).         |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                       | Method and Description                                                                                                                                                                                                         |
    |-----------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                      | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Deprecated. <br>As of Oracle 11g, Release 1 (11.1); replaced by [`MdmHierarchyLevel.acceptVisitor`](MdmHierarchyLevel.md). |
    | `oracle.olapi.metadata.mtm.MtmLevelMap` | `getLevelMap``()`<br>Deprecated. <br>As of Oracle 11g, Release 1 (11.1); replaced by [`getHierarchyLevelMap`](MdmHierarchyLevel.md).                                                                                           |
    | `java.lang.String`                      | `getLevelType``()`<br>Deprecated. <br>As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.getLevelType`](MdmDimensionLevel.md)                                                                                 |
    | `void`                                  | `setLevelType``(java.lang.String levelType)`<br>Deprecated. <br>As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.setLevelType`](MdmDimensionLevel.md)                                                       |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmHierarchyLevel](MdmHierarchyLevel.md)

      [`findOrCreateHierarchyLevelMap`](MdmHierarchyLevel.md)`, `[`getDimensionLevel`](MdmHierarchyLevel.md)`, `[`getHierarchyLevelMap`](MdmHierarchyLevel.md)`, `[`getLevelDepth`](MdmHierarchyLevel.md)`, `[`getLevelHierarchy`](MdmHierarchyLevel.md)`, `[`getName`](MdmHierarchyLevel.md)`, `[`setHierarchyLevelMap`](MdmHierarchyLevel.md)

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

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### LEVELTYPE_STANDARD

          public static final java.lang.String LEVELTYPE_STANDARD

      Deprecated. As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.LEVEL_TYPE_STANDARD`](MdmDimensionLevel.md).
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVELTYPE_YEAR

          public static final java.lang.String LEVELTYPE_YEAR

      Deprecated. As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.LEVEL_TYPE_YEAR`](MdmDimensionLevel.md).
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVELTYPE_HALFYEAR

          public static final java.lang.String LEVELTYPE_HALFYEAR

      Deprecated. As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.LEVEL_TYPE_HALFYEAR`](MdmDimensionLevel.md).
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVELTYPE_QUARTER

          public static final java.lang.String LEVELTYPE_QUARTER

      Deprecated. As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.LEVEL_TYPE_QUARTER`](MdmDimensionLevel.md).
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVELTYPE_MONTH

          public static final java.lang.String LEVELTYPE_MONTH

      Deprecated. As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.LEVEL_TYPE_MONTH`](MdmDimensionLevel.md)
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVELTYPE_WEEK

          public static final java.lang.String LEVELTYPE_WEEK

      Deprecated. As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.LEVEL_TYPE_WEEK`](MdmDimensionLevel.md)
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVELTYPE_DAY

          public static final java.lang.String LEVELTYPE_DAY

      Deprecated. As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.LEVEL_TYPE_DAY`](MdmDimensionLevel.md)
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVELTYPE_HOUR

          public static final java.lang.String LEVELTYPE_HOUR

      Deprecated. As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.LEVEL_TYPE_HOUR`](MdmDimensionLevel.md)
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVELTYPE_MINUTE

          public static final java.lang.String LEVELTYPE_MINUTE

      Deprecated. As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.LEVEL_TYPE_MINUTE`](MdmDimensionLevel.md)
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LEVELTYPE_SECOND

          public static final java.lang.String LEVELTYPE_SECOND

      Deprecated. As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.LEVEL_TYPE_SECOND`](MdmDimensionLevel.md)
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### acceptVisitor

          public java.lang.Object acceptVisitor(MdmObjectVisitor visitor,
                                                java.lang.Object context)

      Deprecated. As of Oracle 11g, Release 1 (11.1); replaced by [`MdmHierarchyLevel.acceptVisitor`](MdmHierarchyLevel.md).
      Description copied from class: [`MdmHierarchyLevel`](MdmHierarchyLevel.md)
      Calls the `visitMdmHierarchyLevel` method of the specified `MdmObjectVisitor` and passes that method this `MdmHierarchyLevel` and an `Object`.
      Overrides:
      [`acceptVisitor`](MdmHierarchyLevel.md) in class [`MdmHierarchyLevel`](MdmHierarchyLevel.md)

      Parameters:
      `visitor` - An `Mdm11_ObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmHierarchyLevel` method.

    <!-- -->

    - #### getLevelType

          public java.lang.String getLevelType()
                                        throws oracle.express.mdm.MetadataNotFoundException

      Deprecated. As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.getLevelType`](MdmDimensionLevel.md)
      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### setLevelType

          public void setLevelType(java.lang.String levelType)
                            throws MdmInvalidValueException

      Deprecated. As of Oracle 11g, Release 1 (11.1); replaced by [`MdmDimensionLevel.setLevelType`](MdmDimensionLevel.md)
      Throws:
      [`MdmInvalidValueException`](MdmInvalidValueException.md)

    <!-- -->

    - #### getLevelMap

          public oracle.olapi.metadata.mtm.MtmLevelMap getLevelMap()
                                                            throws oracle.express.mdm.MetadataNotFoundException

      Deprecated. As of Oracle 11g, Release 1 (11.1); replaced by [`getHierarchyLevelMap`](MdmHierarchyLevel.md).
      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmInvalidValueException.md)
- [Next Class](MdmLevelHierarchy.md)

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
