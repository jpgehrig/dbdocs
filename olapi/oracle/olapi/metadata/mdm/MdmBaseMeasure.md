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

- [Prev Class](MdmBaseAttribute.md)
- [Next Class](MdmBaseObjectVisitor.md)

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

## Class MdmBaseMeasure

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - [oracle.olapi.metadata.mdm.MdmDimensionedObject](MdmDimensionedObject.md)

          - - [oracle.olapi.metadata.mdm.MdmMeasure](MdmMeasure.md)

            - - oracle.olapi.metadata.mdm.MdmBaseMeasure

<!-- -->

- All Implemented Interfaces:
  [MdmMember](MdmMember.md), [MdmQueryColumn](MdmQueryColumn.md), [MdmViewColumnOwner](MdmViewColumnOwner.md), [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public class MdmBaseMeasure
      extends MdmMeasure

  An `MdmMeasure` that is mapped to a persistent physical storage structure. An `MdmBaseMeasure` can have a `ConsistentSolveSpecification` that specifies how Oracle OLAP generates solved data for the measure.
  With the [`findOrCreateBaseMeasure`](MdmCube.md) method of an `MdmCube`, you can get an existing `MdmBaseMeasure` or create a new one. Committing the `Transaction` in which you create a base measure makes the `MdmBaseMeasure` a persistent object. It adds the `MdmBaseMeasure` to the data dictionary, which makes it available to other applications.

  When you create an `MdmBaseMeasure`, you can specify a SQL data type for it with the `setSQLDataType` method. If you do not specify a SQL data type but you do associate a `MeasureMap` with the measure, Oracle OLAP automatically sets the SQL data type of the measure to be the data type of the `Expression` in the `MeasureMap`. If the `MdmBaseMeasure` has no `MeasureMap` and has no specified SQL data type, Oracle OLAP assigns it the default SQL data type of NUMBER.

  For an existing `MdmBaseMeasure`, the AllowAutoDataTypeChange property of the measure determines how the SQL data type can change. If the AllowAutoDataTypeChange property is `false`, which is the default setting, you can only change the SQL data type of the measure by using the `setSQLDataType` method; adding or removing `MeasureMap` objects, or changing the `Expression` of a `MeasureMap`, does not change the SQL data type of the `MdmBaseMeasure`.

  However, if the AllowAutoDataTypeChange property is `true`, then the `setSQLDataType` method does not change the SQL data type of the `MdmBaseMeasure`. Instead, Oracle OLAP automatically sets the SQL data type of the `MdmBaseMeasure` to the data type that is common to all of the `Expression` objects in the `MeasureMap` objects that are associated with the `MdmBaseMeasure`. Therefore, if the AllowAutoDataTypeChange property is `true`, then adding or removing a `MeasureMap` in a `CubeMap`, or changing the `Expression` of a `MeasureMap`, may change the SQL data type of the `MdmBaseMeasure`. You can set the value of the AllowAutoDataTypeChange property with the `setAllowAutoDataTypeChange` method.

  You can get the SQL data type with the `getSQLDataType` method. For the data type returned in the various conditions, see [Possible Data Types Returned by getSQLDataType](doc-files/pdtr.md) table.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                              | Method and Description                                                                                                                                                                                                             |
    |--------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                                                             | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmBaseMeasure` method of the `MdmObjectVisitor` and passes that method this `MdmBaseMeasure` and an `Object`. |
    | `boolean`                                                                      | `allowAutoDataTypeChange``()`<br>Indicates whether Oracle OLAP is allowed to automatically change the data type of the measure.                                                                                                    |
    | [`ConsistentSolveSpecification`](../../syntax/ConsistentSolveSpecification.md) | `getConsistentSolveSpecification``()`<br>Gets the `ConsistentSolveSpecification` specified for this `MdmBaseMeasure`.                                                                                                              |
    | [`SQLDataType`](../../syntax/SQLDataType.md)                                   | `getSQLDataType``()`<br>Gets the SQL data type for the `MdmBaseMeasure`.                                                                                                                                                           |
    | `void`                                                                         | `setAllowAutoDataTypeChange``(boolean allowAutoDataTypeChange)`<br>Specifies whether to allow Oracle OLAP to automatically change the data type of the measure.                                                                    |
    | `void`                                                                         | `setConsistentSolveSpecification``(`[`ConsistentSolveSpecification`](../../syntax/ConsistentSolveSpecification.md)` input)`<br>Specifies a `ConsistentSolveSpecification` for this `MdmBaseMeasure`.                               |
    | `void`                                                                         | `setSQLDataType``(`[`SQLDataType`](../../syntax/SQLDataType.md)` type)`<br>Specifies a SQL data type for the `MdmBaseMeasure`.                                                                                                     |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmMeasure](MdmMeasure.md)

      [`addDimensionality`](MdmMeasure.md)`, `[`getColumnObject`](MdmMeasure.md)`, `[`getCube`](MdmMeasure.md)`, `[`getDimensionality`](MdmMeasure.md)`, `[`getETMeasureColumn`](MdmMeasure.md)`, `[`getLevel`](MdmMeasure.md)`, `[`getLevelDepth`](MdmMeasure.md)`, `[`getLocalValue`](MdmMeasure.md)`, `[`getMeasureDimension`](MdmMeasure.md)`, `[`getOwnerDimension`](MdmMeasure.md)`, `[`getParentLevel`](MdmMeasure.md)`, `[`getParentLocalValue`](MdmMeasure.md)`, `[`getParentValue`](MdmMeasure.md)`, `[`getPrecedence`](MdmMeasure.md)`, `[`getType`](MdmMeasure.md)`, `[`getUnits`](MdmMeasure.md)`, `[`getValue`](MdmMeasure.md)`, `[`getValueFormat`](MdmMeasure.md)`, `[`removeDimensionality`](MdmMeasure.md)`, `[`setCube`](MdmMeasure.md)`, `[`setUnits`](MdmMeasure.md)`, `[`setValueFormat`](MdmMeasure.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmDimensionedObject](MdmDimensionedObject.md)

      [`addDimension`](MdmDimensionedObject.md)`, `[`getDimensions`](MdmDimensionedObject.md)`, `[`isBooleanValued`](MdmDimensionedObject.md)`, `[`setBooleanValued`](MdmDimensionedObject.md)

    <!-- -->

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

    - ### Methods inherited from interface oracle.olapi.metadata.mdm.[MdmQueryColumn](MdmQueryColumn.md)

      [`getName`](MdmQueryColumn.md)

<!-- -->

- - ### Method Detail

    - #### acceptVisitor

          public java.lang.Object acceptVisitor(MdmObjectVisitor visitor,
                                                java.lang.Object context)

      Calls the `visitMdmBaseMeasure` method of the `MdmObjectVisitor` and passes that method this `MdmBaseMeasure` and an `Object`.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor` that is an instance of `Mdm11_ObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmBaseMeasure` method.

    <!-- -->

    - #### getConsistentSolveSpecification

          public final ConsistentSolveSpecification getConsistentSolveSpecification()

      Gets the `ConsistentSolveSpecification` specified for this `MdmBaseMeasure`.
      Returns:
      The `ConsistentSolveSpecification` for this `MdmBaseMeasure`.

    <!-- -->

    - #### setConsistentSolveSpecification

          public final void setConsistentSolveSpecification(ConsistentSolveSpecification input)

      Specifies a `ConsistentSolveSpecification` for this `MdmBaseMeasure`.
      Parameters:
      `input` - The `ConsistentSolveSpecification` to associate with this `MdmBaseMeasure`.

    <!-- -->

    - #### getSQLDataType

          public final SQLDataType getSQLDataType()

      Gets the SQL data type for the `MdmBaseMeasure`. Oracle OLAP determines the data type in one of the following ways.
      - If the `MdmBaseMeasure` has the AllowAutoDataTypeChange property set to `true`:
        - If the `MdmBaseMeasure` has `MeasureMap` objects that are associated with it, then the data type is the common data type of all of the `Expression` objects of the `MeasureMap` objects.
          **Note:**An `MdmBaseMeasure` typically has only one `MeasureMap`. However, a single `MdmBaseMeasure` can have multiple `MeasureMap` objects, with each `MeasureMap` contained by a different `CubeMap`.
        - If the `MdmBaseMeasure` has no associated `MeasureMap` objects, then the data type is the default type, which is NUMBER.
      - If the `MdmBaseMeasure` has the AllowAutoDataTypeChange property set to `false`, which is the default value:
        - If the SQL data type has been specified by a call to the `setSQLDataType` method of the measure, then the data type is the one specified by that method.
        - If the SQL data type has not been specified by a call to the `setSQLDataType` method of the measure and the `MdmBaseMeasure` has one or more `MeasureMap` objects associated with it, then the data type is the common data type of all of the `Expression` objects of the `MeasureMap` objects that were associated with the `MdmBaseMeasure` when it was first committed. If the `MdmBaseMeasure` had no associated `MeasureMap` objects when it was first committed, then the data type is the default type, NUMBER.

      For the data type returned in the various conditions, see [Possible Data Types Returned by getSQLDataType](doc-files/pdtr.md).
      Returns:
      A `SQLDataType` that represents the SQL data type.

      See Also:
      `allowAutoDataTypeChange()`, `setAllowAutoDataTypeChange(boolean allowAutoDataTypeChange)`

    <!-- -->

    - #### setSQLDataType

          public final void setSQLDataType(SQLDataType type)

      Specifies a SQL data type for the `MdmBaseMeasure`. If the `MdmBaseMeasure` does not have a specified SQL data type and the measure has one or more associated `MeasureMap` objects with valid expressions, then Oracle OLAP uses the common data type of the values specified by the mappings. If you do not specify a SQL data type and the measure does not have an associated `MeasureMap`, then Oracle OLAP uses the default SQL data type of NUMBER.
      If the AutoDataTypeChange property of the `MdmBaseMeasure` is set to true, then Oracle OLAP ignores the data type specified by this method and automatically sets the SQL data type.

      Parameters:
      `type` - The `SQLDataType` to use as the data type for the `MdmBaseMeasure`.

      See Also:
      `allowAutoDataTypeChange()`, `setAllowAutoDataTypeChange(boolean allowAutoDataTypeChange)`

    <!-- -->

    - #### allowAutoDataTypeChange

          public final boolean allowAutoDataTypeChange()

      Indicates whether Oracle OLAP is allowed to automatically change the data type of the measure.
      Returns:
      A `boolean` that is `true` if Oracle OLAP can automatically change the data type of the measure or `false` otherwise.

    <!-- -->

    - #### setAllowAutoDataTypeChange

          public final void setAllowAutoDataTypeChange(boolean allowAutoDataTypeChange)

      Specifies whether to allow Oracle OLAP to automatically change the data type of the measure. If you specify `true` to allow the automatic changing of data types, then Oracle OLAP evaluates the expressions of the `MeasureMap` of each `CubeMap` object of the `MdmCube` that contains the measure. Based on the data types of those expressions, Oracle OLAP determines the appropriate data type for the measure. If the measure mappings have different data types, then Oracle OLAP automatically assigns a data type that is a common supertype of all of the mapped expressions.
      Parameters:
      `allowAutoDataTypeChange` - Specify `true` if you want to allow Oracle OLAP to automatically change the data type of the measure or `false` otherwise.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmBaseAttribute.md)
- [Next Class](MdmBaseObjectVisitor.md)

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
