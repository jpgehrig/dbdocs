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

- [Prev Package](../edit/undo/package-summary.md)
- [Next Package](../feature/package-summary.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

# Package oracle.spatial.network.nfe.model.event

Contains event definitions and listeners used in an NFE model

See: Description

- **Interface Summary**

  | Interface                                                                        | Description                                                                                                                  |
  |----------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
  | [NFEEventDispatcher](NFEEventDispatcher.md)\<U extends java.util.EventListener\> | Defines a utility component used for firing events                                                                           |
  | [NFEModelListener](NFEModelListener.md)                                          | The listener interface for receiving events from a first class model object such as NFEModel, NFENetwork or NFEFeatureLayer. |

- **Class Summary**

  | Class                                                                                      | Description                                                                                |
  |--------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
  | [NFEBasicEventDispatcher](NFEBasicEventDispatcher.md)\<U extends java.util.EventListener\> | An implementation of NFEEventDispatcher that fires all the event in a single thread.       |
  | [NFEEventSupport](NFEEventSupport.md)\<U extends java.util.EventListener\>                 | Utility class used to subscribe and remove listener used by class which fire model events. |
  | [NFEModelEvent](NFEModelEvent.md)                                                          | Root class of the Model Event hierarchy.                                                   |
  | [NFEModelObjectEvent](NFEModelObjectEvent.md)                                              | Represent a generic event related to an Object from the NFEModel.                          |
  | [NFEModelObjectPropertyChangedEvent](NFEModelObjectPropertyChangedEvent.md)                | Event that contains information regarding to a changed property of a model object.         |
  | [NFEModelObjectsEvent](NFEModelObjectsEvent.md)                                            | An event where one or more model objects are involved                                      |

- **Exception Summary**

  | Exception                                                 | Description                                                                                                                        |
  |-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
  | [NFEEventDispatchException](NFEEventDispatchException.md) | Represents an error when dispatching events and contains one or more EventListeners which failed to be notified for certain event. |

## Package oracle.spatial.network.nfe.model.event Description

Contains event definitions and listeners used in an NFE model

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

- [Prev Package](../edit/undo/package-summary.md)
- [Next Package](../feature/package-summary.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
