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

- [Prev Class](NFEFeatureIOService.md)
- [Next Class](NFEIOServiceProvider.md)

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

## Interface NFEIOService

- All Known Subinterfaces:
  [NFEAnalysisIOService](NFEAnalysisIOService.md), [NFEFeatureIOService](NFEFeatureIOService.md), [NFEModelIOService](NFEModelIOService.md), [NFEWorkspaceIOService](NFEWorkspaceIOService.md)

  <!-- -->

  All Known Implementing Classes:
  [JDBCAbstractIOService](../jdbc/service/JDBCAbstractIOService.md), [JDBCAnalysisIOService](../jdbc/service/JDBCAnalysisIOService.md), [JDBCFeatureIOService](../jdbc/service/JDBCFeatureIOService.md), [JDBCModelIOService](../jdbc/service/JDBCModelIOService.md), [JDBCWorkspaceIOService](../jdbc/service/JDBCWorkspaceIOService.md)

  ------------------------------------------------------------------------



      public interface NFEIOService

  This interface defines methods supported by the NFE services to access the NFE model and the data source.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                 | Method and Description                                                                              |
    |---------------------------------------------------|-----------------------------------------------------------------------------------------------------|
    | [`NFEDataSource`](../NFEDataSource.md)            | `getDataSource``()`<br>Returns the NFE data source.                                                 |
    | [`NFEModel`](../../model/NFEModel.md)             | `getModel``()`<br>Returns the NFE model.                                                            |
    | [`NFEIOServiceProvider`](NFEIOServiceProvider.md) | `getServiceProvider``()`<br>Returns the service provider.                                           |
    | `void`                                            | `setDataSource``(`[`NFEDataSource`](../NFEDataSource.md)` dataSource)`<br>Sets the NFE data source. |
    | `void`                                            | `setModel``(`[`NFEModel`](../../model/NFEModel.md)` model)`<br>Sets the NFE model.                  |

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

      Returns the NFE model.
      Returns:
      NFE model

    <!-- -->

    - #### setDataSource

          void setDataSource(NFEDataSource dataSource)

      Sets the NFE data source.
      Parameters:
      `dataSource` - NFE data source

    <!-- -->

    - #### getDataSource

          NFEDataSource getDataSource()

      Returns the NFE data source.
      Returns:
      NFE data source

    <!-- -->

    - #### getServiceProvider

          NFEIOServiceProvider getServiceProvider()

      Returns the service provider.
      Returns:
      service provider

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

- [Prev Class](NFEFeatureIOService.md)
- [Next Class](NFEIOServiceProvider.md)

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
