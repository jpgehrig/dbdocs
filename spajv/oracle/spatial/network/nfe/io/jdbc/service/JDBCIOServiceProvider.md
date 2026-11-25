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

- [Prev Class](JDBCFeatureIOService.md)
- [Next Class](JDBCModelIOService.md)

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

## Class JDBCIOServiceProvider

- java.lang.Object

- - oracle.spatial.network.nfe.io.jdbc.service.JDBCIOServiceProvider

<!-- -->

- All Implemented Interfaces:
  [NFEIOServiceProvider](../../service/NFEIOServiceProvider.md)

  ------------------------------------------------------------------------



      public class JDBCIOServiceProvider
      extends java.lang.Object
      implements NFEIOServiceProvider

  Provides the default implementation for the service provider.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description  |
    |------------------------------|
    | `JDBCIOServiceProvider``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                 | Method and Description                                                                             |
    |-------------------------------------------------------------------|----------------------------------------------------------------------------------------------------|
    | [`NFEAnalysisIOService`](../../service/NFEAnalysisIOService.md)   | `getAnalysisService``()`<br>Returns analysis service.                                              |
    | [`NFEDataSource`](../../NFEDataSource.md)                         | `getDataSource``()`<br>Returns NFE data source.                                                    |
    | [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)     | `getFeatureService``()`<br>Returns the feature service.                                            |
    | [`NFEModel`](../../../model/NFEModel.md)                          | `getModel``()`<br>Returns NFE model.                                                               |
    | [`NFEModelIOService`](../../service/NFEModelIOService.md)         | `getModelService``()`<br>Returns the model service.                                                |
    | [`NFEWorkspaceIOService`](../../service/NFEWorkspaceIOService.md) | `getWorkspaceService``()`<br>Returns workspace service.                                            |
    | `void`                                                            | `setDataSource``(`[`NFEDataSource`](../../NFEDataSource.md)` dataSource)`<br>Sets NFE data source. |
    | `void`                                                            | `setModel``(`[`NFEModel`](../../../model/NFEModel.md)` model)`<br>Sets the NFE model.              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### JDBCIOServiceProvider

          public JDBCIOServiceProvider()

  <!-- -->

  - ### Method Detail

    - #### setModel

          public void setModel(NFEModel model)

      Description copied from interface: [`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)
      Sets the NFE model.
      Specified by:
      [`setModel`](../../service/NFEIOServiceProvider.md) in interface [`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)

      Parameters:
      `model` - NFE model

    <!-- -->

    - #### getModel

          public NFEModel getModel()

      Description copied from interface: [`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)
      Returns NFE model.
      Specified by:
      [`getModel`](../../service/NFEIOServiceProvider.md) in interface [`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)

      Returns:
      NFE model

    <!-- -->

    - #### setDataSource

          public void setDataSource(NFEDataSource dataSource)

      Description copied from interface: [`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)
      Sets NFE data source.
      Specified by:
      [`setDataSource`](../../service/NFEIOServiceProvider.md) in interface [`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)

      Parameters:
      `dataSource` - NFE data source

    <!-- -->

    - #### getDataSource

          public NFEDataSource getDataSource()

      Description copied from interface: [`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)
      Returns NFE data source.
      Specified by:
      [`getDataSource`](../../service/NFEIOServiceProvider.md) in interface [`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)

      Returns:
      NFE data source

    <!-- -->

    - #### getModelService

          public NFEModelIOService getModelService()

      Description copied from interface: [`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)
      Returns the model service.
      Specified by:
      [`getModelService`](../../service/NFEIOServiceProvider.md) in interface [`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)

      Returns:
      model service

    <!-- -->

    - #### getFeatureService

          public NFEFeatureIOService getFeatureService()

      Description copied from interface: [`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)
      Returns the feature service.
      Specified by:
      [`getFeatureService`](../../service/NFEIOServiceProvider.md) in interface [`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)

      Returns:
      feature service

    <!-- -->

    - #### getWorkspaceService

          public NFEWorkspaceIOService getWorkspaceService()

      Description copied from interface: [`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)
      Returns workspace service.
      Specified by:
      [`getWorkspaceService`](../../service/NFEIOServiceProvider.md) in interface [`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)

      Returns:
      workspace service

    <!-- -->

    - #### getAnalysisService

          public NFEAnalysisIOService getAnalysisService()

      Description copied from interface: [`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)
      Returns analysis service.
      Specified by:
      [`getAnalysisService`](../../service/NFEIOServiceProvider.md) in interface [`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)

      Returns:
      analysis service

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

- [Prev Class](JDBCFeatureIOService.md)
- [Next Class](JDBCModelIOService.md)

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
