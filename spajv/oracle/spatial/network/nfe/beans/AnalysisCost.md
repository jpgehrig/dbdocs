Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](AnalysisCustomizedCost.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.beans

## Class AnalysisCost

- java.lang.Object

- - oracle.spatial.network.nfe.beans.AnalysisCost

<!-- -->

-

  ------------------------------------------------------------------------



      public class AnalysisCost
      extends java.lang.Object

  An AnalysisCost describes the NFE analysis cost. The cost options are AnalysisCost.LINE_LENGTH (default) and AnalysisCost.CUSTOM. If AnalysisCost.LINE_LENGTH is chosen the costs that are defined in the node and link tables will be used, also it is possible to define the NodeCostCalculator and LinkCostCalculator. If AnalysisCost.CUSTOM is chosen then the cost has to be defined by the feature attributes using analysisCustomizedCosts, with this option the nodes and links calculators are define automatically.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                     |
    |---------------------------|-------------------------------------------|
    | `static java.lang.String` | `CUSTOM`<br>Cost option custom.           |
    | `static java.lang.String` | `LINE_LENGTH`<br>Cost option Line length. |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `AnalysisCost``()`          |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                         | Method and Description                                                                                                                                                 |
    |---------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.util.List<`[`AnalysisCustomizedCost`](AnalysisCustomizedCost.md)`>` | `getAnalysisCustomizedCosts``()`<br>Returns the analysis customized costs.                                                                                             |
    | `java.lang.String`                                                        | `getCostOption``()`<br>Returns the cost option.                                                                                                                        |
    | [`LinkCostCalculator`](../../lod/LinkCostCalculator.md)                   | `getLinkCostCalculator``()`<br>Returns the link cost calculator.                                                                                                       |
    | [`NodeCostCalculator`](../../lod/NodeCostCalculator.md)                   | `getNodeCostCalculator``()`<br>Returns the node cost calculator.                                                                                                       |
    | `void`                                                                    | `setAnalysisCustomizedCosts``(java.util.List<`[`AnalysisCustomizedCost`](AnalysisCustomizedCost.md)`> analysisCustomizedCosts)`<br>Sets the analysis customized costs. |
    | `void`                                                                    | `setCostOption``(java.lang.String costOption)`<br>Sets the cost option.                                                                                                |
    | `void`                                                                    | `setLinkCostCalculator``(`[`LinkCostCalculator`](../../lod/LinkCostCalculator.md)` linkCostCalculator)`<br>Sets the link cost calculator.                              |
    | `void`                                                                    | `setNodeCostCalculator``(`[`NodeCostCalculator`](../../lod/NodeCostCalculator.md)` nodeCostCalculator)`<br>Sets the node cost calculator.                              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### LINE_LENGTH

          public static final java.lang.String LINE_LENGTH

      Cost option Line length. The costs that are defined in the node and link tables will be used.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### CUSTOM

          public static final java.lang.String CUSTOM

      Cost option custom. The analysisCustomizedCost will be used.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### AnalysisCost

          public AnalysisCost()

  <!-- -->

  - ### Method Detail

    - #### getAnalysisCustomizedCosts

          public java.util.List<AnalysisCustomizedCost> getAnalysisCustomizedCosts()

      Returns the analysis customized costs.
      Returns:
      analysis customized costs

    <!-- -->

    - #### setAnalysisCustomizedCosts

          public void setAnalysisCustomizedCosts(java.util.List<AnalysisCustomizedCost> analysisCustomizedCosts)

      Sets the analysis customized costs.
      Parameters:
      `analysisCustomizedCosts` - analysis customized costs.

    <!-- -->

    - #### getCostOption

          public java.lang.String getCostOption()

      Returns the cost option. One of the following constants: AnalysisCost.LINE_LENGTH or AnalysisCost.CUSTOM.
      Returns:
      cost option. One of the following constants: AnalysisCost.LINE_LENGTH or AnalysisCost.CUSTOM.

    <!-- -->

    - #### setCostOption

          public void setCostOption(java.lang.String costOption)

      Sets the cost option. One of the following constants: AnalysisCost.LINE_LENGTH or AnalysisCost.CUSTOM.
      Parameters:
      `costOption` - cost option. One of the following constants: AnalysisCost.LINE_LENGTH or AnalysisCost.CUSTOM.

    <!-- -->

    - #### getNodeCostCalculator

          public NodeCostCalculator getNodeCostCalculator()

      Returns the node cost calculator. The node cost calculator is used if the LINE_LENGTH option is chosen.
      Returns:
      node cost calculator

    <!-- -->

    - #### setNodeCostCalculator

          public void setNodeCostCalculator(NodeCostCalculator nodeCostCalculator)

      Sets the node cost calculator. The node cost calculator is used if the LINE_LENGTH option is chosen.
      Parameters:
      `nodeCostCalculator` - node cost calculator

    <!-- -->

    - #### getLinkCostCalculator

          public LinkCostCalculator getLinkCostCalculator()

      Returns the link cost calculator. The link cost calculator is used if the LINE_LENGTH option is chosen.
      Returns:
      link cost calculator

    <!-- -->

    - #### setLinkCostCalculator

          public void setLinkCostCalculator(LinkCostCalculator linkCostCalculator)

      Sets the link cost calculator. The link cost calculator is used if the LINE_LENGTH option is chosen.
      Parameters:
      `linkCostCalculator` - link cost calculator

Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](AnalysisCustomizedCost.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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
