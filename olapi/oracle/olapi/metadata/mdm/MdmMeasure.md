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

- [Prev Class](MdmLevelHierarchy.md)
- [Next Class](MdmMeasureDimension.md)

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

## Class MdmMeasure

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - [oracle.olapi.metadata.mdm.MdmDimensionedObject](MdmDimensionedObject.md)

          - - oracle.olapi.metadata.mdm.MdmMeasure

<!-- -->

- All Implemented Interfaces:
  [MdmMember](MdmMember.md), [MdmQueryColumn](MdmQueryColumn.md), [MdmViewColumnOwner](MdmViewColumnOwner.md), [MetadataObject](../MetadataObject.md)

  <!-- -->

  Direct Known Subclasses:
  [MdmBaseMeasure](MdmBaseMeasure.md), [MdmDerivedMeasure](MdmDerivedMeasure.md)

  ------------------------------------------------------------------------



      public abstract class MdmMeasure
      extends MdmDimensionedObject
      implements MdmMember, MdmViewColumnOwner, MdmQueryColumn

  An `MdmDimensionedObject` that represents a set of data to use in analytical processing. An `MdmMeasure` is owned by an `MdmCube`. The dimensionality of the `MdmMeasure` is defined by the `MdmCube`. The type of an `MdmMeasure` is based on the data type of the information that the `MdmMeasure` represents.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                | Method and Description                                                                                                                 |
    |--------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                           | `addDimensionality``(`[`MdmDimensionality`](MdmDimensionality.md)` value)`<br>Adds an `MdmDimensionality` to the `MdmMeasure`.         |
    | [`BaseMetadataObject`](../BaseMetadataObject.md) | `getColumnObject``()`<br>Gets the Column                                                                                               |
    | [`MdmCube`](MdmCube.md)                          | `getCube``()`<br>Gets the `MdmCube` that is associated with this `MdmMeasure`.                                                         |
    | `java.util.List`                                 | `getDimensionality``()`<br>Gets the `MdmDimensionality` objects that are associated with the `MdmMeasure`.                             |
    | [`MdmViewColumn`](MdmViewColumn.md)              | `getETMeasureColumn``()`<br>Gets the ET (Embedded Totals) column for the `MdmMeasure`.                                                 |
    | [`MdmLevel`](MdmLevel.md)                        | `getLevel``()`<br>Gets the `MdmLevel` of the `MdmMeasureDimension` of which the `MdmMeasure` is a member.                              |
    | `int`                                            | `getLevelDepth``()`<br>Because an `MdmMeasureDimension` has only one level, this method returns `0`.                                   |
    | `java.lang.String`                               | `getLocalValue``()`<br>Gets the local value of this `MdmMeasure`, which is its name.                                                   |
    | [`MdmMeasureDimension`](MdmMeasureDimension.md)  | `getMeasureDimension``()`<br>Gets the `MdmMeasureDimension` of the `MdmRootSchema`.                                                    |
    | [`MdmPrimaryDimension`](MdmPrimaryDimension.md)  | `getOwnerDimension``()`<br>Gets the `MdmPrimaryDimension` of which this `MdmMeasure` is a member.                                      |
    | [`MdmLevel`](MdmLevel.md)                        | `getParentLevel``()`<br>Because an `MdmMeasure` does not have a parent in a dimension hierarchy, this method returns `null`.           |
    | `java.lang.String`                               | `getParentLocalValue``()`<br>Because an `MdmMeasure` does not have a parent in a dimension hierarchy, this method returns `null`.      |
    | `java.lang.String`                               | `getParentValue``()`<br>Because an `MdmMeasure` does not have a parent in a dimension hierarchy, this method returns `null`.           |
    | `int`                                            | `getPrecedence``()`<br>Gets the precedence of this `MdmMeasure`.                                                                       |
    | [`MetadataObject`](../MetadataObject.md)         | `getType``()`<br>Gets the OLAP Java API data type for the `MdmMeasure`.                                                                |
    | `java.lang.String`                               | `getUnits``()`<br>Gets the type of units specified for this `MdmMeasure`.                                                              |
    | `java.lang.String`                               | `getValue``()`<br>Gets the value of this `MdmMeasure`, which is the identifier for the `Source` for this `MdmMeasure`.                 |
    | `java.lang.String`                               | `getValueFormat``()`<br>Gets the format specified for the values of this `MdmMeasure`.                                                 |
    | `void`                                           | `removeDimensionality``(`[`MdmDimensionality`](MdmDimensionality.md)` value)`<br>Removes an `MdmDimensionality` from the `MdmMeasure`. |
    | `void`                                           | `setCube``(`[`MdmCube`](MdmCube.md)` input)`<br>Specifies the `MdmCube` to associate with this `MdmMeasure`.                           |
    | `void`                                           | `setUnits``(java.lang.String newUnits)`<br>Specifies a type of units for the values of this `MdmMeasure`.                              |
    | `void`                                           | `setValueFormat``(java.lang.String formatString)`<br>Specifies a format for the values of this `MdmMeasure`.                           |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmDimensionedObject](MdmDimensionedObject.md)

      [`addDimension`](MdmDimensionedObject.md)`, `[`getDimensions`](MdmDimensionedObject.md)`, `[`isBooleanValued`](MdmDimensionedObject.md)`, `[`setBooleanValued`](MdmDimensionedObject.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmSource](MdmSource.md)

      [`getDataType`](MdmSource.md)`, `[`getSource`](MdmSource.md)

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

    - ### Methods inherited from interface oracle.olapi.metadata.mdm.[MdmMember](MdmMember.md)

      [`getDataType`](MdmMember.md)`, `[`getDescription`](MdmMember.md)`, `[`getShortDescription`](MdmMember.md)`, `[`getSource`](MdmMember.md)

    <!-- -->

    - ### Methods inherited from interface oracle.olapi.metadata.mdm.[MdmQueryColumn](MdmQueryColumn.md)

      [`getName`](MdmQueryColumn.md)`, `[`getSQLDataType`](MdmQueryColumn.md)

<!-- -->

- - ### Method Detail

    - #### getValue

          public java.lang.String getValue()

      Gets the value of this `MdmMeasure`, which is the identifier for the `Source` for this `MdmMeasure`.
      Specified by:
      [`getValue`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      A `String` that is the identifier for the `Source` for this `MdmMeasure`.

    <!-- -->

    - #### getLocalValue

          public java.lang.String getLocalValue()

      Gets the local value of this `MdmMeasure`, which is its name.
      Specified by:
      [`getLocalValue`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      A `String` that contains the local value of this `MdmMeasure`.

    <!-- -->

    - #### getOwnerDimension

          public MdmPrimaryDimension getOwnerDimension()

      Gets the `MdmPrimaryDimension` of which this `MdmMeasure` is a member. An `MdmMeasure` can be a member of an `MdmMeasureDimension`.
      Specified by:
      [`getOwnerDimension`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      The `MdmPrimaryDimension` of which this `MdmMeasure` is a member.

    <!-- -->

    - #### getMeasureDimension

          public MdmMeasureDimension getMeasureDimension()

      Gets the `MdmMeasureDimension` of the `MdmRootSchema`. All `MdmMeasure` objects provided by the `MdmMetadataProvider` are members of that `MdmMeasureDimension`.
      Returns:
      The `MdmMeasureDimension` of the `MdmRootSchema`.

    <!-- -->

    - #### getLevel

          public MdmLevel getLevel()

      Gets the `MdmLevel` of the `MdmMeasureDimension` of which the `MdmMeasure` is a member.
      Specified by:
      [`getLevel`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      The `MdmLevel` of the `MdmMeasureDimension`.

    <!-- -->

    - #### getLevelDepth

          public int getLevelDepth()

      Because an `MdmMeasureDimension` has only one level, this method returns `0`.
      Specified by:
      [`getLevelDepth`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      An integer that indicates the level of this `MdmMeasure` in the `MdmMeasureDimension`.

    <!-- -->

    - #### getParentValue

          public java.lang.String getParentValue()

      Because an `MdmMeasure` does not have a parent in a dimension hierarchy, this method returns `null`.
      Specified by:
      [`getParentValue`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      This method returns `null`.

    <!-- -->

    - #### getParentLocalValue

          public java.lang.String getParentLocalValue()

      Because an `MdmMeasure` does not have a parent in a dimension hierarchy, this method returns `null`.
      Specified by:
      [`getParentLocalValue`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      This method returns `null`.

    <!-- -->

    - #### getParentLevel

          public MdmLevel getParentLevel()

      Because an `MdmMeasure` does not have a parent in a dimension hierarchy, this method returns `null`.
      Specified by:
      [`getParentLevel`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      This method returns `null`.

    <!-- -->

    - #### getPrecedence

          public int getPrecedence()

      Gets the precedence of this `MdmMeasure`.
      Specified by:
      [`getPrecedence`](MdmMember.md) in interface [`MdmMember`](MdmMember.md)

      Returns:
      An integer that specifies the precedence of this `MdmMeasure`.

    <!-- -->

    - #### getValueFormat

          public java.lang.String getValueFormat()

      Gets the format specified for the values of this `MdmMeasure`.
      Returns:
      A `String` that specifes an Oracle `COLUMN FORMAT` for the values of this `MdmMeasure`.

    <!-- -->

    - #### setValueFormat

          public void setValueFormat(java.lang.String formatString)

      Specifies a format for the values of this `MdmMeasure`.
      Parameters:
      `formatString` - A `String` that specifes an Oracle `COLUMN FORMAT` to use for the values of this `MdmMeasure`.

    <!-- -->

    - #### getUnits

          public java.lang.String getUnits()

      Gets the type of units specified for this `MdmMeasure`.
      Returns:
      A `String` that indicates the type of units for the values of this `MdmMeasure`.

    <!-- -->

    - #### setUnits

          public void setUnits(java.lang.String newUnits)

      Specifies a type of units for the values of this `MdmMeasure`. For example, the following code specifies `kilograms` as the type of units for the values of the `MdmMeasure` `mdmWeight`.
           mdmWeight.setUnits("kilograms");

      Parameters:
      `newUnits` - A `String` that indicates the type of units for the values of this `MdmMeasure`.

    <!-- -->

    - #### getCube

          public final MdmCube getCube()

      Gets the `MdmCube` that is associated with this `MdmMeasure`.
      Returns:
      The `MdmCube` associated with this `MdmMeasure`.

    <!-- -->

    - #### setCube

          public final void setCube(MdmCube input)

      Specifies the `MdmCube` to associate with this `MdmMeasure`.
      Parameters:
      `input` - The `MdmCube` to associate with this `MdmMeasure`.

    <!-- -->

    - #### getDimensionality

          public final java.util.List getDimensionality()

      Gets the `MdmDimensionality` objects that are associated with the `MdmMeasure`. An `MdmDimensionality` contains a reference to an `MdmDimension`.
      Overrides:
      [`getDimensionality`](MdmDimensionedObject.md) in class [`MdmDimensionedObject`](MdmDimensionedObject.md)

      Returns:
      A `List` of the `MdmDimensionality` objects associated with the `MdmMeasure`.

    <!-- -->

    - #### addDimensionality

          public final void addDimensionality(MdmDimensionality value)

      Adds an `MdmDimensionality` to the `MdmMeasure`.
      Overrides:
      [`addDimensionality`](MdmDimensionedObject.md) in class [`MdmDimensionedObject`](MdmDimensionedObject.md)

      Parameters:
      `value` - The `MdmDimensionality` to add to the `MdmMeasure`.

    <!-- -->

    - #### removeDimensionality

          public final void removeDimensionality(MdmDimensionality value)

      Removes an `MdmDimensionality` from the `MdmMeasure`.
      Overrides:
      [`removeDimensionality`](MdmDimensionedObject.md) in class [`MdmDimensionedObject`](MdmDimensionedObject.md)

      Parameters:
      `value` - The `MdmDimensionality` to remove from the `MdmMeasure`.

    <!-- -->

    - #### getETMeasureColumn

          public MdmViewColumn getETMeasureColumn()

      Gets the ET (Embedded Totals) column for the `MdmMeasure`.
      Returns:
      The `MdmViewColumn` that represents the ET column.

    <!-- -->

    - #### getType

          public final MetadataObject getType()

      Gets the OLAP Java API data type for the `MdmMeasure`.
      Specified by:
      [`getType`](MdmSource.md) in class [`MdmSource`](MdmSource.md)

      Returns:
      A `MetadataObject` that represents the OLAP Java API data type.

    <!-- -->

    - #### getColumnObject

          public BaseMetadataObject getColumnObject()

      Gets the Column
      Specified by:
      [`getColumnObject`](MdmQueryColumn.md) in interface [`MdmQueryColumn`](MdmQueryColumn.md)

      Returns:
      A `BaseMetadataObject` that represents the column

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmLevelHierarchy.md)
- [Next Class](MdmMeasureDimension.md)

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
