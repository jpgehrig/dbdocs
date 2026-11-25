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

- Prev Class
- [Next Class](JDBCAnalysisIOService.md)

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

## Class JDBCAbstractIOService

- java.lang.Object

- - oracle.spatial.network.nfe.io.jdbc.service.JDBCAbstractIOService

<!-- -->

- All Implemented Interfaces:
  [NFEIOService](../../service/NFEIOService.md)

  <!-- -->

  Direct Known Subclasses:
  [JDBCAnalysisIOService](JDBCAnalysisIOService.md), [JDBCFeatureIOService](JDBCFeatureIOService.md), [JDBCModelIOService](JDBCModelIOService.md), [JDBCWorkspaceIOService](JDBCWorkspaceIOService.md)

  ------------------------------------------------------------------------



      public abstract class JDBCAbstractIOService
      extends java.lang.Object
      implements NFEIOService

  Provides default implementation of some methods shared by all the services.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                   |
    |---------------------------------------------------------------------------------------------------------------|
    | `JDBCAbstractIOService``(`[`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)` serviceProvider)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                               | Method and Description                                                                                 |
    |-----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
    | [`NFEDataSource`](../../NFEDataSource.md)                       | `getDataSource``()`<br>Returns the NFE data source.                                                    |
    | [`NFEModel`](../../../model/NFEModel.md)                        | `getModel``()`<br>Returns the NFE model.                                                               |
    | [`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md) | `getServiceProvider``()`<br>Returns the service provider.                                              |
    | `void`                                                          | `setDataSource``(`[`NFEDataSource`](../../NFEDataSource.md)` dataSource)`<br>Sets the NFE data source. |
    | `void`                                                          | `setModel``(`[`NFEModel`](../../../model/NFEModel.md)` model)`<br>Sets the NFE model.                  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### JDBCAbstractIOService

          public JDBCAbstractIOService(NFEIOServiceProvider serviceProvider)

  <!-- -->

  - ### Method Detail

    - #### setModel

          public void setModel(NFEModel model)

      Description copied from interface: [`NFEIOService`](../../service/NFEIOService.md)
      Sets the NFE model.
      Specified by:
      [`setModel`](../../service/NFEIOService.md) in interface [`NFEIOService`](../../service/NFEIOService.md)

      Parameters:
      `model` - NFE model

    <!-- -->

    - #### getModel

          public NFEModel getModel()

      Description copied from interface: [`NFEIOService`](../../service/NFEIOService.md)
      Returns the NFE model.
      Specified by:
      [`getModel`](../../service/NFEIOService.md) in interface [`NFEIOService`](../../service/NFEIOService.md)

      Returns:
      NFE model

    <!-- -->

    - #### setDataSource

          public void setDataSource(NFEDataSource dataSource)

      Description copied from interface: [`NFEIOService`](../../service/NFEIOService.md)
      Sets the NFE data source.
      Specified by:
      [`setDataSource`](../../service/NFEIOService.md) in interface [`NFEIOService`](../../service/NFEIOService.md)

      Parameters:
      `dataSource` - NFE data source

    <!-- -->

    - #### getDataSource

          public NFEDataSource getDataSource()

      Description copied from interface: [`NFEIOService`](../../service/NFEIOService.md)
      Returns the NFE data source.
      Specified by:
      [`getDataSource`](../../service/NFEIOService.md) in interface [`NFEIOService`](../../service/NFEIOService.md)

      Returns:
      NFE data source

    <!-- -->

    - #### getServiceProvider

          public NFEIOServiceProvider getServiceProvider()

      Description copied from interface: [`NFEIOService`](../../service/NFEIOService.md)
      Returns the service provider.
      Specified by:
      [`getServiceProvider`](../../service/NFEIOService.md) in interface [`NFEIOService`](../../service/NFEIOService.md)

      Returns:
      service provider

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

- Prev Class
- [Next Class](JDBCAnalysisIOService.md)

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
