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

- [Prev Class](UserDataIO.md)
- Next Class

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

## Interface UserDataMetadata

- All Superinterfaces:
  java.lang.Cloneable, java.io.Serializable

  ------------------------------------------------------------------------



      public interface UserDataMetadata
      extends java.lang.Cloneable, java.io.Serializable

  This class defines the metadata for user data. Data names will directly map to table column names Data Types: are INTEGER, NUMBER, VARCHAR2, and SDO_GEOMETRY Data Length is only for data with types of VARCHAR2

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description         |
    |---------------------------|-------------------------------|
    | `static java.lang.String` | `DATE_TYPE`                   |
    | `static int`              | `DEFAULT_USER_DATA_CATEGORY`  |
    | `static java.lang.String` | `INTEGER_TYPE`                |
    | `static java.lang.String` | `LINK_TABLE_TYPE`             |
    | `static java.lang.String` | `NODE_TABLE_TYPE`             |
    | `static java.lang.String` | `NUMBER_TYPE`                 |
    | `static java.lang.String` | `OBJECT_TYPE`                 |
    | `static java.lang.String` | `PATH_TABLE_TYPE`             |
    | `static java.lang.String` | `SDO_GEOMETRY_TYPE`           |
    | `static java.lang.String` | `SUBPATH_TABLE_TYPE`          |
    | `static java.lang.String` | `TIMESTAMP_TYPE`              |
    | `static java.lang.String` | `VARCHAR2_TYPE`               |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                   | Method and Description                                                                                                                                     |
    |-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                              | `addLinkData``(java.lang.String dataName, java.lang.String dataType, int dataLength, int categoryId)`<br>Adds a link user data entry to the metadata       |
    | `void`                                              | `addNodeData``(java.lang.String dataName, java.lang.String dataType, int dataLength, int categoryId)`<br>Adds a node user data entry to the metadata       |
    | `void`                                              | `addPathData``(java.lang.String dataName, java.lang.String dataType, int dataLength, int categoryId)`<br>Adds a path user data entry to the metadata       |
    | `void`                                              | `addSubPathData``(java.lang.String dataName, java.lang.String dataType, int dataLength, int categoryId)`<br>Adds a subpath user data entry to the metadata |
    | `boolean`                                           | `containsLinkUserData``(java.lang.String dataName)`<br>Checks if the given link user data name exists                                                      |
    | `boolean`                                           | `containsNodeUserData``(java.lang.String dataName)`<br>Checks if the given node user data name exists                                                      |
    | `boolean`                                           | `containsPathUserData``(java.lang.String dataName)`<br>Checks if the given path user data name exists                                                      |
    | `boolean`                                           | `containsSubPathUserData``(java.lang.String dataName)`<br>Checks if the given subpath user data name exists                                                |
    | `void`                                              | `deleteLinkData``(java.lang.String dataName)`<br>Deletes a link user data entry from the metadata                                                          |
    | `void`                                              | `deleteNodeData``(java.lang.String dataName)`<br>Deletes a node user data entry from the metadata                                                          |
    | `void`                                              | `deletePathData``(java.lang.String dataName)`<br>Deletes a path user data entry from the metadata                                                          |
    | `void`                                              | `deleteSubPathData``(java.lang.String dataName)`<br>Deletes a subpath user data entry from the metadata                                                    |
    | `java.util.Map<java.lang.String,java.lang.Integer>` | `getLinkDataIndexMap``(int category)`<br>Returns the link user data index map.                                                                             |
    | `int`                                               | `getLinkDataLength``(java.lang.String dataName)`<br>Returns the link user data length                                                                      |
    | `java.lang.String[]`                                | `getLinkDataNames``()`<br>Returns the link user data names in a String array                                                                               |
    | `java.lang.String[]`                                | `getLinkDataNames``(int category)`<br>Returns the link user data names in a String array                                                                   |
    | `java.lang.String`                                  | `getLinkDataType``(java.lang.String dataName)`<br>Returns the link user data type of the given data name                                                   |
    | `java.lang.String`                                  | `getNetworkName``()`<br>Returns the network name                                                                                                           |
    | `java.util.Map<java.lang.String,java.lang.Integer>` | `getNodeDataIndexMap``(int category)`<br>Returns the node user data index map.                                                                             |
    | `int`                                               | `getNodeDataLength``(java.lang.String dataName)`<br>Returns the node user data length                                                                      |
    | `java.lang.String[]`                                | `getNodeDataNames``()`<br>Returns the node user data names in a String array                                                                               |
    | `java.lang.String[]`                                | `getNodeDataNames``(int category)`<br>Returns the node user data names in a String array                                                                   |
    | `java.lang.String`                                  | `getNodeDataType``(java.lang.String dataName)`<br>Returns the node user data type of the given data name                                                   |
    | `int`                                               | `getNumberOfCategories``()`<br>Returns the number of user data categories.                                                                                 |
    | `java.util.Map<java.lang.String,java.lang.Integer>` | `getPathDataIndexMap``(int category)`<br>Returns the path user data index map.                                                                             |
    | `int`                                               | `getPathDataLength``(java.lang.String dataName)`<br>Returns the path user data length                                                                      |
    | `java.lang.String[]`                                | `getPathDataNames``()`<br>Returns the path user data names in a String array                                                                               |
    | `java.lang.String[]`                                | `getPathDataNames``(int category)`<br>Returns the path user data names in a String array                                                                   |
    | `java.lang.String`                                  | `getPathDataType``(java.lang.String dataName)`<br>Returns the path user data type of the given data name                                                   |
    | `java.util.Map<java.lang.String,java.lang.Integer>` | `getSubPathDataIndexMap``(int category)`<br>Returns the subpath user data index map.                                                                       |
    | `int`                                               | `getSubPathDataLength``(java.lang.String dataName)`<br>Returns the subpath user data length                                                                |
    | `java.lang.String[]`                                | `getSubPathDataNames``()`<br>Returns the subpath user data names in a String array                                                                         |
    | `java.lang.String[]`                                | `getSubPathDataNames``(int category)`<br>Returns the subpath user data names in a String array                                                             |
    | `java.lang.String`                                  | `getSubPathDataType``(java.lang.String dataName)`<br>Returns the subpath user data type of the given data name                                             |
    | `java.lang.String[]`                                | `getSupportedDataTypes``()`<br>Returns all surported data type in the user data metadata                                                                   |
    | `int`                                               | `getUserDataIndex``(java.lang.String tableType, java.lang.String dataName, int category)`<br>Returns the user data index.                                  |
    | `java.util.Map<java.lang.String,java.lang.Integer>` | `getUserDataIndexMap``(java.lang.String tableType, int category)`<br>Returns the user data index map for the specified table type or feature layer name.   |
    | `int`                                               | `getUserDataLength``(java.lang.String tableType, java.lang.String dataName)`<br>Returns the user data length                                               |
    | `java.lang.String[]`                                | `getUserDataNames``(java.lang.String tableType)`<br>Returns the user data names in the default category for the specified table type                       |
    | `java.lang.String[]`                                | `getUserDataNames``(java.lang.String tableType, int category)`<br>Returns the user data names in the given category for the specified table type           |
    | `java.lang.String`                                  | `getUserDataType``(java.lang.String tableType, java.lang.String dataName)`<br>Returns the user data type for the give data name                            |
    | `boolean`                                           | `isEmpty``()`<br>Checks if the metadata contains any data                                                                                                  |
    | `boolean`                                           | `validDataType``(java.lang.String dataType)`<br>Checks if the given data type is supported                                                                 |

<!-- -->

- - ### Field Detail

    - #### NODE_TABLE_TYPE

          static final java.lang.String NODE_TABLE_TYPE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LINK_TABLE_TYPE

          static final java.lang.String LINK_TABLE_TYPE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PATH_TABLE_TYPE

          static final java.lang.String PATH_TABLE_TYPE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SUBPATH_TABLE_TYPE

          static final java.lang.String SUBPATH_TABLE_TYPE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### INTEGER_TYPE

          static final java.lang.String INTEGER_TYPE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NUMBER_TYPE

          static final java.lang.String NUMBER_TYPE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### VARCHAR2_TYPE

          static final java.lang.String VARCHAR2_TYPE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SDO_GEOMETRY_TYPE

          static final java.lang.String SDO_GEOMETRY_TYPE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DATE_TYPE

          static final java.lang.String DATE_TYPE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TIMESTAMP_TYPE

          static final java.lang.String TIMESTAMP_TYPE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### OBJECT_TYPE

          static final java.lang.String OBJECT_TYPE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DEFAULT_USER_DATA_CATEGORY

          static final int DEFAULT_USER_DATA_CATEGORY

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getNetworkName

          java.lang.String getNetworkName()

      Returns the network name

    <!-- -->

    - #### getUserDataNames

          java.lang.String[] getUserDataNames(java.lang.String tableType)

      Returns the user data names in the default category for the specified table type
      Parameters:

      `tableType` - table type or feature layer name

      Returns:

    <!-- -->

    - #### getNodeDataNames

          java.lang.String[] getNodeDataNames()

      Returns the node user data names in a String array

    <!-- -->

    - #### getLinkDataNames

          java.lang.String[] getLinkDataNames()

      Returns the link user data names in a String array

    <!-- -->

    - #### getPathDataNames

          java.lang.String[] getPathDataNames()

      Returns the path user data names in a String array

    <!-- -->

    - #### getSubPathDataNames

          java.lang.String[] getSubPathDataNames()

      Returns the subpath user data names in a String array

    <!-- -->

    - #### getUserDataNames

          java.lang.String[] getUserDataNames(java.lang.String tableType,
                                              int category)

      Returns the user data names in the given category for the specified table type
      Parameters:

      `tableType` - table type or feature layer name

      `category` -

      Returns:

    <!-- -->

    - #### getNodeDataNames

          java.lang.String[] getNodeDataNames(int category)

      Returns the node user data names in a String array

    <!-- -->

    - #### getLinkDataNames

          java.lang.String[] getLinkDataNames(int category)

      Returns the link user data names in a String array

    <!-- -->

    - #### getPathDataNames

          java.lang.String[] getPathDataNames(int category)

      Returns the path user data names in a String array

    <!-- -->

    - #### getSubPathDataNames

          java.lang.String[] getSubPathDataNames(int category)

      Returns the subpath user data names in a String array

    <!-- -->

    - #### getUserDataType

          java.lang.String getUserDataType(java.lang.String tableType,
                                           java.lang.String dataName)

      Returns the user data type for the give data name
      Parameters:
      `tableType` - table type of feature layer name

      `dataName` - node user data name

    <!-- -->

    - #### getNodeDataType

          java.lang.String getNodeDataType(java.lang.String dataName)

      Returns the node user data type of the given data name
      Parameters:
      `dataName` - node user data name

    <!-- -->

    - #### getLinkDataType

          java.lang.String getLinkDataType(java.lang.String dataName)

      Returns the link user data type of the given data name
      Parameters:
      `dataName` - link user data name

    <!-- -->

    - #### getPathDataType

          java.lang.String getPathDataType(java.lang.String dataName)

      Returns the path user data type of the given data name
      Parameters:
      `dataName` - path user data name

    <!-- -->

    - #### getSubPathDataType

          java.lang.String getSubPathDataType(java.lang.String dataName)

      Returns the subpath user data type of the given data name
      Parameters:
      `dataName` - subpath user data name

    <!-- -->

    - #### getUserDataLength

          int getUserDataLength(java.lang.String tableType,
                                java.lang.String dataName)

      Returns the user data length
      Parameters:
      `tableType` - table type or feature layer name

      `dataName` - user data name

    <!-- -->

    - #### getNodeDataLength

          int getNodeDataLength(java.lang.String dataName)

      Returns the node user data length
      Parameters:
      `dataName` - node user data name

    <!-- -->

    - #### getLinkDataLength

          int getLinkDataLength(java.lang.String dataName)

      Returns the link user data length
      Parameters:
      `dataName` - link user data name

    <!-- -->

    - #### getPathDataLength

          int getPathDataLength(java.lang.String dataName)

      Returns the path user data length
      Parameters:
      `dataName` - path user data name

    <!-- -->

    - #### getSubPathDataLength

          int getSubPathDataLength(java.lang.String dataName)

      Returns the subpath user data length
      Parameters:
      `dataName` - path user data name

    <!-- -->

    - #### addNodeData

          void addNodeData(java.lang.String dataName,
                           java.lang.String dataType,
                           int dataLength,
                           int categoryId)
                    throws NetworkDataException

      Adds a node user data entry to the metadata
      Parameters:
      `dataName` - node user data name

      `dataType` - node user data type

      `dataLength` - node user data length if applicable

      Throws:
      [`NetworkDataException`](NetworkDataException.md) - if such entry already exists

    <!-- -->

    - #### addLinkData

          void addLinkData(java.lang.String dataName,
                           java.lang.String dataType,
                           int dataLength,
                           int categoryId)
                    throws NetworkDataException

      Adds a link user data entry to the metadata
      Parameters:
      `dataName` - link user data name

      `dataType` - link user data type

      `dataLength` - link user data length if applicable

      Throws:
      [`NetworkDataException`](NetworkDataException.md) - if such entry already exists

    <!-- -->

    - #### addPathData

          void addPathData(java.lang.String dataName,
                           java.lang.String dataType,
                           int dataLength,
                           int categoryId)
                    throws NetworkDataException

      Adds a path user data entry to the metadata
      Parameters:
      `dataName` - path user data name

      `dataType` - path user data type

      `dataLength` - path user data length if applicable

      Throws:
      [`NetworkDataException`](NetworkDataException.md) - if such entry already exists

    <!-- -->

    - #### addSubPathData

          void addSubPathData(java.lang.String dataName,
                              java.lang.String dataType,
                              int dataLength,
                              int categoryId)
                       throws NetworkDataException

      Adds a subpath user data entry to the metadata
      Parameters:
      `dataName` - subpath user data name

      `dataType` - subpath user data type

      `dataLength` - subpath user data length if applicable

      Throws:
      [`NetworkDataException`](NetworkDataException.md) - if such entry already exists

    <!-- -->

    - #### deleteNodeData

          void deleteNodeData(java.lang.String dataName)

      Deletes a node user data entry from the metadata
      Parameters:
      `dataName` - node user data name

    <!-- -->

    - #### deleteLinkData

          void deleteLinkData(java.lang.String dataName)

      Deletes a link user data entry from the metadata
      Parameters:
      `dataName` - link user data name

    <!-- -->

    - #### deletePathData

          void deletePathData(java.lang.String dataName)

      Deletes a path user data entry from the metadata
      Parameters:
      `dataName` - path user data name

    <!-- -->

    - #### deleteSubPathData

          void deleteSubPathData(java.lang.String dataName)

      Deletes a subpath user data entry from the metadata
      Parameters:
      `dataName` - subpath user data name

    <!-- -->

    - #### getSupportedDataTypes

          java.lang.String[] getSupportedDataTypes()

      Returns all surported data type in the user data metadata
      Returns:
      an array of String

    <!-- -->

    - #### validDataType

          boolean validDataType(java.lang.String dataType)

      Checks if the given data type is supported
      Parameters:
      `dataType` - data type

      Returns:
      true if supported, false otherwise

    <!-- -->

    - #### isEmpty

          boolean isEmpty()

      Checks if the metadata contains any data

    <!-- -->

    - #### containsNodeUserData

          boolean containsNodeUserData(java.lang.String dataName)

      Checks if the given node user data name exists
      Parameters:
      `dataName` - node user data name

    <!-- -->

    - #### containsLinkUserData

          boolean containsLinkUserData(java.lang.String dataName)

      Checks if the given link user data name exists
      Parameters:
      `dataName` - link user data name

    <!-- -->

    - #### containsPathUserData

          boolean containsPathUserData(java.lang.String dataName)

      Checks if the given path user data name exists
      Parameters:
      `dataName` - path user data name

    <!-- -->

    - #### containsSubPathUserData

          boolean containsSubPathUserData(java.lang.String dataName)

      Checks if the given subpath user data name exists
      Parameters:
      `dataName` - subpath user data name

    <!-- -->

    - #### getUserDataIndexMap

          java.util.Map<java.lang.String,java.lang.Integer> getUserDataIndexMap(java.lang.String tableType,
                                                                                int category)

      Returns the user data index map for the specified table type or feature layer name.
      Returns:

    <!-- -->

    - #### getUserDataIndex

          int getUserDataIndex(java.lang.String tableType,
                               java.lang.String dataName,
                               int category)

      Returns the user data index.
      Parameters:

      `tableType` - table type or feature layer name

      `dataName` - user data name

      Returns:

    <!-- -->

    - #### getNodeDataIndexMap

          java.util.Map<java.lang.String,java.lang.Integer> getNodeDataIndexMap(int category)

      Returns the node user data index map.
      Returns:

    <!-- -->

    - #### getLinkDataIndexMap

          java.util.Map<java.lang.String,java.lang.Integer> getLinkDataIndexMap(int category)

      Returns the link user data index map.
      Returns:

    <!-- -->

    - #### getPathDataIndexMap

          java.util.Map<java.lang.String,java.lang.Integer> getPathDataIndexMap(int category)

      Returns the path user data index map.
      Returns:

    <!-- -->

    - #### getSubPathDataIndexMap

          java.util.Map<java.lang.String,java.lang.Integer> getSubPathDataIndexMap(int category)

      Returns the subpath user data index map.
      Returns:

    <!-- -->

    - #### getNumberOfCategories

          int getNumberOfCategories()

      Returns the number of user data categories.
      Returns:

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

- [Prev Class](UserDataIO.md)
- Next Class

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
