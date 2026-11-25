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

- [Prev Class](LogicalBasicNetwork.md)
- [Next Class](LogicalLightPath.md)

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

## Interface LogicalHeavyPath

- All Known Subinterfaces:
  [SpatialHeavyPath](SpatialHeavyPath.md)

  ------------------------------------------------------------------------



      public interface LogicalHeavyPath

  A LogicalHeavyPath is a logical path with detailed node and link information.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                  | Method and Description                                                                                                                                                                                    |
    |----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LogicalHeavyPath`                                 | `append``(LogicalHeavyPath path)`<br>Appends a path after this path.                                                                                                                                      |
    | `LogicalHeavyPath`                                 | `append``(`[`LogicalLink`](LogicalLink.md)` nextLink, `[`LogicalNode`](LogicalNode.md)` nextNode, double[] nextLinkCosts, double[] nextNodeCosts)`<br>Appends a link at the end of this path.             |
    | `java.lang.Object`                                 | `clone``()`<br>Support cloneable                                                                                                                                                                          |
    | [`CategorizedUserData`](CategorizedUserData.md)    | `getCategorizedUserData``()`<br>Returns categorized user data.                                                                                                                                            |
    | `double`                                           | `getCost``()`<br>Deprecated. <br>use getCosts();                                                                                                                                                          |
    | `double[]`                                         | `getCosts``()`<br>Returns the costs of this path.                                                                                                                                                         |
    | [`LogicalNode`](LogicalNode.md)                    | `getEndNode``()`<br>Returns the last node on this path.                                                                                                                                                   |
    | [`LogicalLink`](LogicalLink.md)                    | `getFirstLink``()`<br>Returns the first link on this path.                                                                                                                                                |
    | [`LogicalLink`](LogicalLink.md)                    | `getLastLink``()`<br>Returns the last link on this path.                                                                                                                                                  |
    | [`LogicalLink`](LogicalLink.md)`[]`                | `getLinks``()`<br>Returns the logical links on this path.                                                                                                                                                 |
    | [`LogicalNode`](LogicalNode.md)`[]`                | `getNodes``()`<br>Returns the logical nodes on this path.                                                                                                                                                 |
    | [`LogicalNode`](LogicalNode.md)                    | `getStartNode``()`<br>Returns the first node on this path.                                                                                                                                                |
    | `java.util.Map<java.lang.String,java.lang.Object>` | `getUserData``()`<br>Deprecated.                                                                                                                                                                          |
    | [`UserData`](UserData.md)                          | `getUserData``(int category)`<br>Returns user data for the specified category.                                                                                                                            |
    | `java.lang.Object`                                 | `getUserData``(java.lang.String dataName)`<br>Deprecated.                                                                                                                                                 |
    | `boolean`                                          | `isReverse``()`<br>Returns whether the path is reverse path or not.                                                                                                                                       |
    | `LogicalHeavyPath`                                 | `prepend``(LogicalHeavyPath path)`<br>Appends a path before this path.                                                                                                                                    |
    | `LogicalHeavyPath`                                 | `prepend``(`[`LogicalLink`](LogicalLink.md)` prevLink, `[`LogicalNode`](LogicalNode.md)` prevNode, double[] prevLinkCosts, double[] connectorNodeCosts)`<br>Appends a link at the beginning of this path. |
    | `void`                                             | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Sets categorized user data.                                                                                     |
    | `void`                                             | `setCost``(double cost)`<br>Deprecated. <br>use setCosts(double\[\] costs);                                                                                                                               |
    | `void`                                             | `setCosts``(double[] costs)`<br>Sets the costs of this path.                                                                                                                                              |
    | `void`                                             | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.                                                                                         |
    | `void`                                             | `setUserData``(java.util.Map<java.lang.String,java.lang.Object> userDataMap)`<br>Deprecated.                                                                                                              |
    | `void`                                             | `setUserData``(java.lang.String dataName, java.lang.Object dataValue)`<br>Deprecated.                                                                                                                     |
    | [`LogicalPath`](LogicalPath.md)                    | `toLogicalPath``()`<br>Converts the heavy-weight path to a light-weight path.                                                                                                                             |

<!-- -->

- - ### Method Detail

    - #### getLinks

          LogicalLink[] getLinks()

      Returns the logical links on this path.
      Returns:
      logical links

    <!-- -->

    - #### getNodes

          LogicalNode[] getNodes()

      Returns the logical nodes on this path.
      Returns:
      logical nodes

    <!-- -->

    - #### getStartNode

          LogicalNode getStartNode()

      Returns the first node on this path.
      Returns:
      first node

    <!-- -->

    - #### getEndNode

          LogicalNode getEndNode()

      Returns the last node on this path.
      Returns:
      last node

    <!-- -->

    - #### getFirstLink

          LogicalLink getFirstLink()

      Returns the first link on this path.
      Returns:
      first link

    <!-- -->

    - #### getLastLink

          LogicalLink getLastLink()

      Returns the last link on this path.
      Returns:
      last link

    <!-- -->

    - #### getCost

          double getCost()

      Deprecated. use getCosts();
      Returns the cost of this path.
      Returns:
      cost of this path

    <!-- -->

    - #### setCost

          void setCost(double cost)

      Deprecated. use setCosts(double\[\] costs);
      Sets the cost of this path.
      Parameters:
      `cost` - path cost

    <!-- -->

    - #### getCosts

          double[] getCosts()

      Returns the costs of this path.
      Returns:
      costs of this path

    <!-- -->

    - #### setCosts

          void setCosts(double[] costs)

      Sets the costs of this path.
      Parameters:
      `costs` - path costs

    <!-- -->

    - #### getUserData

          java.lang.Object getUserData(java.lang.String dataName)

      Deprecated. 
      Returns the user data object for the specified data name.
      Parameters:
      `dataName` - name of the user data

      Returns:
      value of the user data

    <!-- -->

    - #### setUserData

          void setUserData(java.lang.String dataName,
                           java.lang.Object dataValue)

      Deprecated. 
      Sets the value of the user data. No verification of the validity of the data name is done inside this method, therefore, the caller must ensure that the input data name is valid.
      Parameters:
      `dataName` - name of the user data

      `dataValue` - value of the user data

    <!-- -->

    - #### getUserData

          java.util.Map<java.lang.String,java.lang.Object> getUserData()

      Deprecated. 
      Returns all the user data name value pairs.
      Returns:
      user data name value pairs

    <!-- -->

    - #### setUserData

          void setUserData(java.util.Map<java.lang.String,java.lang.Object> userDataMap)

      Deprecated. 
      Sets the value of the user data. No verification of the validity of the data name is done inside this method, therefore, the caller must ensure that the input data name is valid.
      Parameters:
      `userDataMap` - a map of userdata name value pairs

    <!-- -->

    - #### append

          LogicalHeavyPath append(LogicalLink nextLink,
                                  LogicalNode nextNode,
                                  double[] nextLinkCosts,
                                  double[] nextNodeCosts)

      Appends a link at the end of this path.
      Parameters:
      `nextLink` - next link

      `nextNode` - next node

      `nextLinkCosts` - costs of the next link

      `nextNodeCosts` - costs of the next node

    <!-- -->

    - #### append

          LogicalHeavyPath append(LogicalHeavyPath path)

      Appends a path after this path.
      Parameters:
      `path` - path to append after this path

    <!-- -->

    - #### prepend

          LogicalHeavyPath prepend(LogicalLink prevLink,
                                   LogicalNode prevNode,
                                   double[] prevLinkCosts,
                                   double[] connectorNodeCosts)

      Appends a link at the beginning of this path.
      Parameters:

      `prevLink` - previous link

      `prevNode` - previous node

      `prevLinkCosts` - costs of the previous link

      `connectorNodeCosts` - costs of the previous node

      Returns:

    <!-- -->

    - #### prepend

          LogicalHeavyPath prepend(LogicalHeavyPath path)

      Appends a path before this path.
      Parameters:
      `path` - path to append before this path

    <!-- -->

    - #### toLogicalPath

          LogicalPath toLogicalPath()

      Converts the heavy-weight path to a light-weight path.
      Returns:
      the light-weight path

    <!-- -->

    - #### isReverse

          boolean isReverse()

      Returns whether the path is reverse path or not.
      Returns:

    <!-- -->

    - #### getCategorizedUserData

          CategorizedUserData getCategorizedUserData()

      Returns categorized user data.
      Returns:

    <!-- -->

    - #### setCategorizedUserData

          void setCategorizedUserData(CategorizedUserData userData)

      Sets categorized user data.
      Parameters:
      `userData` -

    <!-- -->

    - #### getUserData

          UserData getUserData(int category)

      Returns user data for the specified category.
      Returns:

    <!-- -->

    - #### setUserData

          void setUserData(int category,
                           UserData userData)

      Sets user data for the specified category.
      Parameters:
      `userData` -

    <!-- -->

    - #### clone

          java.lang.Object clone()
                          throws java.lang.CloneNotSupportedException

      Support cloneable
      Returns:
      cloned object

      Throws:
      `java.lang.CloneNotSupportedException`

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

- [Prev Class](LogicalBasicNetwork.md)
- [Next Class](LogicalLightPath.md)

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
