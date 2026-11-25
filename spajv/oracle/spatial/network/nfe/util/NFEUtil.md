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

- [Prev Class](NFEResources.md)
- [Next Class](PathUtil.md)

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

oracle.spatial.network.nfe.util

## Class NFEUtil

- java.lang.Object

- - oracle.spatial.network.nfe.util.NFEUtil

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFEUtil
      extends java.lang.Object

  Provides some utilities functions used by NFE.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEUtil``()`               |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type         | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                            |
    |---------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `getCostExpression``(`[`AnalysisCustomizedCost`](../beans/AnalysisCustomizedCost.md)` analysisCustomizedCost, `[`NFEFeatureLayer`](../model/feature/NFEFeatureLayer.md)` featureLayer, `[`NFEFeatureClass`](../model/feature/NFEFeatureClass.md)` featureClass)`<br>Returns the customized expression (analysisCustomizedCost.getExpression) if the customized cost applies to the featureLayer and featureClass, null otherwise. |
    | `static double`           | `getCustCostOfLink``(java.sql.Connection conn, `[`NFEModel`](../model/NFEModel.md)` nfeModel, java.util.List<`[`AnalysisCustomizedCost`](../beans/AnalysisCustomizedCost.md)`> analysisCustomizedCosts, java.lang.Long linkId, `[`NFEExpressionAnalyzer`](../expression/NFEExpressionAnalyzer.md)` nfeExpressionAnalyzer)`<br>Returns the link custom cost.                                                                       |
    | `static java.lang.String` | `getErrorMessage``(java.lang.String exceptionMessage)`<br>Extracts the error message from an exception message.                                                                                                                                                                                                                                                                                                                   |
    | `static byte[]`           | `getFileAsByteArray``(java.lang.String fileName)`<br>Returns the file in path oracle/spatial/network/nfe/images/imageName                                                                                                                                                                                                                                                                                                         |
    | `static java.lang.Object` | `getResultSetColumnValue``(java.sql.ResultSet resultSet, java.lang.String columnName, `[`NFEAttributeType`](../model/feature/NFEAttributeType.md)` expectedType)`<br>Returns the column value of the result set.                                                                                                                                                                                                                  |
    | `static java.lang.String` | `getSQLInStringWithLimit``(java.util.List<java.lang.Long> ids, java.lang.String columnToBeUsed, int limit)`<br>Creates a SQL string in format: columnToBeUsed IN (id\[1\], id\[2\],...id\[limit\]) OR IN (id\[x\], id\[x+1\],...id\[x+limit\])                                                                                                                                                                                    |
    | `static java.lang.String` | `getStringWithoutLastComma``(java.lang.String s)`<br>Gets a substring from the string start to the first comma.                                                                                                                                                                                                                                                                                                                   |
    | `static boolean`          | `isEmpty``(java.lang.String propertyValue)`<br>Checks for nulls and empty strings.                                                                                                                                                                                                                                                                                                                                                |
    | `static java.lang.Object` | `toAttributeType``(java.lang.String strValue, `[`NFEAttributeDescriptor`](../model/feature/NFEAttributeDescriptor.md)` attrDesc)`<br>Returns the string value in the type of the specified attribute.                                                                                                                                                                                                                             |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEUtil

          public NFEUtil()

  <!-- -->

  - ### Method Detail

    - #### isEmpty

          public static boolean isEmpty(java.lang.String propertyValue)

      Checks for nulls and empty strings.
      Parameters:
      `propertyValue` - string to be evaluates

      Returns:
      true if propertyValue is null or empty, false otherwise

    <!-- -->

    - #### getStringWithoutLastComma

          public static java.lang.String getStringWithoutLastComma(java.lang.String s)

      Gets a substring from the string start to the first comma.
      Parameters:
      `s` - string

      Returns:
      substring from the string start to the first comma

    <!-- -->

    - #### getResultSetColumnValue

          public static java.lang.Object getResultSetColumnValue(java.sql.ResultSet resultSet,
                                                                 java.lang.String columnName,
                                                                 NFEAttributeType expectedType)
                                                          throws java.sql.SQLException

      Returns the column value of the result set. The returned result will be on the type expectedType. The mapping is as follows:
           NUMBER = resultSet.getDouble(columnName)
           INTEGER = resultSet.getLong(columnName)
           VARCHAR2 = resultSet.getString(columnName)
           DATE = resultSet.getDate(columnName)
           TIMESTAMP = resultSet.getTime(columnName)
           SDO_GEOMETRY = resultSet.getObject(columnName)


      Parameters:
      `resultSet` - result set

      `columnName` - column name

      `expectedType` - expected type

      Returns:
      column value

      Throws:
      `java.sql.SQLException` - if an SQL exception is thrown

    <!-- -->

    - #### toAttributeType

          public static java.lang.Object toAttributeType(java.lang.String strValue,
                                                         NFEAttributeDescriptor attrDesc)

      Returns the string value in the type of the specified attribute.
      Parameters:
      `strValue` - string

      `attrDesc` - attribute

      Returns:
      the string value in the type of the specified attribute

    <!-- -->

    - #### getSQLInStringWithLimit

          public static java.lang.String getSQLInStringWithLimit(java.util.List<java.lang.Long> ids,
                                                                 java.lang.String columnToBeUsed,
                                                                 int limit)

      Creates a SQL string in format: columnToBeUsed IN (id\[1\], id\[2\],...id\[limit\]) OR IN (id\[x\], id\[x+1\],...id\[x+limit\])
      Parameters:
      `ids` - identifiers

      `columnToBeUsed` - column

      `limit` - limit

      Returns:
      SQL string

    <!-- -->

    - #### getErrorMessage

          public static java.lang.String getErrorMessage(java.lang.String exceptionMessage)

      Extracts the error message from an exception message.
      Parameters:
      `exceptionMessage` - Message from an exception. Format expected: "ORA-\[error-code\]: \[error-message\] \n\[posible-extra-information\]"

      Returns:
      the \[error-message\] contained in the exception Message, or the original string if the `exceptionMessage` format is not as indicated.

    <!-- -->

    - #### getCustCostOfLink

          public static double getCustCostOfLink(java.sql.Connection conn,
                                                 NFEModel nfeModel,
                                                 java.util.List<AnalysisCustomizedCost> analysisCustomizedCosts,
                                                 java.lang.Long linkId,
                                                 NFEExpressionAnalyzer nfeExpressionAnalyzer)

      Returns the link custom cost. This function can be used during the analysis.
      Parameters:
      `conn` - connection

      `nfeModel` - model

      `analysisCustomizedCosts` - customized cost data

      `linkId` - link identifier

      `nfeExpressionAnalyzer` - expression analyzer

      Returns:
      link custom cost

    <!-- -->

    - #### getCostExpression

          public static java.lang.String getCostExpression(AnalysisCustomizedCost analysisCustomizedCost,
                                                           NFEFeatureLayer featureLayer,
                                                           NFEFeatureClass featureClass)

      Returns the customized expression (analysisCustomizedCost.getExpression) if the customized cost applies to the featureLayer and featureClass, null otherwise.
      Parameters:
      `analysisCustomizedCost` - customized cost data

      `featureLayer` - feature layer

      `featureClass` - feature class

      Returns:
      customized expression if the customized cost applies to the featureLayer and featureClass, null otherwise

    <!-- -->

    - #### getFileAsByteArray

          public static byte[] getFileAsByteArray(java.lang.String fileName)

      Returns the file in path oracle/spatial/network/nfe/images/imageName
      Parameters:
      `fileName` - file name

      Returns:
      file in path oracle/spatial/network/nfe/images/imageName

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

- [Prev Class](NFEResources.md)
- [Next Class](PathUtil.md)

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
