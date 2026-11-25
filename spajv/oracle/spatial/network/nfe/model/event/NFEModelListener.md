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

- [Prev Class](NFEModelEvent.md)
- [Next Class](NFEModelObjectEvent.md)

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

oracle.spatial.network.nfe.model.event

## Interface NFEModelListener

- All Superinterfaces:
  java.util.EventListener

  <!-- -->

  All Known Implementing Classes:
  [NFEBasicModel](../NFEBasicModel.md), [NFEBlockUndoableEdit](../edit/undo/NFEBlockUndoableEdit.md), [NFEEditionManager](../edit/NFEEditionManager.md), [NFEFeatureLayerRenderer](../../vis/mapcanvas/render/NFEFeatureLayerRenderer.md), [NFEManipulableFeatureLayerRenderer](../../vis/mapcanvas/render/NFEManipulableFeatureLayerRenderer.md), [NFENetworkRenderer](../../vis/mapcanvas/render/NFENetworkRenderer.md), [NFEPathRenderer](../../vis/mapcanvas/render/NFEPathRenderer.md), [NFERulesModel](../rule/NFERulesModel.md)

  ------------------------------------------------------------------------



      public interface NFEModelListener
      extends java.util.EventListener

  The listener interface for receiving events from a first class model object such as NFEModel, NFENetwork or NFEFeatureLayer. A class implementing this interface should then be subscribed to the desired model object using the model object's addModelListener() method.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description           |
    |---------------------------|---------------------------------|
    | `static java.lang.String` | `METHOD_MODEL_OBJECT_ADDED`     |
    | `static java.lang.String` | `METHOD_MODEL_OBJECT_REMOVED`   |
    | `static java.lang.String` | `METHOD_MODEL_OBJECTS_ADDED`    |
    | `static java.lang.String` | `METHOD_MODEL_OBJECTS_REMOVED`  |
    | `static java.lang.String` | `METHOD_PROPERTY_CHANGED`       |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                           |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `modelObjectAdded``(`[`NFEModelObjectEvent`](NFEModelObjectEvent.md)` event)`<br>Invoked when a model object has been added                                                      |
    | `void`            | `modelObjectPropertyChanged``(`[`NFEModelObjectPropertyChangedEvent`](NFEModelObjectPropertyChangedEvent.md)` event)`<br>Invoked when a model object's property has been changed |
    | `void`            | `modelObjectRemoved``(`[`NFEModelObjectEvent`](NFEModelObjectEvent.md)` event)`<br>Invoked when a model object has been removed                                                  |
    | `void`            | `modelObjectsAdded``(`[`NFEModelObjectsEvent`](NFEModelObjectsEvent.md)` event)`<br>Invoked when one or more model objects have been added                                       |
    | `void`            | `modelObjectsRemoved``(`[`NFEModelObjectsEvent`](NFEModelObjectsEvent.md)` event)`<br>Invoked when one or more model objects have been removed                                   |

<!-- -->

- - ### Field Detail

    - #### METHOD_MODEL_OBJECT_ADDED

          static final java.lang.String METHOD_MODEL_OBJECT_ADDED

      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### METHOD_MODEL_OBJECT_REMOVED

          static final java.lang.String METHOD_MODEL_OBJECT_REMOVED

      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### METHOD_PROPERTY_CHANGED

          static final java.lang.String METHOD_PROPERTY_CHANGED

      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### METHOD_MODEL_OBJECTS_REMOVED

          static final java.lang.String METHOD_MODEL_OBJECTS_REMOVED

      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### METHOD_MODEL_OBJECTS_ADDED

          static final java.lang.String METHOD_MODEL_OBJECTS_ADDED

      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### modelObjectAdded

          void modelObjectAdded(NFEModelObjectEvent event)

      Invoked when a model object has been added
      Parameters:
      `event` - contains a reference to the model object that has been added

    <!-- -->

    - #### modelObjectsAdded

          void modelObjectsAdded(NFEModelObjectsEvent event)

      Invoked when one or more model objects have been added
      Parameters:
      `event` - contains a collection of references to the model objects that have been added

    <!-- -->

    - #### modelObjectRemoved

          void modelObjectRemoved(NFEModelObjectEvent event)

      Invoked when a model object has been removed
      Parameters:
      `event` - contains a reference to the model object that has been removed

    <!-- -->

    - #### modelObjectsRemoved

          void modelObjectsRemoved(NFEModelObjectsEvent event)

      Invoked when one or more model objects have been removed
      Parameters:
      `event` - contains a collection of references to the model objects that have been removed

    <!-- -->

    - #### modelObjectPropertyChanged

          void modelObjectPropertyChanged(NFEModelObjectPropertyChangedEvent event)

      Invoked when a model object's property has been changed
      Parameters:
      `event` - contains a reference to the model objects which property has been changed and the name and previous value of the changed property

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

- [Prev Class](NFEModelEvent.md)
- [Next Class](NFEModelObjectEvent.md)

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
