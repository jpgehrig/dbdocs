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

- [Prev Class](NFEShortestPath.md)
- [Next Class](NFEWithinCost.md)

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

## Class NFETsp

- java.lang.Object

- - oracle.spatial.network.nfe.beans.NFETsp

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFETsp
      extends java.lang.Object

  Provides the data to run the traveling salesman tour analysis.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFETsp``()`                |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                  | Method and Description                                                                                                                                                                                                       |
    |--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`AnalysisCost`](AnalysisCost.md)                                  | `getAnalysisCost``()`<br>Returns the analysis cost.                                                                                                                                                                          |
    | `java.util.List<`[`NFEFeature`](../model/feature/NFEFeature.md)`>` | `getFeatureList``()`<br>Returns the features to visit on the tour.                                                                                                                                                           |
    | [`TSP.TourFlag`](../../lod/TSP.TourFlag.md)                        | `getTourFlag``()`<br>Returns a flag indicating whether the tour should be open or closed, and if the tour is open, whether the tour should have fixed start or end point.                                                    |
    | `void`                                                             | `setAnalysisCost``(`[`AnalysisCost`](AnalysisCost.md)` analysisCost)`<br>Sets the analysis cost.                                                                                                                             |
    | `void`                                                             | `setFeatureList``(java.util.List<`[`NFEFeature`](../model/feature/NFEFeature.md)`> featureList)`<br>Sets the features to visit on the tour.                                                                                  |
    | `void`                                                             | `setTourFlag``(`[`TSP.TourFlag`](../../lod/TSP.TourFlag.md)` tourFlag)`<br>Sets a flag indicating whether the tour should be open or closed, and if the tour is open, whether the tour should have fixed start or end point. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFETsp

          public NFETsp()

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

    - #### getFeatureList

          public java.util.List<NFEFeature> getFeatureList()

      Returns the features to visit on the tour.
      Returns:
      features to visit on the tour

    <!-- -->

    - #### setFeatureList

          public void setFeatureList(java.util.List<NFEFeature> featureList)

      Sets the features to visit on the tour.
      Parameters:
      `featureList` - the features to visit on the tour.

    <!-- -->

    - #### getTourFlag

          public TSP.TourFlag getTourFlag()

      Returns a flag indicating whether the tour should be open or closed, and if the tour is open, whether the tour should have fixed start or end point.
      Returns:
      flag indicating whether the tour should be open or closed, and if the tour is open, whether the tour should have fixed start or end point.

    <!-- -->

    - #### setTourFlag

          public void setTourFlag(TSP.TourFlag tourFlag)

      Sets a flag indicating whether the tour should be open or closed, and if the tour is open, whether the tour should have fixed start or end point.
      Parameters:
      `tourFlag` - flag indicating whether the tour should be open or closed, and if the tour is open, whether the tour should have fixed start or end point.

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

- [Prev Class](NFEShortestPath.md)
- [Next Class](NFEWithinCost.md)

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
