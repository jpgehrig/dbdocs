Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](LODNetworkException.md)
- [Next Class](LODNetworkManager.md)

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

oracle.spatial.network.lod

## Class LODNetworkFactory

- java.lang.Object

- - oracle.spatial.network.lod.LODNetworkFactory

<!-- -->

-

  ------------------------------------------------------------------------



      public class LODNetworkFactory
      extends java.lang.Object

  This class handles network element creation for Oracle Spatial Network Data Model.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static int`      | `MIN_LINK_LEVEL`      |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                        | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                |
    |----------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`LogicalBasicNetwork`](LogicalBasicNetwork.md) | `createLogicalBasicNetwork``(java.lang.String networkName, int linkLevel)`<br>Creates an empty logical network.                                                                                                                                                                                                                                                                                                                       |
    | `static `[`LogicalBasicNetwork`](LogicalBasicNetwork.md) | `createLogicalBasicNetwork``(java.lang.String networkName, int linkLevel, int numNodes, int numLinks)`<br>Creates an empty logical network.                                                                                                                                                                                                                                                                                           |
    | `static `[`LogicalHeavyPath`](LogicalHeavyPath.md)       | `createLogicalHeavyPath``(`[`LogicalLink`](LogicalLink.md)`[] links, `[`LogicalNode`](LogicalNode.md)`[] nodes, double[] costs, `[`CategorizedUserData`](CategorizedUserData.md)` userData, boolean isReverse)`<br>Creates a heavy-weight logical path, which contains the object representation of the links and nodes on the path.                                                                                                  |
    | `static `[`LogicalHeavyPath`](LogicalHeavyPath.md)       | `createLogicalHeavyPath``(`[`LogicalLink`](LogicalLink.md)`[] links, `[`LogicalNode`](LogicalNode.md)`[] nodes, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated. <br>use createLogicalHeavyPath( LogicalLink\[\] links, LogicalNode\[\] nodes, double\[\] costs, CategorizedUserData userData)                                                                                                              |
    | `static `[`LogicalLightPath`](LogicalLightPath.md)       | `createLogicalLightPath``(long startNodeId, long endNodeId, long firstLink, long lastLink, int numberOfNodes, int numberOfLinks, double[] costs, `[`CategorizedUserData`](CategorizedUserData.md)` userData, boolean isReverse)`<br>Creates a light-weight logical path, which contains only the start and end node IDs and costs of the path.                                                                                        |
    | `static `[`LogicalLightSubPath`](LogicalLightSubPath.md) | `createLogicalLightSubPath``(`[`LogicalLightPath`](LogicalLightPath.md)` refPath, int startLinkIndex, double startPercentage, int endLinkIndex, double endPercentage, double[] costs, `[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Creates a light-weight logical sub-path, i.e., a logical sub-path that refers to a light-weight logical path.                                                                   |
    | `static `[`LogicalLink`](LogicalLink.md)                 | `createLogicalLink``(long id, int level, long startNodeId, long endNodeId, double cost, boolean isBidirected, boolean isActive, `[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Creates a stand-alone logical link.                                                                                                                                                                                                   |
    | `static `[`LogicalLink`](LogicalLink.md)                 | `createLogicalLink``(long id, int level, long startNodeId, long endNodeId, double cost, boolean isBidirected, boolean isActive, `[`LODUserDataIO`](LODUserDataIO.md)` udio)`<br>Deprecated.                                                                                                                                                                                                                                           |
    | `static `[`LogicalLink`](LogicalLink.md)                 | `createLogicalLink``(long id, int level, long startNodeId, long endNodeId, double cost, boolean isBidirected, boolean isActive, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                                                                                                                                            |
    | `static `[`LogicalLink`](LogicalLink.md)                 | `createLogicalLink``(long id, long startNodeId, long endNodeId, double cost, boolean isBidirected, boolean isActive, `[`LODUserDataIO`](LODUserDataIO.md)` udio)`<br>Deprecated.                                                                                                                                                                                                                                                      |
    | `static `[`LogicalLink`](LogicalLink.md)                 | `createLogicalLink``(long id, long startNodeId, long endNodeId, double cost, boolean isBidirected, boolean isActive, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                                                                                                                                                       |
    | `static `[`LogicalNetLink`](LogicalNetLink.md)           | `createLogicalNetLink``(long id, int level, `[`LogicalNetNode`](LogicalNetNode.md)` startNode, `[`LogicalNetNode`](LogicalNetNode.md)` endNode, double cost, boolean isBidirected, boolean isActive, `[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Creates a logical link with reference to its start and end node objects.                                                                                         |
    | `static `[`LogicalNetLink`](LogicalNetLink.md)           | `createLogicalNetLink``(long id, int level, `[`LogicalNetNode`](LogicalNetNode.md)` startNode, `[`LogicalNetNode`](LogicalNetNode.md)` endNode, double cost, boolean isBidirected, boolean isActive, `[`LODUserDataIO`](LODUserDataIO.md)` udio)`<br>Deprecated.                                                                                                                                                                      |
    | `static `[`LogicalNetLink`](LogicalNetLink.md)           | `createLogicalNetLink``(long id, int level, `[`LogicalNetNode`](LogicalNetNode.md)` startNode, `[`LogicalNetNode`](LogicalNetNode.md)` endNode, double cost, boolean isBidirected, boolean isActive, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                                                                       |
    | `static `[`LogicalNetLink`](LogicalNetLink.md)           | `createLogicalNetLink``(long id, `[`LogicalNetNode`](LogicalNetNode.md)` startNode, `[`LogicalNetNode`](LogicalNetNode.md)` endNode, double cost, boolean isBidirected, boolean isActive, `[`LODUserDataIO`](LODUserDataIO.md)` udio)`<br>Deprecated.                                                                                                                                                                                 |
    | `static `[`LogicalNetLink`](LogicalNetLink.md)           | `createLogicalNetLink``(long id, `[`LogicalNetNode`](LogicalNetNode.md)` startNode, `[`LogicalNetNode`](LogicalNetNode.md)` endNode, double cost, boolean isBidirected, boolean isActive, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                                                                                  |
    | `static `[`LogicalNetNode`](LogicalNetNode.md)           | `createLogicalNetNode``(long id, double cost, boolean isActive, int maxLinkLevel, int numInLinks, int numOutLinks, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                                                                                                                                                         |
    | `static `[`LogicalNetNode`](LogicalNetNode.md)           | `createLogicalNetNode``(long id, double cost, boolean isActive, int maxLinkLevel, `[`LODUserDataIO`](LODUserDataIO.md)` udio)`<br>Deprecated.                                                                                                                                                                                                                                                                                         |
    | `static `[`LogicalNetNode`](LogicalNetNode.md)           | `createLogicalNetNode``(long id, double cost, boolean isActive, int maxLinkLevel, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                                                                                                                                                                                          |
    | `static `[`LogicalNetNode`](LogicalNetNode.md)           | `createLogicalNetNode``(long id, double cost, boolean isActive, `[`LODUserDataIO`](LODUserDataIO.md)` udio)`<br>Deprecated.                                                                                                                                                                                                                                                                                                           |
    | `static `[`LogicalNetNode`](LogicalNetNode.md)           | `createLogicalNetNode``(long id, double cost, boolean isActive, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                                                                                                                                                                                                            |
    | `static `[`LogicalNetNode`](LogicalNetNode.md)           | `createLogicalNetNode``(long id, int partitionId, int linkLevel, double cost, boolean isActive, int maxLinkLevel, int numInLinks, int numOutLinks, `[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Creates a logical node to which we can add reference to incident links.                                                                                                                                            |
    | `static `[`LogicalNetNode`](LogicalNetNode.md)           | `createLogicalNetNode``(long id, int partitionId, int linkLevel, double cost, boolean isActive, int maxLinkLevel, int numInLinks, int numOutLinks, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                                                                                                                         |
    | `static `[`LogicalNode`](LogicalNode.md)                 | `createLogicalNode``(long id, double cost, boolean isActive, int maxLinkLevel, `[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Creates a stand-alone logical node.                                                                                                                                                                                                                                                    |
    | `static `[`LogicalNode`](LogicalNode.md)                 | `createLogicalNode``(long id, double cost, boolean isActive, int maxLinkLevel, `[`LODUserDataIO`](LODUserDataIO.md)` udio)`<br>Creates a stand-alone logical node.                                                                                                                                                                                                                                                                    |
    | `static `[`LogicalNode`](LogicalNode.md)                 | `createLogicalNode``(long id, double cost, boolean isActive, int maxLinkLevel, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                                                                                                                                                                                             |
    | `static `[`LogicalNode`](LogicalNode.md)                 | `createLogicalNode``(long id, double cost, boolean isActive, `[`LODUserDataIO`](LODUserDataIO.md)` udio)`<br>Deprecated.                                                                                                                                                                                                                                                                                                              |
    | `static `[`LogicalNode`](LogicalNode.md)                 | `createLogicalNode``(long id, double cost, boolean isActive, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                                                                                                                                                                                                               |
    | `static `[`LogicalPartition`](LogicalPartition.md)       | `createLogicalPartition``(java.lang.String networkName, int partitionId, int linkLevel)`<br>Creates an empty logical partition.                                                                                                                                                                                                                                                                                                       |
    | `static `[`LogicalPartition`](LogicalPartition.md)       | `createLogicalPartition``(java.lang.String networkName, int partitionId, int linkLevel, int numInternalNodes, int numExternalNodes, int numInternalLinks, int numBoundaryLinks)`<br>Creates an empty logical partition.                                                                                                                                                                                                               |
    | `static `[`LogicalPath`](LogicalPath.md)                 | `createLogicalPath``(long[] linkIds, long[] nodeIds, double[] costs, `[`CategorizedUserData`](CategorizedUserData.md)` userData, boolean isReverse)`<br>Creates a logical path, which contains only the IDs of the links and the nodes on the path, instead of the link and node objects.                                                                                                                                             |
    | `static `[`LogicalPath`](LogicalPath.md)                 | `createLogicalPath``(long[] linkIds, long[] nodeIds, double[] costs, java.util.Map<java.lang.String,java.lang.Object> userData, boolean isReverse)`<br>Deprecated.                                                                                                                                                                                                                                                                    |
    | `static `[`LogicalPath`](LogicalPath.md)                 | `createLogicalPath``(long[] linkIds, long[] nodeIds, double cost, java.util.Map<java.lang.String,java.lang.Object> userData, boolean isReverse)`<br>Deprecated. <br>use createLogicalPath( long\[\] linkIds, long\[\] nodeIds, double\[\] costs, Map userData)                                                                                                                                                                        |
    | `static `[`LogicalSubPath`](LogicalSubPath.md)           | `createLogicalSubPath``(`[`LogicalPath`](LogicalPath.md)` refPath, int startLinkIndex, double startPercentage, int endLinkIndex, double endPercentage, double[] costs, `[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Creates a logical sub-path.                                                                                                                                                                    |
    | `static `[`LogicalSubPath`](LogicalSubPath.md)           | `createLogicalSubPath``(`[`LogicalPath`](LogicalPath.md)` refPath, int startLinkIndex, double startPercentage, int endLinkIndex, double endPercentage, double[] costs, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                                                                                                     |
    | `static `[`LogicalSubPath`](LogicalSubPath.md)           | `createLogicalSubPath``(`[`LogicalPath`](LogicalPath.md)` refPath, int startLinkIndex, double startPercentage, int endLinkIndex, double endPercentage, double cost, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated. <br>use createLogicalSubPath( LogicalPath refPath, int startLinkIndex, double startPercentage, int endLinkIndex, double endPercentage, double\[\] costs, CategorizedUserData userData) |
    | `static `[`SpatialBasicNetwork`](SpatialBasicNetwork.md) | `createSpatialBasicNetwork``(java.lang.String networkName, int linkLevel)`<br>Creates an empty spatial network.                                                                                                                                                                                                                                                                                                                       |
    | `static `[`SpatialBasicNetwork`](SpatialBasicNetwork.md) | `createSpatialBasicNetwork``(java.lang.String networkName, int linkLevel, int numNodes, int numLinks)`<br>Creates an empty spatial network.                                                                                                                                                                                                                                                                                           |
    | `static `[`SpatialHeavyPath`](SpatialHeavyPath.md)       | `createSpatialHeavyPath``(`[`SpatialLink`](SpatialLink.md)`[] links, `[`SpatialNode`](SpatialNode.md)`[] nodes, double[] costs, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, `[`CategorizedUserData`](CategorizedUserData.md)` userData, boolean isReverse)`<br>Creates a heavy-weight spatial path, which contains the object representation of the links and nodes on the path.                                           |
    | `static `[`SpatialHeavyPath`](SpatialHeavyPath.md)       | `createSpatialHeavyPath``(`[`SpatialLink`](SpatialLink.md)`[] links, `[`SpatialNode`](SpatialNode.md)`[] nodes, double[] costs, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, java.util.Map<java.lang.String,java.lang.Object> userData, boolean isReverse)`<br>Creates a heavy-weight spatial path, which contains the object representation of the links and nodes on the path.                                            |
    | `static `[`SpatialHeavyPath`](SpatialHeavyPath.md)       | `createSpatialHeavyPath``(`[`SpatialLink`](SpatialLink.md)`[] links, `[`SpatialNode`](SpatialNode.md)`[] nodes, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Creates a heavy-weight spatial path, which contains the object representation of the links and nodes on the path.                                                                               |
    | `static `[`SpatialLink`](SpatialLink.md)                 | `createSpatialLink``(long id, int level, long startNodeId, long endNodeId, double cost, boolean isBidirected, boolean isActive, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, `[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Creates a stand-alone spatial link.                                                                                                                                            |
    | `static `[`SpatialLink`](SpatialLink.md)                 | `createSpatialLink``(long id, int level, long startNodeId, long endNodeId, double cost, boolean isBidirected, boolean isActive, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, `[`LODUserDataIO`](LODUserDataIO.md)` udio)`<br>Deprecated.                                                                                                                                                                                    |
    | `static `[`SpatialLink`](SpatialLink.md)                 | `createSpatialLink``(long id, int level, long startNodeId, long endNodeId, double cost, boolean isBidirected, boolean isActive, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                                                                                     |
    | `static `[`SpatialLink`](SpatialLink.md)                 | `createSpatialLink``(long id, long startNodeId, long endNodeId, double cost, boolean isBidirected, boolean isActive, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, `[`LODUserDataIO`](LODUserDataIO.md)` udio)`<br>Deprecated.                                                                                                                                                                                               |
    | `static `[`SpatialLink`](SpatialLink.md)                 | `createSpatialLink``(long id, long startNodeId, long endNodeId, double cost, boolean isBidirected, boolean isActive, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                                                                                                |
    | `static `[`SpatialNetLink`](SpatialNetLink.md)           | `createSpatialNetLink``(long id, int level, `[`SpatialNetNode`](SpatialNetNode.md)` startNode, `[`SpatialNetNode`](SpatialNetNode.md)` endNode, double cost, boolean isBidirected, boolean isActive, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, `[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Creates a spatial link with reference to its start and end node objects.                                  |
    | `static `[`SpatialNetLink`](SpatialNetLink.md)           | `createSpatialNetLink``(long id, int level, `[`SpatialNetNode`](SpatialNetNode.md)` startNode, `[`SpatialNetNode`](SpatialNetNode.md)` endNode, double cost, boolean isBidirected, boolean isActive, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, `[`LODUserDataIO`](LODUserDataIO.md)` udio)`<br>Deprecated.                                                                                                               |
    | `static `[`SpatialNetLink`](SpatialNetLink.md)           | `createSpatialNetLink``(long id, int level, `[`SpatialNetNode`](SpatialNetNode.md)` startNode, `[`SpatialNetNode`](SpatialNetNode.md)` endNode, double cost, boolean isBidirected, boolean isActive, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                |
    | `static `[`SpatialNetLink`](SpatialNetLink.md)           | `createSpatialNetLink``(long id, `[`SpatialNetNode`](SpatialNetNode.md)` startNode, `[`SpatialNetNode`](SpatialNetNode.md)` endNode, double cost, boolean isBidirected, boolean isActive, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, `[`LODUserDataIO`](LODUserDataIO.md)` udio)`<br>Creates a spatial link with reference to its start and end node objects.                                                             |
    | `static `[`SpatialNetLink`](SpatialNetLink.md)           | `createSpatialNetLink``(long id, `[`SpatialNetNode`](SpatialNetNode.md)` startNode, `[`SpatialNetNode`](SpatialNetNode.md)` endNode, double cost, boolean isBidirected, boolean isActive, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Creates a spatial link with reference to its start and end node objects.                                              |
    | `static `[`SpatialNetNode`](SpatialNetNode.md)           | `createSpatialNetNode``(long id, int linkLevel, double cost, boolean isActive, int maxLinkLevel, int numInLinks, int numOutLinks, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                                                                                   |
    | `static `[`SpatialNetNode`](SpatialNetNode.md)           | `createSpatialNetNode``(long id, int linkLevel, double cost, boolean isActive, int maxLinkLevel, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, `[`LODUserDataIO`](LODUserDataIO.md)` udio)`<br>Deprecated.                                                                                                                                                                                                                   |
    | `static `[`SpatialNetNode`](SpatialNetNode.md)           | `createSpatialNetNode``(long id, int linkLevel, double cost, boolean isActive, int maxLinkLevel, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                                                                                                                    |
    | `static `[`SpatialNetNode`](SpatialNetNode.md)           | `createSpatialNetNode``(long id, int linkLevel, double cost, boolean isActive, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, `[`LODUserDataIO`](LODUserDataIO.md)` udio)`<br>Deprecated.                                                                                                                                                                                                                                     |
    | `static `[`SpatialNetNode`](SpatialNetNode.md)           | `createSpatialNetNode``(long id, int linkLevel, double cost, boolean isActive, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                                                                                                                                      |
    | `static `[`SpatialNetNode`](SpatialNetNode.md)           | `createSpatialNetNode``(long id, int partitionId, int linkLevel, double cost, boolean isActive, int maxLinkLevel, int numInLinks, int numOutLinks, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, `[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Creates a spatial node to which we can add reference to incident links.                                                                                     |
    | `static `[`SpatialNetNode`](SpatialNetNode.md)           | `createSpatialNetNode``(long id, int partitionId, int linkLevel, double cost, boolean isActive, int maxLinkLevel, int numInLinks, int numOutLinks, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                                                                  |
    | `static `[`SpatialNode`](SpatialNode.md)                 | `createSpatialNode``(long id, double cost, boolean isActive, int maxLinkLevel, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, `[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Creates a stand-alone spatial node.                                                                                                                                                                                             |
    | `static `[`SpatialNode`](SpatialNode.md)                 | `createSpatialNode``(long id, double cost, boolean isActive, int maxLinkLevel, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                                                                                                                                      |
    | `static `[`SpatialNode`](SpatialNode.md)                 | `createSpatialNode``(long id, double cost, boolean isActive, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, `[`LODUserDataIO`](LODUserDataIO.md)` udio)`<br>Deprecated.                                                                                                                                                                                                                                                       |
    | `static `[`SpatialNode`](SpatialNode.md)                 | `createSpatialNode``(long id, double cost, boolean isActive, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                                                                                                                                                        |
    | `static `[`SpatialNode`](SpatialNode.md)                 | `createSpatialNode``(long id, double cost, int maxLinkLevel, boolean isActive, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, `[`LODUserDataIO`](LODUserDataIO.md)` udio)`<br>Creates a stand-alone spatial node.                                                                                                                                                                                                             |
    | `static `[`SpatialPartition`](SpatialPartition.md)       | `createSpatialPartition``(java.lang.String networkName, int partitionId, int linkLevel)`<br>Creates an empty spatial partition.                                                                                                                                                                                                                                                                                                       |
    | `static `[`SpatialPartition`](SpatialPartition.md)       | `createSpatialPartition``(java.lang.String networkName, int partitionId, int linkLevel, int numInternalNodes, int numExternalNodes, int numInternalLinks, int numBoundaryLinks)`<br>Creates an empty spatial partition.                                                                                                                                                                                                               |
    | `static `[`SpatialPath`](SpatialPath.md)                 | `createSpatialPath``(long[] linkIds, long[] nodeIds, double[] costs, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, `[`CategorizedUserData`](CategorizedUserData.md)` userData, boolean isReverse)`<br>Creates a light-weight spatial path, which contains only the IDs of the links and the nodes on the path, instead of the link and node objects.                                                                         |
    | `static `[`SpatialPath`](SpatialPath.md)                 | `createSpatialPath``(long[] linkIds, long[] nodeIds, double[] costs, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, java.util.Map<java.lang.String,java.lang.Object> userData, boolean isReverse)`<br>Deprecated.                                                                                                                                                                                                             |
    | `static `[`SpatialSubPath`](SpatialSubPath.md)           | `createSpatialSubPath``(`[`SpatialPath`](SpatialPath.md)` referencePath, int startLinkIndex, double startPercentage, int endLinkIndex, double endPercentage, double[] costs, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, `[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Creates a spatial sub-path.                                                                                                       |
    | `static `[`SpatialSubPath`](SpatialSubPath.md)           | `createSpatialSubPath``(`[`SpatialPath`](SpatialPath.md)` referencePath, int startLinkIndex, int endLinkIndex, double startPercentage, double endPercentage, double[] costs, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, java.util.Map<java.lang.String,java.lang.Object> userData)`<br>Deprecated.                                                                                                                        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### MIN_LINK_LEVEL

          public static int MIN_LINK_LEVEL

  <!-- -->

  - ### Method Detail

    - #### createLogicalBasicNetwork

          public static LogicalBasicNetwork createLogicalBasicNetwork(java.lang.String networkName,
                                                                      int linkLevel)

      Creates an empty logical network.
      Parameters:
      `networkName` - network name

      Returns:
      an empty logical network

    <!-- -->

    - #### createLogicalBasicNetwork

          public static LogicalBasicNetwork createLogicalBasicNetwork(java.lang.String networkName,
                                                                      int linkLevel,
                                                                      int numNodes,
                                                                      int numLinks)

      Creates an empty logical network. The variables in this netowrk is initialized according to the input number of nodes and links. Compared with the previous method, using this method will improve the performance of adding node and links to the network later on.
      Parameters:
      `networkName` - network name

      `numNodes` - estimated number of nodes

      `numLinks` - estimated number of links

      Returns:
      an empty network

    <!-- -->

    - #### createLogicalPartition

          public static LogicalPartition createLogicalPartition(java.lang.String networkName,
                                                                int partitionId,
                                                                int linkLevel)

      Creates an empty logical partition.
      Parameters:
      `networkName` - network name

      `partitionId` - partition ID

      Returns:
      an empty logical partition

    <!-- -->

    - #### createLogicalPartition

          public static LogicalPartition createLogicalPartition(java.lang.String networkName,
                                                                int partitionId,
                                                                int linkLevel,
                                                                int numInternalNodes,
                                                                int numExternalNodes,
                                                                int numInternalLinks,
                                                                int numBoundaryLinks)

      Creates an empty logical partition. The variables in this partition are initialized according to the estimated number of nodes and links. Compared with the previous method, using this method will improve the performance of adding node and links to the partition later on.
      Parameters:
      `networkName` - network name

      `partitionId` - partition ID

      `numInternalNodes` - estimated number of internal nodes

      `numExternalNodes` - estimated number of external nodes

      `numInternalLinks` - estimated number of internal links

      `numBoundaryLinks` - estimated number of external links

      Returns:
      an empty logical partition

    <!-- -->

    - #### createLogicalNode

          public static LogicalNode createLogicalNode(long id,
                                                      double cost,
                                                      boolean isActive,
                                                      int maxLinkLevel,
                                                      LODUserDataIO udio)

      Creates a stand-alone logical node.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `udio` - user data IO implementation

      Returns:
      logical node

    <!-- -->

    - #### createLogicalNode

          public static LogicalNode createLogicalNode(long id,
                                                      double cost,
                                                      boolean isActive,
                                                      LODUserDataIO udio)

      Deprecated. 
      Creates a stand-alone logical node.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `udio` - user data IO implementation

      Returns:
      logical node

    <!-- -->

    - #### createLogicalNode

          public static LogicalNode createLogicalNode(long id,
                                                      double cost,
                                                      boolean isActive,
                                                      java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a stand-alone logical node.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `userData` - user data name-value pairs

      Returns:
      logical node

    <!-- -->

    - #### createLogicalNode

          public static LogicalNode createLogicalNode(long id,
                                                      double cost,
                                                      boolean isActive,
                                                      int maxLinkLevel,
                                                      java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a stand-alone logical node.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `userData` - user data name-value pairs

      Returns:
      logical node

    <!-- -->

    - #### createLogicalNode

          public static LogicalNode createLogicalNode(long id,
                                                      double cost,
                                                      boolean isActive,
                                                      int maxLinkLevel,
                                                      CategorizedUserData userData)

      Creates a stand-alone logical node.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `userData` - user data

      Returns:
      logical node

    <!-- -->

    - #### createLogicalNetNode

          public static LogicalNetNode createLogicalNetNode(long id,
                                                            double cost,
                                                            boolean isActive,
                                                            LODUserDataIO udio)

      Deprecated. 
      Creates a logical node to which we can add reference to incident links.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `udio` - user data IO implementation

      Returns:
      a logical node to which we can add reference to incident links

    <!-- -->

    - #### createLogicalNetNode

          public static LogicalNetNode createLogicalNetNode(long id,
                                                            double cost,
                                                            boolean isActive,
                                                            int maxLinkLevel,
                                                            LODUserDataIO udio)

      Deprecated. 
      Creates a logical node to which we can add reference to incident links.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `udio` - user data IO implementation

      Returns:
      a logical node to which we can add reference to incident links

    <!-- -->

    - #### createLogicalNetNode

          public static LogicalNetNode createLogicalNetNode(long id,
                                                            double cost,
                                                            boolean isActive,
                                                            java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a logical node to which we can add reference to incident links.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `userData` - user data name-value pairs

      Returns:
      a logical node to which we can add reference to incident links

    <!-- -->

    - #### createLogicalNetNode

          public static LogicalNetNode createLogicalNetNode(long id,
                                                            double cost,
                                                            boolean isActive,
                                                            int maxLinkLevel,
                                                            java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a logical node to which we can add reference to incident links.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `userData` - user data name-value pairs

      Returns:
      a logical node to which we can add reference to incident links

    <!-- -->

    - #### createLogicalNetNode

          public static LogicalNetNode createLogicalNetNode(long id,
                                                            double cost,
                                                            boolean isActive,
                                                            int maxLinkLevel,
                                                            int numInLinks,
                                                            int numOutLinks,
                                                            java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a logical node to which we can add reference to incident links.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `userData` - user data name-value pairs

      Returns:
      a logical node to which we can add reference to incident links

    <!-- -->

    - #### createLogicalNetNode

          public static LogicalNetNode createLogicalNetNode(long id,
                                                            int partitionId,
                                                            int linkLevel,
                                                            double cost,
                                                            boolean isActive,
                                                            int maxLinkLevel,
                                                            int numInLinks,
                                                            int numOutLinks,
                                                            java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a logical node to which we can add reference to incident links.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `userData` - user data name-value pairs

      Returns:
      a logical node to which we can add reference to incident links

    <!-- -->

    - #### createLogicalNetNode

          public static LogicalNetNode createLogicalNetNode(long id,
                                                            int partitionId,
                                                            int linkLevel,
                                                            double cost,
                                                            boolean isActive,
                                                            int maxLinkLevel,
                                                            int numInLinks,
                                                            int numOutLinks,
                                                            CategorizedUserData userData)

      Creates a logical node to which we can add reference to incident links.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `userData` - user data name-value pairs

      Returns:
      a logical node to which we can add reference to incident links

    <!-- -->

    - #### createLogicalLink

          public static LogicalLink createLogicalLink(long id,
                                                      long startNodeId,
                                                      long endNodeId,
                                                      double cost,
                                                      boolean isBidirected,
                                                      boolean isActive,
                                                      LODUserDataIO udio)

      Deprecated. 
      Creates a stand-alone logical link.
      Parameters:
      `id` - link ID

      `startNodeId` - start node ID

      `endNodeId` - end node ID

      `cost` - link cost

      `isBidirected` - whether the link is bidirected or not

      `isActive` - whether the link is active or not

      `udio` - user data IO implementation

      Returns:
      a stand-alone logical link

    <!-- -->

    - #### createLogicalLink

          public static LogicalLink createLogicalLink(long id,
                                                      long startNodeId,
                                                      long endNodeId,
                                                      double cost,
                                                      boolean isBidirected,
                                                      boolean isActive,
                                                      java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a stand-alone logical link.
      Parameters:
      `id` - link ID

      `startNodeId` - start node ID

      `endNodeId` - end node ID

      `cost` - link cost

      `isBidirected` - whether the link is bidirected or not

      `isActive` - whether the link is active or not

      `userData` - user data name-value pairs

      Returns:
      a stand-alone logical link

    <!-- -->

    - #### createLogicalLink

          public static LogicalLink createLogicalLink(long id,
                                                      int level,
                                                      long startNodeId,
                                                      long endNodeId,
                                                      double cost,
                                                      boolean isBidirected,
                                                      boolean isActive,
                                                      LODUserDataIO udio)

      Deprecated. 
      Creates a stand-alone logical link.
      Parameters:
      `id` - link ID

      `level` - link level

      `startNodeId` - start node ID

      `endNodeId` - end node ID

      `cost` - link cost

      `isBidirected` - whether the link is bidirected or not

      `isActive` - whether the link is active or not

      `udio` - user data IO implementation

      Returns:
      a stand-alone logical link

    <!-- -->

    - #### createLogicalLink

          public static LogicalLink createLogicalLink(long id,
                                                      int level,
                                                      long startNodeId,
                                                      long endNodeId,
                                                      double cost,
                                                      boolean isBidirected,
                                                      boolean isActive,
                                                      java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a stand-alone logical link.
      Parameters:
      `id` - link ID

      `level` - link level

      `startNodeId` - start node ID

      `endNodeId` - end node ID

      `cost` - link cost

      `isBidirected` - whether the link is bidirected or not

      `isActive` - whether the link is active or not

      `userData` - user data name-value pairs

      Returns:
      a stand-alone logical link

    <!-- -->

    - #### createLogicalLink

          public static LogicalLink createLogicalLink(long id,
                                                      int level,
                                                      long startNodeId,
                                                      long endNodeId,
                                                      double cost,
                                                      boolean isBidirected,
                                                      boolean isActive,
                                                      CategorizedUserData userData)

      Creates a stand-alone logical link.
      Parameters:
      `id` - link ID

      `level` - link level

      `startNodeId` - start node ID

      `endNodeId` - end node ID

      `cost` - link cost

      `isBidirected` - whether the link is bidirected or not

      `isActive` - whether the link is active or not

      `userData` - user data

      Returns:
      a stand-alone logical link

    <!-- -->

    - #### createLogicalNetLink

          public static LogicalNetLink createLogicalNetLink(long id,
                                                            LogicalNetNode startNode,
                                                            LogicalNetNode endNode,
                                                            double cost,
                                                            boolean isBidirected,
                                                            boolean isActive,
                                                            LODUserDataIO udio)

      Deprecated. 
      Creates a logical link with reference to its start and end node objects.
      Parameters:
      `id` - link ID

      `startNode` - start node object

      `endNode` - end node object

      `cost` - link cost

      `isBidirected` - whether the link is bidirected or not

      `isActive` - whether the link is active or not

      `udio` - user data IO implementation

      Returns:
      a logical link with reference to its start and end node objects

    <!-- -->

    - #### createLogicalNetLink

          public static LogicalNetLink createLogicalNetLink(long id,
                                                            LogicalNetNode startNode,
                                                            LogicalNetNode endNode,
                                                            double cost,
                                                            boolean isBidirected,
                                                            boolean isActive,
                                                            java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a logical link with reference to its start and end node objects.
      Parameters:
      `id` - link ID

      `startNode` - start node object

      `endNode` - end node object

      `cost` - link cost

      `isBidirected` - whether the link is bidirected or not

      `isActive` - whether the link is active or not

      `userData` - user data name-value pairs

      Returns:
      a logical link with reference to its start and end node objects

    <!-- -->

    - #### createLogicalNetLink

          public static LogicalNetLink createLogicalNetLink(long id,
                                                            int level,
                                                            LogicalNetNode startNode,
                                                            LogicalNetNode endNode,
                                                            double cost,
                                                            boolean isBidirected,
                                                            boolean isActive,
                                                            LODUserDataIO udio)

      Deprecated. 
      Creates a logical link with reference to its start and end node objects.
      Parameters:
      `id` - link ID

      `level` - link level

      `startNode` - start node object

      `endNode` - end node object

      `cost` - link cost

      `isBidirected` - whether the link is bidirected or not

      `isActive` - whether the link is active or not

      `udio` - user data IO implementation

      Returns:
      a logical link with reference to its start and end node objects

    <!-- -->

    - #### createLogicalNetLink

          public static LogicalNetLink createLogicalNetLink(long id,
                                                            int level,
                                                            LogicalNetNode startNode,
                                                            LogicalNetNode endNode,
                                                            double cost,
                                                            boolean isBidirected,
                                                            boolean isActive,
                                                            java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a logical link with reference to its start and end node objects.
      Parameters:
      `id` - link ID

      `level` - link level

      `startNode` - start node object

      `endNode` - end node object

      `cost` - link cost

      `isBidirected` - whether the link is bidirected or not

      `isActive` - whether the link is active or not

      `userData` - user data name-value pairs

      Returns:
      a logical link with reference to its start and end node objects

    <!-- -->

    - #### createLogicalNetLink

          public static LogicalNetLink createLogicalNetLink(long id,
                                                            int level,
                                                            LogicalNetNode startNode,
                                                            LogicalNetNode endNode,
                                                            double cost,
                                                            boolean isBidirected,
                                                            boolean isActive,
                                                            CategorizedUserData userData)

      Creates a logical link with reference to its start and end node objects.
      Parameters:
      `id` - link ID

      `level` - link level

      `startNode` - start node object

      `endNode` - end node object

      `cost` - link cost

      `isBidirected` - whether the link is bidirected or not

      `isActive` - whether the link is active or not

      `userData` - user data

      Returns:
      a logical link with reference to its start and end node objects

    <!-- -->

    - #### createLogicalPath

          public static LogicalPath createLogicalPath(long[] linkIds,
                                                      long[] nodeIds,
                                                      double cost,
                                                      java.util.Map<java.lang.String,java.lang.Object> userData,
                                                      boolean isReverse)

      Deprecated. use createLogicalPath( long\[\] linkIds, long\[\] nodeIds, double\[\] costs, Map userData)
      Creates a light-weight logical path, which contains only the IDs of the links and the nodes on the path, instead of the link and node objects.
      Parameters:
      `linkIds` - IDs of the links on the path

      `nodeIds` - IDs of the nodes on the path

      `cost` - path cost, which is the sum of all the link and nodes on the path less the cost of the start and end nodes.

      `userData` - user data name-value pairs

      Returns:
      a light-weight logical path

    <!-- -->

    - #### createLogicalPath

          public static LogicalPath createLogicalPath(long[] linkIds,
                                                      long[] nodeIds,
                                                      double[] costs,
                                                      java.util.Map<java.lang.String,java.lang.Object> userData,
                                                      boolean isReverse)

      Deprecated. 
      Creates a logical path, which contains only the IDs of the links and the nodes on the path, instead of the link and node objects.
      Parameters:
      `linkIds` - IDs of the links on the path

      `nodeIds` - IDs of the nodes on the path

      `costs` - path costs, which is the sum of all the link and node costs on the path less the cost of the end node.

      `userData` - user data name-value pairs

      Returns:
      a light-weight logical path

    <!-- -->

    - #### createLogicalPath

          public static LogicalPath createLogicalPath(long[] linkIds,
                                                      long[] nodeIds,
                                                      double[] costs,
                                                      CategorizedUserData userData,
                                                      boolean isReverse)

      Creates a logical path, which contains only the IDs of the links and the nodes on the path, instead of the link and node objects.
      Parameters:
      `linkIds` - IDs of the links on the path

      `nodeIds` - IDs of the nodes on the path

      `costs` - path costs, which is the sum of all the link and node costs on the path less the cost of the end node.

      `userData` - user data

      Returns:
      a light-weight logical path

    <!-- -->

    - #### createLogicalLightPath

          public static LogicalLightPath createLogicalLightPath(long startNodeId,
                                                                long endNodeId,
                                                                long firstLink,
                                                                long lastLink,
                                                                int numberOfNodes,
                                                                int numberOfLinks,
                                                                double[] costs,
                                                                CategorizedUserData userData,
                                                                boolean isReverse)

      Creates a light-weight logical path, which contains only the start and end node IDs and costs of the path.
      Parameters:
      `startNodeId` - start node ID

      `endNodeId` - end node ID

      `costs` - path costs, which is the sum of all the link and node costs on the path less the cost of the end node.

      Returns:
      a light-weight logical path

    <!-- -->

    - #### createLogicalHeavyPath

          public static LogicalHeavyPath createLogicalHeavyPath(LogicalLink[] links,
                                                                LogicalNode[] nodes,
                                                                java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. use createLogicalHeavyPath( LogicalLink\[\] links, LogicalNode\[\] nodes, double\[\] costs, CategorizedUserData userData)
      Creates a heavy-weight logical path, which contains the object representation of the links and nodes on the path.
      Parameters:
      `links` - links on the path

      `nodes` - nodes on the path

      `userData` - user data name-value pairs

      Returns:
      a heavy-weight logical path

    <!-- -->

    - #### createLogicalHeavyPath

          public static LogicalHeavyPath createLogicalHeavyPath(LogicalLink[] links,
                                                                LogicalNode[] nodes,
                                                                double[] costs,
                                                                CategorizedUserData userData,
                                                                boolean isReverse)

      Creates a heavy-weight logical path, which contains the object representation of the links and nodes on the path.
      Parameters:
      `links` - links on the path

      `nodes` - nodes on the path

      `costs` - path costs

      `userData` - user data

      Returns:
      a heavy-weight logical path

    <!-- -->

    - #### createLogicalSubPath

          public static LogicalSubPath createLogicalSubPath(LogicalPath refPath,
                                                            int startLinkIndex,
                                                            double startPercentage,
                                                            int endLinkIndex,
                                                            double endPercentage,
                                                            double cost,
                                                            java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. use createLogicalSubPath( LogicalPath refPath, int startLinkIndex, double startPercentage, int endLinkIndex, double endPercentage, double\[\] costs, CategorizedUserData userData)
      Creates a logical sub-path.
      Parameters:
      `refPath` - the reference path that contains the sub-path

      `startLinkIndex` - index of the start link

      `startPercentage` - location of the start point represented as a percentage on the start link

      `endLinkIndex` - index of the end link

      `endPercentage` - location of the end point represented as a percentage on the end link

      `cost` - sub-path cost

      `userData` - user data name-value pairs

      Returns:
      a logical sub-path

    <!-- -->

    - #### createLogicalSubPath

          public static LogicalSubPath createLogicalSubPath(LogicalPath refPath,
                                                            int startLinkIndex,
                                                            double startPercentage,
                                                            int endLinkIndex,
                                                            double endPercentage,
                                                            double[] costs,
                                                            java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a logical sub-path.
      Parameters:
      `refPath` - the reference path that contains the sub-path

      `startLinkIndex` - index of the start link

      `startPercentage` - location of the start point represented as a percentage on the start link

      `endLinkIndex` - index of the end link

      `endPercentage` - location of the end point represented as a percentage on the end link

      `costs` - sub-path costs

      `userData` - user data name-value pairs

      Returns:
      a logical sub-path

    <!-- -->

    - #### createLogicalSubPath

          public static LogicalSubPath createLogicalSubPath(LogicalPath refPath,
                                                            int startLinkIndex,
                                                            double startPercentage,
                                                            int endLinkIndex,
                                                            double endPercentage,
                                                            double[] costs,
                                                            CategorizedUserData userData)

      Creates a logical sub-path.
      Parameters:
      `refPath` - the reference path that contains the sub-path

      `startLinkIndex` - index of the start link

      `startPercentage` - location of the start point represented as a percentage on the start link

      `endLinkIndex` - index of the end link

      `endPercentage` - location of the end point represented as a percentage on the end link

      `costs` - sub-path costs

      `userData` - user data name-value pairs

      Returns:
      a logical sub-path

    <!-- -->

    - #### createLogicalLightSubPath

          public static LogicalLightSubPath createLogicalLightSubPath(LogicalLightPath refPath,
                                                                      int startLinkIndex,
                                                                      double startPercentage,
                                                                      int endLinkIndex,
                                                                      double endPercentage,
                                                                      double[] costs,
                                                                      CategorizedUserData userData)

      Creates a light-weight logical sub-path, i.e., a logical sub-path that refers to a light-weight logical path.
      Parameters:
      `refPath` - the reference path that contains the sub-path

      `startPercentage` - location of the start point represented as a percentage on the start link

      `endPercentage` - location of the end point represented as a percentage on the end link

      `costs` - sub-path costs

      Returns:
      a logical sub-path

    <!-- -->

    - #### createSpatialBasicNetwork

          public static SpatialBasicNetwork createSpatialBasicNetwork(java.lang.String networkName,
                                                                      int linkLevel)

      Creates an empty spatial network.
      Parameters:
      `networkName` - network name

      Returns:
      an empty spatial network

    <!-- -->

    - #### createSpatialBasicNetwork

          public static SpatialBasicNetwork createSpatialBasicNetwork(java.lang.String networkName,
                                                                      int linkLevel,
                                                                      int numNodes,
                                                                      int numLinks)

      Creates an empty spatial network. The variables in this netowrk is initialized according to the input number of nodes and links. Compared with the previous method, using this method will improve the performance of adding node and links to the network later on.
      Parameters:
      `networkName` - network name

      `numNodes` - estimated number of nodes

      `numLinks` - estimated number of links

      Returns:
      an empty spatial network

    <!-- -->

    - #### createSpatialPartition

          public static SpatialPartition createSpatialPartition(java.lang.String networkName,
                                                                int partitionId,
                                                                int linkLevel)

      Creates an empty spatial partition.
      Parameters:
      `networkName` - network name

      `partitionId` - partition ID

      Returns:
      an empty spatial partition

    <!-- -->

    - #### createSpatialPartition

          public static SpatialPartition createSpatialPartition(java.lang.String networkName,
                                                                int partitionId,
                                                                int linkLevel,
                                                                int numInternalNodes,
                                                                int numExternalNodes,
                                                                int numInternalLinks,
                                                                int numBoundaryLinks)

      Creates an empty spatial partition. The variables in this partition are initialized according to the estimated nubmer of nodes and links. Compared with the previous method, using this method will improve the performance of adding node and links to the partition later on.
      Parameters:
      `networkName` - network name

      `partitionId` - partition ID

      `numInternalNodes` - estimated number of internal nodes

      `numExternalNodes` - estimated number of external nodes

      `numInternalLinks` - estimated number of internal links

      `numBoundaryLinks` - estimated number of external links

      Returns:
      an empty spatial partition

    <!-- -->

    - #### createSpatialNode

          public static SpatialNode createSpatialNode(long id,
                                                      double cost,
                                                      boolean isActive,
                                                      JGeometry geometry,
                                                      LODUserDataIO udio)

      Deprecated. 
      Creates a stand-alone spatial node.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `udio` - user data IO implementation

      Returns:
      spatial node

    <!-- -->

    - #### createSpatialNode

          public static SpatialNode createSpatialNode(long id,
                                                      double cost,
                                                      int maxLinkLevel,
                                                      boolean isActive,
                                                      JGeometry geometry,
                                                      LODUserDataIO udio)

      Creates a stand-alone spatial node.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `udio` - user data IO implementation

      Returns:
      spatial node

    <!-- -->

    - #### createSpatialNode

          public static SpatialNode createSpatialNode(long id,
                                                      double cost,
                                                      boolean isActive,
                                                      JGeometry geometry,
                                                      java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a stand-alone spatial node.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `userData` - user data name-value pairs

      Returns:
      spatial node

    <!-- -->

    - #### createSpatialNode

          public static SpatialNode createSpatialNode(long id,
                                                      double cost,
                                                      boolean isActive,
                                                      int maxLinkLevel,
                                                      JGeometry geometry,
                                                      java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a stand-alone spatial node.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `userData` - user data name-value pairs

      Returns:
      spatial node

    <!-- -->

    - #### createSpatialNode

          public static SpatialNode createSpatialNode(long id,
                                                      double cost,
                                                      boolean isActive,
                                                      int maxLinkLevel,
                                                      JGeometry geometry,
                                                      CategorizedUserData userData)

      Creates a stand-alone spatial node.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `userData` - user data name-value pairs

      Returns:
      spatial node

    <!-- -->

    - #### createSpatialNetNode

          public static SpatialNetNode createSpatialNetNode(long id,
                                                            int linkLevel,
                                                            double cost,
                                                            boolean isActive,
                                                            JGeometry geometry,
                                                            LODUserDataIO udio)

      Deprecated. 
      Creates a logical node to which we can add reference to incident links.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `udio` - user data IO implementation

      Returns:
      a spatial node to which we can add reference to incident links

    <!-- -->

    - #### createSpatialNetNode

          public static SpatialNetNode createSpatialNetNode(long id,
                                                            int linkLevel,
                                                            double cost,
                                                            boolean isActive,
                                                            int maxLinkLevel,
                                                            JGeometry geometry,
                                                            LODUserDataIO udio)

      Deprecated. 
      Creates a logical node to which we can add reference to incident links.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `udio` - user data IO implementation

      Returns:
      a spatial node to which we can add reference to incident links

    <!-- -->

    - #### createSpatialNetNode

          public static SpatialNetNode createSpatialNetNode(long id,
                                                            int linkLevel,
                                                            double cost,
                                                            boolean isActive,
                                                            JGeometry geometry,
                                                            java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a logical node to which we can add reference to incident links.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `userData` - user data name-value pairs

      Returns:
      a logical node to which we can add reference to incident links

    <!-- -->

    - #### createSpatialNetNode

          public static SpatialNetNode createSpatialNetNode(long id,
                                                            int linkLevel,
                                                            double cost,
                                                            boolean isActive,
                                                            int maxLinkLevel,
                                                            JGeometry geometry,
                                                            java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a logical node to which we can add reference to incident links.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `userData` - user data name-value pairs

      Returns:
      a logical node to which we can add reference to incident links

    <!-- -->

    - #### createSpatialNetNode

          public static SpatialNetNode createSpatialNetNode(long id,
                                                            int linkLevel,
                                                            double cost,
                                                            boolean isActive,
                                                            int maxLinkLevel,
                                                            int numInLinks,
                                                            int numOutLinks,
                                                            JGeometry geometry,
                                                            java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a spatial node to which we can add reference to incident links.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `userData` - user data name-value pairs

      Returns:
      a logical node to which we can add reference to incident links

    <!-- -->

    - #### createSpatialNetNode

          public static SpatialNetNode createSpatialNetNode(long id,
                                                            int partitionId,
                                                            int linkLevel,
                                                            double cost,
                                                            boolean isActive,
                                                            int maxLinkLevel,
                                                            int numInLinks,
                                                            int numOutLinks,
                                                            JGeometry geometry,
                                                            java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a spatial node to which we can add reference to incident links.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `userData` - user data name-value pairs

      Returns:
      a spatial node to which we can add reference to incident links

    <!-- -->

    - #### createSpatialNetNode

          public static SpatialNetNode createSpatialNetNode(long id,
                                                            int partitionId,
                                                            int linkLevel,
                                                            double cost,
                                                            boolean isActive,
                                                            int maxLinkLevel,
                                                            int numInLinks,
                                                            int numOutLinks,
                                                            JGeometry geometry,
                                                            CategorizedUserData userData)

      Creates a spatial node to which we can add reference to incident links.
      Parameters:
      `id` - node ID

      `cost` - node cost

      `isActive` - whether the node is active or not

      `userData` - user data name-value pairs

      Returns:
      a logical node to which we can add reference to incident links

    <!-- -->

    - #### createSpatialLink

          public static SpatialLink createSpatialLink(long id,
                                                      long startNodeId,
                                                      long endNodeId,
                                                      double cost,
                                                      boolean isBidirected,
                                                      boolean isActive,
                                                      JGeometry geometry,
                                                      LODUserDataIO udio)

      Deprecated. 
      Creates a stand-alone spatial link.
      Parameters:
      `id` - link ID

      `startNodeId` - start node ID

      `endNodeId` - end node ID

      `cost` - link cost

      `isBidirected` - whether the link is bidirected or not

      `isActive` - whether the link is active or not

      `udio` - user data IO implementation

      Returns:
      a stand-alone spatial link

    <!-- -->

    - #### createSpatialLink

          public static SpatialLink createSpatialLink(long id,
                                                      int level,
                                                      long startNodeId,
                                                      long endNodeId,
                                                      double cost,
                                                      boolean isBidirected,
                                                      boolean isActive,
                                                      JGeometry geometry,
                                                      LODUserDataIO udio)

      Deprecated. 
      Creates a stand-alone spatial link.
      Parameters:
      `id` - link ID

      `level` - link level

      `startNodeId` - start node ID

      `endNodeId` - end node ID

      `cost` - link cost

      `isBidirected` - whether the link is bidirected or not

      `isActive` - whether the link is active or not

      `udio` - user data IO implementation

      Returns:
      a stand-alone spatial link

    <!-- -->

    - #### createSpatialLink

          public static SpatialLink createSpatialLink(long id,
                                                      long startNodeId,
                                                      long endNodeId,
                                                      double cost,
                                                      boolean isBidirected,
                                                      boolean isActive,
                                                      JGeometry geometry,
                                                      java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a stand-alone spatial link.
      Parameters:
      `id` - link ID

      `startNodeId` - start node ID

      `endNodeId` - end node ID

      `cost` - link cost

      `isBidirected` - whether the link is bidirected or not

      `isActive` - whether the link is active or not

      `userData` - user data name-value pair

      Returns:
      a stand-alone spatial link

    <!-- -->

    - #### createSpatialLink

          public static SpatialLink createSpatialLink(long id,
                                                      int level,
                                                      long startNodeId,
                                                      long endNodeId,
                                                      double cost,
                                                      boolean isBidirected,
                                                      boolean isActive,
                                                      JGeometry geometry,
                                                      java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a stand-alone spatial link.
      Parameters:
      `id` - link ID

      `level` - link level

      `startNodeId` - start node ID

      `endNodeId` - end node ID

      `cost` - link cost

      `isBidirected` - whether the link is bidirected or not

      `isActive` - whether the link is active or not

      `userData` - user data name-value pair

      Returns:
      a stand-alone spatial link

    <!-- -->

    - #### createSpatialLink

          public static SpatialLink createSpatialLink(long id,
                                                      int level,
                                                      long startNodeId,
                                                      long endNodeId,
                                                      double cost,
                                                      boolean isBidirected,
                                                      boolean isActive,
                                                      JGeometry geometry,
                                                      CategorizedUserData userData)

      Creates a stand-alone spatial link.
      Parameters:
      `id` - link ID

      `level` - link level

      `startNodeId` - start node ID

      `endNodeId` - end node ID

      `cost` - link cost

      `isBidirected` - whether the link is bidirected or not

      `isActive` - whether the link is active or not

      `userData` - user data object

      Returns:
      a stand-alone spatial link

    <!-- -->

    - #### createSpatialNetLink

          public static SpatialNetLink createSpatialNetLink(long id,
                                                            SpatialNetNode startNode,
                                                            SpatialNetNode endNode,
                                                            double cost,
                                                            boolean isBidirected,
                                                            boolean isActive,
                                                            JGeometry geometry,
                                                            LODUserDataIO udio)

      Creates a spatial link with reference to its start and end node objects.
      Parameters:
      `id` - link ID

      `startNode` - start node object

      `endNode` - end node object

      `cost` - link cost

      `isBidirected` - whether the link is bidirected or not

      `isActive` - whether the link is active or not

      `udio` - user data IO implementation

      Returns:
      a spatial link with reference to its start and end node objects

    <!-- -->

    - #### createSpatialNetLink

          public static SpatialNetLink createSpatialNetLink(long id,
                                                            int level,
                                                            SpatialNetNode startNode,
                                                            SpatialNetNode endNode,
                                                            double cost,
                                                            boolean isBidirected,
                                                            boolean isActive,
                                                            JGeometry geometry,
                                                            LODUserDataIO udio)

      Deprecated. 
      Creates a spatial link with reference to its start and end node objects.
      Parameters:
      `id` - link ID

      `level` - link level

      `startNode` - start node object

      `endNode` - end node object

      `cost` - link cost

      `isBidirected` - whether the link is bidirected or not

      `isActive` - whether the link is active or not

      `udio` - user data IO implementation

      Returns:
      a spatial link with reference to its start and end node objects

    <!-- -->

    - #### createSpatialNetLink

          public static SpatialNetLink createSpatialNetLink(long id,
                                                            SpatialNetNode startNode,
                                                            SpatialNetNode endNode,
                                                            double cost,
                                                            boolean isBidirected,
                                                            boolean isActive,
                                                            JGeometry geometry,
                                                            java.util.Map<java.lang.String,java.lang.Object> userData)

      Creates a spatial link with reference to its start and end node objects.
      Parameters:
      `id` - link ID

      `startNode` - start node object

      `endNode` - end node object

      `cost` - link cost

      `isBidirected` - whether the link is bidirected or not

      `isActive` - whether the link is active or not

      `userData` - user data name-value pairs: ignored

      Returns:
      a spatial link with reference to its start and end node objects

    <!-- -->

    - #### createSpatialNetLink

          public static SpatialNetLink createSpatialNetLink(long id,
                                                            int level,
                                                            SpatialNetNode startNode,
                                                            SpatialNetNode endNode,
                                                            double cost,
                                                            boolean isBidirected,
                                                            boolean isActive,
                                                            JGeometry geometry,
                                                            java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a spatial link with reference to its start and end node objects.
      Parameters:
      `id` - link ID

      `level` - link level

      `startNode` - start node object

      `endNode` - end node object

      `cost` - link cost

      `isBidirected` - whether the link is bidirected or not

      `isActive` - whether the link is active or not

      `userData` - user data name-value pairs: ignored

      Returns:
      a spatial link with reference to its start and end node objects

    <!-- -->

    - #### createSpatialNetLink

          public static SpatialNetLink createSpatialNetLink(long id,
                                                            int level,
                                                            SpatialNetNode startNode,
                                                            SpatialNetNode endNode,
                                                            double cost,
                                                            boolean isBidirected,
                                                            boolean isActive,
                                                            JGeometry geometry,
                                                            CategorizedUserData userData)

      Creates a spatial link with reference to its start and end node objects.
      Parameters:
      `id` - link ID

      `level` - link level

      `startNode` - start node object

      `endNode` - end node object

      `cost` - link cost

      `isBidirected` - whether the link is bidirected or not

      `isActive` - whether the link is active or not

      `userData` - user data

      Returns:
      a spatial link with reference to its start and end node objects

    <!-- -->

    - #### createSpatialPath

          public static SpatialPath createSpatialPath(long[] linkIds,
                                                      long[] nodeIds,
                                                      double[] costs,
                                                      JGeometry geometry,
                                                      java.util.Map<java.lang.String,java.lang.Object> userData,
                                                      boolean isReverse)

      Deprecated. 
      Creates a light-weight spatial path, which contains only the IDs of the links and the nodes on the path, instead of the link and node objects.
      Parameters:
      `linkIds` - IDs of the links on the path

      `nodeIds` - IDs of the nodes on the path

      `costs` - path costs, which is the sum of all the link and nodes on the path less the cost of the end node.

      `userData` - user data name value pairs : ignored

      Returns:
      a spatial path

    <!-- -->

    - #### createSpatialPath

          public static SpatialPath createSpatialPath(long[] linkIds,
                                                      long[] nodeIds,
                                                      double[] costs,
                                                      JGeometry geometry,
                                                      CategorizedUserData userData,
                                                      boolean isReverse)

      Creates a light-weight spatial path, which contains only the IDs of the links and the nodes on the path, instead of the link and node objects.
      Parameters:
      `linkIds` - IDs of the links on the path

      `nodeIds` - IDs of the nodes on the path

      `costs` - path costs, which is the sum of all the link and nodes on the path less the cost of the end node.

      `userData` - user data

      Returns:
      a spatial path

    <!-- -->

    - #### createSpatialSubPath

          public static SpatialSubPath createSpatialSubPath(SpatialPath referencePath,
                                                            int startLinkIndex,
                                                            int endLinkIndex,
                                                            double startPercentage,
                                                            double endPercentage,
                                                            double[] costs,
                                                            JGeometry geometry,
                                                            java.util.Map<java.lang.String,java.lang.Object> userData)

      Deprecated. 
      Creates a spatial sub-path.
      Parameters:
      `referencePath` - the reference path that contains the sub-path

      `startLinkIndex` - index of the start link

      `startPercentage` - location of the start point represented as a percentage on the start link

      `endLinkIndex` - index of the end link

      `endPercentage` - location of the end point represented as a percentage on the end link

      `costs` - sub-path costs

      `userData` - user data: ignored

      Returns:
      a spatial sub-path

    <!-- -->

    - #### createSpatialSubPath

          public static SpatialSubPath createSpatialSubPath(SpatialPath referencePath,
                                                            int startLinkIndex,
                                                            double startPercentage,
                                                            int endLinkIndex,
                                                            double endPercentage,
                                                            double[] costs,
                                                            JGeometry geometry,
                                                            CategorizedUserData userData)

      Creates a spatial sub-path.
      Parameters:
      `referencePath` - the reference path that contains the sub-path

      `startLinkIndex` - index of the start link

      `startPercentage` - location of the start point represented as a percentage on the start link

      `endLinkIndex` - index of the end link

      `endPercentage` - location of the end point represented as a percentage on the end link

      `costs` - sub-path costs

      `userData` - user data

      Returns:
      a spatial sub-path

    <!-- -->

    - #### createSpatialHeavyPath

          public static SpatialHeavyPath createSpatialHeavyPath(SpatialLink[] links,
                                                                SpatialNode[] nodes,
                                                                double[] costs,
                                                                JGeometry geometry,
                                                                CategorizedUserData userData,
                                                                boolean isReverse)

      Creates a heavy-weight spatial path, which contains the object representation of the links and nodes on the path.
      Parameters:
      `links` - links on the path

      `nodes` - nodes on the path

      `userData` - user data

      Returns:
      a heavy-weight spatial path

    <!-- -->

    - #### createSpatialHeavyPath

          public static SpatialHeavyPath createSpatialHeavyPath(SpatialLink[] links,
                                                                SpatialNode[] nodes,
                                                                double[] costs,
                                                                JGeometry geometry,
                                                                java.util.Map<java.lang.String,java.lang.Object> userData,
                                                                boolean isReverse)

      Creates a heavy-weight spatial path, which contains the object representation of the links and nodes on the path.
      Parameters:
      `links` - links on the path

      `nodes` - nodes on the path

      `costs` - path costs

      `userData` - user data

      Returns:
      a heavy-weight spatial path

    <!-- -->

    - #### createSpatialHeavyPath

          public static SpatialHeavyPath createSpatialHeavyPath(SpatialLink[] links,
                                                                SpatialNode[] nodes,
                                                                JGeometry geometry,
                                                                java.util.Map<java.lang.String,java.lang.Object> userData)

      Creates a heavy-weight spatial path, which contains the object representation of the links and nodes on the path.
      Parameters:
      `links` - links on the path

      `nodes` - nodes on the path

      `userData` - user data

      Returns:
      a heavy-weight spatial path

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](LODNetworkException.md)
- [Next Class](LODNetworkManager.md)

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

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
