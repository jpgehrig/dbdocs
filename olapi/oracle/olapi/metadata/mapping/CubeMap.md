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

- [Prev Class](CubeDimensionalityMap.md)
- [Next Class](DimensionMap.md)

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

oracle.olapi.metadata.mapping

## Class CubeMap

- java.lang.Object

- - [oracle.olapi.metadata.BaseMetadataObject](../BaseMetadataObject.md)

  - - [oracle.olapi.metadata.PublicMetadataObject](../PublicMetadataObject.md)

    - - [oracle.olapi.metadata.mapping.ObjectMap](ObjectMap.md)

      - - oracle.olapi.metadata.mapping.CubeMap

<!-- -->

- All Implemented Interfaces:
  [MetadataObject](../MetadataObject.md)

  ------------------------------------------------------------------------



      public final class CubeMap
      extends ObjectMap

  An `ObjectMap` that maps an `MdmCube` to an `Expression`. An application gets a `CubeMap` by calling the [`createCubeMap`](../mdm/MdmCube.md) method of an `MdmCube`.
  A `CubeMap` has a `MeasureMap` for each `MdmMeasure` that is contained by the cube and a `CubeDimensionalityMap` for each `MdmPrimaryDimension` that is associated with the cube. It has an associated `Query` or `FromClause` and an aggregation method. It can have a `Condition`, which functions like a `WHERE` clause in a SQL `SELECT` statement.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                   | Method and Description                                                                                                                                                                                                             |
    |-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                              | `addDimensionalityMap``(`[`CubeDimensionalityMap`](CubeDimensionalityMap.md)` value)`<br>Adds a `CubeDimensionalityMap` to the `CubeMap`.                                                                                          |
    | `void`                                              | `addMeasureMap``(`[`MeasureMap`](MeasureMap.md)` value)`<br>Adds a `MeasureMap` to the `CubeMap`.                                                                                                                                  |
    | [`CubeDimensionalityMap`](CubeDimensionalityMap.md) | `findOrCreateCubeDimensionalityMap``(`[`MdmDimensionality`](../mdm/MdmDimensionality.md)` diml)`<br>Gets the `CubeDimensionalityMap` that has the specified name or, if the map does not exist, creates a `CubeDimensionalityMap`. |
    | [`MeasureMap`](MeasureMap.md)                       | `findOrCreateMeasureMap``(`[`MdmBaseMeasure`](../mdm/MdmBaseMeasure.md)` measure)`<br>Gets the `MeasureMap` for the specified measure or, if the map does not exist, creates a `MeasureMap` for the measure.                       |
    | `java.lang.String`                                  | `getAggregationMethod``()`<br>Gets the aggregation method specified for the cube.                                                                                                                                                  |
    | [`MdmCube`](../mdm/MdmCube.md)                      | `getCube``()`<br>Gets the `MdmCube` that contains the `CubeMap`.                                                                                                                                                                   |
    | `java.util.List`                                    | `getDimensionalityMaps``()`<br>Gets the `CubeDimensionalityMap` objects that are associated with the `CubeMap`.                                                                                                                    |
    | [`FromClause`](../../syntax/FromClause.md)          | `getFromClause``()`<br>Gets the `FromClause` that is associated with the `CubeMap`.                                                                                                                                                |
    | `java.util.List`                                    | `getMeasureMaps``()`<br>Gets the `MeasureMap` objects associated with the `CubeMap`.                                                                                                                                               |
    | `java.lang.String`                                  | `getName``()`<br>Gets the name of the `CubeMap`.                                                                                                                                                                                   |
    | [`Query`](../../syntax/Query.md)                    | `getQuery``()`<br>Gets the `Query` that is associated with the `CubeMap`.                                                                                                                                                          |
    | [`Condition`](../../syntax/Condition.md)            | `getWhereClause``()`<br>Gets the `Condition` associated with the `CubeMap`.                                                                                                                                                        |
    | `void`                                              | `removeDimensionalityMap``(`[`CubeDimensionalityMap`](CubeDimensionalityMap.md)` value)`<br>Removes a `CubeDimensionalityMap` from the `CubeMap`.                                                                                  |
    | `void`                                              | `removeMeasureMap``(`[`MeasureMap`](MeasureMap.md)` value)`<br>Removes a `MeasureMap` from the `CubeMap`.                                                                                                                          |
    | `void`                                              | `setAggregationMethod``(java.lang.String input)`<br>Specifies an aggregation method for the cube.                                                                                                                                  |
    | `void`                                              | `setFromClause``(`[`FromClause`](../../syntax/FromClause.md)` fromClause)`<br>Specifies a `FromClause` to associate with the `CubeMap`.                                                                                            |
    | `void`                                              | `setName``(java.lang.String name)`<br>Specifies a name for the `CubeMap`.                                                                                                                                                          |
    | `void`                                              | `setQuery``(`[`Query`](../../syntax/Query.md)` input)`<br>Specifies a query for the `CubeMap`.                                                                                                                                     |
    | `void`                                              | `setWhereClause``(`[`Condition`](../../syntax/Condition.md)` whereClause)`<br>Specifies a `Condition` to associate with the `CubeMap`.                                                                                             |

    - ### Methods inherited from class oracle.olapi.metadata.[BaseMetadataObject](../BaseMetadataObject.md)

      [`getContainedByObject`](../BaseMetadataObject.md)`, `[`getID`](../BaseMetadataObject.md)`, `[`getNewName`](../BaseMetadataObject.md)`, `[`getOwner`](../BaseMetadataObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### setWhereClause

          public void setWhereClause(Condition whereClause)

      Specifies a `Condition` to associate with the `CubeMap`. The `Condition` functions like a `WHERE` clause in a SQL `SELECT` statement.
      Parameters:
      `whereClause` - The `Condition` to associate with the `CubeMap`.

    <!-- -->

    - #### getWhereClause

          public Condition getWhereClause()

      Gets the `Condition` associated with the `CubeMap`.
      Returns:
      The `Condition` associated with the `CubeMap`.

    <!-- -->

    - #### setFromClause

          public void setFromClause(FromClause fromClause)

      Specifies a `FromClause` to associate with the `CubeMap`. A `CubeMap` can have a `FromClause` or a `Query`, but not both.
      A `FromClause` specifies tables that Oracle OLAP joins to get the leaf-level values that it requires for aggregating the data for the measures of the cube. A `FromClause` that specifies only one table is functionally the same as a `Query`.

      A `FromClause` that specifies two or more tables requires a `Condition` that specifies the join conditions for the tables. You specify the `Condition` with the `setWhereClause` method.

      Parameters:
      `fromClause` - The `FromClause` to associate with the `CubeMap`.

    <!-- -->

    - #### getFromClause

          public FromClause getFromClause()

      Gets the `FromClause` that is associated with the `CubeMap`.
      Returns:
      The `FromClause` associated with the `CubeMap`.

    <!-- -->

    - #### setQuery

          public void setQuery(Query input)

      Specifies a query for the `CubeMap`. A `CubeMap` can have a `Query` or a `FromClause`, but not both.
      The `Query` for a cube identifies the relational table that contains the leaf-level data for the measures of the cube. The following example gets the `Query` for an `MdmTable` and then specifies it as the `Query` for an `MdmCube`. In the example, the `mdmDBSchema` object is an `MdmDatabaseSchema`.

           // Get the MdmTable and the Query for the cube.
           MdmTable unitsTable = null;
           Query cubeQuery = null;

           try
           {
             unitsTable = (MdmTable)
                           mdmDBSchema.getTopLevelObject("UNITS_FACT");
             cubeQuery = unitsTable.getQuery();
           }
           catch (Exception ex)
           {
             println("Could not get the UNITS_FACT table. " + ex);
           }

           CubeMap cubeMap = mdmUnitsCube.createCubeMap();
           cubeMap.setQuery(cubeQuery);


      Parameters:
      `input` - The `Query` to specify for the `CubeMap`.

    <!-- -->

    - #### getQuery

          public Query getQuery()

      Gets the `Query` that is associated with the `CubeMap`.
      Returns:
      The `Query` associated with the `CubeMap`.

    <!-- -->

    - #### addMeasureMap

          public void addMeasureMap(MeasureMap value)

      Adds a `MeasureMap` to the `CubeMap`.
      Parameters:
      `value` - The `MeasureMap` to add.

    <!-- -->

    - #### removeMeasureMap

          public void removeMeasureMap(MeasureMap value)

      Removes a `MeasureMap` from the `CubeMap`.
      Parameters:
      `value` - The `MeasureMap` to remove.

    <!-- -->

    - #### getMeasureMaps

          public java.util.List getMeasureMaps()

      Gets the `MeasureMap` objects associated with the `CubeMap`.
      Returns:
      A `List` that contains the `MeasureMap` objects associated with the `CubeMap`.

    <!-- -->

    - #### addDimensionalityMap

          public void addDimensionalityMap(CubeDimensionalityMap value)

      Adds a `CubeDimensionalityMap` to the `CubeMap`.
      Parameters:
      `value` - The `CubeDimensionalityMap` to add.

    <!-- -->

    - #### removeDimensionalityMap

          public void removeDimensionalityMap(CubeDimensionalityMap value)

      Removes a `CubeDimensionalityMap` from the `CubeMap`.
      Parameters:
      `value` - The `CubeDimensionalityMap` to remove.

    <!-- -->

    - #### getDimensionalityMaps

          public java.util.List getDimensionalityMaps()

      Gets the `CubeDimensionalityMap` objects that are associated with the `CubeMap`.
      Returns:
      A `List` that contains the `CubeDimensionalityMap` objects associated with the `CubeMap`.

    <!-- -->

    - #### getCube

          public MdmCube getCube()

      Gets the `MdmCube` that contains the `CubeMap`.

    <!-- -->

    - #### getAggregationMethod

          public java.lang.String getAggregationMethod()

      Gets the aggregation method specified for the cube.
      Returns:
      A `String` that contains the aggregation method of the cube.

    <!-- -->

    - #### setAggregationMethod

          public void setAggregationMethod(java.lang.String input)

      Specifies an aggregation method for the cube. You can specify any valid single value SQL aggregation method, such as `SUM`, `MAX`, `AVG`, and so on. The aggregation method specified by this method should typically be the same method as the method in the `ConsistentSolveSpecification` for the cube. The method in the `ConsistentSolveSpecification` specifies the aggregation method to use when aggregating the leaf-level data before loading it into the analytic workspace.
      Parameters:
      `input` - A `String` that contains an aggregation method for the cube.

    <!-- -->

    - #### findOrCreateMeasureMap

          public MeasureMap findOrCreateMeasureMap(MdmBaseMeasure measure)

      Gets the `MeasureMap` for the specified measure or, if the map does not exist, creates a `MeasureMap` for the measure.
      Parameters:
      `measure` - The `MdmBaseMeasure` for which to get a `MeasureMap`.

      Returns:
      A `MeasureMap` for the specified measure.

    <!-- -->

    - #### findOrCreateCubeDimensionalityMap

          public CubeDimensionalityMap findOrCreateCubeDimensionalityMap(MdmDimensionality diml)

      Gets the `CubeDimensionalityMap` that has the specified name or, if the map does not exist, creates a `CubeDimensionalityMap`.
      Parameters:
      `diml` - The `MdmDimensionality` for which to get a `CubeDimensionalityMap`.

      Returns:
      A `CubeDimensionalityMap` for the specified `MdmDimensionality`.

    <!-- -->

    - #### getName

          public final java.lang.String getName()

      Gets the name of the `CubeMap`.
      Overrides:
      [`getName`](ObjectMap.md) in class [`ObjectMap`](ObjectMap.md)

      Returns:
      A `String` that contains the name of the `CubeMap`.

    <!-- -->

    - #### setName

          public void setName(java.lang.String name)

      Specifies a name for the `CubeMap`.
      Parameters:
      `name` - A `String` that contains a name for the `CubeMap`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](CubeDimensionalityMap.md)
- [Next Class](DimensionMap.md)

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
