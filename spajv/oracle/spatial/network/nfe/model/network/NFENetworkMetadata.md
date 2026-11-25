Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFENetworkElement.md)
- [Next Class](NFENode.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.model.network

## Class NFENetworkMetadata

- java.lang.Object

- - [oracle.spatial.network.nfe.model.NFEMetadata](../NFEMetadata.md)

  - - oracle.spatial.network.nfe.model.network.NFENetworkMetadata

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFENetworkMetadata
      extends NFEMetadata

  This class holds metadata for an NFE Network.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFENetworkMetadata``()`    |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type    | Method and Description                                                                              |
    |----------------------|-----------------------------------------------------------------------------------------------------|
    | `NFENetworkMetadata` | `createCopy``()`<br>Returns a copy of the network.                                                  |
    | `java.lang.String`   | `getGeometryType``()`<br>Returns the network geometry type.                                         |
    | `long`               | `getId``()`<br>Returns the network id.                                                              |
    | `java.lang.String`   | `getLinkCostColumn``()`<br>Returns the link table cost column.                                      |
    | `java.lang.String`   | `getLinkDirection``()`<br>Returns the link direction.                                               |
    | `java.lang.String`   | `getLinkGeomColumn``()`<br>Returns the link table geometry column.                                  |
    | `java.lang.String`   | `getLinkTable``()`<br>Returns the link table.                                                       |
    | `java.lang.String`   | `getLinkTableIndexName``()`<br>Returns the link table index name.                                   |
    | `java.lang.String`   | `getName``()`<br>Returns the network name.                                                          |
    | `java.lang.String`   | `getNetworkCategory``()`<br>Returns the network category.                                           |
    | `java.lang.String`   | `getNodeCostColumn``()`<br>Returns the node table cost column.                                      |
    | `java.lang.String`   | `getNodeGeomColumn``()`<br>Returns the node table geometry column.                                  |
    | `java.lang.String`   | `getNodeTable``()`<br>Returns the node table.                                                       |
    | `java.lang.String`   | `getNodeTableIndexName``()`<br>Returns the node table index name.                                   |
    | `int`                | `getNoOfHierarchyLevels``()`<br>Returns the network number of hierarchy levels.                     |
    | `java.lang.String`   | `getPathGeomColumn``()`<br>Returns the path table geometry column.                                  |
    | `java.lang.String`   | `getPathLinkTableName``()`<br>Returns the path link table name.                                     |
    | `java.lang.String`   | `getPathTableName``()`<br>Returns the network path table name.                                      |
    | `boolean`            | `isDirected``()`<br>Returns true if the network is directed, false otherwise.                       |
    | `void`               | `setDirected``(boolean directedLink)`<br>Sets true if the network is directed, false otherwise.     |
    | `void`               | `setGeometryType``(java.lang.String geometryType)`<br>Sets the network geometry type.               |
    | `void`               | `setId``(long id)`<br>Sets the network id.                                                          |
    | `void`               | `setLinkCostColumn``(java.lang.String linkCostColumn)`<br>Sets the link table cost column.          |
    | `void`               | `setLinkDirection``(java.lang.String linkDirection)`<br>Sets the link direction.                    |
    | `void`               | `setLinkGeomColumn``(java.lang.String linkGeomColumn)`<br>Sets the link table geometry column.      |
    | `void`               | `setLinkTableName``(java.lang.String linkTableName)`<br>Sets the link table name.                   |
    | `void`               | `setName``(java.lang.String name)`<br>Sets the network name.                                        |
    | `void`               | `setNetworkCategory``(java.lang.String networkCategory)`<br>Sets the network category.              |
    | `void`               | `setNodeCostColumn``(java.lang.String nodeCostColumn)`<br>Sets the node table cost column.          |
    | `void`               | `setNodeGeomColumn``(java.lang.String nodeGeomColumn)`<br>Sets the node table geometry column       |
    | `void`               | `setNodeTableName``(java.lang.String nodeTableName)`<br>Sets the node table name.                   |
    | `void`               | `setNoOfHierarchyLevels``(int noOfHierarchyLevels)`<br>Sets the network number of hierarchy levels. |
    | `void`               | `setPathGeomColumn``(java.lang.String pathGeomColumn)`<br>Sets the path table geometry column.      |
    | `void`               | `setPathLinkTableName``(java.lang.String pathLinkTableName)`<br>Sets the path link table name.      |
    | `void`               | `setPathTableName``(java.lang.String pathTableName)`<br>Sets the network path table name.           |
    | `java.lang.String`   | `toString``()`                                                                                      |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.[NFEMetadata](../NFEMetadata.md)

      [`getTableSequence`](../NFEMetadata.md)`, `[`getTablesWithSequence`](../NFEMetadata.md)`, `[`hasSequence`](../NFEMetadata.md)`, `[`setTableSequence`](../NFEMetadata.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFENetworkMetadata

          public NFENetworkMetadata()

  <!-- -->

  - ### Method Detail

    - #### getName

          public java.lang.String getName()

      Returns the network name.
      Returns:
      network name

    <!-- -->

    - #### setName

          public void setName(java.lang.String name)

      Sets the network name.
      Parameters:
      `name` - network name

    <!-- -->

    - #### getId

          public long getId()

      Returns the network id.
      Returns:
      network id

    <!-- -->

    - #### setId

          public void setId(long id)

      Sets the network id.
      Parameters:
      `id` - network id

    <!-- -->

    - #### getNetworkCategory

          public java.lang.String getNetworkCategory()

      Returns the network category.
      Returns:
      network category

    <!-- -->

    - #### setNetworkCategory

          public void setNetworkCategory(java.lang.String networkCategory)

      Sets the network category.
      Parameters:
      `networkCategory` - network category

    <!-- -->

    - #### getGeometryType

          public java.lang.String getGeometryType()

      Returns the network geometry type.
      Returns:
      network geometry type

    <!-- -->

    - #### setGeometryType

          public void setGeometryType(java.lang.String geometryType)

      Sets the network geometry type.
      Parameters:
      `geometryType` - network geometry type

    <!-- -->

    - #### getNoOfHierarchyLevels

          public int getNoOfHierarchyLevels()

      Returns the network number of hierarchy levels.
      Returns:
      network number of hierarchy levels

    <!-- -->

    - #### setNoOfHierarchyLevels

          public void setNoOfHierarchyLevels(int noOfHierarchyLevels)

      Sets the network number of hierarchy levels.
      Parameters:
      `noOfHierarchyLevels` - network number of hierarchy levels

    <!-- -->

    - #### getNodeTable

          public java.lang.String getNodeTable()

      Returns the node table.
      Returns:
      note table

    <!-- -->

    - #### setNodeTableName

          public void setNodeTableName(java.lang.String nodeTableName)

      Sets the node table name.
      Parameters:
      `nodeTableName` - node table name

    <!-- -->

    - #### getNodeGeomColumn

          public java.lang.String getNodeGeomColumn()

      Returns the node table geometry column.
      Returns:
      node table geometry column

    <!-- -->

    - #### setNodeGeomColumn

          public void setNodeGeomColumn(java.lang.String nodeGeomColumn)

      Sets the node table geometry column
      Parameters:
      `nodeGeomColumn` - node table geometry column

    <!-- -->

    - #### getNodeTableIndexName

          public java.lang.String getNodeTableIndexName()

      Returns the node table index name.
      Returns:
      node table index name

    <!-- -->

    - #### getNodeCostColumn

          public java.lang.String getNodeCostColumn()

      Returns the node table cost column.
      Returns:
      node table cost column

    <!-- -->

    - #### setNodeCostColumn

          public void setNodeCostColumn(java.lang.String nodeCostColumn)

      Sets the node table cost column.
      Parameters:
      `nodeCostColumn` - node table cost column

    <!-- -->

    - #### getLinkTable

          public java.lang.String getLinkTable()

      Returns the link table.
      Returns:
      link table

    <!-- -->

    - #### setLinkTableName

          public void setLinkTableName(java.lang.String linkTableName)

      Sets the link table name.
      Parameters:
      `linkTableName` - link table name

    <!-- -->

    - #### getLinkGeomColumn

          public java.lang.String getLinkGeomColumn()

      Returns the link table geometry column.
      Returns:
      link table geometry column

    <!-- -->

    - #### setLinkGeomColumn

          public void setLinkGeomColumn(java.lang.String linkGeomColumn)

      Sets the link table geometry column.
      Parameters:
      `linkGeomColumn` - link table geometry column

    <!-- -->

    - #### getLinkTableIndexName

          public java.lang.String getLinkTableIndexName()

      Returns the link table index name.
      Returns:
      link table index name

    <!-- -->

    - #### getLinkDirection

          public java.lang.String getLinkDirection()

      Returns the link direction.
      Returns:
      link direction

    <!-- -->

    - #### setLinkDirection

          public void setLinkDirection(java.lang.String linkDirection)

      Sets the link direction.
      Parameters:
      `linkDirection` - link direction

    <!-- -->

    - #### isDirected

          public boolean isDirected()

      Returns true if the network is directed, false otherwise.
      Returns:
      true if the network is directed, false otherwise.

    <!-- -->

    - #### setDirected

          public void setDirected(boolean directedLink)

      Sets true if the network is directed, false otherwise.
      Parameters:
      `directedLink` - true if the network is directed, false otherwise

    <!-- -->

    - #### getLinkCostColumn

          public java.lang.String getLinkCostColumn()

      Returns the link table cost column.
      Returns:
      link table cost column

    <!-- -->

    - #### setLinkCostColumn

          public void setLinkCostColumn(java.lang.String linkCostColumn)

      Sets the link table cost column.
      Parameters:
      `linkCostColumn` - link table cost column

    <!-- -->

    - #### getPathTableName

          public java.lang.String getPathTableName()

      Returns the network path table name.
      Returns:
      network path table name

    <!-- -->

    - #### setPathTableName

          public void setPathTableName(java.lang.String pathTableName)

      Sets the network path table name.
      Parameters:
      `pathTableName` - network path table name

    <!-- -->

    - #### getPathGeomColumn

          public java.lang.String getPathGeomColumn()

      Returns the path table geometry column.
      Returns:
      path table geometry column

    <!-- -->

    - #### setPathGeomColumn

          public void setPathGeomColumn(java.lang.String pathGeomColumn)

      Sets the path table geometry column.
      Parameters:
      `pathGeomColumn` - path table geometry column

    <!-- -->

    - #### getPathLinkTableName

          public java.lang.String getPathLinkTableName()

      Returns the path link table name.
      Returns:
      path link table name

    <!-- -->

    - #### setPathLinkTableName

          public void setPathLinkTableName(java.lang.String pathLinkTableName)

      Sets the path link table name.
      Parameters:
      `pathLinkTableName` - path link table name

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### createCopy

          public NFENetworkMetadata createCopy()

      Returns a copy of the network.
      Returns:
      copy of the network

Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFENetworkElement.md)
- [Next Class](NFENode.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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
