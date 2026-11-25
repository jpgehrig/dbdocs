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

- [Prev Class](NFEBasicFeature.md)
- [Next Class](NFEBasicFeatureElement.md)

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

## Class NFEBasicFeatureClass

- java.lang.Object

- - [oracle.spatial.network.nfe.model.feature.NFEFeatureClass](NFEFeatureClass.md)

  - - oracle.spatial.network.nfe.model.feature.NFEBasicFeatureClass

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFEBasicFeatureClass
      extends NFEFeatureClass

  The default implementation of [`NFEFeatureClass`](NFEFeatureClass.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEBasicFeatureClass``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                   | Method and Description                                                                                                                                                                                 |
    |-------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                              | `addAttributeConstraint``(`[`NFEAttributeConstraint`](NFEAttributeConstraint.md)` attrConstraint)`<br>Adds an attribute constraint to the feature class                                                |
    | `void`                                                                              | `addPredefinedConnectedPoint``(`[`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)` predefConnPoint)`<br>Adds a predefined connected point descriptor to the feature class                |
    | [`NFEFeatureClass`](NFEFeatureClass.md)                                             | `createCopy``()`<br>Returns object copy.                                                                                                                                                               |
    | `java.util.Collection<`[`NFEAttributeConstraint`](NFEAttributeConstraint.md)`>`     | `getAttributeConstraints``()`<br>Gets all the attribute constraint contained by the feature class                                                                                                      |
    | [`NFEFeatureLayer`](NFEFeatureLayer.md)                                             | `getFeatureLayer``()`<br>Gets the feature class' feature layer                                                                                                                                         |
    | `long`                                                                              | `getId``()`<br>Gets the feature class' ID                                                                                                                                                              |
    | `int`                                                                               | `getMaxInConnections``()`<br>Gets the maximum number of in connections when the feature class' shape type is point                                                                                     |
    | `int`                                                                               | `getMaxOutConnections``()`<br>Gets the maximum number of out connections when the feature class' shape type is point                                                                                   |
    | `java.lang.String`                                                                  | `getName``()`<br>Gets the feature class' name                                                                                                                                                          |
    | `java.util.List<`[`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)`>` | `getPredefinedConnectedPoints``()`<br>Gets the predefined connected points set to the feature class when the shape type is LINE or COMPLEX_LINE                                                        |
    | [`NFEFeatureShape`](NFEFeatureShape.md)                                             | `getShape``()`<br>Gets the feature class' feature shape type                                                                                                                                           |
    | `Style`                                                                             | `getStyle``()`<br>Gets the SDO style instance assigned to the feature class                                                                                                                            |
    | `java.lang.String`                                                                  | `getStyleName``()`<br>Gets the name of the style associated to this style                                                                                                                              |
    | `boolean`                                                                           | `removeAttributeContraint``(`[`NFEAttributeConstraint`](NFEAttributeConstraint.md)` attrConstraint)`<br>Removes an attribute constraint from the feature class                                         |
    | `boolean`                                                                           | `removePredefinedConnectedPoint``(`[`NFEPredefinedConnectedPoint`](NFEPredefinedConnectedPoint.md)` predefConnPoint)`<br>Removes the give predefined connected point descriptor from the feature class |
    | `void`                                                                              | `setFeatureLayer``(`[`NFEFeatureLayer`](NFEFeatureLayer.md)` featureLayer)`<br>Sets the feature class' feature layer                                                                                   |
    | `void`                                                                              | `setId``(long id)`<br>Sets the feature class' ID                                                                                                                                                       |
    | `void`                                                                              | `setMaxInConnections``(int maxInConnections)`<br>Sets the maximum number of in connections when the feature class' shape type is point                                                                 |
    | `void`                                                                              | `setMaxOutConnections``(int maxOutConnections)`<br>Gets the maximum number of out connections when the feature class' shape type is point                                                              |
    | `void`                                                                              | `setName``(java.lang.String name)`<br>Sets the feature class' name                                                                                                                                     |
    | `void`                                                                              | `setShape``(`[`NFEFeatureShape`](NFEFeatureShape.md)` shape)`<br>Sets the feature class' feature shape type                                                                                            |
    | `void`                                                                              | `setStyle``(Style style)`<br>Sets the SDO style instance assigned to the feature class.                                                                                                                |
    | `void`                                                                              | `setStyleName``(java.lang.String styleName)`<br>Sets the name of the style associated to this style.                                                                                                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEBasicFeatureClass

          public NFEBasicFeatureClass()

  <!-- -->

  - ### Method Detail

    - #### getId

          public long getId()

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Gets the feature class' ID
      Specified by:
      [`getId`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Returns:
      a feature class ID

    <!-- -->

    - #### setId

          public void setId(long id)

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Sets the feature class' ID
      Specified by:
      [`setId`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Parameters:
      `id` - a feature class ID

    <!-- -->

    - #### getFeatureLayer

          public NFEFeatureLayer getFeatureLayer()

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Gets the feature class' feature layer
      Specified by:
      [`getFeatureLayer`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Returns:
      a feature layer instance

    <!-- -->

    - #### setFeatureLayer

          public void setFeatureLayer(NFEFeatureLayer featureLayer)

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Sets the feature class' feature layer
      Specified by:
      [`setFeatureLayer`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Parameters:
      `featureLayer` - a feature layer instance

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Gets the feature class' name
      Specified by:
      [`getName`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Returns:
      the feature class' name

    <!-- -->

    - #### setName

          public void setName(java.lang.String name)

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Sets the feature class' name
      Specified by:
      [`setName`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Parameters:
      `name` - the feature class' name

    <!-- -->

    - #### getShape

          public NFEFeatureShape getShape()

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Gets the feature class' feature shape type
      Specified by:
      [`getShape`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Returns:
      a feature shape type

    <!-- -->

    - #### setShape

          public void setShape(NFEFeatureShape shape)

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Sets the feature class' feature shape type
      Specified by:
      [`setShape`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Parameters:
      `shape` - a feature shape type

    <!-- -->

    - #### getMaxInConnections

          public int getMaxInConnections()

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Gets the maximum number of in connections when the feature class' shape type is point
      Specified by:
      [`getMaxInConnections`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Returns:
      the maximum number of in connections

    <!-- -->

    - #### setMaxInConnections

          public void setMaxInConnections(int maxInConnections)

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Sets the maximum number of in connections when the feature class' shape type is point
      Specified by:
      [`setMaxInConnections`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Parameters:
      `maxInConnections` - the maximum number of in connections

    <!-- -->

    - #### getMaxOutConnections

          public int getMaxOutConnections()

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Gets the maximum number of out connections when the feature class' shape type is point
      Specified by:
      [`getMaxOutConnections`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Returns:
      the maximum number of out connections

    <!-- -->

    - #### setMaxOutConnections

          public void setMaxOutConnections(int maxOutConnections)

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Gets the maximum number of out connections when the feature class' shape type is point
      Specified by:
      [`setMaxOutConnections`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Parameters:
      `maxOutConnections` - the maximum number of out connections

    <!-- -->

    - #### getStyleName

          public java.lang.String getStyleName()

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Gets the name of the style associated to this style
      Specified by:
      [`getStyleName`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Returns:
      a style name

    <!-- -->

    - #### setStyleName

          public void setStyleName(java.lang.String styleName)

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Sets the name of the style associated to this style. This name is used to reference the style in the database.
      Specified by:
      [`setStyleName`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Parameters:
      `styleName` - a style name

    <!-- -->

    - #### getStyle

          public Style getStyle()

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Gets the SDO style instance assigned to the feature class
      Specified by:
      [`getStyle`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Returns:
      an SDO style instance

    <!-- -->

    - #### setStyle

          public void setStyle(Style style)

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Sets the SDO style instance assigned to the feature class. More information about how to define styles is available in the in the User's Guide for Oracle MapViewer.
      Specified by:
      [`setStyle`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Parameters:
      `style` - an SDO style instance

    <!-- -->

    - #### getAttributeConstraints

          public java.util.Collection<NFEAttributeConstraint> getAttributeConstraints()

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Gets all the attribute constraint contained by the feature class
      Specified by:
      [`getAttributeConstraints`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Returns:
      a collection of attribute constraint instances

    <!-- -->

    - #### addAttributeConstraint

          public void addAttributeConstraint(NFEAttributeConstraint attrConstraint)

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Adds an attribute constraint to the feature class
      Specified by:
      [`addAttributeConstraint`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Parameters:
      `attrConstraint` - an attribute constraint instance

    <!-- -->

    - #### removeAttributeContraint

          public boolean removeAttributeContraint(NFEAttributeConstraint attrConstraint)

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Removes an attribute constraint from the feature class
      Specified by:
      [`removeAttributeContraint`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Parameters:
      `attrConstraint` - an attribute constraint instance

      Returns:
      true if the attribute was removed

    <!-- -->

    - #### getPredefinedConnectedPoints

          public java.util.List<NFEPredefinedConnectedPoint> getPredefinedConnectedPoints()

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Gets the predefined connected points set to the feature class when the shape type is LINE or COMPLEX_LINE
      Specified by:
      [`getPredefinedConnectedPoints`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Returns:
      a list of predefined feature point descriptors

    <!-- -->

    - #### addPredefinedConnectedPoint

          public void addPredefinedConnectedPoint(NFEPredefinedConnectedPoint predefConnPoint)

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Adds a predefined connected point descriptor to the feature class
      Specified by:
      [`addPredefinedConnectedPoint`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Parameters:
      `predefConnPoint` - a predefined connected point descriptor

    <!-- -->

    - #### removePredefinedConnectedPoint

          public boolean removePredefinedConnectedPoint(NFEPredefinedConnectedPoint predefConnPoint)

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Removes the give predefined connected point descriptor from the feature class
      Specified by:
      [`removePredefinedConnectedPoint`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

      Parameters:
      `predefConnPoint` - a predefined connected point descriptor

      Returns:
      true if the element was removed

    <!-- -->

    - #### createCopy

          public NFEFeatureClass createCopy()

      Description copied from class: [`NFEFeatureClass`](NFEFeatureClass.md)
      Returns object copy.
      Specified by:
      [`createCopy`](NFEFeatureClass.md) in class [`NFEFeatureClass`](NFEFeatureClass.md)

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

- [Prev Class](NFEBasicFeature.md)
- [Next Class](NFEBasicFeatureElement.md)

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
