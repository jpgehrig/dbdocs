Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](JDBCAbstractIOService.md)
- [Next Class](JDBCFeatureIOService.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.io.jdbc.service

## Class JDBCAnalysisIOService

- java.lang.Object

- - [oracle.spatial.network.nfe.io.jdbc.service.JDBCAbstractIOService](JDBCAbstractIOService.md)

  - - oracle.spatial.network.nfe.io.jdbc.service.JDBCAnalysisIOService

<!-- -->

- All Implemented Interfaces:
  [NFEAnalysisIOService](../../service/NFEAnalysisIOService.md), [NFEIOService](../../service/NFEIOService.md)

  ------------------------------------------------------------------------



      public class JDBCAnalysisIOService
      extends JDBCAbstractIOService
      implements NFEAnalysisIOService

  Provides the default implementation for the analysis service.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                   |
    |---------------------------------------------------------------------------------------------------------------|
    | `JDBCAnalysisIOService``(`[`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)` serviceProvider)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                        | Method and Description                                                                                                                                                                                                                                                                                                                                                      |
    |--------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                   | `deletePath``(`[`NFEFeature`](../../../model/feature/NFEFeature.md)` nfeFeature)`<br>Deletes feature path.                                                                                                                                                                                                                                                                  |
    | `java.util.List<`[`NFEFeature`](../../../model/feature/NFEFeature.md)`>` | `runNearestNeighbors``(`[`NFENearestNeighbors`](../../../beans/NFENearestNeighbors.md)` nearestNeighbors, boolean useCachedNetwork, `[`NFEExpressionAnalyzer`](../../../expression/NFEExpressionAnalyzer.md)` nfeExpressionAnalyzer, `[`LODNetworkConstraint`](../../../../lod/LODNetworkConstraint.md)` constraint)`<br>Finds the nearest features from the start feature. |
    | [`NFEFeature`](../../../model/feature/NFEFeature.md)                     | `runShortestPath``(`[`NFEShortestPath`](../../../beans/NFEShortestPath.md)` shortestPath, boolean useCachedNetwork, `[`NFEExpressionAnalyzer`](../../../expression/NFEExpressionAnalyzer.md)` nfeExpressionAnalyzer, `[`LODNetworkConstraint`](../../../../lod/LODNetworkConstraint.md)` constraint)`<br>Finds the shortest path from the start feature to the end feature. |
    | `java.util.List<`[`NFEFeature`](../../../model/feature/NFEFeature.md)`>` | `runTSP``(`[`NFETsp`](../../../beans/NFETsp.md)` nfeTsp, boolean useCachedNetwork, `[`NFEExpressionAnalyzer`](../../../expression/NFEExpressionAnalyzer.md)` nfeExpressionAnalyzer, `[`LODNetworkConstraint`](../../../../lod/LODNetworkConstraint.md)` constraint)`<br>Returns the traveling salesman tour covering the input features.                                    |
    | `java.util.List<`[`NFEFeature`](../../../model/feature/NFEFeature.md)`>` | `runWithinCost``(`[`NFEWithinCost`](../../../beans/NFEWithinCost.md)` withinCost, boolean useCachedNetwork, `[`NFEExpressionAnalyzer`](../../../expression/NFEExpressionAnalyzer.md)` nfeExpressionAnalyzer, `[`LODNetworkConstraint`](../../../../lod/LODNetworkConstraint.md)` constraint)`<br>Finds features within the given cost from the start feature.               |
    | `void`                                                                   | `savePaths``(java.util.List<`[`NFEFeature`](../../../model/feature/NFEFeature.md)`> featureList)`<br>Saves feature paths.                                                                                                                                                                                                                                                   |

    - ### Methods inherited from class oracle.spatial.network.nfe.io.jdbc.service.[JDBCAbstractIOService](JDBCAbstractIOService.md)

      [`getDataSource`](JDBCAbstractIOService.md)`, `[`getModel`](JDBCAbstractIOService.md)`, `[`getServiceProvider`](JDBCAbstractIOService.md)`, `[`setDataSource`](JDBCAbstractIOService.md)`, `[`setModel`](JDBCAbstractIOService.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.io.service.[NFEIOService](../../service/NFEIOService.md)

      [`getDataSource`](../../service/NFEIOService.md)`, `[`getModel`](../../service/NFEIOService.md)`, `[`getServiceProvider`](../../service/NFEIOService.md)`, `[`setDataSource`](../../service/NFEIOService.md)`, `[`setModel`](../../service/NFEIOService.md)

<!-- -->

- - ### Constructor Detail

    - #### JDBCAnalysisIOService

          public JDBCAnalysisIOService(NFEIOServiceProvider serviceProvider)

  <!-- -->

  - ### Method Detail

    - #### savePaths

          public void savePaths(java.util.List<NFEFeature> featureList)
                         throws NFEIOException

      Description copied from interface: [`NFEAnalysisIOService`](../../service/NFEAnalysisIOService.md)
      Saves feature paths.
      Specified by:
      [`savePaths`](../../service/NFEAnalysisIOService.md) in interface [`NFEAnalysisIOService`](../../service/NFEAnalysisIOService.md)

      Parameters:
      `featureList` - list of the feature paths to save

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deletePath

          public void deletePath(NFEFeature nfeFeature)
                          throws NFEIOException

      Description copied from interface: [`NFEAnalysisIOService`](../../service/NFEAnalysisIOService.md)
      Deletes feature path.
      Specified by:
      [`deletePath`](../../service/NFEAnalysisIOService.md) in interface [`NFEAnalysisIOService`](../../service/NFEAnalysisIOService.md)

      Parameters:
      `nfeFeature` - path to delete

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### runShortestPath

          public NFEFeature runShortestPath(NFEShortestPath shortestPath,
                                            boolean useCachedNetwork,
                                            NFEExpressionAnalyzer nfeExpressionAnalyzer,
                                            LODNetworkConstraint constraint)
                                     throws NFEIOException

      Description copied from interface: [`NFEAnalysisIOService`](../../service/NFEAnalysisIOService.md)
      Finds the shortest path from the start feature to the end feature. The start feature and the end feature can belong to different feature layers. Set shortestPath.setReverseDirection to true to use reverse search direction. Enable the analysis on the model before to use this function with modelService.enableAnalysisInModel.
      Specified by:
      [`runShortestPath`](../../service/NFEAnalysisIOService.md) in interface [`NFEAnalysisIOService`](../../service/NFEAnalysisIOService.md)

      Parameters:
      `shortestPath` - shortest path analysis data

      `useCachedNetwork` - if true use a cached network, if false reload the needed network data

      `nfeExpressionAnalyzer` - needed in case of customized cost, the analyzer will be used to calculate the customized cost expression

      `constraint` - network constraint

      Returns:
      path feature representing the shortest path from the start feature to the end feature

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### runNearestNeighbors

          public java.util.List<NFEFeature> runNearestNeighbors(NFENearestNeighbors nearestNeighbors,
                                                                boolean useCachedNetwork,
                                                                NFEExpressionAnalyzer nfeExpressionAnalyzer,
                                                                LODNetworkConstraint constraint)
                                                         throws NFEIOException

      Description copied from interface: [`NFEAnalysisIOService`](../../service/NFEAnalysisIOService.md)
      Finds the nearest features from the start feature. The searched features will belong to the featureLayer specified in the NFENearestNeighbors object. For example if the feature layer is HOTEL and numberOfNeighbors is 5 then the analysis will find the 5 nearest hotels. Enable the analysis on the model before to use this function with modelService.enableAnalysisInModel.
      Specified by:
      [`runNearestNeighbors`](../../service/NFEAnalysisIOService.md) in interface [`NFEAnalysisIOService`](../../service/NFEAnalysisIOService.md)

      Parameters:
      `nearestNeighbors` - nearest neighbor analysis data

      `useCachedNetwork` - if true use a cached network, if false reload the needed network data

      `nfeExpressionAnalyzer` - needed in case of customized cost, the analyzer will be used to calculate the customized cost expression

      `constraint` - network constraint

      Returns:
      path features representing the shortest paths from a start feature to the nearest neighbors

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### runWithinCost

          public java.util.List<NFEFeature> runWithinCost(NFEWithinCost withinCost,
                                                          boolean useCachedNetwork,
                                                          NFEExpressionAnalyzer nfeExpressionAnalyzer,
                                                          LODNetworkConstraint constraint)
                                                   throws NFEIOException

      Description copied from interface: [`NFEAnalysisIOService`](../../service/NFEAnalysisIOService.md)
      Finds features within the given cost from the start feature. The searched features will belong to the featureLayer specified in the NFEWithinCost object. Enable the analysis on the model before to use this function with modelService.enableAnalysisInModel.
      Specified by:
      [`runWithinCost`](../../service/NFEAnalysisIOService.md) in interface [`NFEAnalysisIOService`](../../service/NFEAnalysisIOService.md)

      Parameters:
      `withinCost` - within cost analysis data

      `useCachedNetwork` - if true use a cached network, if false reload the needed network data

      `nfeExpressionAnalyzer` - needed in case of customized cost, the analyzer will be used to calculate the customized cost expression

      `constraint` - network constraint

      Returns:
      path features representing the shortest paths from a start feature to the features within the given cost

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### runTSP

          public java.util.List<NFEFeature> runTSP(NFETsp nfeTsp,
                                                   boolean useCachedNetwork,
                                                   NFEExpressionAnalyzer nfeExpressionAnalyzer,
                                                   LODNetworkConstraint constraint)
                                            throws NFEIOException

      Description copied from interface: [`NFEAnalysisIOService`](../../service/NFEAnalysisIOService.md)
      Returns the traveling salesman tour covering the input features. Enable the analysis on the model before to use this function with modelService.enableAnalysisInModel.
      Specified by:
      [`runTSP`](../../service/NFEAnalysisIOService.md) in interface [`NFEAnalysisIOService`](../../service/NFEAnalysisIOService.md)

      Parameters:
      `nfeTsp` - TSP analysis data

      `useCachedNetwork` - if true use a cached network, if false reload the needed network data

      `nfeExpressionAnalyzer` - needed in case of customized cost, the analyzer will be used to calculate the customized cost expression

      `constraint` - network constraint

      Returns:
      traveling salesman tour

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](JDBCAbstractIOService.md)
- [Next Class](JDBCFeatureIOService.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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
