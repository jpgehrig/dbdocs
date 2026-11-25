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

- [Prev Class](NFEFeature.md)
- [Next Class](NFEFeatureElement.md)

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

oracle.spatial.network.nfe.model.feature

## Class NFEFeatureClass

- java.lang.Object

- - oracle.spatial.network.nfe.model.feature.NFEFeatureClass

<!-- -->

- Direct Known Subclasses:
  [NFEBasicFeatureClass](NFEBasicFeatureClass.md)

  ------------------------------------------------------------------------



      public abstract class NFEFeatureClass
      extends java.lang.Object

  Base class for representing a feature class. A feature class contains information about the shape and visual style of a feature. It constraints the type of feature elements and the value of the attributes of a feature. A feature class can be seen as a template for creating features. A feature layer must contain at least one feature class definition before any feature is added to this feature layer.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEFeatureClass``()`       |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                            | Method and Description                                                                                                                                                                                 |
    |----------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract void`                                                                              | `addAttributeConstraint``(`[`NFEAttributeConstraint`](NFEAttributeConstraint.md)` attrConstraint)`<br>Adds an attribute constraint to the feature class                                                |
    | `abstract void`                                                                              | `addPredefinedConnectedPoint``(`[`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)` predefConnPoint)`<br>Adds a predefined connected point descriptor to the feature class                |
    | `abstract NFEFeatureClass`                                                                   | `createCopy``()`<br>Returns object copy.                                                                                                                                                               |
    | `abstract java.util.Collection<`[`NFEAttributeConstraint`](NFEAttributeConstraint.md)`>`     | `getAttributeConstraints``()`<br>Gets all the attribute constraint contained by the feature class                                                                                                      |
    | `abstract `[`NFEFeatureLayer`](NFEFeatureLayer.md)                                           | `getFeatureLayer``()`<br>Gets the feature class' feature layer                                                                                                                                         |
    | `abstract long`                                                                              | `getId``()`<br>Gets the feature class' ID                                                                                                                                                              |
    | `abstract int`                                                                               | `getMaxInConnections``()`<br>Gets the maximum number of in connections when the feature class' shape type is point                                                                                     |
    | `abstract int`                                                                               | `getMaxOutConnections``()`<br>Gets the maximum number of out connections when the feature class' shape type is point                                                                                   |
    | `abstract java.lang.String`                                                                  | `getName``()`<br>Gets the feature class' name                                                                                                                                                          |
    | `abstract java.util.List<`[`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)`>` | `getPredefinedConnectedPoints``()`<br>Gets the predefined connected points set to the feature class when the shape type is LINE or COMPLEX_LINE                                                        |
    | `abstract `[`NFEFeatureShape`](NFEFeatureShape.md)                                           | `getShape``()`<br>Gets the feature class' feature shape type                                                                                                                                           |
    | `abstract Style`                                                                             | `getStyle``()`<br>Gets the SDO style instance assigned to the feature class                                                                                                                            |
    | `abstract java.lang.String`                                                                  | `getStyleName``()`<br>Gets the name of the style associated to this style                                                                                                                              |
    | `abstract boolean`                                                                           | `removeAttributeContraint``(`[`NFEAttributeConstraint`](NFEAttributeConstraint.md)` attrConstraint)`<br>Removes an attribute constraint from the feature class                                         |
    | `abstract boolean`                                                                           | `removePredefinedConnectedPoint``(`[`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)` predefConnPoint)`<br>Removes the give predefined connected point descriptor from the feature class |
    | `abstract void`                                                                              | `setFeatureLayer``(`[`NFEFeatureLayer`](NFEFeatureLayer.md)` featureLayer)`<br>Sets the feature class' feature layer                                                                                   |
    | `abstract void`                                                                              | `setId``(long id)`<br>Sets the feature class' ID                                                                                                                                                       |
    | `abstract void`                                                                              | `setMaxInConnections``(int maxInConnections)`<br>Sets the maximum number of in connections when the feature class' shape type is point                                                                 |
    | `abstract void`                                                                              | `setMaxOutConnections``(int maxOutConnections)`<br>Gets the maximum number of out connections when the feature class' shape type is point                                                              |
    | `abstract void`                                                                              | `setName``(java.lang.String name)`<br>Sets the feature class' name                                                                                                                                     |
    | `abstract void`                                                                              | `setShape``(`[`NFEFeatureShape`](NFEFeatureShape.md)` shape)`<br>Sets the feature class' feature shape type                                                                                            |
    | `abstract void`                                                                              | `setStyle``(Style style)`<br>Sets the SDO style instance assigned to the feature class.                                                                                                                |
    | `abstract void`                                                                              | `setStyleName``(java.lang.String styleName)`<br>Sets the name of the style associated to this style.                                                                                                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEFeatureClass

          public NFEFeatureClass()

  <!-- -->

  - ### Method Detail

    - #### getId

          public abstract long getId()

      Gets the feature class' ID
      Returns:
      a feature class ID

    <!-- -->

    - #### setId

          public abstract void setId(long id)

      Sets the feature class' ID
      Parameters:
      `id` - a feature class ID

    <!-- -->

    - #### getFeatureLayer

          public abstract NFEFeatureLayer getFeatureLayer()

      Gets the feature class' feature layer
      Returns:
      a feature layer instance

    <!-- -->

    - #### setFeatureLayer

          public abstract void setFeatureLayer(NFEFeatureLayer featureLayer)

      Sets the feature class' feature layer
      Parameters:
      `featureLayer` - a feature layer instance

    <!-- -->

    - #### getName

          public abstract java.lang.String getName()

      Gets the feature class' name
      Returns:
      the feature class' name

    <!-- -->

    - #### setName

          public abstract void setName(java.lang.String name)

      Sets the feature class' name
      Parameters:
      `name` - the feature class' name

    <!-- -->

    - #### getShape

          public abstract NFEFeatureShape getShape()

      Gets the feature class' feature shape type
      Returns:
      a feature shape type

    <!-- -->

    - #### setShape

          public abstract void setShape(NFEFeatureShape shape)

      Sets the feature class' feature shape type
      Parameters:
      `shape` - a feature shape type

    <!-- -->

    - #### getMaxInConnections

          public abstract int getMaxInConnections()

      Gets the maximum number of in connections when the feature class' shape type is point
      Returns:
      the maximum number of in connections

    <!-- -->

    - #### setMaxInConnections

          public abstract void setMaxInConnections(int maxInConnections)

      Sets the maximum number of in connections when the feature class' shape type is point
      Parameters:
      `maxInConnections` - the maximum number of in connections

    <!-- -->

    - #### getMaxOutConnections

          public abstract int getMaxOutConnections()

      Gets the maximum number of out connections when the feature class' shape type is point
      Returns:
      the maximum number of out connections

    <!-- -->

    - #### setMaxOutConnections

          public abstract void setMaxOutConnections(int maxOutConnections)

      Gets the maximum number of out connections when the feature class' shape type is point
      Parameters:
      `maxOutConnections` - the maximum number of out connections

    <!-- -->

    - #### getStyleName

          public abstract java.lang.String getStyleName()

      Gets the name of the style associated to this style
      Returns:
      a style name

    <!-- -->

    - #### setStyleName

          public abstract void setStyleName(java.lang.String styleName)

      Sets the name of the style associated to this style. This name is used to reference the style in the database.
      Parameters:
      `styleName` - a style name

    <!-- -->

    - #### getStyle

          public abstract Style getStyle()

      Gets the SDO style instance assigned to the feature class
      Returns:
      an SDO style instance

    <!-- -->

    - #### setStyle

          public abstract void setStyle(Style style)

      Sets the SDO style instance assigned to the feature class. More information about how to define styles is available in the in the User's Guide for Oracle MapViewer.
      Parameters:
      `style` - an SDO style instance

    <!-- -->

    - #### getAttributeConstraints

          public abstract java.util.Collection<NFEAttributeConstraint> getAttributeConstraints()

      Gets all the attribute constraint contained by the feature class
      Returns:
      a collection of attribute constraint instances

    <!-- -->

    - #### addAttributeConstraint

          public abstract void addAttributeConstraint(NFEAttributeConstraint attrConstraint)

      Adds an attribute constraint to the feature class
      Parameters:
      `attrConstraint` - an attribute constraint instance

    <!-- -->

    - #### removeAttributeContraint

          public abstract boolean removeAttributeContraint(NFEAttributeConstraint attrConstraint)

      Removes an attribute constraint from the feature class
      Parameters:
      `attrConstraint` - an attribute constraint instance

      Returns:
      true if the attribute was removed

    <!-- -->

    - #### getPredefinedConnectedPoints

          public abstract java.util.List<NFEPredefinedConnectedPoint> getPredefinedConnectedPoints()

      Gets the predefined connected points set to the feature class when the shape type is LINE or COMPLEX_LINE
      Returns:
      a list of predefined feature point descriptors

    <!-- -->

    - #### addPredefinedConnectedPoint

          public abstract void addPredefinedConnectedPoint(NFEPredefinedConnectedPoint predefConnPoint)

      Adds a predefined connected point descriptor to the feature class
      Parameters:
      `predefConnPoint` - a predefined connected point descriptor

    <!-- -->

    - #### removePredefinedConnectedPoint

          public abstract boolean removePredefinedConnectedPoint(NFEPredefinedConnectedPoint predefConnPoint)

      Removes the give predefined connected point descriptor from the feature class
      Parameters:
      `predefConnPoint` - a predefined connected point descriptor

      Returns:
      true if the element was removed

    <!-- -->

    - #### createCopy

          public abstract NFEFeatureClass createCopy()

      Returns object copy.
      Returns:
      object copy

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

- [Prev Class](NFEFeature.md)
- [Next Class](NFEFeatureElement.md)

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
