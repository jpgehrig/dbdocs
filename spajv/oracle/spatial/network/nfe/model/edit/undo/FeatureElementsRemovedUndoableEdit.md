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

- [Prev Class](FeatureElementsAddedUndoableEdit.md)
- [Next Class](FeaturePropertyChangedUndoableEdit.md)

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

## Class FeatureElementsRemovedUndoableEdit

- java.lang.Object

- - javax.swing.undo.AbstractUndoableEdit

  - - [oracle.spatial.network.nfe.model.edit.undo.NFEAtomicUndoableEdit](NFEAtomicUndoableEdit.md)

    - - oracle.spatial.network.nfe.model.edit.undo.FeatureElementsRemovedUndoableEdit

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, javax.swing.undo.UndoableEdit

  ------------------------------------------------------------------------



      public class FeatureElementsRemovedUndoableEdit
      extends NFEAtomicUndoableEdit

  Atomic undoable edit implementation that performs the undo/redo actions when a one or more feature elements are removed from the model.
  See Also:
  [Serialized Form](../../../../../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                             |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `FeatureElementsRemovedUndoableEdit``(`[`NFEModel`](../../NFEModel.md)` model, java.util.Collection<`[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)`> featureElementsList)`  |
    | `FeatureElementsRemovedUndoableEdit``(`[`NFEModel`](../../NFEModel.md)` model, `[`NFEFeatureElement`](../../feature/NFEFeatureElement.md)` featureElement)`                             |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description |
    |-------------------|------------------------|
    | `void`            | `redo``()`             |
    | `void`            | `undo``()`             |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.edit.undo.[NFEAtomicUndoableEdit](NFEAtomicUndoableEdit.md)

      [`getTimeStamp`](NFEAtomicUndoableEdit.md)`, `[`setTimeStamp`](NFEAtomicUndoableEdit.md)

    <!-- -->

    - ### Methods inherited from class javax.swing.undo.AbstractUndoableEdit

      `addEdit, canRedo, canUndo, die, getPresentationName, getRedoPresentationName, getUndoPresentationName, isSignificant, replaceEdit, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FeatureElementsRemovedUndoableEdit

          public FeatureElementsRemovedUndoableEdit(NFEModel model,
                                                    java.util.Collection<NFEFeatureElement> featureElementsList)

    <!-- -->

    - #### FeatureElementsRemovedUndoableEdit

          public FeatureElementsRemovedUndoableEdit(NFEModel model,
                                                    NFEFeatureElement featureElement)

  <!-- -->

  - ### Method Detail

    - #### undo

          public void undo()
                    throws javax.swing.undo.CannotRedoException

      Specified by:
      `undo` in interface `javax.swing.undo.UndoableEdit`

      Overrides:
      `undo` in class `javax.swing.undo.AbstractUndoableEdit`

      Throws:
      `javax.swing.undo.CannotRedoException`

    <!-- -->

    - #### redo

          public void redo()
                    throws javax.swing.undo.CannotUndoException

      Specified by:
      `redo` in interface `javax.swing.undo.UndoableEdit`

      Overrides:
      `redo` in class `javax.swing.undo.AbstractUndoableEdit`

      Throws:
      `javax.swing.undo.CannotUndoException`

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

- [Prev Class](FeatureElementsAddedUndoableEdit.md)
- [Next Class](FeaturePropertyChangedUndoableEdit.md)

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
