Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Package](../package-summary.md)
- [Next Package](../geoobject/package-summary.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

# Package oracle.spatial.network.nfe.vis.maps.core

Contains the core components for working with a mapcanvas

See: Description

- **Interface Summary**

  | Interface                                   | Description                                                                                                         |
  |---------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
  | [DataProducer](DataProducer.md)             | A generic interface for all types of data producers.                                                                |
  | [EditableLayer](EditableLayer.md)           | A layer which support editing actions on its content                                                                |
  | [EditChangeListener](EditChangeListener.md) | Implementers will be notified when a layer content is edited                                                        |
  | [Filter](Filter.md)\<E\>                    | Interface used to customize searches by filtering                                                                   |
  | [GeoDataProducer](GeoDataProducer.md)       | A generic spatial data producer that gets data from MDS on demand.                                                  |
  | [GeoObject](GeoObject.md)                   | An interface representing a piece of geo-spatial object.                                                            |
  | [GeoObjectLayer](GeoObjectLayer.md)         | A layer to keep track of a group of GeoObjects                                                                      |
  | [HoverableLayer](HoverableLayer.md)         | An interface for layers that have objects that can be hovered over                                                  |
  | [Layer](Layer.md)                           | A Layer represents a graphics layer that handles the display of and interaction with a particular type of contents. |
  | [MVThemeLayer](MVThemeLayer.md)             | A layer that renders a MapViewer theme                                                                              |
  | [SelectableLayer](SelectableLayer.md)       | An interface for layers that have objects that can be selected They use a SelectionManager to handle selections     |
  | [SelectionListener](SelectionListener.md)   | Defines an interface for listening to selection changes.                                                            |

- **Class Summary**

  | Class                                                                                        | Description                                                                                                         |
  |----------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
  | [CoreLoop](CoreLoop.md)                                                                      | Each MapCanvas instance has a core rendering loop.                                                                  |
  | [DefaultSelectionManager](DefaultSelectionManager.md)\<V extends [GeoObject](GeoObject.md)\> | A helper component that can be used by a [`Layer`](Layer.md) to keep track of the geo-objects selected              |
  | [Drawable](Drawable.md)                                                                      | A Drawable references either a Java2D Shape or Point2D instance, but never both.                                    |
  | [EventManager](EventManager.md)                                                              | EventManager keeps track of current keyboard, mouse inputs and other critical events for the associated map canvas. |
  | [HoverManager](HoverManager.md)                                                              | A HoverManager is associated with a MapCanvas, and keeps a reference to the GeoObject that is currently in hover.   |
  | [LayerManager](LayerManager.md)                                                              | Contains and manages all the Layers to be displayed by the MapCanvas                                                |
  | [LayerManager.Entry](LayerManager.Entry.md)                                                  |                                                                                                                     |
  | [LayerManagerEvent](LayerManagerEvent.md)                                                    | Represents an event in a LayerManager                                                                               |
  | [MapCanvas](MapCanvas.md)                                                                    | MapCanvas provides a canvas component for displaying and interacting with various spatial data layers.              |
  | [MapRegion](MapRegion.md)                                                                    | MapRegion defines the current map display region, including the image (device) area and the data window.            |
  | [MapRegionEvent](MapRegionEvent.md)                                                          | Contains information regarding a change in a canvas's map region                                                    |
  | [MapUndoManager](MapUndoManager.md)                                                          | A subclass of `UndoManager` that notifies about any edit to the subscribed ChangeListeners.                         |
  | [SelectionEvent](SelectionEvent.md)                                                          | Represents a geo-object selection event.                                                                            |

## Package oracle.spatial.network.nfe.vis.maps.core Description

Contains the core components for working with a mapcanvas

Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Package](../package-summary.md)
- [Next Package](../geoobject/package-summary.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
