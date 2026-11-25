Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](Node.md)
- [Next Class](Path.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.spatial.network

## Class OraTst

- java.lang.Object

- - oracle.spatial.network.OraTst

<!-- -->

-

  ------------------------------------------------------------------------



      public class OraTst
      extends java.lang.Object

  This class defines print methods for the network elements in Network Data Model. This is for debugging purpose.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `OraTst``()`                |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type               | Method and Description                                                                                          |
    |---------------------------------|-----------------------------------------------------------------------------------------------------------------|
    | `static java.text.NumberFormat` | `getNumberformat``()`                                                                                           |
    | `static void`                   | `print``(`[`JGeometry`](../geometry/JGeometry.md)` geom)`                                                       |
    | `static void`                   | `print``(`[`Link`](Link.md)` link)`<br>Prints the link.                                                         |
    | `static void`                   | `print``(`[`Link`](Link.md)`[] linkArray)`<br>Prints the link array.                                            |
    | `static void`                   | `print``(`[`Link`](Link.md)`[] linkArray, boolean verbose)`<br>Prints the link array with detailed information. |
    | `static void`                   | `print``(`[`Link`](Link.md)` link, boolean verbose)`<br>Prints the link with detailed information.              |
    | `static void`                   | `print``(`[`MBR`](MBR.md)` mbr)`<br>Prints the MBR.                                                             |
    | `static void`                   | `print``(`[`Network`](Network.md)` network)`<br>Prints the network.                                             |
    | `static void`                   | `print``(`[`Network`](Network.md)`[] networkArray)`<br>Prints the network array.                                |
    | `static void`                   | `print``(`[`Network`](Network.md)` network, boolean verbose)`<br>Prints the network with detailed information.  |
    | `static void`                   | `print``(oracle.spatial.network.NetworkCache cache)`<br>Prints the network cache.                               |
    | `static void`                   | `print``(`[`NetworkMetadata`](NetworkMetadata.md)` metadata)`<br>Prints the network metadata.                   |
    | `static void`                   | `print``(`[`NetworkMetadata`](NetworkMetadata.md)`[] metadataArray)`<br>Prints the network metadata array.      |
    | `static void`                   | `print``(`[`Node`](Node.md)` node)`<br>Prints the node.                                                         |
    | `static void`                   | `print``(`[`Node`](Node.md)`[] nodeArray)`<br>Prints the node array.                                            |
    | `static void`                   | `print``(`[`Node`](Node.md)`[] nodeArray, boolean verbose)`<br>Prints the node array with detailed information. |
    | `static void`                   | `print``(`[`Node`](Node.md)` node, boolean verbose)`<br>Prints the node with detailed information.              |
    | `static void`                   | `print``(`[`Path`](Path.md)` path)`<br>Prints the path.                                                         |
    | `static void`                   | `print``(`[`Path`](Path.md)`[] pathArray)`<br>Prints the path array.                                            |
    | `static void`                   | `print``(`[`Path`](Path.md)` path, boolean printPathId)`<br>Prints the path.                                    |
    | `static void`                   | `print``(java.lang.String msg)`<br>Prints the message.                                                          |
    | `static void`                   | `print``(`[`SubPath`](SubPath.md)` subPath)`                                                                    |
    | `static void`                   | `print``(`[`SubPath`](SubPath.md)`[] pathArray)`                                                                |
    | `static void`                   | `print``(`[`SubPath`](SubPath.md)` subPath, int subPathID)`                                                     |
    | `static void`                   | `print``(`[`Tree`](Tree.md)` tree)`                                                                             |
    | `static void`                   | `print``(`[`TreeLink`](TreeLink.md)` treeLink)`                                                                 |
    | `static void`                   | `print``(`[`TreeNode`](TreeNode.md)` treeNode)`                                                                 |
    | `static void`                   | `print``(`[`TreeNode`](TreeNode.md)`[] treeNodeArray)`                                                          |
    | `static void`                   | `printUserData``(java.lang.Object element)`                                                                     |
    | `static void`                   | `printVerbose``(`[`Node`](Node.md)` node)`                                                                      |
    | `static void`                   | `setNumberFormat``(java.lang.String format)`                                                                    |
    | `static java.lang.Object[]`     | `sortByID``(java.lang.Object[] objArray)`<br>Sorts the network elements by IDs.                                 |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### OraTst

          public OraTst()

  <!-- -->

  - ### Method Detail

    - #### setNumberFormat

          public static void setNumberFormat(java.lang.String format)

    <!-- -->

    - #### getNumberformat

          public static java.text.NumberFormat getNumberformat()

    <!-- -->

    - #### print

          public static void print(java.lang.String msg)

      Prints the message.
      Parameters:
      `msg` - the message to be printed

    <!-- -->

    - #### print

          public static void print(MBR mbr)

      Prints the MBR.
      Parameters:
      `mbr` - the MBR to be printed

    <!-- -->

    - #### print

          public static void print(Node node)

      Prints the node.
      Parameters:
      `node` - the node to be printed

    <!-- -->

    - #### print

          public static void print(Node node,
                                   boolean verbose)

      Prints the node with detailed information.
      Parameters:
      `node` - the node to be printed

      `verbose` - set to true for detailed information

    <!-- -->

    - #### printVerbose

          public static void printVerbose(Node node)

    <!-- -->

    - #### print

          public static void print(Node[] nodeArray)

      Prints the node array.
      Parameters:
      `nodeArray` - the node array to be printed

    <!-- -->

    - #### print

          public static void print(Node[] nodeArray,
                                   boolean verbose)

      Prints the node array with detailed information.
      Parameters:
      `nodeArray` - the nnode array to be printed

      `verbose` - set to true for detailed information

    <!-- -->

    - #### print

          public static void print(Link link)

      Prints the link.
      Parameters:
      `link` - link to be printed

    <!-- -->

    - #### print

          public static void print(Link link,
                                   boolean verbose)

      Prints the link with detailed information.
      Parameters:
      `link` - link to be printed

      `verbose` - set to true for deltailed information

    <!-- -->

    - #### print

          public static void print(Link[] linkArray)

      Prints the link array.
      Parameters:
      `linkArray` - link array to be printed

    <!-- -->

    - #### print

          public static void print(Link[] linkArray,
                                   boolean verbose)

      Prints the link array with detailed information.
      Parameters:
      `linkArray` - link array to be printed

      `verbose` - set to true for deltailed information

    <!-- -->

    - #### print

          public static void print(Path path)

      Prints the path.
      Parameters:
      `path` - the path to be printed

    <!-- -->

    - #### print

          public static void print(Path path,
                                   boolean printPathId)

      Prints the path.
      Parameters:
      `path` - the path to be printed

    <!-- -->

    - #### print

          public static void print(SubPath subPath,
                                   int subPathID)

    <!-- -->

    - #### print

          public static void print(SubPath subPath)

    <!-- -->

    - #### print

          public static void print(Tree tree)

    <!-- -->

    - #### print

          public static void print(TreeNode treeNode)

    <!-- -->

    - #### print

          public static void print(TreeLink treeLink)

    <!-- -->

    - #### print

          public static void print(TreeNode[] treeNodeArray)

    <!-- -->

    - #### print

          public static void print(SubPath[] pathArray)

    <!-- -->

    - #### print

          public static void print(oracle.spatial.network.NetworkCache cache)

      Prints the network cache.
      Parameters:
      `cache` - network cache to be printed

    <!-- -->

    - #### print

          public static void print(Path[] pathArray)

      Prints the path array.
      Parameters:
      `pathArray` - the path array to be printed

    <!-- -->

    - #### print

          public static void print(NetworkMetadata metadata)

      Prints the network metadata.
      Parameters:
      `metadata` - the network metadata to be printed

    <!-- -->

    - #### print

          public static void print(NetworkMetadata[] metadataArray)

      Prints the network metadata array.
      Parameters:
      `metadataArray` - the metadata array to be printed

    <!-- -->

    - #### print

          public static void print(Network network)

      Prints the network.
      Parameters:
      `network` - the network to be printed

    <!-- -->

    - #### print

          public static void print(Network network,
                                   boolean verbose)

      Prints the network with detailed information.
      Parameters:
      `network` - the network to be printed

      `verbose` - set to true for detailed information

    <!-- -->

    - #### print

          public static void print(Network[] networkArray)

      Prints the network array.
      Parameters:
      `networkArray` - the network array to be printed

    <!-- -->

    - #### sortByID

          public static java.lang.Object[] sortByID(java.lang.Object[] objArray)

      Sorts the network elements by IDs.
      Parameters:
      `objArray` - network elements in an Object array

    <!-- -->

    - #### print

          public static void print(JGeometry geom)

    <!-- -->

    - #### printUserData

          public static void printUserData(java.lang.Object element)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](Node.md)
- [Next Class](Path.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
