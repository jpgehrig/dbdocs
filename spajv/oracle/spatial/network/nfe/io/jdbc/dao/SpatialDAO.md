Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](RuleDAO.md)
- [Next Class](WorkspaceDAO.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.io.jdbc.dao

## Class SpatialDAO

- java.lang.Object

- - [oracle.spatial.network.nfe.io.jdbc.dao.AbstractDAO](AbstractDAO.md)

  - - oracle.spatial.network.nfe.io.jdbc.dao.SpatialDAO

<!-- -->

-

  ------------------------------------------------------------------------



      public class SpatialDAO
      extends AbstractDAO

  The SpatialDAO data access object provides methods to load, create and manage spatial related data. It is not recommended to use the data access objects methods, instead use the NFE services.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                 |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `SpatialDAO``(java.sql.Connection conn, `[`NFEModel`](../../../model/NFEModel.md)` model)`<br>Creates a SpatialDAO with the specified connection and model. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                  | Method and Description                                                                                                                                                                                        |
    |--------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                             | `createNFEGeometryMetadata``(java.lang.String tableName, java.lang.String geomColumn, `[`NFEGeometryDescriptor`](../../../model/NFEGeometryDescriptor.md)` geomDesc)`<br>Creates a spatial geometry metadata. |
    | `void`                                                             | `createSpatialIndex``(java.lang.String indexName, java.lang.String tableName, java.lang.String spatialColumn)`<br>Creates the spatial index.                                                                  |
    | `void`                                                             | `createStyle``(Style style, java.lang.String styleName)`<br>Creates a style record in the view user_sdo_styles.                                                                                               |
    | `void`                                                             | `deleteStyle``(`[`NFEFeatureClass`](../../../model/feature/NFEFeatureClass.md)` nfeFeatureClass)`<br>Deletes the styles related to the specified feature class.                                               |
    | `void`                                                             | `deleteStyles``(`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` nfeFeatureLayer)`<br>Deletes the styles related to the specified feature layer.                                              |
    | [`JGeometry`](../../../../../geometry/JGeometry.md)                | `fetchGeometryLayerMBR``(java.lang.String tableName, java.lang.String geomColumnName)`<br>Returns the minimum bounding rectangle (MBR) of the geometries in the specified table and column.                   |
    | [`NFEGeometryDescriptor`](../../../model/NFEGeometryDescriptor.md) | `fetchGeometryMetadata``(java.lang.String tableName, java.lang.String columnName)`<br>Returns the metadata information for the specified geometry column.                                                     |
    | `SRS`                                                              | `fetchSRS``(long srid)`<br>Returns the spatial reference system (SRS) referred by the specified Spatial Reference System Identifier (SRID).                                                                   |
    | `void`                                                             | `updateStyle``(Style style, java.lang.String styleName)`<br>Updates the style record of the specified style in the view user_sdo_styles.                                                                      |

    - ### Methods inherited from class oracle.spatial.network.nfe.io.jdbc.dao.[AbstractDAO](AbstractDAO.md)

      [`getConnection`](AbstractDAO.md)`, `[`getModel`](AbstractDAO.md)`, `[`getSQLValidator`](AbstractDAO.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SpatialDAO

          public SpatialDAO(java.sql.Connection conn,
                            NFEModel model)

      Creates a SpatialDAO with the specified connection and model.
      Parameters:
      `conn` - connection

      `model` - model

  <!-- -->

  - ### Method Detail

    - #### fetchGeometryMetadata

          public NFEGeometryDescriptor fetchGeometryMetadata(java.lang.String tableName,
                                                             java.lang.String columnName)
                                                      throws NFEIOException

      Returns the metadata information for the specified geometry column. The information is store in the view user_sdo_geom_metadata.
      Parameters:
      `tableName` - column's table

      `columnName` - geometry column name

      Returns:
      the metadata information for the specified geometry column

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### createNFEGeometryMetadata

          public void createNFEGeometryMetadata(java.lang.String tableName,
                                                java.lang.String geomColumn,
                                                NFEGeometryDescriptor geomDesc)
                                         throws NFEIOException

      Creates a spatial geometry metadata.
      Parameters:
      `tableName` - column's table

      `geomColumn` - the geometry column name

      `geomDesc` - geometry descriptor used to access the SRID and the dimensions.

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### createSpatialIndex

          public void createSpatialIndex(java.lang.String indexName,
                                         java.lang.String tableName,
                                         java.lang.String spatialColumn)
                                  throws NFEIOException

      Creates the spatial index.
      Parameters:
      `indexName` - index name

      `tableName` - index table name

      `spatialColumn` - index geometry column

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### createStyle

          public void createStyle(Style style,
                                  java.lang.String styleName)
                           throws NFEIOException

      Creates a style record in the view user_sdo_styles.
      Parameters:
      `style` - style

      `styleName` - style name

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateStyle

          public void updateStyle(Style style,
                                  java.lang.String styleName)
                           throws NFEIOException

      Updates the style record of the specified style in the view user_sdo_styles.
      Parameters:
      `style` - style

      `styleName` - style name

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteStyles

          public void deleteStyles(NFEFeatureLayer nfeFeatureLayer)
                            throws NFEIOException

      Deletes the styles related to the specified feature layer. The styles with the name following the pattern \[featureLayerId\]\_\[featureClassId\]\_STYLE will be deleted.
      Parameters:
      `nfeFeatureLayer` - feature layer

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteStyle

          public void deleteStyle(NFEFeatureClass nfeFeatureClass)
                           throws NFEIOException

      Deletes the styles related to the specified feature class. The styles with the name following the pattern \[featureLayerId\]\_\[featureClassId\]\_STYLE will be deleted.
      Parameters:
      `nfeFeatureClass` - feature class

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### fetchGeometryLayerMBR

          public JGeometry fetchGeometryLayerMBR(java.lang.String tableName,
                                                 java.lang.String geomColumnName)
                                          throws NFEIOException

      Returns the minimum bounding rectangle (MBR) of the geometries in the specified table and column.
      Parameters:
      `tableName` - table name

      `geomColumnName` - geometry column name

      Returns:
      minimum bounding rectangle (MBR) geometry

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### fetchSRS

          public SRS fetchSRS(long srid)
                       throws NFEIOException

      Returns the spatial reference system (SRS) referred by the specified Spatial Reference System Identifier (SRID).
      Parameters:
      `srid` - SRID

      Returns:
      the spatial reference system (SRS) referred by the specified Spatial Reference System Identifier (SRID)

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](RuleDAO.md)
- [Next Class](WorkspaceDAO.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
