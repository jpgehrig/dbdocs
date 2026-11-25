Skip navigation links

- [Overview](../../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Package](../ranges/package-summary.md)**
- **[Next Package](../validation/package-summary.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

# **Package org.w3c.dom.traversal**

**A W3C standard package, that provides a framework of interfaces for implementing DOM level 2 Traversal feature for dynamically traversing the XML document.**

**See: Description**

- **Interface Summary**

  | Interface                                 | Description                                                                                                                                                                                                                                                                      |
  |-------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [DocumentTraversal](DocumentTraversal.md) | `DocumentTraversal` contains methods that create iterators and tree-walkers to traverse a node and its children in document order (depth first, pre-order traversal, which is equivalent to the order in which the start tags occur in the text representation of the document). |
  | [NodeFilter](NodeFilter.md)               | Filters are objects that know how to "filter out" nodes.                                                                                                                                                                                                                         |
  | [NodeIterator](NodeIterator.md)           | `Iterators` are used to step through a set of nodes, e.g. the set of nodes in a `NodeList`, the document subtree governed by a particular `Node`, the results of a query, or any other set of nodes.                                                                             |
  | [TreeWalker](TreeWalker.md)               | `TreeWalker` objects are used to navigate a document tree or subtree using the view of the document defined by their `whatToShow` flags and filter (if any).                                                                                                                     |

## **Package org.w3c.dom.traversal Description**

**A W3C standard package, that provides a framework of interfaces for implementing DOM level 2 Traversal feature for dynamically traversing the XML document.
**

**Skip navigation links**

- **[Overview](../../../../overview-summary.md)**
- **Package**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../../../deprecated-list.md)**
- **[Index](../../../../index-all.md)**
- **[Help](../../../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Package](../ranges/package-summary.md)**
- **[Next Package](../validation/package-summary.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

**Copyright © 2000 [W3C](http://www.w3.org/)<sup>®</sup> ([MIT](http://www.csail.mit.edu/), [INRIA](http://www.inria.fr/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [trademark](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [document use](http://www.w3.org/Consortium/Legal/copyright-documents-19990405) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software-19980720) rules apply. This document has been reviewed by W3C Members and other interested parties and has been endorsed by the Director as a [W3C Recommendation](http://www.w3.org/Consortium/Process/Process-19991111/tr.html#RecsW3C).**
