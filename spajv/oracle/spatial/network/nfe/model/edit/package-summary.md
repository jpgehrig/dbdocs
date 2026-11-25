Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Package](../package-summary.md)
- [Next Package](undo/package-summary.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

# Package oracle.spatial.network.nfe.model.edit

Provides classes that aid on the edition of an NFE model

See: Description

- **Interface Summary**

  | Interface                           | Description                                                                                                        |
  |-------------------------------------|--------------------------------------------------------------------------------------------------------------------|
  | [NFEManipulator](NFEManipulator.md) | An NFEManipulator implementation should ease in-memory edition tasks such as adding, removing and moving features. |

- **Class Summary**

  | Class                                                        | Description                                                                                                                                                                                                                |
  |--------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [NFEBasicModelManipulator](NFEBasicModelManipulator.md)      | The default implementation of NFEModelManipulator                                                                                                                                                                          |
  | [NFEChangesKeeper](NFEChangesKeeper.md)                      | This class is meant to keep the references to the edited objects (network elements and features) in a project session, in order to keep the tracking of the changes performed and then save them into the DB when desired. |
  | [NFEConnectableEdge](NFEConnectableEdge.md)\<V\>             | Represents an edge and the location (relative to the edge and as a point in space) where the connection must be performed.                                                                                                 |
  | [NFEConnectionDescriptor](NFEConnectionDescriptor.md)\<U,V\> | Holds a vertex a collections of edges to be connected to the point.                                                                                                                                                        |
  | [NFEConnectionManager](NFEConnectionManager.md)              | Component in charge of connecting/disconnecting network/feature elements.                                                                                                                                                  |
  | [NFEEditionManager](NFEEditionManager.md)                    | This class keeps tracks of all the changes made to the model's content such as network elements, features, feature elements and rule instances.                                                                            |

## Package oracle.spatial.network.nfe.model.edit Description

Provides classes that aid on the edition of an NFE model

Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Package](../package-summary.md)
- [Next Package](undo/package-summary.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
