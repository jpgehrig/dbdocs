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
- [Next Class](NFEConnectivityRule.md)

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

oracle.spatial.network.nfe.model.rule

## Class NFECardinalityRule

- java.lang.Object

- - oracle.spatial.network.nfe.model.rule.NFECardinalityRule

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFECardinalityRule
      extends java.lang.Object

  Represents a cardinality rule associated to a feature layer and (optionally) a point feature class

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                           |
    |-------------------|-------------------------------------------------|
    | `static int`      | `CARDINALITY_UNBOUNDED`<br>No cardinality limit |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                         |
    |---------------------------------------------------------------------|
    | `NFECardinalityRule``(long id)`<br>Allocates a new cardinality rule |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                           |
    |-------------------|------------------------------------------------------------------------------------------------------------------|
    | `long`            | `getFeatureClassId``()`<br>Gets the feature class id for which the rule is applicable                            |
    | `long`            | `getFeatureLayerId``()`<br>Gets the feature layer id for which the rule is applicable                            |
    | `long`            | `getId``()`<br>Gets the cardinality rule id                                                                      |
    | `int`             | `getMaxInConnections``()`<br>Gets the maximum number of incoming connections defined by this rule                |
    | `int`             | `getMaxOutConnections``()`<br>Gets the maximum number of outgoing connections defined by this rule               |
    | `void`            | `setFeatureClassId``(long featClassId)`<br>Sets the feature class id for which the rule is applicable            |
    | `void`            | `setFeatureLayerId``(long featLayerId)`<br>Sets the feature layer id for which the rule is applicable            |
    | `void`            | `setId``(long id)`<br>Sets the cardinality rule id                                                               |
    | `void`            | `setMaxInConnections``(int maxInConn)`<br>Sets the maximum number of incoming connections defined by this rule   |
    | `void`            | `setMaxOutConnections``(int maxOutConn)`<br>Sets the maximum number of outgoing connections defined by this rule |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### CARDINALITY_UNBOUNDED

          public static final int CARDINALITY_UNBOUNDED

      No cardinality limit
      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### NFECardinalityRule

          public NFECardinalityRule(long id)

      Allocates a new cardinality rule
      Parameters:
      `id` - the cardinality rule id

  <!-- -->

  - ### Method Detail

    - #### getId

          public long getId()

      Gets the cardinality rule id
      Returns:
      the cardinality rule id

    <!-- -->

    - #### setId

          public void setId(long id)

      Sets the cardinality rule id
      Parameters:
      `id` - the cardinality rule id

    <!-- -->

    - #### getFeatureLayerId

          public long getFeatureLayerId()

      Gets the feature layer id for which the rule is applicable
      Returns:
      a feature layer id

    <!-- -->

    - #### setFeatureLayerId

          public void setFeatureLayerId(long featLayerId)

      Sets the feature layer id for which the rule is applicable
      Parameters:
      `featLayerId` - a feature layer id

    <!-- -->

    - #### getFeatureClassId

          public long getFeatureClassId()

      Gets the feature class id for which the rule is applicable
      Returns:
      a point feature class id

    <!-- -->

    - #### setFeatureClassId

          public void setFeatureClassId(long featClassId)

      Sets the feature class id for which the rule is applicable
      Parameters:
      `featClassId` - a point feature class id or

    <!-- -->

    - #### getMaxInConnections

          public int getMaxInConnections()

      Gets the maximum number of incoming connections defined by this rule
      Returns:
      the maximum number of incoming connections

    <!-- -->

    - #### setMaxInConnections

          public void setMaxInConnections(int maxInConn)

      Sets the maximum number of incoming connections defined by this rule
      Parameters:
      `maxInConn` - the maximum number of incoming connections

    <!-- -->

    - #### getMaxOutConnections

          public int getMaxOutConnections()

      Gets the maximum number of outgoing connections defined by this rule
      Returns:
      the maximum number of outgoing connections

    <!-- -->

    - #### setMaxOutConnections

          public void setMaxOutConnections(int maxOutConn)

      Sets the maximum number of outgoing connections defined by this rule
      Parameters:
      `maxOutConn` - the maximum number of outgoing connections

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
- [Next Class](NFEConnectivityRule.md)

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
