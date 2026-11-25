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

- [Prev Class](NFEIOService.md)
- [Next Class](NFEModelIOService.md)

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

## Interface NFEIOServiceProvider

- All Known Implementing Classes:
  [JDBCIOServiceProvider](../jdbc/service/JDBCIOServiceProvider.md)

  ------------------------------------------------------------------------



      public interface NFEIOServiceProvider

  This interface defines the single entry point to access NFE services.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                   | Method and Description                                                                          |
    |-----------------------------------------------------|-------------------------------------------------------------------------------------------------|
    | [`NFEAnalysisIOService`](NFEAnalysisIOService.md)   | `getAnalysisService``()`<br>Returns analysis service.                                           |
    | [`NFEDataSource`](../NFEDataSource.md)              | `getDataSource``()`<br>Returns NFE data source.                                                 |
    | [`NFEFeatureIOService`](NFEFeatureIOService.md)     | `getFeatureService``()`<br>Returns the feature service.                                         |
    | [`NFEModel`](../../model/NFEModel.md)               | `getModel``()`<br>Returns NFE model.                                                            |
    | [`NFEModelIOService`](NFEModelIOService.md)         | `getModelService``()`<br>Returns the model service.                                             |
    | [`NFEWorkspaceIOService`](NFEWorkspaceIOService.md) | `getWorkspaceService``()`<br>Returns workspace service.                                         |
    | `void`                                              | `setDataSource``(`[`NFEDataSource`](../NFEDataSource.md)` dataSource)`<br>Sets NFE data source. |
    | `void`                                              | `setModel``(`[`NFEModel`](../../model/NFEModel.md)` model)`<br>Sets the NFE model.              |

<!-- -->

- - ### Method Detail

    - #### setModel

          void setModel(NFEModel model)

      Sets the NFE model.
      Parameters:
      `model` - NFE model

    <!-- -->

    - #### getModel

          NFEModel getModel()

      Returns NFE model.
      Returns:
      NFE model

    <!-- -->

    - #### setDataSource

          void setDataSource(NFEDataSource dataSource)

      Sets NFE data source.
      Parameters:
      `dataSource` - NFE data source

    <!-- -->

    - #### getDataSource

          NFEDataSource getDataSource()

      Returns NFE data source.
      Returns:
      NFE data source

    <!-- -->

    - #### getModelService

          NFEModelIOService getModelService()

      Returns the model service.
      Returns:
      model service

    <!-- -->

    - #### getFeatureService

          NFEFeatureIOService getFeatureService()

      Returns the feature service.
      Returns:
      feature service

    <!-- -->

    - #### getWorkspaceService

          NFEWorkspaceIOService getWorkspaceService()

      Returns workspace service.
      Returns:
      workspace service

    <!-- -->

    - #### getAnalysisService

          NFEAnalysisIOService getAnalysisService()

      Returns analysis service.
      Returns:
      analysis service

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

- [Prev Class](NFEIOService.md)
- [Next Class](NFEModelIOService.md)

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
