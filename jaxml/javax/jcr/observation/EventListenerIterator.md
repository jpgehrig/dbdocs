Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](EventListener.md)**
- **[Next Class](ObservationManager.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**javax.jcr.observation**

## **Interface EventListenerIterator**

- **All Superinterfaces:**
  **java.util.Iterator, [RangeIterator](../RangeIterator.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface EventListenerIterator
      extends RangeIterator

  **Allows easy iteration through a list of `EventListener`s with `nextEventListener` as well as a `skip` method inherited from `RangeIterator`.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                   | Method and Description                                                        |
    |-------------------------------------|-------------------------------------------------------------------------------|
    | [`EventListener`](EventListener.md) | `nextEventListener``()`<br>Returns the next `EventListener` in the iteration. |

    - ### Methods inherited from interface javax.jcr.[RangeIterator](../RangeIterator.md)

      [`getPosition`](../RangeIterator.md)`, `[`getSize`](../RangeIterator.md)`, `[`skip`](../RangeIterator.md)

    <!-- -->

    - ### Methods inherited from interface java.util.Iterator

      `forEachRemaining, hasNext, next, remove`

<!-- -->

- - ### Method Detail

    - #### nextEventListener

          EventListener nextEventListener()

      Returns the next `EventListener` in the iteration.
      Returns:
      the next `EventListener` in the iteration.

      Throws:
      `java.util.NoSuchElementException` - if iteration has no more `EventListener`s.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](EventListener.md)**
- **[Next Class](ObservationManager.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2004-2005 Day Software Management AG. All Rights Reserved.**
