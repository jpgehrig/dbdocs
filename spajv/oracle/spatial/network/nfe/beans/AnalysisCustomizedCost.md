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

- [Prev Class](AnalysisCost.md)
- [Next Class](NFENearestNeighbors.md)

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

## Class AnalysisCustomizedCost

- java.lang.Object

- - oracle.spatial.network.nfe.beans.AnalysisCustomizedCost

<!-- -->

-

  ------------------------------------------------------------------------



      public class AnalysisCustomizedCost
      extends java.lang.Object

  An AnalysisCustomizedCost describes a customized cost.
  The feature layer and feature class will provide the attributes that will be used in the expression.
  If feature class is null then the cost expression will apply to all the feature classes of the feature layer.

  As example assume that the feature layer is Conductor and the feature class is HT Conductor, one of the attributes is LENGTH. Using the default expression analyzer ExpressionLexicalAnalyzer then valid expressions would be:

       1) LENGTH
       2) LENGTH*(4-3)


  If LENGTH is chosen then the length attribute of the HT Conductor is used as cost in an NFE analysis.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description   |
    |-------------------------------|
    | `AnalysisCustomizedCost``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                        | Method and Description                                                                                                        |
    |----------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`                                       | `getExpression``()`<br>Returns the cost expression.                                                                           |
    | [`NFEFeatureClass`](../model/feature/NFEFeatureClass.md) | `getNFEFeatureClass``()`<br>Returns the feature class.                                                                        |
    | [`NFEFeatureLayer`](../model/feature/NFEFeatureLayer.md) | `getNFEFeatureLayer``()`<br>Returns the feature layer.                                                                        |
    | `void`                                                   | `setExpression``(java.lang.String expression)`<br>Sets the cost expression                                                    |
    | `void`                                                   | `setNFEFeatureClass``(`[`NFEFeatureClass`](../model/feature/NFEFeatureClass.md)` nfeFeatureClass)`<br>Sets the feature class. |
    | `void`                                                   | `setNFEFeatureLayer``(`[`NFEFeatureLayer`](../model/feature/NFEFeatureLayer.md)` nfeFeatureLayer)`<br>Sets the feature layer. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### AnalysisCustomizedCost

          public AnalysisCustomizedCost()

  <!-- -->

  - ### Method Detail

    - #### getNFEFeatureLayer

          public NFEFeatureLayer getNFEFeatureLayer()

      Returns the feature layer.
      Returns:
      feature layer

    <!-- -->

    - #### setNFEFeatureLayer

          public void setNFEFeatureLayer(NFEFeatureLayer nfeFeatureLayer)

      Sets the feature layer.
      Parameters:
      `nfeFeatureLayer` - feature layer

    <!-- -->

    - #### getNFEFeatureClass

          public NFEFeatureClass getNFEFeatureClass()

      Returns the feature class.
      Returns:
      feature class

    <!-- -->

    - #### setNFEFeatureClass

          public void setNFEFeatureClass(NFEFeatureClass nfeFeatureClass)

      Sets the feature class.
      Parameters:
      `nfeFeatureClass` - feature class

    <!-- -->

    - #### getExpression

          public java.lang.String getExpression()

      Returns the cost expression.
      Returns:
      cost expression

    <!-- -->

    - #### setExpression

          public void setExpression(java.lang.String expression)

      Sets the cost expression
      Parameters:
      `expression` - cost expression

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

- [Prev Class](AnalysisCost.md)
- [Next Class](NFENearestNeighbors.md)

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
