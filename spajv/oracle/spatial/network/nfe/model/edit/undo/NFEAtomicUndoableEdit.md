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

- [Prev Class](NetworkElementsRemovedUndoableEdit.md)
- [Next Class](NFEBlockUndoableEdit.md)

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

## Class NFEAtomicUndoableEdit

- java.lang.Object

- - javax.swing.undo.AbstractUndoableEdit

  - - oracle.spatial.network.nfe.model.edit.undo.NFEAtomicUndoableEdit

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, javax.swing.undo.UndoableEdit

  <!-- -->

  Direct Known Subclasses:
  [FeatureElementPropertyChangedUndoableEdit](FeatureElementPropertyChangedUndoableEdit.md), [FeatureElementsAddedUndoableEdit](FeatureElementsAddedUndoableEdit.md), [FeatureElementsRemovedUndoableEdit](FeatureElementsRemovedUndoableEdit.md), [FeaturePropertyChangedUndoableEdit](FeaturePropertyChangedUndoableEdit.md), [FeaturesAddedUndoableEdit](FeaturesAddedUndoableEdit.md), [FeaturesRemovedUndoableEdit](FeaturesRemovedUndoableEdit.md), [NetworkElementPropertyChangedUndoableEdit](NetworkElementPropertyChangedUndoableEdit.md), [NetworkElementsAddedUndoableEdit](NetworkElementsAddedUndoableEdit.md), [NetworkElementsRemovedUndoableEdit](NetworkElementsRemovedUndoableEdit.md), [RuleInstanceAddedUndoableEdit](RuleInstanceAddedUndoableEdit.md), [RuleInstanceRelationAddedUndoableEdit](RuleInstanceRelationAddedUndoableEdit.md), [RuleInstanceRelationRemovedUndoableEdit](RuleInstanceRelationRemovedUndoableEdit.md), [RuleInstanceRemovedUndoableEdit](RuleInstanceRemovedUndoableEdit.md)

  ------------------------------------------------------------------------



      public abstract class NFEAtomicUndoableEdit
      extends javax.swing.undo.AbstractUndoableEdit

  A base abstract class that should be extended by any undoable edit implementation that wants to perform a undo/redo action for a specific NFE model event.
  See Also:
  [Serialized Form](../../../../../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                         |
    |---------------------------------------------------------------------|
    | `NFEAtomicUndoableEdit``(`[`NFEModel`](../../NFEModel.md)` model)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                          |
    |-------------------|---------------------------------------------------------------------------------|
    | `long`            | `getTimeStamp``()`<br>Gets the time when this object was created.               |
    | `void`            | `setTimeStamp``(long timeStamp)`<br>Sets the time when this object was created. |

    - ### Methods inherited from class javax.swing.undo.AbstractUndoableEdit

      `addEdit, canRedo, canUndo, die, getPresentationName, getRedoPresentationName, getUndoPresentationName, isSignificant, redo, replaceEdit, toString, undo`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEAtomicUndoableEdit

          public NFEAtomicUndoableEdit(NFEModel model)

  <!-- -->

  - ### Method Detail

    - #### getTimeStamp

          public long getTimeStamp()

      Gets the time when this object was created. It should be approximate to the time where the event was fired.
      Returns:
      the time in milliseconds

    <!-- -->

    - #### setTimeStamp

          public void setTimeStamp(long timeStamp)

      Sets the time when this object was created. It should be approximate to the time where the event was fired.
      Parameters:
      `timeStamp` - the time in milliseconds

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

- [Prev Class](NetworkElementsRemovedUndoableEdit.md)
- [Next Class](NFEBlockUndoableEdit.md)

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
