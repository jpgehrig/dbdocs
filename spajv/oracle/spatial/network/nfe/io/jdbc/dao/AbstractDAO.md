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
- [Next Class](FeatureDAO.md)

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

oracle.spatial.network.nfe.io.jdbc.dao

## Class AbstractDAO

- java.lang.Object

- - oracle.spatial.network.nfe.io.jdbc.dao.AbstractDAO

<!-- -->

- Direct Known Subclasses:
  [FeatureDAO](FeatureDAO.md), [ModelDAO](ModelDAO.md), [NetworkDAO](NetworkDAO.md), [RuleDAO](RuleDAO.md), [SpatialDAO](SpatialDAO.md), [WorkspaceDAO](WorkspaceDAO.md)

  ------------------------------------------------------------------------



      public class AbstractDAO
      extends java.lang.Object

  A base class for data access objects (DAOs), providing methods to access the model and the connection.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                    |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `AbstractDAO``(java.sql.Connection conn, `[`NFEModel`](../../../model/NFEModel.md)` model)`<br>Creates an AbstractDAO with the specified connection and model. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                        | Method and Description                            |
    |------------------------------------------|---------------------------------------------------|
    | `java.sql.Connection`                    | `getConnection``()`<br>Returns the connection.    |
    | [`NFEModel`](../../../model/NFEModel.md) | `getModel``()`<br>Returns the model.              |
    | [`SQLValidator`](../SQLValidator.md)     | `getSQLValidator``()`<br>Returns the SQLValidator |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### AbstractDAO

          public AbstractDAO(java.sql.Connection conn,
                             NFEModel model)

      Creates an AbstractDAO with the specified connection and model.
      Parameters:
      `conn` - connection

      `model` - model

  <!-- -->

  - ### Method Detail

    - #### getConnection

          public java.sql.Connection getConnection()

      Returns the connection.
      Returns:
      connection

    <!-- -->

    - #### getModel

          public NFEModel getModel()

      Returns the model.
      Returns:
      model

    <!-- -->

    - #### getSQLValidator

          public SQLValidator getSQLValidator()

      Returns the SQLValidator
      Returns:
      sqlValidator

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
- [Next Class](FeatureDAO.md)

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
