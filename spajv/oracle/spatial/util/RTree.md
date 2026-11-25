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

- [Prev Class](PcSampleDataSet.md)
- [Next Class](RTree.ComparatorImpl.md)

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

oracle.spatial.util

## Class RTree

- java.lang.Object

- - oracle.spatial.util.RTree

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class RTree
      extends java.lang.Object
      implements java.io.Serializable

  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                              |
    |-------------------|----------------------------------------------------|
    | `class `          | [`RTree.ComparatorImpl`](RTree.ComparatorImpl.md)  |
    | `class `          | [`RTree.RTreePlot`](RTree.RTreePlot.md)            |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                          |
    |------------------------------------------------------------------------------------------------------|
    | `RTree``(int nD, int nS, int mF)`<br>Constructs an empty RTree with specified parameters             |
    | `RTree``(int nD, int nS, int mF, double tol)`<br>Constructs an empty RTree with specified parameters |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                     |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `addEntry``(double[][] h, java.lang.Object o)`<br>addEntry adds an entry at leaf level to the RTree.                                                                                                                                                                       |
    | `boolean`         | `anyInteract``(boolean chkLfIntsxn, boolean getAllResults, java.util.ArrayList res, boolean reverse)`                                                                                                                                                                      |
    | `boolean`         | `anyInteract``(RTree b, java.util.ArrayList res)`                                                                                                                                                                                                                          |
    | `boolean`         | `anyInteract``(RTree a, boolean chkLfIntsxn, boolean getAllResults, java.util.ArrayList res)`                                                                                                                                                                              |
    | `boolean`         | `anyInteract``(RTree a, boolean chkLfIntsxn, boolean getAllResults, java.util.ArrayList res, boolean reverse)`                                                                                                                                                             |
    | `double`          | `compArea``(oracle.spatial.util.RTree.Span[] a)`                                                                                                                                                                                                                           |
    | `void`            | `compIntsxn``(oracle.spatial.util.RTree.Span[] a, oracle.spatial.util.RTree.Span[] b, oracle.spatial.util.RTree.Span[] res)`                                                                                                                                               |
    | `double`          | `compMinDistance``(oracle.spatial.util.RTree.Span[] a, oracle.spatial.util.RTree.Span[] b)`                                                                                                                                                                                |
    | `double`          | `compMinDistance``(oracle.spatial.util.RTree.Span[] a, oracle.spatial.util.RTree.Span[] b, double tol)`                                                                                                                                                                    |
    | `int`             | `getEntryCount``()`<br>Gets the number of entries (inserted objects) in the tree                                                                                                                                                                                           |
    | `double[][]`      | `getMBH``()`<br>Gets the bounds of the whole tree                                                                                                                                                                                                                          |
    | `boolean`         | `intscts``(oracle.spatial.util.RTree.Span[] a, oracle.spatial.util.RTree.Span[] b)`                                                                                                                                                                                        |
    | `boolean`         | `intscts``(oracle.spatial.util.RTree.Span[] a, oracle.spatial.util.RTree.Span[] b, double tol)`                                                                                                                                                                            |
    | `void`            | `leafDump``()`                                                                                                                                                                                                                                                             |
    | `static void`     | `main``(java.lang.String[] args)`                                                                                                                                                                                                                                          |
    | `boolean`         | `nnSearch``(double[][] searchMBR, java.util.ArrayList res)`                                                                                                                                                                                                                |
    | `boolean`         | `nnSearch``(RTree b, boolean chkLfIntsxn, boolean getAllResults, java.util.ArrayList res)`                                                                                                                                                                                 |
    | `boolean`         | `nnSearch``(RTree b, boolean chkLfIntsxn, boolean getAllResults, java.util.ArrayList res, boolean reverse)`                                                                                                                                                                |
    | `void`            | `packTree``(double[][][] mbhList, java.lang.Object[] pList)`<br>Generates a highly ordered packed tree using the scan-tile-recursive method                                                                                                                                |
    | `boolean`         | `removeEntry``(double[][] h, java.lang.Object obj)`<br>removeEntry removes an entry from the leaf level of the RTree and makes any other tree adjustments necessary, including possibly the orphaning and reinsertion of subtrees at any level if nodes become underfilled |
    | `boolean`         | `search``(double[][] h, java.util.ArrayList a)`<br>Searches an RTree for all objects whose minimum bounding hypersolids intersect the input search hypersolid                                                                                                              |
    | `void`            | `showRTreePlot``()`                                                                                                                                                                                                                                                        |
    | `void`            | `showRTreePlot``(java.lang.String title)`                                                                                                                                                                                                                                  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### RTree

          public RTree(int nD,
                       int nS,
                       int mF,
                       double tol)

      Constructs an empty RTree with specified parameters
      Parameters:
      `nD` - Number of dimensions in the space indexed by the tree. Can be 1, 2, 3,...

      `nS` - Node size; the number of entries per node. Since this is a RAM- resident tree there is no need to match node size with disk pages and node sizes of 5-12 will give best results

      `mF` - Minimum fill - the number of entries in a node below which the node is considered underfull and the remaining entries orphaned and reinserted in the tree. If set to 1, there will be no orphaning

      `tol` - Tolerance value

    <!-- -->

    - #### RTree

          public RTree(int nD,
                       int nS,
                       int mF)

      Constructs an empty RTree with specified parameters
      Parameters:
      `nD` - Number of dimensions in the space indexed by the tree. Can be 1, 2, 3,...

      `nS` - Node size; the number of entries per node. Since this is a RAM- resident tree there is no need to match node size with disk pages and node sizes of 5-12 will give best results

      `mF` - Minimum fill - the number of entries in a node below which the node is considered underfull and the remaining entries orphaned and reinserted in the tree. If set to 1, there will be no orphaning

  <!-- -->

  - ### Method Detail

    - #### getMBH

          public double[][] getMBH()

      Gets the bounds of the whole tree
      Returns:
      an 2-dimensional array of doubles where the first index ranges over \[0,nDim-1\], the dimension of the indexed space and the second index ranges over \[0,1\], the min and max on each dimension

    <!-- -->

    - #### getEntryCount

          public int getEntryCount()

      Gets the number of entries (inserted objects) in the tree
      Returns:
      the number of entries at leaf level of the tree

    <!-- -->

    - #### search

          public boolean search(double[][] h,
                                java.util.ArrayList a)

      Searches an RTree for all objects whose minimum bounding hypersolids intersect the input search hypersolid
      Parameters:
      `h` - two dimensional array of doubles which are the minimum bounding hypersolid defining the search. The first index ranges over 0,nDimensions-1 and is the dimension of the space. The second index ranges over 0,1 and specifies the min and max.

      `a` - The ArrayList holds the objects found to satisfy the search. Should be preallocated by the caller and set via the constructor or ensureCapacity(int) for expected result size (for efficiency). Will not overflow if undersized.

      Returns:
      true if there are some results of the search; false if none. ArrayList a.size() will return the number of hits.

    <!-- -->

    - #### addEntry

          public void addEntry(double[][] h,
                               java.lang.Object o)

      addEntry adds an entry at leaf level to the RTree.
      Parameters:
      `h` - two dimensional array of doubles defining the minimum bounding hypersolid of the added object. The first index ranges over 0,nDim-1 where nDim is the dimension of the space (1,2,3...). The second index ranges over 0,1 and selects the min and max

      `o` - The inserted Object reference

    <!-- -->

    - #### removeEntry

          public boolean removeEntry(double[][] h,
                                     java.lang.Object obj)

      removeEntry removes an entry from the leaf level of the RTree and makes any other tree adjustments necessary, including possibly the orphaning and reinsertion of subtrees at any level if nodes become underfilled
      Parameters:
      `h` - two dimensional array of doubles defining the minimum bounding hypersolid of the removed object. The first index ranges over 0,nDimensions-1 and is the dimension of the space. The second index ranges over 0,1 and specifies the min or max

      `obj` - The removed Object reference

      Returns:
      true if the object was found and removed; false if not in tree

    <!-- -->

    - #### packTree

          public void packTree(double[][][] mbhList,
                               java.lang.Object[] pList)
                        throws java.lang.Exception

      Generates a highly ordered packed tree using the scan-tile-recursive method
      Parameters:
      `mbhList` - A list of mbh objects which is a three dimensional array of doubles. The first index ranges over 0,num-1 of entries. The second index ranges over 0,ndim-1 the size of the space The third index ranges over 0,1 for min, max.

      `pList` - An array of Object references. The length of the array is the same as the number of entries in the array of MBHs (the first index).

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### intscts

          public boolean intscts(oracle.spatial.util.RTree.Span[] a,
                                 oracle.spatial.util.RTree.Span[] b)

    <!-- -->

    - #### intscts

          public boolean intscts(oracle.spatial.util.RTree.Span[] a,
                                 oracle.spatial.util.RTree.Span[] b,
                                 double tol)

    <!-- -->

    - #### compMinDistance

          public double compMinDistance(oracle.spatial.util.RTree.Span[] a,
                                        oracle.spatial.util.RTree.Span[] b)

    <!-- -->

    - #### compMinDistance

          public double compMinDistance(oracle.spatial.util.RTree.Span[] a,
                                        oracle.spatial.util.RTree.Span[] b,
                                        double tol)

    <!-- -->

    - #### compIntsxn

          public void compIntsxn(oracle.spatial.util.RTree.Span[] a,
                                 oracle.spatial.util.RTree.Span[] b,
                                 oracle.spatial.util.RTree.Span[] res)

    <!-- -->

    - #### compArea

          public double compArea(oracle.spatial.util.RTree.Span[] a)

    <!-- -->

    - #### anyInteract

          public boolean anyInteract(RTree b,
                                     java.util.ArrayList res)
                              throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### anyInteract

          public boolean anyInteract(RTree a,
                                     boolean chkLfIntsxn,
                                     boolean getAllResults,
                                     java.util.ArrayList res)
                              throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### anyInteract

          public boolean anyInteract(RTree a,
                                     boolean chkLfIntsxn,
                                     boolean getAllResults,
                                     java.util.ArrayList res,
                                     boolean reverse)
                              throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### anyInteract

          public boolean anyInteract(boolean chkLfIntsxn,
                                     boolean getAllResults,
                                     java.util.ArrayList res,
                                     boolean reverse)
                              throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### nnSearch

          public boolean nnSearch(double[][] searchMBR,
                                  java.util.ArrayList res)
                           throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### nnSearch

          public boolean nnSearch(RTree b,
                                  boolean chkLfIntsxn,
                                  boolean getAllResults,
                                  java.util.ArrayList res)
                           throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### nnSearch

          public boolean nnSearch(RTree b,
                                  boolean chkLfIntsxn,
                                  boolean getAllResults,
                                  java.util.ArrayList res,
                                  boolean reverse)
                           throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### main

          public static void main(java.lang.String[] args)
                           throws java.io.IOException,
                                  java.lang.Exception

      Throws:
      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### leafDump

          public void leafDump()

    <!-- -->

    - #### showRTreePlot

          public void showRTreePlot(java.lang.String title)

    <!-- -->

    - #### showRTreePlot

          public void showRTreePlot()

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

- [Prev Class](PcSampleDataSet.md)
- [Next Class](RTree.ComparatorImpl.md)

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
