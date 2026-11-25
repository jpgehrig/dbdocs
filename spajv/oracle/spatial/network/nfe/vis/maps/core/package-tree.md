Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev](../package-tree.md)
-

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

# Hierarchy For Package oracle.spatial.network.nfe.vis.maps.core

Package Hierarchies:

- [All Packages](../../../../../../../overview-tree.md)

## Class Hierarchy

- java.lang.Object
  - javax.swing.undo.AbstractUndoableEdit (implements java.io.Serializable, javax.swing.undo.UndoableEdit)
    - javax.swing.undo.CompoundEdit
      - javax.swing.undo.UndoManager (implements javax.swing.event.UndoableEditListener)
        - oracle.spatial.network.nfe.vis.maps.core.[MapUndoManager](MapUndoManager.md)
  - java.awt.Component (implements java.awt.image.ImageObserver, java.awt.MenuContainer, java.io.Serializable)
    - java.awt.Container
      - javax.swing.JComponent (implements java.io.Serializable)
        - javax.swing.JPanel (implements javax.accessibility.Accessible)
          - oracle.spatial.network.nfe.vis.maps.core.[MapCanvas](MapCanvas.md) (implements java.beans.PropertyChangeListener)
  - oracle.spatial.network.nfe.vis.maps.core.[CoreLoop](CoreLoop.md) (implements java.awt.event.ActionListener)
  - oracle.spatial.network.nfe.vis.maps.core.[DefaultSelectionManager](DefaultSelectionManager.md)\<V\>
  - oracle.spatial.network.nfe.vis.maps.core.[Drawable](Drawable.md)
  - oracle.spatial.network.nfe.vis.maps.core.[EventManager](EventManager.md) (implements java.awt.event.ActionListener, javax.swing.event.ChangeListener, java.awt.event.ComponentListener, java.awt.event.FocusListener, java.awt.event.KeyListener, java.awt.event.MouseListener, java.awt.event.MouseMotionListener, java.awt.event.MouseWheelListener)
  - java.util.EventObject (implements java.io.Serializable)
    - javax.swing.event.ChangeEvent
      - oracle.spatial.network.nfe.vis.maps.core.[LayerManagerEvent](LayerManagerEvent.md)
      - oracle.spatial.network.nfe.vis.maps.core.[MapRegionEvent](MapRegionEvent.md)
      - oracle.spatial.network.nfe.vis.maps.core.[SelectionEvent](SelectionEvent.md)
  - oracle.spatial.network.nfe.vis.maps.core.[HoverManager](HoverManager.md)
  - oracle.spatial.network.nfe.vis.maps.core.[LayerManager](LayerManager.md) (implements java.util.Collection\<E\>, oracle.spatial.network.nfe.vis.maps.core.[EditChangeListener](EditChangeListener.md), java.beans.PropertyChangeListener, oracle.spatial.network.nfe.vis.maps.core.[SelectionListener](SelectionListener.md))
  - oracle.spatial.network.nfe.vis.maps.core.[LayerManager.Entry](LayerManager.Entry.md)
  - oracle.spatial.network.nfe.vis.maps.core.[MapRegion](MapRegion.md)

## Interface Hierarchy

- java.lang.Cloneable
  - oracle.spatial.network.nfe.vis.maps.core.[GeoObject](GeoObject.md)
- oracle.spatial.network.nfe.vis.maps.core.[DataProducer](DataProducer.md)
  - oracle.spatial.network.nfe.vis.maps.core.[GeoDataProducer](GeoDataProducer.md)
- java.util.EventListener
  - oracle.spatial.network.nfe.vis.maps.core.[EditChangeListener](EditChangeListener.md)
  - oracle.spatial.network.nfe.vis.maps.core.[SelectionListener](SelectionListener.md)
- oracle.spatial.network.nfe.vis.maps.core.[Filter](Filter.md)\<E\>
- oracle.spatial.network.nfe.vis.maps.core.[Layer](Layer.md)
  - oracle.spatial.network.nfe.vis.maps.core.[GeoObjectLayer](GeoObjectLayer.md)
    - oracle.spatial.network.nfe.vis.maps.core.[EditableLayer](EditableLayer.md)
    - oracle.spatial.network.nfe.vis.maps.core.[HoverableLayer](HoverableLayer.md)
    - oracle.spatial.network.nfe.vis.maps.core.[SelectableLayer](SelectableLayer.md)
  - oracle.spatial.network.nfe.vis.maps.core.[MVThemeLayer](MVThemeLayer.md)

Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev](../package-tree.md)
-

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
