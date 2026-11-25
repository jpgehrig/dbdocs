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

- [Prev Class](MdmRootSchema.md)
- [Next Class](MdmSingleValuedAttribute.md)

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

## Class MdmSchema

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mdm.MdmObject](MdmObject.md)

      - - oracle.olapi.metadata.mdm.MdmSchema

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  <!-- -->

  Direct Known Subclasses:
  [MdmDatabaseSchema](MdmDatabaseSchema.md), [MdmOrganizationalSchema](MdmOrganizationalSchema.md), [MdmRootSchema](MdmRootSchema.md)

  ------------------------------------------------------------------------



      public class MdmSchema
      extends MdmObject

  A container for `MdmCube`, `MdmPrimaryDimension`, `MdmTable`, and other metadata objects. `MdmSchema` objects organize the metadata objects that are provided by an `MdmMetadataProvider`. The `MdmRootSchema` contains all of the objects provided by an `MdmMetadataProvider`. An `MdmDatabaseSchema` represents a database schema, which has all of the metadata objects associated with a particular database user. An `MdmDatabaseSchema` can have subschema objects, which are instances of `MdmOrganizationalSchema`, that organize the metadata objects into related groups.
  To begin navigating the metadata that is accessible through an `MdmMetadataProvider`, call the `getRootSchema` method of the `MdmMetadataProvider`.

  See Also:
  [`MdmMetadataProvider`](MdmMetadataProvider.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                                                                                                                                                                                                               |
    |-------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                              | `acceptVisitor``(`[`MdmObjectVisitor`](MdmObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitMdmSchema` method of the specified `MdmObjectVisitor` and passes that method the `MdmSchema` and the specified `context` object. |
    | `void`                                          | `addCube``(`[`MdmCube`](MdmCube.md)` cube)`<br>Adds the specified `MdmCube` to the `MdmSchema`.                                                                                                                                                      |
    | `void`                                          | `addDimension``(`[`MdmPrimaryDimension`](MdmPrimaryDimension.md)` dimension)`<br>Adds the specified `MdmPrimaryDimension` to the `MdmSchema`.                                                                                                        |
    | `void`                                          | `addMeasure``(`[`MdmMeasure`](MdmMeasure.md)` measure)`<br>Adds the specified `MdmMeasure` to the `MdmSchema`.                                                                                                                                       |
    | `void`                                          | `addSubSchema``(MdmSchema subschema)`<br>Adds the specified `MdmSchema` to the `MdmSchema`.                                                                                                                                                          |
    | `java.util.List`                                | `getCubes``()`<br>Gets the `MdmCube` objects that the `MdmSchema` contains.                                                                                                                                                                          |
    | `java.util.List`                                | `getDimensions``()`<br>Gets the `MdmPrimaryDimension` objects that the `MdmSchema` contains.                                                                                                                                                         |
    | [`MdmMeasureDimension`](MdmMeasureDimension.md) | `getMeasureDimension``()`<br>Gets the `MdmMeasureDimension` for the `MdmMetadataProvider` that is associated with the `MdmRootSchema`.                                                                                                               |
    | `java.util.List`                                | `getMeasures``()`<br>Gets the `MdmMeasure` objects that the `MdmSchema` contains.                                                                                                                                                                    |
    | `MdmSchema`                                     | `getOuterSchema``()`<br>Gets the `MdmSchema` that contains the `MdmSchema`, if the `MdmSchema` is a subschema of another `MdmSchema`.                                                                                                                |
    | `java.util.List`                                | `getSubSchemas``()`<br>Gets a `List` of the subschemas of the `MdmSchema`.                                                                                                                                                                           |
    | `void`                                          | `removeCube``(`[`MdmCube`](MdmCube.md)` cube)`<br>Removes the specified `MdmCube` from the `MdmSchema`.                                                                                                                                              |
    | `void`                                          | `removeDimension``(`[`MdmPrimaryDimension`](MdmPrimaryDimension.md)` dimension)`<br>Removes the specified `MdmPrimaryDimension` from the `MdmSchema`.                                                                                                |
    | `void`                                          | `removeMeasure``(`[`MdmMeasure`](MdmMeasure.md)` measure)`<br>Removes the specified `MdmMeasure` from the `MdmSchema`.                                                                                                                               |
    | `void`                                          | `removeSubSchema``(MdmSchema subschema)`<br>Removes the specified `MdmSchema` from the `MdmSchema`.                                                                                                                                                  |

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

      Calls the `visitMdmSchema` method of the specified `MdmObjectVisitor` and passes that method the `MdmSchema` and the specified `context` object.
      Specified by:
      [`acceptVisitor`](MdmObject.md) in class [`MdmObject`](MdmObject.md)

      Parameters:
      `visitor` - An `MdmObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitMdmSchema` method.

    <!-- -->

    - #### getDimensions

          public java.util.List getDimensions()

      Gets the `MdmPrimaryDimension` objects that the `MdmSchema` contains. The root `MdmSchema` contains all of the `MdmPrimaryDimension` objects available through an `MdmMetadataProvider`, except for the `MdmMeasureDimension`. To get the `MdmMeasureDimension`, call the `getMeasureDimension` method. `MdmSchema` objects under the root schema contain only the dimensions in the subschema and any subschemas that they contain.
      Returns:
      A `List` of the `MdmPrimaryDimension` objects in the `MdmSchema` and its subschemas.

    <!-- -->

    - #### getMeasureDimension

          public MdmMeasureDimension getMeasureDimension()
                                                  throws oracle.express.mdm.MetadataNotFoundException

      Gets the `MdmMeasureDimension` for the `MdmMetadataProvider` that is associated with the `MdmRootSchema`. The `getMeasureDimension` method of the `MdmRootSchema` returns the `MdmMeasureDimension`. For an `MdmDatabaseSchema` or `MdmOrganizationalSchema`, this method returns `null`.
      The `MdmMeasureDimension` has all of the `MdmMeasure` objects that the `MdmMetadataProvider` provides. The `getMeasures` method of an `MdmSchema` returns a `List` of the measures associated with that `MdmSchema`.

      Returns:
      The `MdmMeasureDimension` associated with the `MdmMetadataProvider`.

      Throws:
      `oracle.express.mdm.MetadataNotFoundException`

    <!-- -->

    - #### getMeasures

          public java.util.List getMeasures()

      Gets the `MdmMeasure` objects that the `MdmSchema` contains.
      Returns:
      A `List` of `MdmMeasure` objects that the `MdmSchema` contains.

    <!-- -->

    - #### getSubSchemas

          public java.util.List getSubSchemas()

      Gets a `List` of the subschemas of the `MdmSchema`. The `List` contains instances of `MdmOrganizationalSchema`.
      Returns:
      A `List` of the subschemas of the `MdmSchema`.

    <!-- -->

    - #### addMeasure

          public void addMeasure(MdmMeasure measure)

      Adds the specified `MdmMeasure` to the `MdmSchema`.
      Parameters:
      `measure` - The `MdmMeasure` to add to the `MdmSchema`.

    <!-- -->

    - #### removeMeasure

          public void removeMeasure(MdmMeasure measure)

      Removes the specified `MdmMeasure` from the `MdmSchema`.
      Parameters:
      `measure` - The `MdmMeasure` to remove from the `MdmSchema`.

    <!-- -->

    - #### addDimension

          public final void addDimension(MdmPrimaryDimension dimension)

      Adds the specified `MdmPrimaryDimension` to the `MdmSchema`.
      Parameters:
      `dimension` - The `MdmPrimaryDimension` to add to the `MdmSchema`.

    <!-- -->

    - #### removeDimension

          public final void removeDimension(MdmPrimaryDimension dimension)

      Removes the specified `MdmPrimaryDimension` from the `MdmSchema`.
      Parameters:
      `dimension` - The `MdmPrimaryDimension` to remove from the `MdmSchema`.

    <!-- -->

    - #### addSubSchema

          public void addSubSchema(MdmSchema subschema)

      Adds the specified `MdmSchema` to the `MdmSchema`.
      Parameters:
      `subschema` - The `MdmSchema` to add to the `MdmSchema`.

    <!-- -->

    - #### removeSubSchema

          public void removeSubSchema(MdmSchema subschema)

      Removes the specified `MdmSchema` from the `MdmSchema`.
      Parameters:
      `subschema` - The `MdmSchema` to remove from the `MdmSchema`.

    <!-- -->

    - #### addCube

          public final void addCube(MdmCube cube)

      Adds the specified `MdmCube` to the `MdmSchema`.
      Parameters:
      `cube` - The `MdmCube` to add to the `MdmSchema`.

    <!-- -->

    - #### removeCube

          public final void removeCube(MdmCube cube)

      Removes the specified `MdmCube` from the `MdmSchema`.
      Parameters:
      `cube` - The `MdmCube` to remove from the `MdmSchema`.

    <!-- -->

    - #### getCubes

          public java.util.List getCubes()

      Gets the `MdmCube` objects that the `MdmSchema` contains.
      Returns:
      A `List` of `MdmCube` objects that the `MdmSchema` contains.

    <!-- -->

    - #### getOuterSchema

          public final MdmSchema getOuterSchema()

      Gets the `MdmSchema` that contains the `MdmSchema`, if the `MdmSchema` is a subschema of another `MdmSchema`.
      Returns:
      The `MdmSchema` that contains the `MdmSchema`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](MdmRootSchema.md)
- [Next Class](MdmSingleValuedAttribute.md)

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
