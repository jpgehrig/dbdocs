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

- [Prev Class](AnalysisCustomizedCost.md)
- [Next Class](NFESearchParams.md)

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

## Class NFENearestNeighbors

- java.lang.Object

- - oracle.spatial.network.nfe.beans.NFENearestNeighbors

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFENearestNeighbors
      extends java.lang.Object

  Provides the data to run a nearest neighbor analysis.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFENearestNeighbors``()`   |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                        | Method and Description                                                                                                                                |
    |----------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`AnalysisCost`](AnalysisCost.md)                        | `getAnalysisCost``()`<br>Returns the analysis cost.                                                                                                   |
    | [`NFEFeatureLayer`](../model/feature/NFEFeatureLayer.md) | `getNFEFeatureLayer``()`<br>Returns the feature layer to search for neighbors.                                                                        |
    | [`NFEFeature`](../model/feature/NFEFeature.md)           | `getNFEStartFeature``()`<br>Returns the start feature.                                                                                                |
    | `int`                                                    | `getNumberOfNeighbors``()`<br>Returns the number of neighbors to be returned.                                                                         |
    | `void`                                                   | `setAnalysisCost``(`[`AnalysisCost`](AnalysisCost.md)` analysisCost)`<br>Sets the analysis cost.                                                      |
    | `void`                                                   | `setNFEFeatureLayer``(`[`NFEFeatureLayer`](../model/feature/NFEFeatureLayer.md)` nfeFeatureLayer)`<br>Sets the feature layer to search for neighbors. |
    | `void`                                                   | `setNFEStartFeature``(`[`NFEFeature`](../model/feature/NFEFeature.md)` nfeStartFeature)`<br>Sets the start feature.                                   |
    | `void`                                                   | `setNumberOfNeighbors``(int numberOfNeighbors)`<br>Sets the number of neighbors to be returned.                                                       |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFENearestNeighbors

          public NFENearestNeighbors()

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

    - #### getNFEFeatureLayer

          public NFEFeatureLayer getNFEFeatureLayer()

      Returns the feature layer to search for neighbors. Only the feature in this feature layer will included in the search.
      Returns:
      feature layer to search for neighbors

    <!-- -->

    - #### setNFEFeatureLayer

          public void setNFEFeatureLayer(NFEFeatureLayer nfeFeatureLayer)

      Sets the feature layer to search for neighbors. Only the feature in this feature layer will included in the search.
      Parameters:
      `nfeFeatureLayer` - feature layer to search for neighbors

    <!-- -->

    - #### getNumberOfNeighbors

          public int getNumberOfNeighbors()

      Returns the number of neighbors to be returned.
      Returns:
      number of neighbors to be returned

    <!-- -->

    - #### setNumberOfNeighbors

          public void setNumberOfNeighbors(int numberOfNeighbors)

      Sets the number of neighbors to be returned.
      Parameters:
      `numberOfNeighbors` - number of neighbors to be returned

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

- [Prev Class](AnalysisCustomizedCost.md)
- [Next Class](NFESearchParams.md)

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
