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

- **[Prev Class](Property.md)**
- **[Next Class](PropertyType.md)**

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

## **Interface PropertyIterator**

- **All Superinterfaces:**
  **java.util.Iterator, [RangeIterator](RangeIterator.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface PropertyIterator
      extends RangeIterator

  **Allows easy iteration through a list of `Property`s with `nextProperty` as well as a `skip` method.**

<!-- -->

-
  -

    ### **Property Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Type                      | Property and Description                      |
    |---------------------------|-----------------------------------------------|
    | [`Property`](Property.md) | Returns the next `Property` in the iteration. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type         | Method and Description                                              |
    |---------------------------|---------------------------------------------------------------------|
    | [`Property`](Property.md) | `nextProperty``()`<br>Returns the next `Property` in the iteration. |

    - ### Methods inherited from interface javax.jcr.[RangeIterator](RangeIterator.md)

      [`getPosition`](RangeIterator.md)`, `[`getSize`](RangeIterator.md)`, `[`skip`](RangeIterator.md)

    <!-- -->

    - ### Methods inherited from interface java.util.Iterator

      `forEachRemaining, hasNext, next, remove`

<!-- -->

- - ### Property Detail

    - #### next

          Property nextProperty

      Returns the next `Property` in the iteration.

  <!-- -->

  - ### Method Detail

    - #### nextProperty

          Property nextProperty()

      Returns the next `Property` in the iteration.

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

- **[Prev Class](Property.md)**
- **[Next Class](PropertyType.md)**

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
