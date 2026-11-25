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

- [Prev Class](NFEConnectionManager.md)
- [Next Class](NFEManipulator.md)

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

oracle.spatial.network.nfe.model.edit

## Class NFEEditionManager

- java.lang.Object

- - oracle.spatial.network.nfe.model.edit.NFEEditionManager

<!-- -->

- All Implemented Interfaces:
  java.util.EventListener, [NFEModelListener](../event/NFEModelListener.md)

  ------------------------------------------------------------------------



      public class NFEEditionManager
      extends java.lang.Object
      implements NFEModelListener

  This class keeps tracks of all the changes made to the model's content such as network elements, features, feature elements and rule instances.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.model.event.[NFEModelListener](../event/NFEModelListener.md)

      [`METHOD_MODEL_OBJECT_ADDED`](../event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECT_REMOVED`](../event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECTS_ADDED`](../event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECTS_REMOVED`](../event/NFEModelListener.md)`, `[`METHOD_PROPERTY_CHANGED`](../event/NFEModelListener.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEEditionManager``()`     |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                         | Method and Description                                                                                                                                                                    |
    |-------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                    | `addChangeListener``(javax.swing.event.ChangeListener listener)`<br>Adds a change lister                                                                                                  |
    | `boolean`                                 | `canSave``()`<br>Tells whether currently exist changes that can be saved.                                                                                                                 |
    | `void`                                    | `clearChanges``()`<br>Removes all the changes currently held in the class.                                                                                                                |
    | [`NFEChangesKeeper`](NFEChangesKeeper.md) | `getChangesKeeper``()`<br>Gets the current [`NFEChangesKeeper`](NFEChangesKeeper.md) instance used to store changes.                                                                      |
    | `void`                                    | `modelObjectAdded``(`[`NFEModelObjectEvent`](../event/NFEModelObjectEvent.md)` event)`<br>Invoked when a model object has been added                                                      |
    | `void`                                    | `modelObjectPropertyChanged``(`[`NFEModelObjectPropertyChangedEvent`](../event/NFEModelObjectPropertyChangedEvent.md)` event)`<br>Invoked when a model object's property has been changed |
    | `void`                                    | `modelObjectRemoved``(`[`NFEModelObjectEvent`](../event/NFEModelObjectEvent.md)` event)`<br>Invoked when a model object has been removed                                                  |
    | `void`                                    | `modelObjectsAdded``(`[`NFEModelObjectsEvent`](../event/NFEModelObjectsEvent.md)` event)`<br>Invoked when one or more model objects have been added                                       |
    | `void`                                    | `modelObjectsRemoved``(`[`NFEModelObjectsEvent`](../event/NFEModelObjectsEvent.md)` event)`<br>Invoked when one or more model objects have been removed                                   |
    | `void`                                    | `removeChangeListener``(javax.swing.event.ChangeListener listener)`<br>Removes a change listener                                                                                          |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEEditionManager

          public NFEEditionManager()

  <!-- -->

  - ### Method Detail

    - #### clearChanges

          public void clearChanges()

      Removes all the changes currently held in the class.

    <!-- -->

    - #### getChangesKeeper

          public NFEChangesKeeper getChangesKeeper()

      Gets the current [`NFEChangesKeeper`](NFEChangesKeeper.md) instance used to store changes.
      Returns:
      the current changes keeper instance

    <!-- -->

    - #### canSave

          public boolean canSave()

      Tells whether currently exist changes that can be saved.
      Returns:
      true if there are changes to be saved

    <!-- -->

    - #### addChangeListener

          public void addChangeListener(javax.swing.event.ChangeListener listener)

      Adds a change lister
      Parameters:
      `listener` - a change listener implementation

    <!-- -->

    - #### removeChangeListener

          public void removeChangeListener(javax.swing.event.ChangeListener listener)

      Removes a change listener
      Parameters:
      `listener` - a change listener implementation

    <!-- -->

    - #### modelObjectAdded

          public void modelObjectAdded(NFEModelObjectEvent event)

      Description copied from interface: [`NFEModelListener`](../event/NFEModelListener.md)
      Invoked when a model object has been added
      Specified by:
      [`modelObjectAdded`](../event/NFEModelListener.md) in interface [`NFEModelListener`](../event/NFEModelListener.md)

      Parameters:
      `event` - contains a reference to the model object that has been added

    <!-- -->

    - #### modelObjectsAdded

          public void modelObjectsAdded(NFEModelObjectsEvent event)

      Description copied from interface: [`NFEModelListener`](../event/NFEModelListener.md)
      Invoked when one or more model objects have been added
      Specified by:
      [`modelObjectsAdded`](../event/NFEModelListener.md) in interface [`NFEModelListener`](../event/NFEModelListener.md)

      Parameters:
      `event` - contains a collection of references to the model objects that have been added

    <!-- -->

    - #### modelObjectRemoved

          public void modelObjectRemoved(NFEModelObjectEvent event)

      Description copied from interface: [`NFEModelListener`](../event/NFEModelListener.md)
      Invoked when a model object has been removed
      Specified by:
      [`modelObjectRemoved`](../event/NFEModelListener.md) in interface [`NFEModelListener`](../event/NFEModelListener.md)

      Parameters:
      `event` - contains a reference to the model object that has been removed

    <!-- -->

    - #### modelObjectsRemoved

          public void modelObjectsRemoved(NFEModelObjectsEvent event)

      Description copied from interface: [`NFEModelListener`](../event/NFEModelListener.md)
      Invoked when one or more model objects have been removed
      Specified by:
      [`modelObjectsRemoved`](../event/NFEModelListener.md) in interface [`NFEModelListener`](../event/NFEModelListener.md)

      Parameters:
      `event` - contains a collection of references to the model objects that have been removed

    <!-- -->

    - #### modelObjectPropertyChanged

          public void modelObjectPropertyChanged(NFEModelObjectPropertyChangedEvent event)

      Description copied from interface: [`NFEModelListener`](../event/NFEModelListener.md)
      Invoked when a model object's property has been changed
      Specified by:
      [`modelObjectPropertyChanged`](../event/NFEModelListener.md) in interface [`NFEModelListener`](../event/NFEModelListener.md)

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

- [Prev Class](NFEConnectionManager.md)
- [Next Class](NFEManipulator.md)

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
