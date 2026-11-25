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

- [Prev Class](MdmDerivedAttribute.md)
- [Next Class](MdmDescription.md)

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

## Class MdmDerivedMeasure

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - [oracle.olapi.metadata.mdm.MdmDimensionedObject](MdmDimensionedObject.md)

          - - [oracle.olapi.metadata.mdm.MdmMeasure](MdmMeasure.md)

            - - oracle.olapi.metadata.mdm.MdmDerivedMeasure

<!-- -->

- All Implemented Interfaces:
  [MdmMember](MdmMember.md), [MdmQueryColumn](MdmQueryColumn.md), [MdmViewColumnOwner](MdmViewColumnOwner.md), [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public class MdmDerivedMeasure
      extends MdmMeasure

  An `MdmMeasure` that has values that Oracle OLAP derives from an `Expression`. The values of an `MdmDerivedMeasure` are calculated on the fly by Oracle OLAP and are not stored in the database. An `MdmDerivedMeasure` does not have an associated `ConsistentSolveSpecification`.
  With the [`findOrCreateDerivedMeasure`](MdmCube.md) method of an `MdmCube`, you can get an existing `MdmDerivedMeasure` or create a new one. Committing the `Transaction` in which you create a derived measure makes the `MdmDerivedMeasure` a persistent object. It adds the `MdmDerivedMeasure` to the data dictionary, which makes it available to other applications.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                                                         |
    |---------------------------|---------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `LOOP_TYPE_DENSE`<br>A static constant that represents the OLAP DML `$LOOP_TYPE` system property value DENSE. |
    | `static java.lang.String` | `LOOP_TYPE_INNER`<br>A static constant that represents the OLAP DML `$LOOP_TYPE` system property value INNER. |
    | `static java.lang.String` | `LOOP_TYPE_OUTER`<br>A static constant that represents the OLAP DML `$LOOP_TYPE` system property value OUTER. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                            | Method and Description                                                                                                                                                                                                                   |
    |----------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                           | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmDerivedMeasure` method of the `MdmObjectVisitor` and passes that method this `MdmDerivedMeasure` and an `Object`. |
    | [`MdmViewColumn`](MdmViewColumn.md)          | `getETMeasureColumn``()`<br>Gets the ET (Embedded Totals) column for the MdmMeasure.                                                                                                                                                     |
    | `boolean`                                    | `getFailedCompile``()`<br>Gets the value of the OLAP DML `$FAILED_COMPILE` system property for the measure in the analytic workspace.                                                                                                    |
    | `java.lang.String`                           | `getLoopDenseOverride``()`<br>Gets the value of the OLAP DML `$LOOP_DENSE` system property of the measure in the analytic workspace.                                                                                                     |
    | `java.lang.String`                           | `getLoopDenseThresholdOverride``()`                                                                                                                                                                                                      |
    | `java.lang.String`                           | `getLoopInvariantOverride``()`                                                                                                                                                                                                           |
    | `java.lang.String`                           | `getLoopInvariantValuesetOverride``()`                                                                                                                                                                                                   |
    | `java.lang.String`                           | `getLoopType``()`<br>Gets the value of the OLAP DML `$LOOP_TYPE` system property for the measure in the analytic workspace.                                                                                                              |
    | `java.lang.String`                           | `getLoopVarOverride``()`<br>Gets the value of the OLAP DML `$LOOP_VAR` system property for the measure in the analytic workspace.                                                                                                        |
    | [`Expression`](../../syntax/Expression.md)   | `getMeasureExpression``()`<br>Gets the `Expression` that determines the values of this `MdmDerivedMeasure`.                                                                                                                              |
    | [`SQLDataType`](../../syntax/SQLDataType.md) | `getSQLDataType``()`<br>Gets the SQL data type for this `MdmDerivedMeasure`.                                                                                                                                                             |
    | `void`                                       | `setLoopDenseOverride``(java.lang.String value)`<br>Specifies the OLAP DML dimensions for the OLAP DML `$LOOP_DENSE` system property of the measure in the analytic workspace.                                                           |
    | `void`                                       | `setLoopDenseThresholdOverride``(java.lang.String val)`                                                                                                                                                                                  |
    | `void`                                       | `setLoopInvariantOverride``(java.lang.String val)`                                                                                                                                                                                       |
    | `void`                                       | `setLoopInvariantValuesetOverride``(java.lang.String val)`                                                                                                                                                                               |
    | `void`                                       | `setLoopType``(java.lang.String value)`<br>Specifies the OLAP DML `$LOOP_TYPE` system property for the derived measure in the analytic workspace.                                                                                        |
    | `void`                                       | `setLoopVarOverride``(java.lang.String value)`<br>Specifies the OLAP DML variables for the OLAP DML `$LOOP_VAR` system property for the derived measure in the analytic workspace.                                                       |
    | `void`                                       | `setMeasureExpression``(`[`Expression`](../../syntax/Expression.md)` input)`<br>Specifies an `Expression` that determines the values of this `MdmDerivedMeasure`.                                                                        |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmMeasure](MdmMeasure.md)

      [`addDimensionality`](MdmMeasure.md)`, `[`getColumnObject`](MdmMeasure.md)`, `[`getCube`](MdmMeasure.md)`, `[`getDimensionality`](MdmMeasure.md)`, `[`getLevel`](MdmMeasure.md)`, `[`getLevelDepth`](MdmMeasure.md)`, `[`getLocalValue`](MdmMeasure.md)`, `[`getMeasureDimension`](MdmMeasure.md)`, `[`getOwnerDimension`](MdmMeasure.md)`, `[`getParentLevel`](MdmMeasure.md)`, `[`getParentLocalValue`](MdmMeasure.md)`, `[`getParentValue`](MdmMeasure.md)`, `[`getPrecedence`](MdmMeasure.md)`, `[`getType`](MdmMeasure.md)`, `[`getUnits`](MdmMeasure.md)`, `[`getValue`](MdmMeasure.md)`, `[`getValueFormat`](MdmMeasure.md)`, `[`removeDimensionality`](MdmMeasure.md)`, `[`setCube`](MdmMeasure.md)`, `[`setUnits`](MdmMeasure.md)`, `[`setValueFormat`](MdmMeasure.md)

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

- - ### Field Detail

    - #### LOOP_TYPE_INNER

          public static final java.lang.String LOOP_TYPE_INNER

      A static constant that represents the OLAP DML `$LOOP_TYPE` system property value INNER.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LOOP_TYPE_OUTER

          public static final java.lang.String LOOP_TYPE_OUTER

      A static constant that represents the OLAP DML `$LOOP_TYPE` system property value OUTER.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### LOOP_TYPE_DENSE

          public static final java.lang.String LOOP_TYPE_DENSE

      A static constant that represents the OLAP DML `$LOOP_TYPE` system property value DENSE.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### acceptVisitor

          public java.lang.Object acceptVisitor(MdmObjectVisitor visitor,
                                                java.lang.Object context)

      Calls the `visitMdmDerivedMeasure` method of the `MdmObjectVisitor` and passes that method this `MdmDerivedMeasure` and an `Object`.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor` that is an instance of `Mdm11_ObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmDerivedMeasure` method.

    <!-- -->

    - #### getMeasureExpression

          public final Expression getMeasureExpression()

      Gets the `Expression` that determines the values of this `MdmDerivedMeasure`.
      Returns:
      The `Expression` that determines the values of this `MdmDerivedMeasure`.

    <!-- -->

    - #### setMeasureExpression

          public final void setMeasureExpression(Expression input)

      Specifies an `Expression` that determines the values of this `MdmDerivedMeasure`.
      Parameters:
      `input` - An `Expression` that determines the values of this `MdmDerivedMeasure`.

    <!-- -->

    - #### getSQLDataType

          public final SQLDataType getSQLDataType()

      Gets the SQL data type for this `MdmDerivedMeasure`.
      Returns:
      A `SQLDataType` that represents the SQL data type.

    <!-- -->

    - #### getLoopVarOverride

          public final java.lang.String getLoopVarOverride()

      Gets the value of the OLAP DML `$LOOP_VAR` system property for the measure in the analytic workspace. For information on the `$LOOP_VAR` property, see *Oracle OLAP DML Reference*.
      Returns:
      A `String` that contains the names of the OLAP DML variables that are specified by the `$LOOP_VAR` property.

    <!-- -->

    - #### setLoopVarOverride

          public final void setLoopVarOverride(java.lang.String value)

      Specifies the OLAP DML variables for the OLAP DML `$LOOP_VAR` system property for the derived measure in the analytic workspace. The `$LOOP_VAR` property applies to the underlying formula for the measure. For information on OLAP DML variables, formulas, and system properties, see *Oracle OLAP DML Reference*.
      The value specified by this method overrides the default \$LOOP_VAR value set by Oracle OLAP. If you use this method to set the \$LOOP_VAR value, then Oracle OLAP uses OUTER looping and ignores any value set by the `setLoopType` method.

      **Note:** You might want to use this method if the `Expression` of the `MdmDerivedMeasure` includes an `OLAPDMLExpression`.

      Parameters:
      `value` - A `String` that contains the names of one or more variables on separate lines, as in `"var1\nvar2"`.

      See Also:
      `setLoopType(String value)`

    <!-- -->

    - #### getLoopType

          public final java.lang.String getLoopType()

      Gets the value of the OLAP DML `$LOOP_TYPE` system property for the measure in the analytic workspace. For information on the `$LOOP_TYPE` property, see *Oracle OLAP DML Reference*.
      Returns:
      A `String` that contains the value of the OLAP DML `$LOOP_TYPE` system property.

    <!-- -->

    - #### setLoopType

          public final void setLoopType(java.lang.String value)

      Specifies the OLAP DML `$LOOP_TYPE` system property for the derived measure in the analytic workspace. The `$LOOP_TYPE` property controls the type of looping that Oracle OLAP does for a derived measure that has an `Expression` that references measures from more than one cube. The value specified by this method overrides the default \$LOOP_TYPE value set by Oracle OLAP, which is INNER.
      The `$LOOP_TYPE` property applies to the underlying formula for the measure. For information on OLAP DML composites, formulas, and system properties, see *Oracle OLAP DML Reference*.

      **Note:** You might want to use this method if the `Expression` of the `MdmDerivedMeasure` includes an `OLAPDMLExpression`.

      Parameters:
      `value` - One of the static constants `MdmDerivedMeasure.LOOP_TYPE_INNER`, `MdmDerivedMeasure.LOOP_TYPE_OUTER`, or `MdmDerivedMeasure.LOOP_TYPE_DENSE`.

      See Also:
      `setLoopVarOverride(String value)`

    <!-- -->

    - #### getFailedCompile

          public final boolean getFailedCompile()

      Gets the value of the OLAP DML `$FAILED_COMPILE` system property for the measure in the analytic workspace.
      Returns:
      A `Boolean` that contains the value of the OLAP DML `$FAILED_COMPILE` property.

    <!-- -->

    - #### getLoopDenseOverride

          public final java.lang.String getLoopDenseOverride()

      Gets the value of the OLAP DML `$LOOP_DENSE` system property of the measure in the analytic workspace. For information on the `$LOOP_DENSE` property, see *Oracle OLAP DML Reference*.
      Returns:
      A `String` that contains the names of the OLAP DML dimensions that are specified by the `$LOOP_DENSE` property.

    <!-- -->

    - #### setLoopDenseOverride

          public final void setLoopDenseOverride(java.lang.String value)

      Specifies the OLAP DML dimensions for the OLAP DML `$LOOP_DENSE` system property of the measure in the analytic workspace. The value specified by this method overrides the default `$LOOP_DENSE`value used by Oracle OLAP.
      The `$LOOP_DENSE` property applies to the underlying formula for the derived measure. For information on the `$LOOP_DENSE` property, see *Oracle OLAP DML Reference*.

      **Note:** You might want to use this method if the `Expression` of the `MdmDerivedMeasure` includes an `OLAPDMLExpression`.

      Parameters:
      `value` - A `String` that contains the names of one or more dimensions on separate lines, as in `"dim1\ndim2"`.

    <!-- -->

    - #### getETMeasureColumn

          public final MdmViewColumn getETMeasureColumn()

      Gets the ET (Embedded Totals) column for the MdmMeasure. If the object created is not yet sent over to the server or the server complilation fails, the ET column name is not impacted.
      Overrides:
      [`getETMeasureColumn`](MdmMeasure.md) in class [`MdmMeasure`](MdmMeasure.md)

      Returns:
      The `MdmViewColumn` that represents the ET column. If the server compilation fails or is not yet sent over to the server, returns null.

    <!-- -->

    - #### getLoopInvariantOverride

          public final java.lang.String getLoopInvariantOverride()

    <!-- -->

    - #### setLoopInvariantOverride

          public final void setLoopInvariantOverride(java.lang.String val)

    <!-- -->

    - #### getLoopInvariantValuesetOverride

          public final java.lang.String getLoopInvariantValuesetOverride()

    <!-- -->

    - #### setLoopInvariantValuesetOverride

          public final void setLoopInvariantValuesetOverride(java.lang.String val)

    <!-- -->

    - #### getLoopDenseThresholdOverride

          public final java.lang.String getLoopDenseThresholdOverride()

    <!-- -->

    - #### setLoopDenseThresholdOverride

          public final void setLoopDenseThresholdOverride(java.lang.String val)

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmDerivedAttribute.md)
- [Next Class](MdmDescription.md)

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
