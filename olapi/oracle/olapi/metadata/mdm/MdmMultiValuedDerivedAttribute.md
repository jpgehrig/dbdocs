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

- [Prev Class](MdmMultiValuedAttribute.md)
- [Next Class](MdmNamedBuildProcess.md)

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

## Class MdmMultiValuedDerivedAttribute

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - [oracle.olapi.metadata.mdm.MdmSource](MdmSource.md)

        - - [oracle.olapi.metadata.mdm.MdmDimensionedObject](MdmDimensionedObject.md)

          - - [oracle.olapi.metadata.mdm.MdmAttribute](MdmAttribute.md)

            - - [oracle.olapi.metadata.mdm.MdmMultiValuedAttribute](MdmMultiValuedAttribute.md)

              - - oracle.olapi.metadata.mdm.MdmMultiValuedDerivedAttribute

<!-- -->

- All Implemented Interfaces:
  [MdmQueryColumn](MdmQueryColumn.md), [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public final class MdmMultiValuedDerivedAttribute
      extends MdmMultiValuedAttribute

  An `MdmMultiValuedAttribute` that can relate more than a single derived value for a value of an associated `MdmPrimaryDimension`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                            | Method and Description                                                                                                                                                                                                                                             |
    |----------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                           | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmMultiValuedDerivedAttribute` method of the `MdmObjectVisitor` and passes that method this `MdmMultiValuedDerivedAttribute` and an `Object`. |
    | [`Query`](../../syntax/Query.md)             | `getAttributeQuery``()`<br>Gets the `Query` that is associated with this `MdmMultiValuedDerivedAttribute`.                                                                                                                                                         |
    | [`SQLDataType`](../../syntax/SQLDataType.md) | `getSQLDataType``()`<br>Gets the SQL data type for this `MdmMultiValueDerivedAttribute`.                                                                                                                                                                           |
    | `void`                                       | `setAttributeQuery``(`[`Query`](../../syntax/Query.md)` input)`<br>Specifies the `Query` to associate with this `MdmMultiValuedDerivedAttribute`.                                                                                                                  |

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

    - #### getAttributeQuery

          public final Query getAttributeQuery()

      Gets the `Query` that is associated with this `MdmMultiValuedDerivedAttribute`.
      Returns:
      The `Query` associated with this `MdmMultiValuedDerivedAttribute`.

    <!-- -->

    - #### setAttributeQuery

          public final void setAttributeQuery(Query input)

      Specifies the `Query` to associate with this `MdmMultiValuedDerivedAttribute`.
      Parameters:
      `input` - The `Query` to associate with this `MdmMultiValuedDerivedAttribute`.

    <!-- -->

    - #### getSQLDataType

          public final SQLDataType getSQLDataType()

      Gets the SQL data type for this `MdmMultiValueDerivedAttribute`.
      Specified by:
      [`getSQLDataType`](MdmQueryColumn.md) in interface [`MdmQueryColumn`](MdmQueryColumn.md)

      Specified by:
      [`getSQLDataType`](MdmAttribute.md) in class [`MdmAttribute`](MdmAttribute.md)

      Returns:
      A `SQLDataType` that represents the SQL data type.

    <!-- -->

    - #### acceptVisitor

          public java.lang.Object acceptVisitor(MdmObjectVisitor visitor,
                                                java.lang.Object context)

      Calls the `visitMdmMultiValuedDerivedAttribute` method of the `MdmObjectVisitor` and passes that method this `MdmMultiValuedDerivedAttribute` and an `Object`.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor` that implements the `Mdm11_2_ObjectVisitor` interface. .

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmMultiValuedDerivedAttribute` method.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmMultiValuedAttribute.md)
- [Next Class](MdmNamedBuildProcess.md)

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
