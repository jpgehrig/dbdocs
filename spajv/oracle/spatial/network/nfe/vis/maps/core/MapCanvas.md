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

- [Prev Class](LayerManagerEvent.md)
- [Next Class](MapRegion.md)

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

oracle.spatial.network.nfe.vis.maps.core

## Class MapCanvas

- java.lang.Object

- - java.awt.Component

  - - java.awt.Container

    - - javax.swing.JComponent

      - - javax.swing.JPanel

        - - oracle.spatial.network.nfe.vis.maps.core.MapCanvas

<!-- -->

- All Implemented Interfaces:
  java.awt.image.ImageObserver, java.awt.MenuContainer, java.beans.PropertyChangeListener, java.io.Serializable, java.util.EventListener, javax.accessibility.Accessible

  ------------------------------------------------------------------------



      public class MapCanvas
      extends javax.swing.JPanel
      implements java.beans.PropertyChangeListener

  MapCanvas provides a canvas component for displaying and interacting with various spatial data layers.
  MapCanvas provides a physical real estate for displaying geospatial contents.
  MapCanvas contains a LayerManager which manages all the data and interaction-related layers.
  MapCanvas contains a SelectionManager, which manages currently selected spatial objects.
  MapCanvas also contains a HoverManager, which keeps a reference to the spatial object currently in hover.
  MapCanvas uses an animation based rendering model, where the entire scene is repeatedly rendered in a rapid-firing Swing timer based on a dynamically adjusted frame rate. When rendering each frame, MapCanvas will ask each layer to update its data and graphics model as necessary, then render its contents to the canvas.
  MapCanvas uses a single Event manager to handle all input events, as well as feature selection/hover related events. In a nutshell, when MapCanvas intercepts a user or system event, it will poll each layer, asking if it is willing or able to handle the event. If a layer agrees to handle an event, then the layer's handleEvent() method is invoked. The event is then stopped from propagating further down to remaining layers.
  MapCanvas also maintains the current map region, and keeps track of both the device size and query window size. When the map region is changed in any way, MapCanvas will notify each layer which can then react properly.
  See Also:
  [Serialized Form](../../../../../../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from class javax.swing.JComponent

      `javax.swing.JComponent.AccessibleJComponent`

    <!-- -->

    - ### Nested classes/interfaces inherited from class java.awt.Component

      `java.awt.Component.BaselineResizeBehavior`

  <!-- -->

  - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description     |
    |---------------------------|---------------------------|
    | `static java.lang.String` | `PROGRESS_INDETERMINATE`  |
    | `static java.lang.String` | `PROGRESS_STATE`          |
    | `static java.lang.String` | `PROGRESS_STRING`         |
    | `static java.lang.String` | `PROGRESS_VALUE`          |

    - ### Fields inherited from class javax.swing.JComponent

      `TOOL_TIP_TEXT_KEY, UNDEFINED_CONDITION, WHEN_ANCESTOR_OF_FOCUSED_COMPONENT, WHEN_FOCUSED, WHEN_IN_FOCUSED_WINDOW`

    <!-- -->

    - ### Fields inherited from class java.awt.Component

      `BOTTOM_ALIGNMENT, CENTER_ALIGNMENT, LEFT_ALIGNMENT, RIGHT_ALIGNMENT, TOP_ALIGNMENT`

    <!-- -->

    - ### Fields inherited from interface java.awt.image.ImageObserver

      `ABORT, ALLBITS, ERROR, FRAMEBITS, HEIGHT, PROPERTIES, SOMEBITS, WIDTH`

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                      |
    |------------------------------------------------------------------|
    | `MapCanvas``()`                                                  |
    | `MapCanvas``(`[`LayerManager`](LayerManager.md)` layerManager)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                 | Method and Description                                                                                                                                                                     |
    |-------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                            | `actuallySetCursor``()`<br>Calls the Component superclass setCursor() method                                                                                                               |
    | `void`                                                            | `addChangeListener``(javax.swing.event.ChangeListener l)`<br>Adds a change listener to listen for queryWindow changes.                                                                     |
    | [`CoreLoop`](CoreLoop.md)                                         | `getCoreLoop``()`<br>Gets the instance of Core Loop used by this canvas.                                                                                                                   |
    | [`EventManager`](EventManager.md)                                 | `getEventManager``()`<br>Gets the Event Manager instance used by this canvas.                                                                                                              |
    | `java.awt.Frame`                                                  | `getFrameForDialog``()`<br>Gets the containing frame                                                                                                                                       |
    | [`LayerManager`](LayerManager.md)                                 | `getLayerManager``()`<br>Returns the LayerManager associated with this canvas.                                                                                                             |
    | [`MapRegion`](MapRegion.md)                                       | `getMapRegion``()`<br>Returns the current MapRegion                                                                                                                                        |
    | `long`                                                            | `getPaintTime``()`<br>Returns the time spent on painting the last frame                                                                                                                    |
    | `javax.swing.JPopupMenu`                                          | `getPopupMenu``()`<br>Gets the current pop up menu associated to this canvas (if any)                                                                                                      |
    | `javax.swing.JProgressBar`                                        | `getProgressBar``()`                                                                                                                                                                       |
    | [`ProgressIndicatorLayer`](../layer/ui/ProgressIndicatorLayer.md) | `getProgressIndicator``()`<br>Returns the current [`ProgressIndicatorLayer`](../layer/ui/ProgressIndicatorLayer.md) associated to the MapCanvas                                            |
    | [`MapUndoManager`](MapUndoManager.md)                             | `getUndoManager``()`<br>Returns the UndoManager associated with this canvas.                                                                                                               |
    | `java.awt.geom.AffineTransform`                                   | `getViewportTransform``()`<br>A convenience method to get the viewport transformation matrix of the current map region.                                                                    |
    | `void`                                                            | `propertyChange``(java.lang.Object src, java.lang.String propertyName, java.lang.Object oldValue, java.lang.Object newValue)`<br>This method gets called when a bound property is changed. |
    | `void`                                                            | `propertyChange``(java.beans.PropertyChangeEvent evt)`                                                                                                                                     |
    | `void`                                                            | `removeChangeListener``(javax.swing.event.ChangeListener l)`<br>Removes the given listener from listening for queryWindow changes                                                          |
    | `void`                                                            | `setCoreLoop``(`[`CoreLoop`](CoreLoop.md)` loop)`<br>Sets the Core Loop instance to be used by this canvas.                                                                                |
    | `void`                                                            | `setCursor``(java.awt.Cursor cursor)`                                                                                                                                                      |
    | `void`                                                            | `setEventManager``(`[`EventManager`](EventManager.md)` eventManager)`<br>Sets the Event Manager instance to be used by this canvas.                                                        |
    | `void`                                                            | `setLayerManager``(`[`LayerManager`](LayerManager.md)` layerManager)`<br>Sets a LayerManager on this canvas.                                                                               |
    | `void`                                                            | `setMapRegion``(`[`MapRegion`](MapRegion.md)` mapRegion)`<br>Sets the MapRegion                                                                                                            |
    | `void`                                                            | `setPopupMenu``(javax.swing.JPopupMenu popUpMenu)`<br>Sets a pop up menu to the canvas                                                                                                     |
    | `void`                                                            | `setUndoManager``(`[`MapUndoManager`](MapUndoManager.md)` undoManager)`<br>Sets an UndoManager on this canvas.                                                                             |
    | `void`                                                            | `update``(long elapsedTime)`<br>Update all graphics contents as necessary before repainting the next frame.                                                                                |
    | `void`                                                            | `zoomToLayer``(`[`Layer`](Layer.md)` layer)`<br>Zoom the map to the bounding box of the specified layer's contents.                                                                        |

    - ### Methods inherited from class javax.swing.JPanel

      `getAccessibleContext, getUI, getUIClassID, setUI, updateUI`

    <!-- -->

    - ### Methods inherited from class javax.swing.JComponent

      `addAncestorListener, addNotify, addVetoableChangeListener, computeVisibleRect, contains, createToolTip, disable, enable, firePropertyChange, firePropertyChange, firePropertyChange, getActionForKeyStroke, getActionMap, getAlignmentX, getAlignmentY, getAncestorListeners, getAutoscrolls, getBaseline, getBaselineResizeBehavior, getBorder, getBounds, getClientProperty, getComponentPopupMenu, getConditionForKeyStroke, getDebugGraphicsOptions, getDefaultLocale, getFontMetrics, getGraphics, getHeight, getInheritsPopupMenu, getInputMap, getInputMap, getInputVerifier, getInsets, getInsets, getListeners, getLocation, getMaximumSize, getMinimumSize, getNextFocusableComponent, getPopupLocation, getPreferredSize, getRegisteredKeyStrokes, getRootPane, getSize, getToolTipLocation, getToolTipText, getToolTipText, getTopLevelAncestor, getTransferHandler, getVerifyInputWhenFocusTarget, getVetoableChangeListeners, getVisibleRect, getWidth, getX, getY, grabFocus, hide, isDoubleBuffered, isLightweightComponent, isManagingFocus, isOpaque, isOptimizedDrawingEnabled, isPaintingForPrint, isPaintingTile, isRequestFocusEnabled, isValidateRoot, paint, paintImmediately, paintImmediately, print, printAll, putClientProperty, registerKeyboardAction, registerKeyboardAction, removeAncestorListener, removeNotify, removeVetoableChangeListener, repaint, repaint, requestDefaultFocus, requestFocus, requestFocus, requestFocusInWindow, resetKeyboardActions, reshape, revalidate, scrollRectToVisible, setActionMap, setAlignmentX, setAlignmentY, setAutoscrolls, setBackground, setBorder, setComponentPopupMenu, setDebugGraphicsOptions, setDefaultLocale, setDoubleBuffered, setEnabled, setFocusTraversalKeys, setFont, setForeground, setInheritsPopupMenu, setInputMap, setInputVerifier, setMaximumSize, setMinimumSize, setNextFocusableComponent, setOpaque, setPreferredSize, setRequestFocusEnabled, setToolTipText, setTransferHandler, setVerifyInputWhenFocusTarget, setVisible, unregisterKeyboardAction, update`

    <!-- -->

    - ### Methods inherited from class java.awt.Container

      `add, add, add, add, add, addContainerListener, addPropertyChangeListener, addPropertyChangeListener, applyComponentOrientation, areFocusTraversalKeysSet, countComponents, deliverEvent, doLayout, findComponentAt, findComponentAt, getComponent, getComponentAt, getComponentAt, getComponentCount, getComponents, getComponentZOrder, getContainerListeners, getFocusTraversalKeys, getFocusTraversalPolicy, getLayout, getMousePosition, insets, invalidate, isAncestorOf, isFocusCycleRoot, isFocusCycleRoot, isFocusTraversalPolicyProvider, isFocusTraversalPolicySet, layout, list, list, locate, minimumSize, paintComponents, preferredSize, printComponents, remove, remove, removeAll, removeContainerListener, setComponentZOrder, setFocusCycleRoot, setFocusTraversalPolicy, setFocusTraversalPolicyProvider, setLayout, transferFocusDownCycle, validate`

    <!-- -->

    - ### Methods inherited from class java.awt.Component

      `action, add, addComponentListener, addFocusListener, addHierarchyBoundsListener, addHierarchyListener, addInputMethodListener, addKeyListener, addMouseListener, addMouseMotionListener, addMouseWheelListener, bounds, checkImage, checkImage, contains, createImage, createImage, createVolatileImage, createVolatileImage, dispatchEvent, enable, enableInputMethods, firePropertyChange, firePropertyChange, firePropertyChange, firePropertyChange, firePropertyChange, getBackground, getBounds, getColorModel, getComponentListeners, getComponentOrientation, getCursor, getDropTarget, getFocusCycleRootAncestor, getFocusListeners, getFocusTraversalKeysEnabled, getFont, getForeground, getGraphicsConfiguration, getHierarchyBoundsListeners, getHierarchyListeners, getIgnoreRepaint, getInputContext, getInputMethodListeners, getInputMethodRequests, getKeyListeners, getLocale, getLocation, getLocationOnScreen, getMouseListeners, getMouseMotionListeners, getMousePosition, getMouseWheelListeners, getName, getParent, getPeer, getPropertyChangeListeners, getPropertyChangeListeners, getSize, getToolkit, getTreeLock, gotFocus, handleEvent, hasFocus, imageUpdate, inside, isBackgroundSet, isCursorSet, isDisplayable, isEnabled, isFocusable, isFocusOwner, isFocusTraversable, isFontSet, isForegroundSet, isLightweight, isMaximumSizeSet, isMinimumSizeSet, isPreferredSizeSet, isShowing, isValid, isVisible, keyDown, keyUp, list, list, list, location, lostFocus, mouseDown, mouseDrag, mouseEnter, mouseExit, mouseMove, mouseUp, move, nextFocus, paintAll, postEvent, prepareImage, prepareImage, remove, removeComponentListener, removeFocusListener, removeHierarchyBoundsListener, removeHierarchyListener, removeInputMethodListener, removeKeyListener, removeMouseListener, removeMouseMotionListener, removeMouseWheelListener, removePropertyChangeListener, removePropertyChangeListener, repaint, repaint, repaint, resize, resize, setBounds, setBounds, setComponentOrientation, setDropTarget, setFocusable, setFocusTraversalKeysEnabled, setIgnoreRepaint, setLocale, setLocation, setLocation, setName, setSize, setSize, show, show, size, toString, transferFocus, transferFocusBackward, transferFocusUpCycle`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### PROGRESS_STATE

          public static final java.lang.String PROGRESS_STATE

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROGRESS_VALUE

          public static final java.lang.String PROGRESS_VALUE

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROGRESS_STRING

          public static final java.lang.String PROGRESS_STRING

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### PROGRESS_INDETERMINATE

          public static final java.lang.String PROGRESS_INDETERMINATE

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### MapCanvas

          public MapCanvas()

    <!-- -->

    - #### MapCanvas

          public MapCanvas(LayerManager layerManager)

  <!-- -->

  - ### Method Detail

    - #### setCursor

          public void setCursor(java.awt.Cursor cursor)

      Overrides:
      `setCursor` in class `java.awt.Component`

    <!-- -->

    - #### actuallySetCursor

          public void actuallySetCursor()

      Calls the Component superclass setCursor() method

    <!-- -->

    - #### getFrameForDialog

          public java.awt.Frame getFrameForDialog()

      Gets the containing frame
      Returns:
      a Frame instance

    <!-- -->

    - #### getPaintTime

          public long getPaintTime()

      Returns the time spent on painting the last frame
      Returns:

    <!-- -->

    - #### update

          public void update(long elapsedTime)

      Update all graphics contents as necessary before repainting the next frame.
      Parameters:
      `elapsedTime` - the elapsed time since last update, in milliseconds

    <!-- -->

    - #### getLayerManager

          public LayerManager getLayerManager()

      Returns the LayerManager associated with this canvas. Use the LayerManager to add or remove a layer.
      Returns:
      the LayerManager associated.

    <!-- -->

    - #### setLayerManager

          public void setLayerManager(LayerManager layerManager)

      Sets a LayerManager on this canvas.
      Parameters:
      `layerManager` -

    <!-- -->

    - #### getUndoManager

          public MapUndoManager getUndoManager()

      Returns the UndoManager associated with this canvas. Use to keep track of changes.
      Returns:
      the UndoManager associated.

    <!-- -->

    - #### setUndoManager

          public void setUndoManager(MapUndoManager undoManager)

      Sets an UndoManager on this canvas.
      Parameters:
      `undoManager` -

    <!-- -->

    - #### getMapRegion

          public MapRegion getMapRegion()

      Returns the current MapRegion
      Returns:

    <!-- -->

    - #### setMapRegion

          public void setMapRegion(MapRegion mapRegion)

      Sets the MapRegion
      Parameters:
      `mapRegion` -

    <!-- -->

    - #### getViewportTransform

          public java.awt.geom.AffineTransform getViewportTransform()

      A convenience method to get the viewport transformation matrix of the current map region. Same as calling getMapRegion.getViewportTransform(). A viewport transformation defines the mapping from a rectangular region (or window) of the world-coordinate system onto a rectangular region on the device (in this case, this canvas). In computer graphics terms it is also known as the window-to-viewport transformation.

    <!-- -->

    - #### getProgressIndicator

          public ProgressIndicatorLayer getProgressIndicator()

      Returns the current [`ProgressIndicatorLayer`](../layer/ui/ProgressIndicatorLayer.md) associated to the MapCanvas
      Returns:

    <!-- -->

    - #### zoomToLayer

          public void zoomToLayer(Layer layer)

      Zoom the map to the bounding box of the specified layer's contents.
      Parameters:
      `layer` - the layer whose data MBR will be zoomed to.

    <!-- -->

    - #### getEventManager

          public EventManager getEventManager()

      Gets the Event Manager instance used by this canvas.
      Returns:

    <!-- -->

    - #### setEventManager

          public void setEventManager(EventManager eventManager)

      Sets the Event Manager instance to be used by this canvas.
      Parameters:
      `eventManager` -

    <!-- -->

    - #### getCoreLoop

          public CoreLoop getCoreLoop()

      Gets the instance of Core Loop used by this canvas.
      Returns:

    <!-- -->

    - #### setCoreLoop

          public void setCoreLoop(CoreLoop loop)

      Sets the Core Loop instance to be used by this canvas.
      Parameters:
      `loop` -

    <!-- -->

    - #### setPopupMenu

          public void setPopupMenu(javax.swing.JPopupMenu popUpMenu)

      Sets a pop up menu to the canvas
      Parameters:
      `popUpMenu` -

    <!-- -->

    - #### getPopupMenu

          public javax.swing.JPopupMenu getPopupMenu()

      Gets the current pop up menu associated to this canvas (if any)
      Returns:

    <!-- -->

    - #### addChangeListener

          public void addChangeListener(javax.swing.event.ChangeListener l)

      Adds a change listener to listen for queryWindow changes.
      Parameters:
      `l` -

    <!-- -->

    - #### removeChangeListener

          public void removeChangeListener(javax.swing.event.ChangeListener l)

      Removes the given listener from listening for queryWindow changes
      Parameters:
      `l` -

    <!-- -->

    - #### propertyChange

          public void propertyChange(java.lang.Object src,
                                     java.lang.String propertyName,
                                     java.lang.Object oldValue,
                                     java.lang.Object newValue)

      This method gets called when a bound property is changed.
      Parameters:
      `source` - the bean that fired the event

      `propertyName` - the programmatic name of the property that was changed

      `oldValue` - the old value of the property

      `newValue` - the new value of the property

    <!-- -->

    - #### propertyChange

          public void propertyChange(java.beans.PropertyChangeEvent evt)

      Specified by:
      `propertyChange` in interface `java.beans.PropertyChangeListener`

    <!-- -->

    - #### getProgressBar

          public javax.swing.JProgressBar getProgressBar()

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

- [Prev Class](LayerManagerEvent.md)
- [Next Class](MapRegion.md)

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
