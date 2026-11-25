Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](VrpPath.md)
- [Next Class](YenDeviation.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.spatial.network.lod

## Interface XMLConfigurable

- All Known Implementing Classes:
  [AStar](AStar.md), [DefaultPairwiseCostCalculator](DefaultPairwiseCostCalculator.md), [DefaultPairwiseShortestPaths](DefaultPairwiseShortestPaths.md), [Dijkstra](Dijkstra.md), [DynamicLinkLevelSelector](DynamicLinkLevelSelector.md), [EuclideanCostFunction](EuclideanCostFunction.md), [GeodeticCostFunction](GeodeticCostFunction.md), [GeodeticPairwiseCostCalculator](GeodeticPairwiseCostCalculator.md), [TspOp2](TspOp2.md), [YenDeviation](YenDeviation.md)

  ------------------------------------------------------------------------



      public interface XMLConfigurable

  This interface defines methods that make a customized XML configuration implementation.
  Since:
  12.1

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                       |
    |--------------------|--------------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getXMLSchema``()`<br>Returns the XML schema for the input parameter.                                        |
    | `void`             | `init``(org.w3c.dom.Element parameter)`<br>Initializes the XML configurable object with the input parameter. |

<!-- -->

- - ### Method Detail

    - #### init

          void init(org.w3c.dom.Element parameter)

      Initializes the XML configurable object with the input parameter.
      Parameters:
      `parameter` - an XML element containing the necessary information to initialize the object.

    <!-- -->

    - #### getXMLSchema

          java.lang.String getXMLSchema()

      Returns the XML schema for the input parameter.
      Returns:

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](VrpPath.md)
- [Next Class](YenDeviation.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
