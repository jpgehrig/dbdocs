Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](NFEFeatureIOService.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.io.service

## Interface NFEAnalysisIOService

- All Superinterfaces:
  [NFEIOService](NFEIOService.md)

  <!-- -->

  All Known Implementing Classes:
  [JDBCAnalysisIOService](../jdbc/service/JDBCAnalysisIOService.md)

  ------------------------------------------------------------------------



      public interface NFEAnalysisIOService
      extends NFEIOService

  This interface is the entry point to the feature analysis operations supported by NFE.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                     | Method and Description                                                                                                                                                                                                                                                                                                                                             |
    |-----------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                | `deletePath``(`[`NFEFeature`](../../model/feature/NFEFeature.md)` nfeFeature)`<br>Deletes feature path.                                                                                                                                                                                                                                                            |
    | `java.util.List<`[`NFEFeature`](../../model/feature/NFEFeature.md)`>` | `runNearestNeighbors``(`[`NFENearestNeighbors`](../../beans/NFENearestNeighbors.md)` nearestNeighbors, boolean useCachedNetwork, `[`NFEExpressionAnalyzer`](../../expression/NFEExpressionAnalyzer.md)` nfeExpressionAnalyzer, `[`LODNetworkConstraint`](../../../lod/LODNetworkConstraint.md)` constraint)`<br>Finds the nearest features from the start feature. |
    | [`NFEFeature`](../../model/feature/NFEFeature.md)                     | `runShortestPath``(`[`NFEShortestPath`](../../beans/NFEShortestPath.md)` shortestPath, boolean useCachedNetwork, `[`NFEExpressionAnalyzer`](../../expression/NFEExpressionAnalyzer.md)` nfeExpressionAnalyzer, `[`LODNetworkConstraint`](../../../lod/LODNetworkConstraint.md)` constraint)`<br>Finds the shortest path from the start feature to the end feature. |
    | `java.util.List<`[`NFEFeature`](../../model/feature/NFEFeature.md)`>` | `runTSP``(`[`NFETsp`](../../beans/NFETsp.md)` nfeTsp, boolean useCachedNetwork, `[`NFEExpressionAnalyzer`](../../expression/NFEExpressionAnalyzer.md)` nfeExpressionAnalyzer, `[`LODNetworkConstraint`](../../../lod/LODNetworkConstraint.md)` constraint)`<br>Returns the traveling salesman tour covering the input features.                                    |
    | `java.util.List<`[`NFEFeature`](../../model/feature/NFEFeature.md)`>` | `runWithinCost``(`[`NFEWithinCost`](../../beans/NFEWithinCost.md)` withinCost, boolean useCachedNetwork, `[`NFEExpressionAnalyzer`](../../expression/NFEExpressionAnalyzer.md)` nfeExpressionAnalyzer, `[`LODNetworkConstraint`](../../../lod/LODNetworkConstraint.md)` constraint)`<br>Finds features within the given cost from the start feature.               |
    | `void`                                                                | `savePaths``(java.util.List<`[`NFEFeature`](../../model/feature/NFEFeature.md)`> featureList)`<br>Saves feature paths.                                                                                                                                                                                                                                             |

    - ### Methods inherited from interface oracle.spatial.network.nfe.io.service.[NFEIOService](NFEIOService.md)

      [`getDataSource`](NFEIOService.md)`, `[`getModel`](NFEIOService.md)`, `[`getServiceProvider`](NFEIOService.md)`, `[`setDataSource`](NFEIOService.md)`, `[`setModel`](NFEIOService.md)

<!-- -->

- - ### Method Detail

    - #### savePaths

          void savePaths(java.util.List<NFEFeature> featureList)
                  throws NFEIOException

      Saves feature paths.
      Parameters:
      `featureList` - list of the feature paths to save

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deletePath

          void deletePath(NFEFeature nfeFeature)
                   throws NFEIOException

      Deletes feature path.
      Parameters:
      `nfeFeature` - path to delete

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### runShortestPath

          NFEFeature runShortestPath(NFEShortestPath shortestPath,
                                     boolean useCachedNetwork,
                                     NFEExpressionAnalyzer nfeExpressionAnalyzer,
                                     LODNetworkConstraint constraint)
                              throws NFEIOException

      Finds the shortest path from the start feature to the end feature. The start feature and the end feature can belong to different feature layers. Set shortestPath.setReverseDirection to true to use reverse search direction. Enable the analysis on the model before to use this function with modelService.enableAnalysisInModel.
      Parameters:
      `shortestPath` - shortest path analysis data

      `useCachedNetwork` - if true use a cached network, if false reload the needed network data

      `nfeExpressionAnalyzer` - needed in case of customized cost, the analyzer will be used to calculate the customized cost expression

      `constraint` - network constraint

      Returns:
      path feature representing the shortest path from the start feature to the end feature

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### runNearestNeighbors

          java.util.List<NFEFeature> runNearestNeighbors(NFENearestNeighbors nearestNeighbors,
                                                         boolean useCachedNetwork,
                                                         NFEExpressionAnalyzer nfeExpressionAnalyzer,
                                                         LODNetworkConstraint constraint)
                                                  throws NFEIOException

      Finds the nearest features from the start feature. The searched features will belong to the featureLayer specified in the NFENearestNeighbors object. For example if the feature layer is HOTEL and numberOfNeighbors is 5 then the analysis will find the 5 nearest hotels. Enable the analysis on the model before to use this function with modelService.enableAnalysisInModel.
      Parameters:
      `nearestNeighbors` - nearest neighbor analysis data

      `useCachedNetwork` - if true use a cached network, if false reload the needed network data

      `nfeExpressionAnalyzer` - needed in case of customized cost, the analyzer will be used to calculate the customized cost expression

      `constraint` - network constraint

      Returns:
      path features representing the shortest paths from a start feature to the nearest neighbors

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### runWithinCost

          java.util.List<NFEFeature> runWithinCost(NFEWithinCost withinCost,
                                                   boolean useCachedNetwork,
                                                   NFEExpressionAnalyzer nfeExpressionAnalyzer,
                                                   LODNetworkConstraint constraint)
                                            throws NFEIOException

      Finds features within the given cost from the start feature. The searched features will belong to the featureLayer specified in the NFEWithinCost object. Enable the analysis on the model before to use this function with modelService.enableAnalysisInModel.
      Parameters:
      `withinCost` - within cost analysis data

      `useCachedNetwork` - if true use a cached network, if false reload the needed network data

      `nfeExpressionAnalyzer` - needed in case of customized cost, the analyzer will be used to calculate the customized cost expression

      `constraint` - network constraint

      Returns:
      path features representing the shortest paths from a start feature to the features within the given cost

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### runTSP

          java.util.List<NFEFeature> runTSP(NFETsp nfeTsp,
                                            boolean useCachedNetwork,
                                            NFEExpressionAnalyzer nfeExpressionAnalyzer,
                                            LODNetworkConstraint constraint)
                                     throws NFEIOException

      Returns the traveling salesman tour covering the input features. Enable the analysis on the model before to use this function with modelService.enableAnalysisInModel.
      Parameters:
      `nfeTsp` - TSP analysis data

      `useCachedNetwork` - if true use a cached network, if false reload the needed network data

      `nfeExpressionAnalyzer` - needed in case of customized cost, the analyzer will be used to calculate the customized cost expression

      `constraint` - network constraint

      Returns:
      traveling salesman tour

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](NFEFeatureIOService.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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
