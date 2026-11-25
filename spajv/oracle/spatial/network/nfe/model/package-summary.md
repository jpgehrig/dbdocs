Skip navigation links

- [Overview](../../../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Package](../io/service/package-summary.md)
- [Next Package](edit/package-summary.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

# Package oracle.spatial.network.nfe.model

Provides classes for representing and managing an NFE model in memory.

See: Description

- **Interface Summary**

  | Interface                                         | Description                                                                                                                |
  |---------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
  | [NFEIdGenerator](NFEIdGenerator.md)               | Implementations of this interface must provide ID's for a given entity.                                                    |
  | [NFEIdManager](NFEIdManager.md)                   | This interface acts as a holder and manager of different ID generators used for different entities related to an NFEModel. |
  | [NFEModel](NFEModel.md)                           | NFEModel is the entry point for representing Network Feature Model in memory.                                              |
  | [NFEModelObject](NFEModelObject.md)               | Base interface for any object contained directly or indirectly in an NFE Model                                             |
  | [NFEModelObjectFactory](NFEModelObjectFactory.md) | Implementations of this class are used to get new instances of most of the classes in the NFE API.                         |

- **Class Summary**

  | Class                                                       | Description                                                                                                                         |
  |-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
  | [NFEBasicModel](NFEBasicModel.md)                           | The default implementation of NFEModel                                                                                              |
  | [NFEBasicModelObject](NFEBasicModelObject.md)               | The simplest implementation of NFEModelObject                                                                                       |
  | [NFEBasicModelObjectFactory](NFEBasicModelObjectFactory.md) | The dafault implementation of NFEModelObjectFactory                                                                                 |
  | [NFEDBSequenceIdGenerator](NFEDBSequenceIdGenerator.md)     | An implementation of NFEIdGeneratiom that uses a database sequence to generate id's                                                 |
  | [NFEDBSequenceIdManager](NFEDBSequenceIdManager.md)         | An implementation of NFEIdManager that uses instances of [`NFEDBSequenceIdGenerator`](NFEDBSequenceIdGenerator.md) to generate id's |
  | [NFEGeometryDescriptor](NFEGeometryDescriptor.md)           | This class contains the geometry metadata of an NFE model.                                                                          |
  | [NFEMetadata](NFEMetadata.md)                               | Parent class for all classes that hold metadata of any First Class Model Object such as NFEModel, NFENetwork or NFEFeatureLayer.    |
  | [NFEModelMetadata](NFEModelMetadata.md)                     | This class holds metadata for an NFE model.                                                                                         |
  | [NFEWorkspaceInfo](NFEWorkspaceInfo.md)                     | Contains information related to the workspace.                                                                                      |
  | [SDODimElement](SDODimElement.md)                           | This class contains information regarding a spatial dimension such as boundaries and tolerance.                                     |

- **Enum Summary**

  | Enum                                | Description                                                     |
  |-------------------------------------|-----------------------------------------------------------------|
  | [NFEEditionMode](NFEEditionMode.md) | Defines values for the different edition modes supported by NFE |

## Package oracle.spatial.network.nfe.model Description

Provides classes for representing and managing an NFE model in memory.

Skip navigation links

- [Overview](../../../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Package](../io/service/package-summary.md)
- [Next Package](edit/package-summary.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
