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

- [Prev Class](NFETsp.md)
- [Next Class](NFEWorkspace.md)

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

## Class NFEWithinCost

- java.lang.Object

- - oracle.spatial.network.nfe.beans.NFEWithinCost

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFEWithinCost
      extends java.lang.Object

  Provides the data to run a within cost analysis.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEWithinCost``()`         |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                        | Method and Description                                                                                                                                  |
    |----------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`AnalysisCost`](AnalysisCost.md)                        | `getAnalysisCost``()`<br>Returns the analysis cost.                                                                                                     |
    | `double`                                                 | `getCostRange``()`<br>Returns the cost range.                                                                                                           |
    | [`NFEFeatureLayer`](../model/feature/NFEFeatureLayer.md) | `getNFEFeatureLayer``()`<br>Returns the feature layer to search in the analysis.                                                                        |
    | [`NFEFeature`](../model/feature/NFEFeature.md)           | `getNFEStartFeature``()`<br>Returns the start feature.                                                                                                  |
    | `void`                                                   | `setAnalysisCost``(`[`AnalysisCost`](AnalysisCost.md)` analysisCost)`<br>Sets the analysis cost.                                                        |
    | `void`                                                   | `setCostRange``(double costRange)`<br>Sets the cost range.                                                                                              |
    | `void`                                                   | `setNFEFeatureLayer``(`[`NFEFeatureLayer`](../model/feature/NFEFeatureLayer.md)` nfeFeatureLayer)`<br>Sets the feature layer to search in the analysis. |
    | `void`                                                   | `setNFEStartFeature``(`[`NFEFeature`](../model/feature/NFEFeature.md)` nfeStartFeature)`<br>Sets the start feature.                                     |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEWithinCost

          public NFEWithinCost()

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

      Returns the feature layer to search in the analysis. Only the feature in this feature layer will included in the search.
      Returns:
      feature layer to search in the analysis

    <!-- -->

    - #### setNFEFeatureLayer

          public void setNFEFeatureLayer(NFEFeatureLayer nfeFeatureLayer)

      Sets the feature layer to search in the analysis. Only the feature in this feature layer will included in the search.
      Parameters:
      `nfeFeatureLayer` - feature layer to search in the analysis

    <!-- -->

    - #### getCostRange

          public double getCostRange()

      Returns the cost range.
      Returns:
      cost range

    <!-- -->

    - #### setCostRange

          public void setCostRange(double costRange)

      Sets the cost range.
      Parameters:
      `costRange` - cost range

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

- [Prev Class](NFETsp.md)
- [Next Class](NFEWorkspace.md)

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
