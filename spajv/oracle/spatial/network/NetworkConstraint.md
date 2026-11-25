Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](Network.md)
- [Next Class](NetworkDataException.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.spatial.network

## Interface NetworkConstraint

- All Superinterfaces:
  java.lang.Cloneable, java.io.Serializable

  <!-- -->

  All Known Implementing Classes:
  [SystemConstraint](SystemConstraint.md)

  ------------------------------------------------------------------------



      public interface NetworkConstraint
      extends java.lang.Cloneable, java.io.Serializable

  This interface defines a general network constraint for network analysis. A network constraint at the node level means that only the current node and the currrent link are considered. A network constraint at the path level means that some or all path information is considered during the search. Note the constraint is checked during the search and implemented by the users.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                              |
    |-------------------|-----------------------------------------------------------------------------------------------------|
    | `boolean`         | `isSatisfied``(`[`AnalysisInfo`](AnalysisInfo.md)` info)`<br>Checks if the constraint is satisfied. |
    | `boolean`         | `requiresPathLinks``()`<br>Returns true if the constraint requires some or all path information.    |

<!-- -->

- - ### Method Detail

    - #### requiresPathLinks

          boolean requiresPathLinks()

      Returns true if the constraint requires some or all path information.

    <!-- -->

    - #### isSatisfied

          boolean isSatisfied(AnalysisInfo info)

      Checks if the constraint is satisfied.
      Parameters:
      `info` - the analysis information for the network constraint

      See Also:
      [`AnalysisInfo`](AnalysisInfo.md)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](Network.md)
- [Next Class](NetworkDataException.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
