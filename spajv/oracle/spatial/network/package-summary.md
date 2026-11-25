Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Package](../georaster/util/package-summary.md)
- [Next Package](lod/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

# Package oracle.spatial.network

Provides support for the Oracle Spatial network data model, which is documented in *Oracle Spatial Topology and Network Data Models*.

See: Description

- **Interface Summary**

  | Interface                                 | Description                                                                                                                                                                                                                                                                                                                 |
  |-------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [AnalysisInfo](AnalysisInfo.md)           | This interface defines methods for retrieving the analysis information.                                                                                                                                                                                                                                                     |
  | [AStarCostFunction](AStarCostFunction.md) | This interface defines the heuristic cost function for A\* search Users can provide their own cost estimates to guide the A\* search.                                                                                                                                                                                       |
  | [GoalNode](GoalNode.md)                   | This interface defines if a given node is a goal node for network analysis                                                                                                                                                                                                                                                  |
  | [Link](Link.md)                           | This interface defines a network link.                                                                                                                                                                                                                                                                                      |
  | [LinkCostFunction](LinkCostFunction.md)   | User defined link cost interface                                                                                                                                                                                                                                                                                            |
  | [MBR](MBR.md)                             | This interface defines the Minimum Bounding Rectangle (MBR) interface.                                                                                                                                                                                                                                                      |
  | [MDPoint](MDPoint.md)                     | This interface defines a mutilple dimension point.                                                                                                                                                                                                                                                                          |
  | [Network](Network.md)                     | This interface defines a network.                                                                                                                                                                                                                                                                                           |
  | [NetworkConstraint](NetworkConstraint.md) | This interface defines a general network constraint for network analysis.                                                                                                                                                                                                                                                   |
  | [NetworkMetadata](NetworkMetadata.md)     | This class defines a network metadata.                                                                                                                                                                                                                                                                                      |
  | [Node](Node.md)                           | This interface defines a network node.                                                                                                                                                                                                                                                                                      |
  | [Path](Path.md)                           | This interface defines a network path.                                                                                                                                                                                                                                                                                      |
  | [SubPath](SubPath.md)                     | This interface defines a sub path with the following properties: A reference path, a start percentage and a start link index in the reference path link list, an end percentage and an end link index in the reference path link list, The partial link cost is assumed to be linearly propotional to the given percentage. |
  | [Tree](Tree.md)                           | This interface defines a tree for trace-out.                                                                                                                                                                                                                                                                                |
  | [TreeLink](TreeLink.md)                   | This interface defines a tree link for trace-out.                                                                                                                                                                                                                                                                           |
  | [TreeNode](TreeNode.md)                   | This interface defines a tree node for trace-out.                                                                                                                                                                                                                                                                           |
  | [UserDataIO](UserDataIO.md)               | This interface defines methods for users to read and write user defined data from and to the database.                                                                                                                                                                                                                      |
  | [UserDataMetadata](UserDataMetadata.md)   | This class defines the metadata for user data.                                                                                                                                                                                                                                                                              |

- **Class Summary**

  | Class                                   | Description                                                                        |
  |-----------------------------------------|------------------------------------------------------------------------------------|
  | [GeometryMetadata](GeometryMetadata.md) | This class defines geometry metadata for Oracle SDO_GEOMETRY.                      |
  | [HistoryMetadata](HistoryMetadata.md)   |                                                                                    |
  | [NDMTimer](NDMTimer.md)                 | Timer utility class.                                                               |
  | [NetworkFactory](NetworkFactory.md)     | This class handles network element creation for Oracle Spatial Network Data Model. |
  | [NetworkManager](NetworkManager.md)     | This class defines methods for the network data I/O and network analysis.          |
  | [OraTst](OraTst.md)                     | This class defines print methods for the network elements in Network Data Model.   |
  | [SDODimArray](SDODimArray.md)           | This class defines a Java representation for Oracle Spatial SDO_DIM_ARRAY object.  |
  | [SystemConstraint](SystemConstraint.md) | This class defines the common network constraints for network analysis.            |

- **Exception Summary**

  | Exception                                       | Description                                                             |
  |-------------------------------------------------|-------------------------------------------------------------------------|
  | [NetworkDataException](NetworkDataException.md) | This class defines the exceptions for Oracle Spatial Network Data Model |

## Package oracle.spatial.network Description

Provides support for the Oracle Spatial network data model, which is documented in *Oracle Spatial Topology and Network Data Models*.

Skip navigation links

- [Overview](../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Package](../georaster/util/package-summary.md)
- [Next Package](lod/package-summary.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
