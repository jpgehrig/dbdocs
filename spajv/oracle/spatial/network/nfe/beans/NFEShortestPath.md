Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFESearchParams.md)
- [Next Class](NFETsp.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.beans

## Class NFEShortestPath

- java.lang.Object

- - oracle.spatial.network.nfe.beans.NFEShortestPath

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFEShortestPath
      extends java.lang.Object

  Provides the data to run a shortest path analysis.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEShortestPath``()`       |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                              | Method and Description                                                                                                     |
    |------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
    | [`AnalysisCost`](AnalysisCost.md)              | `getAnalysisCost``()`<br>Returns the analysis cost.                                                                        |
    | [`NFEFeature`](../model/feature/NFEFeature.md) | `getNFEEndFeature``()`<br>Returns the end feature.                                                                         |
    | [`NFEFeature`](../model/feature/NFEFeature.md) | `getNFEStartFeature``()`<br>Returns the start feature.                                                                     |
    | `java.lang.Boolean`                            | `getReverseDirection``()`<br>Returns true to use reverse search direction, false otherwise.                                |
    | `void`                                         | `setAnalysisCost``(`[`AnalysisCost`](AnalysisCost.md)` analysisCost)`<br>Sets the analysis cost.                           |
    | `void`                                         | `setNFEEndFeature``(`[`NFEFeature`](../model/feature/NFEFeature.md)` nfeEndFeature)`<br>Sets the end feature.              |
    | `void`                                         | `setNFEStartFeature``(`[`NFEFeature`](../model/feature/NFEFeature.md)` nfeStartFeature)`<br>Sets the start feature.        |
    | `void`                                         | `setReverseDirection``(java.lang.Boolean reverseDirection)`<br>Sets true to use reverse search direction, false otherwise. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEShortestPath

          public NFEShortestPath()

  <!-- -->

  - ### Method Detail

    - #### getAnalysisCost

          public AnalysisCost getAnalysisCost()

      Returns the analysis cost.
      Returns:
      analysis cost

    <!-- -->

    - #### setAnalysisCost

          public void setAnalysisCost(AnalysisCost analysisCost)

      Sets the analysis cost.
      Parameters:
      `analysisCost` - analysis cost

    <!-- -->

    - #### getNFEStartFeature

          public NFEFeature getNFEStartFeature()

      Returns the start feature.
      Returns:
      start feature

    <!-- -->

    - #### setNFEStartFeature

          public void setNFEStartFeature(NFEFeature nfeStartFeature)

      Sets the start feature.
      Parameters:
      `nfeStartFeature` - start feature

    <!-- -->

    - #### getNFEEndFeature

          public NFEFeature getNFEEndFeature()

      Returns the end feature.
      Returns:
      end feature

    <!-- -->

    - #### setNFEEndFeature

          public void setNFEEndFeature(NFEFeature nfeEndFeature)

      Sets the end feature.
      Parameters:
      `nfeEndFeature` - end feature

    <!-- -->

    - #### getReverseDirection

          public java.lang.Boolean getReverseDirection()

      Returns true to use reverse search direction, false otherwise.
      Returns:
      true to use reverse search direction, false otherwise.

    <!-- -->

    - #### setReverseDirection

          public void setReverseDirection(java.lang.Boolean reverseDirection)

      Sets true to use reverse search direction, false otherwise.
      Parameters:
      `reverseDirection` - true to use reverse search direction, false otherwise.

Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFESearchParams.md)
- [Next Class](NFETsp.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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
