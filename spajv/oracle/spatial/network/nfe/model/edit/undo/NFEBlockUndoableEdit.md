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

- [Prev Class](NFEAtomicUndoableEdit.md)
- [Next Class](RuleInstanceAddedUndoableEdit.md)

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

oracle.spatial.network.nfe.model.edit.undo

## Class NFEBlockUndoableEdit

- java.lang.Object

- - javax.swing.undo.AbstractUndoableEdit

  - - oracle.spatial.network.nfe.model.edit.undo.NFEBlockUndoableEdit

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.util.EventListener, javax.swing.undo.UndoableEdit, [NFEModelListener](../../event/NFEModelListener.md)

  ------------------------------------------------------------------------



      public class NFEBlockUndoableEdit
      extends javax.swing.undo.AbstractUndoableEdit
      implements NFEModelListener

  Undoable Edit implementation which contains multiple actions that should be executed altogether in a undo/redo operation. An instance of this class will contain one or more instances of `NFEAttomicUndoableEdit`. Once an undoable block is open, it will catch every model event fired at the same execution thread associated to the block and will assign an undoable edit to manage the undo/redo for that event.
  See Also:
  [Serialized Form](../../../../../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.model.event.[NFEModelListener](../../event/NFEModelListener.md)

      [`METHOD_MODEL_OBJECT_ADDED`](../../event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECT_REMOVED`](../../event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECTS_ADDED`](../../event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECTS_REMOVED`](../../event/NFEModelListener.md)`, `[`METHOD_PROPERTY_CHANGED`](../../event/NFEModelListener.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                            |
    |----------------------------------------------------------------------------------------------------------------------------------------|
    | `NFEBlockUndoableEdit``(java.lang.String presentationName, `[`NFEModel`](../../NFEModel.md)` model)`<br>Allocates a new undoable block |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                       |
    |--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`             | `closeBlock``()`<br>Sets the block to stop listening events.                                                                                                                                 |
    | `java.lang.String` | `getPresentationName``()`                                                                                                                                                                    |
    | `long`             | `getThreadId``()`<br>Gets the id of the execution thread assigned to this block.                                                                                                             |
    | `boolean`          | `isBlockEmpty``()`<br>Tells whether the block is empty, that is, it does not contain actions                                                                                                 |
    | `boolean`          | `isOpen``()`<br>Tells whether the block is listening to events                                                                                                                               |
    | `void`             | `modelObjectAdded``(`[`NFEModelObjectEvent`](../../event/NFEModelObjectEvent.md)` event)`<br>Invoked when a model object has been added                                                      |
    | `void`             | `modelObjectPropertyChanged``(`[`NFEModelObjectPropertyChangedEvent`](../../event/NFEModelObjectPropertyChangedEvent.md)` event)`<br>Invoked when a model object's property has been changed |
    | `void`             | `modelObjectRemoved``(`[`NFEModelObjectEvent`](../../event/NFEModelObjectEvent.md)` event)`<br>Invoked when a model object has been removed                                                  |
    | `void`             | `modelObjectsAdded``(`[`NFEModelObjectsEvent`](../../event/NFEModelObjectsEvent.md)` event)`<br>Invoked when one or more model objects have been added                                       |
    | `void`             | `modelObjectsRemoved``(`[`NFEModelObjectsEvent`](../../event/NFEModelObjectsEvent.md)` event)`<br>Invoked when one or more model objects have been removed                                   |
    | `void`             | `openBlock``()`<br>Sets the block ready to listen for new actions performed in the NFE model.                                                                                                |
    | `void`             | `redo``()`                                                                                                                                                                                   |
    | `void`             | `setThreadId``(long threadId)`<br>Sets the id of the execution thread for the block.                                                                                                         |
    | `void`             | `undo``()`                                                                                                                                                                                   |

    - ### Methods inherited from class javax.swing.undo.AbstractUndoableEdit

      `addEdit, canRedo, canUndo, die, getRedoPresentationName, getUndoPresentationName, isSignificant, replaceEdit, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEBlockUndoableEdit

          public NFEBlockUndoableEdit(java.lang.String presentationName,
                                      NFEModel model)

      Allocates a new undoable block
      Parameters:
      `presentationName` - a user-friendly name that describes the actions performed in the block

      `model` - the current NFE model

  <!-- -->

  - ### Method Detail

    - #### openBlock

          public void openBlock()

      Sets the block ready to listen for new actions performed in the NFE model. Every NFE model event with a corresponding [`NFEAtomicUndoableEdit`](NFEAtomicUndoableEdit.md) implementation will be managed by the current block. During this state, the block's undo/redo methods should not be called

    <!-- -->

    - #### isBlockEmpty

          public boolean isBlockEmpty()

      Tells whether the block is empty, that is, it does not contain actions
      Returns:

    <!-- -->

    - #### closeBlock

          public void closeBlock()

      Sets the block to stop listening events. Once this state is set, no actions will be added to the block and it is ready to perform undo/redo actions.

    <!-- -->

    - #### getThreadId

          public long getThreadId()

      Gets the id of the execution thread assigned to this block.
      Returns:

    <!-- -->

    - #### setThreadId

          public void setThreadId(long threadId)

      Sets the id of the execution thread for the block. All the NFE model events fired from the execution thread with the given id, will be cached by the block.
      Parameters:
      `threadId` - an execution thread's id

    <!-- -->

    - #### isOpen

          public boolean isOpen()

      Tells whether the block is listening to events
      Returns:
      true if the model is listening to events

    <!-- -->

    - #### modelObjectAdded

          public void modelObjectAdded(NFEModelObjectEvent event)

      Description copied from interface: [`NFEModelListener`](../../event/NFEModelListener.md)
      Invoked when a model object has been added
      Specified by:
      [`modelObjectAdded`](../../event/NFEModelListener.md) in interface [`NFEModelListener`](../../event/NFEModelListener.md)

      Parameters:
      `event` - contains a reference to the model object that has been added

    <!-- -->

    - #### modelObjectsAdded

          public void modelObjectsAdded(NFEModelObjectsEvent event)

      Description copied from interface: [`NFEModelListener`](../../event/NFEModelListener.md)
      Invoked when one or more model objects have been added
      Specified by:
      [`modelObjectsAdded`](../../event/NFEModelListener.md) in interface [`NFEModelListener`](../../event/NFEModelListener.md)

      Parameters:
      `event` - contains a collection of references to the model objects that have been added

    <!-- -->

    - #### modelObjectRemoved

          public void modelObjectRemoved(NFEModelObjectEvent event)

      Description copied from interface: [`NFEModelListener`](../../event/NFEModelListener.md)
      Invoked when a model object has been removed
      Specified by:
      [`modelObjectRemoved`](../../event/NFEModelListener.md) in interface [`NFEModelListener`](../../event/NFEModelListener.md)

      Parameters:
      `event` - contains a reference to the model object that has been removed

    <!-- -->

    - #### modelObjectsRemoved

          public void modelObjectsRemoved(NFEModelObjectsEvent event)

      Description copied from interface: [`NFEModelListener`](../../event/NFEModelListener.md)
      Invoked when one or more model objects have been removed
      Specified by:
      [`modelObjectsRemoved`](../../event/NFEModelListener.md) in interface [`NFEModelListener`](../../event/NFEModelListener.md)

      Parameters:
      `event` - contains a collection of references to the model objects that have been removed

    <!-- -->

    - #### modelObjectPropertyChanged

          public void modelObjectPropertyChanged(NFEModelObjectPropertyChangedEvent event)

      Description copied from interface: [`NFEModelListener`](../../event/NFEModelListener.md)
      Invoked when a model object's property has been changed
      Specified by:
      [`modelObjectPropertyChanged`](../../event/NFEModelListener.md) in interface [`NFEModelListener`](../../event/NFEModelListener.md)

      Parameters:
      `event` - contains a reference to the model objects which property has been changed and the name and previous value of the changed property

    <!-- -->

    - #### getPresentationName

          public java.lang.String getPresentationName()

      Specified by:
      `getPresentationName` in interface `javax.swing.undo.UndoableEdit`

      Overrides:
      `getPresentationName` in class `javax.swing.undo.AbstractUndoableEdit`

    <!-- -->

    - #### undo

          public void undo()
                    throws javax.swing.undo.CannotUndoException

      Specified by:
      `undo` in interface `javax.swing.undo.UndoableEdit`

      Overrides:
      `undo` in class `javax.swing.undo.AbstractUndoableEdit`

      Throws:
      `javax.swing.undo.CannotUndoException`

    <!-- -->

    - #### redo

          public void redo()
                    throws javax.swing.undo.CannotRedoException

      Specified by:
      `redo` in interface `javax.swing.undo.UndoableEdit`

      Overrides:
      `redo` in class `javax.swing.undo.AbstractUndoableEdit`

      Throws:
      `javax.swing.undo.CannotRedoException`

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

- [Prev Class](NFEAtomicUndoableEdit.md)
- [Next Class](RuleInstanceAddedUndoableEdit.md)

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
