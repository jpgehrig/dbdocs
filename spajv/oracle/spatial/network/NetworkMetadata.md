Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NetworkManager.md)
- [Next Class](Node.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.spatial.network

## Interface NetworkMetadata

- All Superinterfaces:
  java.lang.Cloneable, java.io.Serializable

  ------------------------------------------------------------------------



      public interface NetworkMetadata
      extends java.lang.Cloneable, java.io.Serializable

  This class defines a network metadata.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static int`      | `BIDIRECTED_LINK`     |
    | `static int`      | `DIRECTED_LINK`       |
    | `static int`      | `UNDIRECTED_LINK`     |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                           | Method and Description                                                                                                     |
    |---------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
    | `void`                                      | `addLinkData``(java.lang.String dataName, java.lang.String dataType, int dataLength)`<br>Adds a link user data entry       |
    | `void`                                      | `addNodeData``(java.lang.String dataName, java.lang.String dataType, int dataLength)`<br>Adds a node user data entry       |
    | `void`                                      | `addPathData``(java.lang.String dataName, java.lang.String dataType, int dataLength)`<br>Adds a path user data entry       |
    | `void`                                      | `addSubPathData``(java.lang.String dataName, java.lang.String dataType, int dataLength)`<br>Adds a subpath user data entry |
    | `java.lang.Object`                          | `clone``()`<br>Clones the metadata.                                                                                        |
    | `boolean`                                   | `containsUserData``()`<br>Checks if the network has user data defined in user_sdo_network_user_data                        |
    | `void`                                      | `deleteLinkData``(java.lang.String dataName)`<br>Deletes a link user data entry                                            |
    | `void`                                      | `deleteNodeData``(java.lang.String dataName)`<br>Deletes a node user data entry                                            |
    | `void`                                      | `deletePathData``(java.lang.String dataName)`<br>Deletes a path user data entry                                            |
    | `void`                                      | `deleteSubPathData``(java.lang.String dataName)`<br>Deletes a subpath user data entry                                      |
    | `int`                                       | `getCategory``()`<br>Returns the network category (spatial or logical).                                                    |
    | `java.lang.String`                          | `getComponentTableName``(boolean addSchemaName)`<br>Returns the component table name                                       |
    | `java.lang.String`                          | `getDefaultComponentTableName``()`<br>Returns the default component table name, which is \_COMP\$                          |
    | `java.lang.String`                          | `getDefaultPartitionBlobTableName``()`<br>Returns the default partition table name, which is \_PBLOB\$                     |
    | [`FeatureMetadata`](lod/FeatureMetadata.md) | `getFeatureMetadata``()`<br>Returns the feature metadata.                                                                  |
    | `int`                                       | `getGeometryType``()`<br>Returns the network geometry type.                                                                |
    | [`HistoryMetadata`](HistoryMetadata.md)     | `getHistoryMetadata``()`<br>Returns the network history metadata.                                                          |
    | `java.lang.String`                          | `getLinkCostColumn``()`<br>Returns the link cost column name.                                                              |
    | `int`                                       | `getLinkDirection``()`<br>Returns the network link type (directed, or undirected).                                         |
    | `java.lang.String`                          | `getLinkDurationColumn``()`<br>Gets link duration column name                                                              |
    | `java.lang.String`                          | `getLinkGeomColumn``()`<br>Returns the link geometry column name in the database.                                          |
    | [`GeometryMetadata`](GeometryMetadata.md)   | `getLinkGeomMetadata``()`<br>Returns the link geometry metadata.                                                           |
    | `java.lang.String`                          | `getLinkPartitionColumn``()`<br>Deprecated.                                                                                |
    | `java.lang.String`                          | `getLinkTableName``(boolean addSchemaName)`<br>Returns the link table name in the database.                                |
    | `java.lang.String`                          | `getLRSGeomColumn``()`<br>Returns the network LRS geometry column name in the database.                                    |
    | [`GeometryMetadata`](GeometryMetadata.md)   | `getLRSGeomMetadata``()`<br>Returns the network LRS geometry metadata.                                                     |
    | `java.lang.String`                          | `getLRSTableName``(boolean addSchemaName)`<br>Returns the network geometry (LRS) table name in the database.               |
    | `java.lang.String`                          | `getName``()`<br>Returns the network name.                                                                                 |
    | [`Network`](Network.md)                     | `getNetwork``()`<br>Gets the network                                                                                       |
    | `int`                                       | `getNetworkID``()`<br>Gets the network ID.                                                                                 |
    | `java.lang.String`                          | `getNodeCostColumn``()`<br>Returns the node cost column name.                                                              |
    | `java.lang.String`                          | `getNodeDurationColumn``()`<br>Gets node duration column name                                                              |
    | `java.lang.String`                          | `getNodeGeomColumn``()`<br>Returns the node geometry column name in the database.                                          |
    | [`GeometryMetadata`](GeometryMetadata.md)   | `getNodeGeomMetadata``()`<br>Returns the node geometry metadata.                                                           |
    | `java.lang.String`                          | `getNodeLevelTableName``(boolean addSchemaName)`<br>Returns the node level table name                                      |
    | `java.lang.String`                          | `getNodePartitionColumn``()`<br>Deprecated.                                                                                |
    | `java.lang.String`                          | `getNodeTableName``(boolean addSchemaName)`<br>Returns the node table name in the database.                                |
    | `int`                                       | `getNoOfHierarchyLevels``()`<br>Returns the number of hierarchy levels.                                                    |
    | `int`                                       | `getNoOfPartitions``()`<br>Deprecated.                                                                                     |
    | `java.lang.String`                          | `getPartitionBlobTableName``(boolean addSchemaName)`<br>Returns the partition BLOB table name                              |
    | `java.lang.String`                          | `getPartitionTableName``()`<br>Deprecated.                                                                                 |
    | `java.lang.String`                          | `getPartitionTableName``(boolean addSchemaName)`<br>Returns the partition table name.                                      |
    | `java.lang.String`                          | `getPathGeomColumn``()`<br>Returns the path geometry column name in the database.                                          |
    | [`GeometryMetadata`](GeometryMetadata.md)   | `getPathGeomMetadata``()`<br>Returns the path geometry metadata.                                                           |
    | `java.lang.String`                          | `getPathLinkTableName``()`<br>Deprecated.                                                                                  |
    | `java.lang.String`                          | `getPathLinkTableName``(boolean addSchemaName)`<br>Returns the path-link table name.                                       |
    | `java.lang.String`                          | `getPathTableName``(boolean addSchemaName)`<br>Returns the path table name in the database.                                |
    | `java.lang.String`                          | `getSubPathGeomColumn``()`<br>Returns the subpath geometry column name in the database.                                    |
    | [`GeometryMetadata`](GeometryMetadata.md)   | `getSubPathGeomMetadata``()`<br>Returns the subpath geometry metadata.                                                     |
    | `java.lang.String`                          | `getSubPathTableName``(boolean addSchemaName)`<br>Returns the subpath table name in the database.                          |
    | `java.lang.String`                          | `getTopology``()`<br>Returns topology name of the network                                                                  |
    | `java.lang.String`                          | `getType``()`<br>Returns the network type.                                                                                 |
    | `java.lang.String`                          | `getUser``()`<br>Returns the network owner.                                                                                |
    | `java.lang.Object`                          | `getUserData``()`<br>Returns the user defined data.                                                                        |
    | `java.lang.Object`                          | `getUserData``(java.lang.String dataName)`<br>Gets user data                                                               |
    | [`UserDataMetadata`](UserDataMetadata.md)   | `getUserDataMetadata``()`<br>Returns the user data metadata                                                                |
    | `boolean`                                   | `isComplex``()`<br>Deprecated.                                                                                             |
    | `boolean`                                   | `isDirected``()`<br>Checks if the network is directed.                                                                     |
    | `boolean`                                   | `isGeodetic``()`<br>Returns if the network is a geodetic spatial network                                                   |
    | `boolean`                                   | `isHierarchical``()`<br>Checks if the network is hierarchical.                                                             |
    | `boolean`                                   | `isLogical``()`<br>Checks if the network is logical.                                                                       |
    | `boolean`                                   | `isLRSGeometry``()`<br>Checks if the network geometries are LRS SDO_GEOMETRY objects.                                      |
    | `boolean`                                   | `isPartitioned``()`<br>Deprecated.                                                                                         |
    | `boolean`                                   | `isSDOGeometry``()`<br>Checks if the network geometries are SDO_GEOMETRY objects.                                          |
    | `boolean`                                   | `isSimple``()`<br>Deprecated.                                                                                              |
    | `boolean`                                   | `isSpatial``()`<br>Checks if the network is spatial.                                                                       |
    | `boolean`                                   | `isTopoGeometry``()`<br>Checks if the network geometries are SDO_TOPO_GEOMETRY objects.                                    |
    | `boolean`                                   | `isUndirected``()`<br>Checks if the network is undirected.                                                                 |
    | `boolean`                                   | `isVersioned``()`<br>Checks if the network is versioned                                                                    |
    | `void`                                      | `setCategory``(int category)`<br>Sets the network category.                                                                |
    | `void`                                      | `setComponentTableName``(java.lang.String componentTableName)`<br>Sets the component table name                            |
    | `void`                                      | `setGeodetic``(boolean flag)`<br>Sets the geodetic geometry to flag                                                        |
    | `void`                                      | `setGeometryType``(int geometryTtype)`<br>Sets the geometry type of the network                                            |
    | `void`                                      | `setLinkCostColumn``(java.lang.String costColumn)`<br>Sets link cost column                                                |
    | `void`                                      | `setLinkDirection``(int direction)`<br>Sets link diretion (Network.UNDIRECTED_LINK or Network.DIRECTED_LINK)               |
    | `void`                                      | `setLinkDurationColumn``(java.lang.String durationColumn)`<br>Sets link duration column name                               |
    | `void`                                      | `setLinkGeomMetadata``(`[`GeometryMetadata`](GeometryMetadata.md)` geomMetadata)`<br>Sets Link Geometry Metadata           |
    | `void`                                      | `setLinkPartitionColumn``(java.lang.String partitionColumn)`<br>Deprecated.                                                |
    | `void`                                      | `setLRSGeomMetadata``(`[`GeometryMetadata`](GeometryMetadata.md)` geomMetadata)`<br>Sets LRS Geometry Metadata             |
    | `void`                                      | `setNodeCostColumn``(java.lang.String costColumn)`<br>Sets node cost column                                                |
    | `void`                                      | `setNodeDurationColumn``(java.lang.String durationColumn)`<br>Sets node duration column name                               |
    | `void`                                      | `setNodeGeomMetadata``(`[`GeometryMetadata`](GeometryMetadata.md)` geomMetadata)`<br>Sets Node Geometry Metadata           |
    | `void`                                      | `setNodeLevelTableName``(java.lang.String nodeLevelTableName)`<br>Sets the node level table name                           |
    | `void`                                      | `setNodePartitionColumn``(java.lang.String partitionColumn)`<br>Deprecated.                                                |
    | `void`                                      | `setNoOfHierarchyLevels``(int no)`<br>Sets the number of hierarchy levels.                                                 |
    | `void`                                      | `setNoOfPartitions``(int no)`<br>Deprecated.                                                                               |
    | `void`                                      | `setPartitionBlobTableName``(java.lang.String partitionBlobTableName)`<br>Sets the partition BLOB table name               |
    | `void`                                      | `setPartitionTableName``(java.lang.String partitionTableName)`<br>Sets partition table name                                |
    | `void`                                      | `setPathGeomMetadata``(`[`GeometryMetadata`](GeometryMetadata.md)` geomMetadata)`<br>Sets Path Geometry Metadata           |
    | `void`                                      | `setPathLinkTableName``(java.lang.String name)`<br>Set the path link table name                                            |
    | `void`                                      | `setSubPathGeomMetadata``(`[`GeometryMetadata`](GeometryMetadata.md)` geomMetadata)`<br>Sets SubPath Geometry Metadata     |
    | `void`                                      | `setType``(java.lang.String type)`<br>Sets network type                                                                    |
    | `void`                                      | `setUserData``(java.lang.Object userData)`<br>Sets user defined data.                                                      |
    | `void`                                      | `setUserData``(java.lang.String dataName, java.lang.Object data)`<br>Sets user data                                        |

<!-- -->

- - ### Field Detail

    - #### UNDIRECTED_LINK

          static final int UNDIRECTED_LINK

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### BIDIRECTED_LINK

          static final int BIDIRECTED_LINK

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DIRECTED_LINK

          static final int DIRECTED_LINK

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getUser

          java.lang.String getUser()

      Returns the network owner.

    <!-- -->

    - #### getName

          java.lang.String getName()

      Returns the network name.

    <!-- -->

    - #### getCategory

          int getCategory()

      Returns the network category (spatial or logical).

    <!-- -->

    - #### getType

          java.lang.String getType()

      Returns the network type.

    <!-- -->

    - #### getLinkDirection

          int getLinkDirection()

      Returns the network link type (directed, or undirected).

    <!-- -->

    - #### getGeometryType

          int getGeometryType()

      Returns the network geometry type.

    <!-- -->

    - #### getUserData

          java.lang.Object getUserData()

      Returns the user defined data.

    <!-- -->

    - #### setUserData

          void setUserData(java.lang.Object userData)

      Sets user defined data.
      Parameters:
      `userData` - the user data

    <!-- -->

    - #### getNodeGeomMetadata

          GeometryMetadata getNodeGeomMetadata()

      Returns the node geometry metadata.

    <!-- -->

    - #### getLinkGeomMetadata

          GeometryMetadata getLinkGeomMetadata()

      Returns the link geometry metadata.

    <!-- -->

    - #### getLRSGeomMetadata

          GeometryMetadata getLRSGeomMetadata()

      Returns the network LRS geometry metadata.

    <!-- -->

    - #### getPathGeomMetadata

          GeometryMetadata getPathGeomMetadata()

      Returns the path geometry metadata.

    <!-- -->

    - #### getSubPathGeomMetadata

          GeometryMetadata getSubPathGeomMetadata()

      Returns the subpath geometry metadata.

    <!-- -->

    - #### getLinkCostColumn

          java.lang.String getLinkCostColumn()

      Returns the link cost column name.

    <!-- -->

    - #### getNodeCostColumn

          java.lang.String getNodeCostColumn()

      Returns the node cost column name.

    <!-- -->

    - #### getPartitionTableName

          java.lang.String getPartitionTableName()

      Deprecated. 
      Returns the partition table name.

    <!-- -->

    - #### getPartitionTableName

          java.lang.String getPartitionTableName(boolean addSchemaName)

      Returns the partition table name.
      Parameters:
      `addSchemaName` - prefix schema name or not

    <!-- -->

    - #### getNodePartitionColumn

          java.lang.String getNodePartitionColumn()

      Deprecated. 
      Returns the node partition column name.

    <!-- -->

    - #### getLinkPartitionColumn

          java.lang.String getLinkPartitionColumn()

      Deprecated. 
      Returns the link partition column name.

    <!-- -->

    - #### getNoOfHierarchyLevels

          int getNoOfHierarchyLevels()

      Returns the number of hierarchy levels.

    <!-- -->

    - #### getNoOfPartitions

          int getNoOfPartitions()

      Deprecated. 
      Returns the number of partitions.

    <!-- -->

    - #### getPathLinkTableName

          java.lang.String getPathLinkTableName()

      Deprecated. 
      Returns the path-link table name.

    <!-- -->

    - #### getPathLinkTableName

          java.lang.String getPathLinkTableName(boolean addSchemaName)

      Returns the path-link table name.
      Parameters:
      `addSchemaName` - prefix schema name or not

    <!-- -->

    - #### isHierarchical

          boolean isHierarchical()

      Checks if the network is hierarchical.

    <!-- -->

    - #### isSpatial

          boolean isSpatial()

      Checks if the network is spatial.

    <!-- -->

    - #### isLogical

          boolean isLogical()

      Checks if the network is logical.

    <!-- -->

    - #### isDirected

          boolean isDirected()

      Checks if the network is directed.

    <!-- -->

    - #### isUndirected

          boolean isUndirected()

      Checks if the network is undirected.

    <!-- -->

    - #### setNoOfHierarchyLevels

          void setNoOfHierarchyLevels(int no)

      Sets the number of hierarchy levels.
      Parameters:
      `no` - the number of hierarchy levels

    <!-- -->

    - #### setNoOfPartitions

          void setNoOfPartitions(int no)

      Deprecated. 
      Sets the number of partitions.
      Parameters:
      `no` - the number of partitions

    <!-- -->

    - #### isSDOGeometry

          boolean isSDOGeometry()

      Checks if the network geometries are SDO_GEOMETRY objects.
      Returns:
      true if the geometry tyep is SDO_GEOMETRY, false otherwise

    <!-- -->

    - #### isLRSGeometry

          boolean isLRSGeometry()

      Checks if the network geometries are LRS SDO_GEOMETRY objects.
      Returns:
      true if the geometry type is LRS SDO_GEOMETRY, false otherwise

    <!-- -->

    - #### isTopoGeometry

          boolean isTopoGeometry()

      Checks if the network geometries are SDO_TOPO_GEOMETRY objects.
      Returns:
      true if the geometry type is SDO_TOPO_GEOMETRY, false otherwise

    <!-- -->

    - #### setCategory

          void setCategory(int category)

      Sets the network category. (Network.LOGICAL_NETWORK or Network.SPATIAL_NETWORK)
      Parameters:
      `category` - the network category to be set

    <!-- -->

    - #### clone

          java.lang.Object clone()

      Clones the metadata.

    <!-- -->

    - #### getNetworkID

          int getNetworkID()

      Gets the network ID.

    <!-- -->

    - #### getNetwork

          Network getNetwork()

      Gets the network

    <!-- -->

    - #### setNodeGeomMetadata

          void setNodeGeomMetadata(GeometryMetadata geomMetadata)

      Sets Node Geometry Metadata

    <!-- -->

    - #### setLinkGeomMetadata

          void setLinkGeomMetadata(GeometryMetadata geomMetadata)

      Sets Link Geometry Metadata

    <!-- -->

    - #### setPathGeomMetadata

          void setPathGeomMetadata(GeometryMetadata geomMetadata)

      Sets Path Geometry Metadata

    <!-- -->

    - #### setSubPathGeomMetadata

          void setSubPathGeomMetadata(GeometryMetadata geomMetadata)

      Sets SubPath Geometry Metadata

    <!-- -->

    - #### setLRSGeomMetadata

          void setLRSGeomMetadata(GeometryMetadata geomMetadata)

      Sets LRS Geometry Metadata

    <!-- -->

    - #### setLinkCostColumn

          void setLinkCostColumn(java.lang.String costColumn)

      Sets link cost column

    <!-- -->

    - #### setNodeCostColumn

          void setNodeCostColumn(java.lang.String costColumn)

      Sets node cost column

    <!-- -->

    - #### setNodePartitionColumn

          void setNodePartitionColumn(java.lang.String partitionColumn)

      Deprecated. 
      Sets node partition column

    <!-- -->

    - #### setLinkPartitionColumn

          void setLinkPartitionColumn(java.lang.String partitionColumn)

      Deprecated. 
      Sets link partition column

    <!-- -->

    - #### setType

          void setType(java.lang.String type)

      Sets network type

    <!-- -->

    - #### setLinkDirection

          void setLinkDirection(int direction)

      Sets link diretion (Network.UNDIRECTED_LINK or Network.DIRECTED_LINK)

    <!-- -->

    - #### setGeometryType

          void setGeometryType(int geometryTtype)

      Sets the geometry type of the network

    <!-- -->

    - #### isSimple

          boolean isSimple()

      Deprecated. 
      Checks if the network is a simple network. That is, it has no external references. to other networks

    <!-- -->

    - #### isComplex

          boolean isComplex()

      Deprecated. 
      Checks if the network is a complex network. That is, it refers other networks.

    <!-- -->

    - #### setPartitionTableName

          void setPartitionTableName(java.lang.String partitionTableName)

      Sets partition table name

    <!-- -->

    - #### setNodeDurationColumn

          void setNodeDurationColumn(java.lang.String durationColumn)

      Sets node duration column name

    <!-- -->

    - #### setLinkDurationColumn

          void setLinkDurationColumn(java.lang.String durationColumn)

      Sets link duration column name

    <!-- -->

    - #### getNodeDurationColumn

          java.lang.String getNodeDurationColumn()

      Gets node duration column name

    <!-- -->

    - #### getLinkDurationColumn

          java.lang.String getLinkDurationColumn()

      Gets link duration column name

    <!-- -->

    - #### isPartitioned

          boolean isPartitioned()

      Deprecated. 
      Checks if the network is partiioned (no of partitions \> 1 )

    <!-- -->

    - #### getTopology

          java.lang.String getTopology()

      Returns topology name of the network

    <!-- -->

    - #### setUserData

          void setUserData(java.lang.String dataName,
                           java.lang.Object data)

      Sets user data
      Parameters:
      `dataName` - name for the user data

      `data` - user data

    <!-- -->

    - #### getUserData

          java.lang.Object getUserData(java.lang.String dataName)

      Gets user data
      Parameters:
      `dataName` - name for the user data

      Returns:
      user data as an Java Object

    <!-- -->

    - #### containsUserData

          boolean containsUserData()

      Checks if the network has user data defined in user_sdo_network_user_data

    <!-- -->

    - #### addNodeData

          void addNodeData(java.lang.String dataName,
                           java.lang.String dataType,
                           int dataLength)
                    throws NetworkDataException

      Adds a node user data entry
      Parameters:
      `dataName` - data name for the user data

      `dataType` - data type for the user data ("INTEGER","NUMBER", "VARCHAR2")

      `dataLength` - data length for "VARCHAR2"

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### addLinkData

          void addLinkData(java.lang.String dataName,
                           java.lang.String dataType,
                           int dataLength)
                    throws NetworkDataException

      Adds a link user data entry
      Parameters:
      `dataName` - data name for the user data

      `dataType` - data type for the user data ("INTEGER","NUMBER", "VARCHAR2")

      `dataLength` - data length for "VARCHAR2"

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### addPathData

          void addPathData(java.lang.String dataName,
                           java.lang.String dataType,
                           int dataLength)
                    throws NetworkDataException

      Adds a path user data entry
      Parameters:
      `dataName` - data name for the user data

      `dataType` - data type for the user data ("INTEGER","NUMBER", "VARCHAR2")

      `dataLength` - data length for "VARCHAR2"

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### addSubPathData

          void addSubPathData(java.lang.String dataName,
                              java.lang.String dataType,
                              int dataLength)
                       throws NetworkDataException

      Adds a subpath user data entry
      Parameters:
      `dataName` - data name for the user data

      `dataType` - data type for the user data ("INTEGER","NUMBER", "VARCHAR2")

      `dataLength` - data length for "VARCHAR2"

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### deleteNodeData

          void deleteNodeData(java.lang.String dataName)

      Deletes a node user data entry
      Parameters:
      `dataName` - data name for the user data

    <!-- -->

    - #### deleteLinkData

          void deleteLinkData(java.lang.String dataName)

      Deletes a link user data entry
      Parameters:
      `dataName` - data name for the user data

    <!-- -->

    - #### deletePathData

          void deletePathData(java.lang.String dataName)

      Deletes a path user data entry
      Parameters:
      `dataName` - data name for the user data

    <!-- -->

    - #### deleteSubPathData

          void deleteSubPathData(java.lang.String dataName)

      Deletes a subpath user data entry
      Parameters:
      `dataName` - data name for the user data

    <!-- -->

    - #### getUserDataMetadata

          UserDataMetadata getUserDataMetadata()

      Returns the user data metadata

    <!-- -->

    - #### getHistoryMetadata

          HistoryMetadata getHistoryMetadata()

      Returns the network history metadata.

    <!-- -->

    - #### setPathLinkTableName

          void setPathLinkTableName(java.lang.String name)

      Set the path link table name

    <!-- -->

    - #### isVersioned

          boolean isVersioned()

      Checks if the network is versioned
      Returns:

    <!-- -->

    - #### getPartitionBlobTableName

          java.lang.String getPartitionBlobTableName(boolean addSchemaName)

      Returns the partition BLOB table name
      Parameters:
      `addSchemaName` - prefix schema name or not

      Returns:
      the partition BLOB table name

    <!-- -->

    - #### setPartitionBlobTableName

          void setPartitionBlobTableName(java.lang.String partitionBlobTableName)

      Sets the partition BLOB table name
      Parameters:
      `partitionBlobTableName` - the partition BLOB table name

    <!-- -->

    - #### getDefaultPartitionBlobTableName

          java.lang.String getDefaultPartitionBlobTableName()

      Returns the default partition table name, which is \_PBLOB\$
      Returns:
      the default partition table name

    <!-- -->

    - #### getComponentTableName

          java.lang.String getComponentTableName(boolean addSchemaName)

      Returns the component table name
      Parameters:
      `addSchemaName` - prefix schema name or not

      Returns:
      the component table name

    <!-- -->

    - #### setComponentTableName

          void setComponentTableName(java.lang.String componentTableName)

      Sets the component table name
      Parameters:
      `componentTableName` -

    <!-- -->

    - #### getDefaultComponentTableName

          java.lang.String getDefaultComponentTableName()

      Returns the default component table name, which is \_COMP\$
      Returns:
      the default component table name

    <!-- -->

    - #### getNodeLevelTableName

          java.lang.String getNodeLevelTableName(boolean addSchemaName)

      Returns the node level table name
      Parameters:
      `addSchemaName` - prefix schema name or not

      Returns:
      the node level table name

    <!-- -->

    - #### setNodeLevelTableName

          void setNodeLevelTableName(java.lang.String nodeLevelTableName)

      Sets the node level table name
      Parameters:
      `nodeLevelTableName` - the node level table name

    <!-- -->

    - #### getNodeTableName

          java.lang.String getNodeTableName(boolean addSchemaName)

      Returns the node table name in the database. This method is a shortcut for getNodeGeomMetadata.getTableName().
      Parameters:
      `addSchemaName` - prefix owner schema name or not

    <!-- -->

    - #### getLinkTableName

          java.lang.String getLinkTableName(boolean addSchemaName)

      Returns the link table name in the database.
      Parameters:
      `addSchemaName` - prefix owner schema name or not

    <!-- -->

    - #### getPathTableName

          java.lang.String getPathTableName(boolean addSchemaName)

      Returns the path table name in the database.
      Parameters:
      `addSchemaName` - prefix owner schema name or not

    <!-- -->

    - #### getSubPathTableName

          java.lang.String getSubPathTableName(boolean addSchemaName)

      Returns the subpath table name in the database.
      Parameters:
      `addSchemaName` - prefix owner schema name or not

    <!-- -->

    - #### getLRSTableName

          java.lang.String getLRSTableName(boolean addSchemaName)

      Returns the network geometry (LRS) table name in the database.
      Parameters:
      `addSchemaName` - prefix owner schema name or not

    <!-- -->

    - #### getNodeGeomColumn

          java.lang.String getNodeGeomColumn()

      Returns the node geometry column name in the database.

    <!-- -->

    - #### getLinkGeomColumn

          java.lang.String getLinkGeomColumn()

      Returns the link geometry column name in the database.

    <!-- -->

    - #### getPathGeomColumn

          java.lang.String getPathGeomColumn()

      Returns the path geometry column name in the database.

    <!-- -->

    - #### getSubPathGeomColumn

          java.lang.String getSubPathGeomColumn()

      Returns the subpath geometry column name in the database.

    <!-- -->

    - #### getLRSGeomColumn

          java.lang.String getLRSGeomColumn()

      Returns the network LRS geometry column name in the database.

    <!-- -->

    - #### getFeatureMetadata

          FeatureMetadata getFeatureMetadata()

      Returns the feature metadata.
      Returns:

    <!-- -->

    - #### isGeodetic

          boolean isGeodetic()

      Returns if the network is a geodetic spatial network
      Returns:
      true is yes, false otherwise

    <!-- -->

    - #### setGeodetic

          void setGeodetic(boolean flag)

      Sets the geodetic geometry to flag
      Parameters:
      `flag` - true if a geodetic spatial network, false otherwise

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NetworkManager.md)
- [Next Class](Node.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
