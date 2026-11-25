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

- **Prev Class**
- **[Next Class](TraversingItemVisitor.Default.md)**

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

**javax.jcr.util**

## **Class TraversingItemVisitor**

- **java.lang.Object**

- - **javax.jcr.util.TraversingItemVisitor**

<!-- -->

- **All Implemented Interfaces:**
  **[ItemVisitor](../ItemVisitor.md)**

  <!-- -->

  **Direct Known Subclasses:**
  **[TraversingItemVisitor.Default](TraversingItemVisitor.Default.md)**

  ------------------------------------------------------------------------

  **
  **

      public abstract class TraversingItemVisitor
      extends java.lang.Object
      implements ItemVisitor

  **An implementation of `ItemVisitor`.**
  **`TraversingItemVisitor` is an abstract utility class which allows to easily traverse an `Item` hierarchy.**

  **`TraversingItemVisitor` makes use of the Visitor Pattern as described in the book 'Design Patterns' by the Gang Of Four (Gamma et al.).**

  **Tree traversal is done observing the left-to-right order of child `Item`s if such an order is supported and exists.**

<!-- -->

-
  -

    ### **Nested Class Summary**

    **Nested Classes**

    | Modifier and Type | Class and Description                                                                                                                                                          |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`TraversingItemVisitor.Default`](TraversingItemVisitor.Default.md)<br>Convenience class providing default implementations of the abstract methods of `TraversingItemVisitor`. |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                               |
    |-----------------------------------------------------------------------------------------------------------|
    | `TraversingItemVisitor``()`<br>Constructs a new instance of this class.                                   |
    | `TraversingItemVisitor``(boolean breadthFirst)`<br>Constructs a new instance of this class.               |
    | `TraversingItemVisitor``(boolean breadthFirst, int maxLevel)`<br>Constructs a new instance of this class. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                   |
    |-------------------|----------------------------------------------------------------------------------------------------------|
    | `void`            | `visit``(`[`Node`](../Node.md)` node)`<br>Called when the Visitor is passed to a `Node`.                 |
    | `void`            | `visit``(`[`Property`](../Property.md)` property)`<br>Called when the Visitor is passed to a `Property`. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### TraversingItemVisitor

          public TraversingItemVisitor()

      Constructs a new instance of this class.
      The tree of `Item`s will be traversed in a depth-first manner (default behaviour).

    <!-- -->

    - #### TraversingItemVisitor

          public TraversingItemVisitor(boolean breadthFirst)

      Constructs a new instance of this class.
      Parameters:
      `breadthFirst` - if `breadthFirst` is true then traversal is done in a breadth-first manner; otherwise it is done in a depth-first manner (which is the default behaviour).

    <!-- -->

    - #### TraversingItemVisitor

          public TraversingItemVisitor(boolean breadthFirst,
                                       int maxLevel)

      Constructs a new instance of this class.
      Parameters:
      `breadthFirst` - if `breadthFirst` is true then traversal is done in a breadth-first manner; otherwise it is done in a depth-first manner (which is the default behaviour).

      `maxLevel` - the 0-based level up to which the hierarchy should be traversed (if it's -1, the hierarchy will be traversed until there are no more children of the current item)

  <!-- -->

  - ### Method Detail

    - #### visit

          public void visit(Property property)
                     throws RepositoryException

      Called when the Visitor is passed to a `Property`.
      It calls `TraversingItemVisitor.entering(Property, int)` followed by `TraversingItemVisitor.leaving(Property, int)`. Implement these abstract methods to specify behaviour on 'arrival at' and 'after leaving' the `Property`.

      If this method throws, the visiting process is aborted.

      Specified by:
      [`visit`](../ItemVisitor.md) in interface [`ItemVisitor`](../ItemVisitor.md)

      Parameters:
      `property` - the `Property` that is accepting this visitor.

      Throws:
      [`RepositoryException`](../RepositoryException.md) - if an error occurrs

    <!-- -->

    - #### visit

          public void visit(Node node)
                     throws RepositoryException

      Called when the Visitor is passed to a `Node`.
      It calls `TraversingItemVisitor.entering(Node, int)` followed by `TraversingItemVisitor.leaving(Node, int)`. Implement these abstract methods to specify behaviour on 'arrival at' and 'after leaving' the `Node`.

      If this method throws, the visiting process is aborted.

      Specified by:
      [`visit`](../ItemVisitor.md) in interface [`ItemVisitor`](../ItemVisitor.md)

      Parameters:
      `node` - the `Node` that is accepting this visitor.

      Throws:
      [`RepositoryException`](../RepositoryException.md) - if an error occurrs

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

- **Prev Class**
- **[Next Class](TraversingItemVisitor.Default.md)**

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
