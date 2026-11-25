Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](PropertyType.md)**
- **[Next Class](ReferentialIntegrityException.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

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

**javax.jcr**

## **Interface RangeIterator**

- **All Superinterfaces:**
  **java.util.Iterator**

  <!-- -->

  **All Known Subinterfaces:**
  **[EventIterator](observation/EventIterator.md), [EventListenerIterator](observation/EventListenerIterator.md), [NodeIterator](NodeIterator.md), [NodeTypeIterator](nodetype/NodeTypeIterator.md), [PropertyIterator](PropertyIterator.md), [RowIterator](query/RowIterator.md), [VersionIterator](version/VersionIterator.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface RangeIterator
      extends java.util.Iterator

  **Extends `Iterator` with the `skip`, `getSize` and `getPosition` methods. The base interface of all type-specific iterators in the `javax.jcr` and its subpackages.**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                 |
    |-------------------|------------------------------------------------------------------------|
    | `long`            | `getPosition``()`<br>Returns the current position within the iterator. |
    | `long`            | `getSize``()`<br>Returns the number of elements in the iterator.       |
    | `void`            | `skip``(long skipNum)`<br>Skip a number of elements in the iterator.   |

    - ### Methods inherited from interface java.util.Iterator

      `forEachRemaining, hasNext, next, remove`

<!-- -->

- - ### Method Detail

    - #### skip

          void skip(long skipNum)

      Skip a number of elements in the iterator.
      Parameters:
      `skipNum` - the non-negative number of elements to skip

      Throws:
      `java.util.NoSuchElementException` - if skipped past the last element in the iterator.

    <!-- -->

    - #### getSize

          long getSize()

      Returns the number of elements in the iterator. If this information is unavailable, returns -1.
      Returns:
      a long

    <!-- -->

    - #### getPosition

          long getPosition()

      Returns the current position within the iterator. The number returned is the 0-based index of the next element in the iterator, i.e. the one that will be returned on the subsequent `next` call.
      Note that this method does not check if there is a next element, i.e. an empty iterator will always return 0.

      Returns:
      a long

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](PropertyType.md)**
- **[Next Class](ReferentialIntegrityException.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

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
