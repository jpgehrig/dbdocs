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

- [Prev Class](MdmAttributeModel.md)
- [Next Class](MdmBaseMeasure.md)

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

## Class MdmBaseAttribute

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - [oracle.olapi.metadata.mdm.MdmDimensionedObject](MdmDimensionedObject.md)

          - - [oracle.olapi.metadata.mdm.MdmAttribute](MdmAttribute.md)

            - - [oracle.olapi.metadata.mdm.MdmSingleValuedAttribute](MdmSingleValuedAttribute.md)

              - - oracle.olapi.metadata.mdm.MdmBaseAttribute

<!-- -->

- All Implemented Interfaces:
  [MdmQueryColumn](MdmQueryColumn.md), [MdmViewColumnOwner](MdmViewColumnOwner.md), [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public final class MdmBaseAttribute
      extends MdmSingleValuedAttribute
      implements MdmViewColumnOwner

  An `MdmSingleValuedAttribute` that is typically mapped to one or more columns of a relational table in the database. You can map the same `MdmBaseAttribute` to a different column for each level of a dimension or hierarchy, and for attribute values in different languages.
  You specify each different mapping with a separate instance of an `AttributeMap`. The `Expression` of the `AttributeMap` can specify a column in a table, or a function or operator that uses one or more columns, or a constant value. You create an `AttributeMap` with a `findOrCreateAttributeMap` method of a `HierarchyLevelMap`, for an `MdmHierarchyLevel`, or a `MemberListMap`, for an `MdmDimensionLevel` or an `MdmPrimaryDimension`. The example in this description creates an `AttributeMap` for a `MemberListMap` for an `MdmDimensionLevel`.

  You can find an existing `MdmBaseAttribute` or create a new one by using the [`findOrCreateBaseAttribute`](MdmPrimaryDimension.md) method of an `MdmPrimaryDimension`. You can get a `List` of the `MdmBaseAttribute` objects for an `MdmDimension` by using the `getAttributes` method.

  You can create an `MdmBaseAttribute` for an `MdmPrimaryDimension` and not associate it with an `AttributeMap`. You can then commit the `Transaction` and build the dimension. The values of such an unmapped attribute are null for any dimension member.

  With the `setNVLExpression` method, you can specify a value that substitutes for a null attribute value. The null-value substitution occurs for any null attribute value whether the `MdmBaseAttribute` is mapped or unmapped.

  When you create an `MdmBaseAttribute`, you can specify a SQL data type for it with the `setSQLDataType` method. If you do not specify a SQL data type, then Oracle OLAP assigns a default SQL data type that is the common data type of all of the `Expression` objects of the `AttributeMap` objects that are associated with the `MdmBaseAttribute`. If no `AttributeMap` objects are associated with the `MdmBaseAttribute`, then Oracle OLAP gives the `MdmBaseAttribute` a default SQL data type of VARCHAR2(256).

  **Note:** The default data type may change in future versions of this API.

  For an existing `MdmBaseAttribute`, the AllowAutoDataTypeChange property of the attribute determines how the SQL data type can change. If the AllowAutoDataTypeChange property is `false`, which is the default setting, you can only change the SQL data type of the attribute by using the `setSQLDataType` method; adding or removing `AttributeMap` objects, or changing the `Expression` of an `AttributeMap`, does not change the SQL data type of the `MdmBaseAttribute`.

  However, if the AllowAutoDataTypeChange property is `true`, then the `setSQLDataType` method does not change the SQL data type of the `MdmBaseAttribute`. Instead, Oracle OLAP automatically sets the SQL data type of the `MdmBaseAttribute` to the data type that is common to all of the `Expression` objects in the `AttributeMap` objects that are associated with the `MdmBaseAttribute`. For example, if you have an attribute that is mapped to a column that has a data type of NUMBER(5) for one level and is also mapped to a column with a data type of NUMBER(12) for another level, then Oracle OLAP uses the NUMBER(12) data type for the attribute. If you then map the same attribute for a third level to a column with a data type of VARCHAR2, then Oracle OLAP determines that it can convert the NUMBER columns to VARCHAR2 data type to match the VARCHAR2 column, and it selects VARCHAR2 as the SQL data type for the `MdmBaseAttribute`.

  If the AllowAutoDataTypeChange property is `true`, then adding or removing an `AttributeMap` of a `DimensionMap`, or changing the `Expression` of an `AttributeMap`, may change the SQL data type of the associated `MdmBaseAttribute`. You can change the AllowAutoDataTypeChange property with the `setAllowAutoDataTypeChange` method.

  You can get the data type by calling the `getSQLDataType` method. For the data type returned in the various conditions, see [Possible Data Types Returned by getSQLDataType](doc-files/pdtr.md) table.

  The following example creates an `MdmBaseAttribute` for a dimension. It associates the attribute with one `MdmDimensionLevel` of the dimension. It maps the attribute to a column in a relational table. It allows the automatic changing of the data type. It commits the transaction and builds the dimension. It then gets and displays the SQL data type of the attribute and of the column in the relational table to which the level is mapped.

       // mdmProdDim is an MdmPrimaryDimension that has an MdmDimensionLevel named
       // ITEM.
       MdmDimensionLevel mdmItemLevel =
         mdmProdDim.findOrCreateDimensionLevel("ITEM");
       MemberListMap mdmItemLevelMemListMap =
         mdmItemLevel.findOrCreateMemberListMap();
       MdmBaseAttribute mdmPkgAttr =
         mdmProdDim.findOrCreateBaseAttribute("PACKAGE");
       // Map the attribute to a column in a relational table.
       AttributeMap pkgAttrMap =
         mdmItemLevelMemListMap.findOrCreateAttributeMap(mdmPkgAttr);
       ColumnExpression attrColExp = (ColumnExpression)
         SyntaxObject.fromSyntax("GLOBAL.PRODUCT_DIM.ITEM_PACKAGE",
                                  metadataProvider);
       pkgAttrMap.setExpression(attrColExp);
       mdmPkgAttr.setAllowAutoDataTypeChange(true);

       try
       {
         // dp is the DataProvider for the session.
         (dp.getTransactionProvider()).commitCurrentTransaction();
       }
       catch (Exception ex)
       {
         println("Could not commit the Transaction. " + ex);
       }
       // Build the dimension.
       BuildItem bldProdDim = new BuildItem(mdmProdDim);
       ArrayList<BuildItem> items = new ArrayList();
       items.add(bldProdDim);
       BuildProcess bldProc = new BuildProcess(items);
       try
       {
         dp.executeBuild(bldProc, 0);
       }
       catch (Exception ex)
       {
          println("Could not execute the BuildProcess.");
       }

       // Get the SQL data type of the attribute.
       println("The SQL data type of the " + mdmPkgAttr.getName() +
               " attribute is " + mdmPkgAttr.getSQLDataType().getSQLText() + ".");

       // Get the SQL data type of the table column.
       MdmTable mdmTable = (MdmTable) mdmDBSchema.getTopLevelObject("PRODUCT_DIM");
       List<MdmColumn> colList = mdmTable.getColumns();
       for (MdmColumn mdmCol : colList)
       {
         if (mdmCol.getName().equals("ITEM_PACKAGE"))
         {
           println("The SQL data type of the " + mdmCol.getName() +
                   " column is " + mdmCol.getSQLDataType().getSQLText() + ".");
         }
       }

  The example displays the following.

       The SQL data type of the PACKAGE attribute is VARCHAR2(20).
       The SQL data type of the ITEM_PACKAGE column is VARCHAR2(20).

<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                     | Method and Description                                                                                                                                                                                                                                                                                                                                |
    |-------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                                    | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmBaseAttribute` method of the `MdmObjectVisitor` and passes that method this `MdmBaseAttribute` and an `Object`.                                                                                                                |
    | `boolean`                                             | `allowAutoDataTypeChange``()`<br>Indicates whether Oracle OLAP is allowed to automatically change the data type of the attribute.                                                                                                                                                                                                                     |
    | `java.lang.String`                                    | `getAttributeGroupName``()`<br>Gets the name of the group to which this attribute belongs.                                                                                                                                                                                                                                                            |
    | `static `[`SQLDataType`](../../syntax/SQLDataType.md) | `getDefaultSQLDataType``()`<br>Gets the default SQL data type for the `MdmBaseAttribute`.                                                                                                                                                                                                                                                             |
    | [`MdmViewColumn`](MdmViewColumn.md)                   | `getETAttributeColumn``()`<br>Gets the `MdmViewColumn` that represents the ET (Embedded Totals) values for this `MdmBaseAttribute`.                                                                                                                                                                                                                   |
    | [`Expression`](../../syntax/Expression.md)            | `getNVLExpression``()`<br>Gets the expression that Oracle OLAP substitutes for an attribute value that is null.                                                                                                                                                                                                                                       |
    | [`SQLDataType`](../../syntax/SQLDataType.md)          | `getSQLDataType``()`<br>Gets the SQL data type for the `MdmBaseAttribute`.                                                                                                                                                                                                                                                                            |
    | `boolean`                                             | `isLoopMask``()`                                                                                                                                                                                                                                                                                                                                      |
    | `boolean`                                             | `isMultiLingual``()`<br>Indicates whether the attribute has values for more than one language.                                                                                                                                                                                                                                                        |
    | `boolean`                                             | `isPopulateLineage``()`<br>Indicates whether an analytic workspace associates the values of the `MdmBaseAttribute` only with the dimension members at the level to which the attribute is mapped or to the members of the mapped level and to the dimension members of all levels that are descendants of the mapped level.                           |
    | `void`                                                | `setAllowAutoDataTypeChange``(boolean allowAutoDataTypeChange)`<br>Specifies whether to allow Oracle OLAP to automatically change the data type of the attribute.                                                                                                                                                                                     |
    | `void`                                                | `setAttributeGroupName``(java.lang.String group)`<br>Specifies the name of the group to which this attribute belongs.                                                                                                                                                                                                                                 |
    | `void`                                                | `setLoopMask``(boolean isLoopMask)`                                                                                                                                                                                                                                                                                                                   |
    | `void`                                                | `setMultiLingual``(boolean isMultiLingual)`<br>Specifies whether the attribute has values for more than one language.                                                                                                                                                                                                                                 |
    | `void`                                                | `setNVLExpression``(`[`Expression`](../../syntax/Expression.md)` input)`<br>Specifies an `Expression` that resolves to a value that that you want to substitute for a null attribute value.                                                                                                                                                           |
    | `void`                                                | `setPopulateLineage``(boolean isPopulateLineage)`<br>Specifies whether an analytic workspace associates the values of the `MdmBaseAttribute` only with the dimension members at the level to which the attribute is mapped or to the members of the mapped level and to the dimension members of all levels that are descendants of the mapped level. |
    | `void`                                                | `setSQLDataType``(`[`SQLDataType`](../../syntax/SQLDataType.md)` type)`<br>Specifies a SQL data type for the `MdmBaseAttribute`.                                                                                                                                                                                                                      |

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmAttribute](MdmAttribute.md)

      [`getColumnObject`](MdmAttribute.md)`, `[`getDescriptionType`](MdmAttribute.md)`, `[`getDimensionality`](MdmAttribute.md)`, `[`getPrimaryDimension`](MdmAttribute.md)`, `[`getTargetDimension`](MdmAttribute.md)`, `[`getType`](MdmAttribute.md)`, `[`isVisibleForAll`](MdmAttribute.md)`, `[`setDescriptionType`](MdmAttribute.md)`, `[`setIsVisibleForAll`](MdmAttribute.md)`, `[`setPrimaryDimension`](MdmAttribute.md)`, `[`setTargetDimension`](MdmAttribute.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.metadata.mdm.[MdmDimensionedObject](MdmDimensionedObject.md)

      [`addDimension`](MdmDimensionedObject.md)`, `[`addDimensionality`](MdmDimensionedObject.md)`, `[`getDimensions`](MdmDimensionedObject.md)`, `[`isBooleanValued`](MdmDimensionedObject.md)`, `[`removeDimensionality`](MdmDimensionedObject.md)`, `[`setBooleanValued`](MdmDimensionedObject.md)

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

    - ### Methods inherited from interface oracle.olapi.metadata.mdm.[MdmQueryColumn](MdmQueryColumn.md)

      [`getName`](MdmQueryColumn.md)

<!-- -->

- - ### Method Detail

    - #### acceptVisitor

          public java.lang.Object acceptVisitor(MdmObjectVisitor visitor,
                                                java.lang.Object context)

      Calls the `visitMdmBaseAttribute` method of the `MdmObjectVisitor` and passes that method this `MdmBaseAttribute` and an `Object`.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor` that implements the `Mdm11_ObjectVisitor` interface. .

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmBaseAttribute` method.

    <!-- -->

    - #### isMultiLingual

          public final boolean isMultiLingual()

      Indicates whether the attribute has values for more than one language.
      Returns:
      A `boolean` that indicates whether the attribute has values for more than one language.

    <!-- -->

    - #### setMultiLingual

          public final void setMultiLingual(boolean isMultiLingual)

      Specifies whether the attribute has values for more than one language.
      Parameters:
      `isMultiLingual` - A `boolean` that specifies whether the attribute has values for more than one language.

    <!-- -->

    - #### isLoopMask

          public final boolean isLoopMask()

    <!-- -->

    - #### setLoopMask

          public final void setLoopMask(boolean isLoopMask)

    <!-- -->

    - #### isPopulateLineage

          public final boolean isPopulateLineage()

      Indicates whether an analytic workspace associates the values of the `MdmBaseAttribute` only with the dimension members at the level to which the attribute is mapped or to the members of the mapped level and to the dimension members of all levels that are descendants of the mapped level.
      Returns:
      A `boolean` that is `true` if attribute values for the mapped level also apply to all descendant levels, or `false` if the attribute values apply only to the mapped level.

    <!-- -->

    - #### setPopulateLineage

          public final void setPopulateLineage(boolean isPopulateLineage)

      Specifies whether an analytic workspace associates the values of the `MdmBaseAttribute` only with the dimension members at the level to which the attribute is mapped or to the members of the mapped level and to the dimension members of all levels that are descendants of the mapped level. You should only specify `true` for the `isPopulateLineage` parameter for an `MdmBaseAttribute` that has the following characteristics:
      - The attribute is visible.
      - The attribute is not multilingual.
      - The attribute is mapped at only one `MdmDimensionLevel`.

      Parameters:
      `isPopulateLineage` - A `boolean` that is `true` to apply the attribute values to the dimension members at the mapped level and to the members at all descendant levels, or `false` to apply the attribute values only to the dimension members at the mapped level.

    <!-- -->

    - #### getAttributeGroupName

          public final java.lang.String getAttributeGroupName()

      Gets the name of the group to which this attribute belongs. This value can be used to group different attributes together in a user interface.
      Returns:
      A `String` that identifies the attribute group.

    <!-- -->

    - #### setAttributeGroupName

          public final void setAttributeGroupName(java.lang.String group)

      Specifies the name of the group to which this attribute belongs. You can use this value to group different attributes together in a user interface.
      Parameters:
      `group` - A `String` that identifies the attribute group.

    <!-- -->

    - #### getDefaultSQLDataType

          public static final SQLDataType getDefaultSQLDataType()

      Gets the default SQL data type for the `MdmBaseAttribute`.
      Returns:
      A `SQLDataType` that represents the default SQL data type.

    <!-- -->

    - #### getSQLDataType

          public final SQLDataType getSQLDataType()

      Gets the SQL data type for the `MdmBaseAttribute`. Oracle OLAP determines the data type in one of the following ways.
      - If the `MdmBaseAttribute` has the AllowAutoDataTypeChange property set to `true`:
        - If the `MdmBaseAttribute` has `AttributeMap` objects that are associated with it, then the data type is the common data type of all of the `Expression` objects of the `AttributeMap` objects.
        - If the `MdmBaseAttribute` has no associated `AttributeMap` objects, then the data type is the default type, which is VARCHAR2(256).
      - If the `MdmBaseAttribute` has the AllowAutoDataTypeChange property set to `false`, which is the default value:
        - If the SQL data type has been specified by a call to the `setSQLDataType` method of the attribute, then the data type is the one specified by that method.
        - If the SQL data type has not been specified by a call to the `setSQLDataType` method of the attribute and the `MdmBaseAttribute` has `AttributeMap` objects associated with it, then the data type is the common data type of all of the `Expression` objects of the `AttributeMap` objects that were associated with the `MdmBaseAttribute` when it was first committed. If the `MdmBaseAttribute` had no associated `AttributeMap` objects when it was first committed, then the data type is the default type, VARCHAR2(256).

      For the data type returned in the various conditions, see [Possible Data Types Returned by getSQLDataType](doc-files/pdtr.md).
      Specified by:
      [`getSQLDataType`](MdmQueryColumn.md) in interface [`MdmQueryColumn`](MdmQueryColumn.md)

      Specified by:
      [`getSQLDataType`](MdmAttribute.md) in class [`MdmAttribute`](MdmAttribute.md)

      Returns:
      A `SQLDataType` that represents the SQL data type.

      See Also:
      `allowAutoDataTypeChange()`, `setAllowAutoDataTypeChange(boolean allowAutoDataTypeChange)`

    <!-- -->

    - #### setSQLDataType

          public final void setSQLDataType(SQLDataType type)

      Specifies a SQL data type for the `MdmBaseAttribute`. If the `MdmBaseAttribute` does not have a specified SQL data type and the attribute has one or more associated `AttributeMap` objects with valid expressions, then Oracle OLAP uses the common data type of the values specified by the mappings. If the attribute does not have a specified SQL data type and it does not have an associated `AttributeMap`, then Oracle OLAP uses the default SQL data type of VARCHAR2(256).
      If the AutoDataTypeChange property of the `MdmBaseAttribute` is set to true, then Oracle OLAP ignores the data type specified by this method and automatically sets the SQL data type.

      Parameters:
      `type` - The `SQLDataType` to associate with this `MdmBaseAttribute`.

      See Also:
      `allowAutoDataTypeChange()`, `setAllowAutoDataTypeChange(boolean allowAutoDataTypeChange)`

    <!-- -->

    - #### allowAutoDataTypeChange

          public final boolean allowAutoDataTypeChange()

      Indicates whether Oracle OLAP is allowed to automatically change the data type of the attribute.
      Returns:
      A `boolean` that is `true` if Oracle OLAP can automatically change the data type of the attribute or `false` otherwise.

    <!-- -->

    - #### setAllowAutoDataTypeChange

          public final void setAllowAutoDataTypeChange(boolean allowAutoDataTypeChange)

      Specifies whether to allow Oracle OLAP to automatically change the data type of the attribute. If you specify `true` to allow the automatic changing of data types, then Oracle OLAP evaluates the expressions of the `AttributeMap` objects for the attribute that are contained by the `DimensionMap` for the `MdmPrimaryDimension` that contains the attribute. Based on the data types of those expressions, Oracle OLAP determines the appropriate data type for the attribute. If the attribute has mappings on several levels or hierarchies of the dimension, then the automatically derived data type is a common supertype of all of the mapped expressions.
      Parameters:
      `allowAutoDataTypeChange` - Specify `true` if you want to allow Oracle OLAP to automatically change the data type of the attribute or `false` otherwise.

    <!-- -->

    - #### getETAttributeColumn

          public final MdmViewColumn getETAttributeColumn()

      Gets the `MdmViewColumn` that represents the ET (Embedded Totals) values for this `MdmBaseAttribute`.
      Returns:
      The `MdmViewColumn` that represents the ET column for this `MdmBaseAttribute`.

    <!-- -->

    - #### getNVLExpression

          public final Expression getNVLExpression()

      Gets the expression that Oracle OLAP substitutes for an attribute value that is null.
      Returns:
      An `Expression` that substitutes for an attribute value that is null.

    <!-- -->

    - #### setNVLExpression

          public final void setNVLExpression(Expression input)

      Specifies an `Expression` that resolves to a value that that you want to substitute for a null attribute value. The `setNVLExpression` is similar to the SQL NVL function, and the OLAP DML NAFILL function and \$NATRIGGER property.
      Parameters:
      `input` - An `Expression` that you want to substitute for an attribute value that is null.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmAttributeModel.md)
- [Next Class](MdmBaseMeasure.md)

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
