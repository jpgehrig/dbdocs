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

- [Prev Class](MapRegionEvent.md)
- [Next Class](MVThemeLayer.md)

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

## Class MapUndoManager

- java.lang.Object

- - javax.swing.undo.AbstractUndoableEdit

  - - javax.swing.undo.CompoundEdit

    - - javax.swing.undo.UndoManager

      - - oracle.spatial.network.nfe.vis.maps.core.MapUndoManager

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.util.EventListener, javax.swing.event.UndoableEditListener, javax.swing.undo.UndoableEdit

  ------------------------------------------------------------------------



      public class MapUndoManager
      extends javax.swing.undo.UndoManager

  A subclass of `UndoManager` that notifies about any edit to the subscribed ChangeListeners.
  See Also:
  [Serialized Form](../../../../../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `MapUndoManager``()`        |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                   |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `addChangeListener``(javax.swing.event.ChangeListener l)`<br>Adds a ChangeListener                                                                                       |
    | `boolean`         | `addEdit``(javax.swing.undo.UndoableEdit anEdit)`                                                                                                                        |
    | `void`            | `discardAllEdits``()`                                                                                                                                                    |
    | `int`             | `getNumberOfEdits``()`<br>Returns the current number of edits                                                                                                            |
    | `void`            | `redo``()`                                                                                                                                                               |
    | `void`            | `removeChangeListener``(javax.swing.event.ChangeListener l)`<br>Removes the given ChangeListener                                                                         |
    | `boolean`         | `trimEdits``(javax.swing.undo.UndoableEdit from, boolean inclusiveFrom)`                                                                                                 |
    | `boolean`         | `trimEdits``(javax.swing.undo.UndoableEdit from, boolean inclusiveFrom, javax.swing.undo.UndoableEdit to, boolean inclusiveTo)`<br>Removes edits in the specified range. |
    | `boolean`         | `trimEdits``(javax.swing.undo.UndoableEdit from, javax.swing.undo.UndoableEdit to)`<br>Removes edits in the specified range.                                             |
    | `void`            | `undo``()`                                                                                                                                                               |
    | `boolean`         | `undoORredoPerfomed``()`<br>Returns true if an undo or redo action was performed                                                                                         |

    - ### Methods inherited from class javax.swing.undo.UndoManager

      `canRedo, canUndo, canUndoOrRedo, end, getLimit, getRedoPresentationName, getUndoOrRedoPresentationName, getUndoPresentationName, setLimit, toString, undoableEditHappened, undoOrRedo`

    <!-- -->

    - ### Methods inherited from class javax.swing.undo.CompoundEdit

      `die, getPresentationName, isInProgress, isSignificant`

    <!-- -->

    - ### Methods inherited from class javax.swing.undo.AbstractUndoableEdit

      `replaceEdit`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### MapUndoManager

          public MapUndoManager()

  <!-- -->

  - ### Method Detail

    - #### addEdit

          public boolean addEdit(javax.swing.undo.UndoableEdit anEdit)

      Specified by:
      `addEdit` in interface `javax.swing.undo.UndoableEdit`

      Overrides:
      `addEdit` in class `javax.swing.undo.UndoManager`

    <!-- -->

    - #### trimEdits

          public boolean trimEdits(javax.swing.undo.UndoableEdit from,
                                   boolean inclusiveFrom)

    <!-- -->

    - #### trimEdits

          public boolean trimEdits(javax.swing.undo.UndoableEdit from,
                                   javax.swing.undo.UndoableEdit to)

      Removes edits in the specified range.
      Parameters:

      `from` - the minimum UndoableEdit to remove

      `to` - the maximum UndoableEdit to remove

      Returns:

    <!-- -->

    - #### trimEdits

          public boolean trimEdits(javax.swing.undo.UndoableEdit from,
                                   boolean inclusiveFrom,
                                   javax.swing.undo.UndoableEdit to,
                                   boolean inclusiveTo)

      Removes edits in the specified range.
      Parameters:

      `from` - the minimum UndoableEdit to remove

      `inclusiveFrom` - true if the 'from' UndoableEdit has to be included

      `to` - the maximum UndoableEdit to remove

      `inclusiveTo` - true if the 'to' UndoableEdit has to be included

      Returns:

    <!-- -->

    - #### discardAllEdits

          public void discardAllEdits()

      Overrides:
      `discardAllEdits` in class `javax.swing.undo.UndoManager`

    <!-- -->

    - #### undo

          public void undo()
                    throws javax.swing.undo.CannotUndoException

      Specified by:
      `undo` in interface `javax.swing.undo.UndoableEdit`

      Overrides:
      `undo` in class `javax.swing.undo.UndoManager`

      Throws:
      `javax.swing.undo.CannotUndoException`

    <!-- -->

    - #### redo

          public void redo()
                    throws javax.swing.undo.CannotRedoException

      Specified by:
      `redo` in interface `javax.swing.undo.UndoableEdit`

      Overrides:
      `redo` in class `javax.swing.undo.UndoManager`

      Throws:
      `javax.swing.undo.CannotRedoException`

    <!-- -->

    - #### undoORredoPerfomed

          public boolean undoORredoPerfomed()

      Returns true if an undo or redo action was performed
      Returns:

    <!-- -->

    - #### addChangeListener

          public void addChangeListener(javax.swing.event.ChangeListener l)

      Adds a ChangeListener
      Parameters:
      `l` -

    <!-- -->

    - #### removeChangeListener

          public void removeChangeListener(javax.swing.event.ChangeListener l)

      Removes the given ChangeListener
      Parameters:
      `l` -

    <!-- -->

    - #### getNumberOfEdits

          public int getNumberOfEdits()

      Returns the current number of edits
      Returns:

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

- [Prev Class](MapRegionEvent.md)
- [Next Class](MVThemeLayer.md)

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
