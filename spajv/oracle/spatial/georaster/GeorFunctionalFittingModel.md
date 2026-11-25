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

- [Prev Class](GeorColormapEntry.md)
- [Next Class](GeorGrayscale.md)

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

oracle.spatial.georaster

## Class GeorFunctionalFittingModel

- java.lang.Object

- - oracle.spatial.georaster.GeorFunctionalFittingModel

<!-- -->

-

  ------------------------------------------------------------------------



      public class GeorFunctionalFittingModel
      extends java.lang.Object

  GeorFunctionFittingModel is a Java class that maps to the XML type rationalPolynomialType defined in the GeoRaster XML schema. A set of get/set APIs is provided to retrieve and set each attribute defined in this georeference model, and four methods are provided to transform 2D/3D coordinates between cell space and model space based on the current setting of this class.
  In the class SpatialReferenceInfo, the following methods are defined to get/set the function fitting model through a GeorFunctionFittingModel instance:

          public GeorFunctionFittingModel getFunctionFittingModel();
          public void setFunctionFittingModel(GeorFunctionalFittingModel srs);


<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                           |
    |---------------------------------------------------------------------------------------|
    | `GeorFunctionalFittingModel``()`<br>Constructs a `GeorFunctionalFittingModel` object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                           |
    |--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
    | `double[]`         | `directTransform2D``(double x, double y)`<br>Given (X,Y) model coordinates, computes its (row, column) cell coordinates.                         |
    | `double[]`         | `directTransform3D``(double x, double y, double z)`<br>Given (X,Y,Z) model coordinates, computes its (row, column) cell coordinates.             |
    | `java.util.Vector` | `getColDenominator``()`<br>Returns the colDenominator vector.                                                                                    |
    | `java.util.Vector` | `getColNumerator``()`<br>Returns the colNumerator vector.                                                                                        |
    | `double`           | `getColumnOff``()`<br>Returns the columnOff value.                                                                                               |
    | `java.lang.Double` | `getColumnRMS``()`<br>Returns the columnRMS value.                                                                                               |
    | `double`           | `getColumnScale``()`<br>Returns the columnScale value.                                                                                           |
    | `java.util.Vector` | `getRowDenominator``()`<br>Returns the rowDenominator vector.                                                                                    |
    | `java.util.Vector` | `getRowNumerator``()`<br>Returns the rowNumerator vector.                                                                                        |
    | `double`           | `getRowOff``()`<br>Returns the rowOff value.                                                                                                     |
    | `java.lang.Double` | `getRowRMS``()`<br>Returns the rowRMS value.                                                                                                     |
    | `double`           | `getRowScale``()`<br>Returns the rowScale value.                                                                                                 |
    | `java.lang.Double` | `getTotalRMS``()`<br>Returns the totalRMS value.                                                                                                 |
    | `double`           | `getXOff``()`<br>Returns the xOff value.                                                                                                         |
    | `double`           | `getXScale``()`<br>Returns the xScale value.                                                                                                     |
    | `double`           | `getYOff``()`<br>Returns the yOff value.                                                                                                         |
    | `double`           | `getYScale``()`<br>Returns the yScale value.                                                                                                     |
    | `double`           | `getZOff``()`<br>Returns the zOff value.                                                                                                         |
    | `double`           | `getZScale``()`<br>Returns the zScale value.                                                                                                     |
    | `double[]`         | `inverseTransform2D``(double row, double column)`<br>Given (row, column) cell coordinates, computes the (X,Y) model coordinates.                 |
    | `double[]`         | `inverseTransform3D``(double row, double column, double z)`<br>Given (row, column) cell coordinates and z, computes the (X,Y) model coordinates. |
    | `void`             | `setColDenominator``(java.util.Vector colDenominator)`<br>Sets the colDenominator vector.                                                        |
    | `void`             | `setColNumerator``(java.util.Vector colNumerator)`<br>Sets the colNumerator vector.                                                              |
    | `void`             | `setColumnOff``(double columnOff)`<br>Sets the columnOff value.                                                                                  |
    | `void`             | `setColumnRMS``(java.lang.Double columnRMS)`<br>Sets the columnRMS value.                                                                        |
    | `void`             | `setColumnScale``(double columnScale)`<br>Sets the columnScale value.                                                                            |
    | `void`             | `setRowDenominator``(java.util.Vector rowDenominator)`<br>Sets the rowDenominator vector.                                                        |
    | `void`             | `setRowNumerator``(java.util.Vector rowNumerator)`<br>Sets the rowNumerator vector.                                                              |
    | `void`             | `setRowOff``(double rowOff)`<br>Sets the rowOff value.                                                                                           |
    | `void`             | `setRowRMS``(java.lang.Double rowRMS)`<br>Sets the rowRMS value.                                                                                 |
    | `void`             | `setRowScale``(double rowScale)`<br>Sets the rowScale value.                                                                                     |
    | `void`             | `setTotalRMS``(java.lang.Double totalRMS)`<br>Sets the totalRMS value.                                                                           |
    | `void`             | `setXOff``(double xOff)`<br>Sets the xOff value.                                                                                                 |
    | `void`             | `setXScale``(double xScale)`<br>Sets the xScale value.                                                                                           |
    | `void`             | `setYOff``(double yOff)`<br>Sets the yOff value.                                                                                                 |
    | `void`             | `setYScale``(double yScale)`<br>Sets the yScale value.                                                                                           |
    | `void`             | `setZOff``(double zOff)`<br>Sets the zOff value.                                                                                                 |
    | `void`             | `setZScale``(double zScale)`<br>Sets the zScale value.                                                                                           |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GeorFunctionalFittingModel

          public GeorFunctionalFittingModel()

      Constructs a `GeorFunctionalFittingModel` object.

  <!-- -->

  - ### Method Detail

    - #### getRowOff

          public double getRowOff()

      Returns the rowOff value.
      Returns:
      rowOff value.

    <!-- -->

    - #### setRowOff

          public void setRowOff(double rowOff)

      Sets the rowOff value.
      Parameters:
      `rowOff` - rowOff value

    <!-- -->

    - #### getColumnOff

          public double getColumnOff()

      Returns the columnOff value.
      Returns:
      columnOff value.

    <!-- -->

    - #### setColumnOff

          public void setColumnOff(double columnOff)

      Sets the columnOff value.
      Parameters:
      `columnOff` - columnOff value

    <!-- -->

    - #### getXOff

          public double getXOff()

      Returns the xOff value.
      Returns:
      xOff value.

    <!-- -->

    - #### setXOff

          public void setXOff(double xOff)

      Sets the xOff value.
      Parameters:
      `xOff` - xOff value

    <!-- -->

    - #### getYOff

          public double getYOff()

      Returns the yOff value.
      Returns:
      yOff value.

    <!-- -->

    - #### setYOff

          public void setYOff(double yOff)

      Sets the yOff value.
      Parameters:
      `yOff` - yOff value

    <!-- -->

    - #### getZOff

          public double getZOff()

      Returns the zOff value.
      Returns:
      zOff value.

    <!-- -->

    - #### setZOff

          public void setZOff(double zOff)

      Sets the zOff value.
      Parameters:
      `zOff` - zOff value

    <!-- -->

    - #### getRowScale

          public double getRowScale()

      Returns the rowScale value.
      Returns:
      rowScale value.

    <!-- -->

    - #### setRowScale

          public void setRowScale(double rowScale)

      Sets the rowScale value.
      Parameters:
      `rowScale` - rowScale value

    <!-- -->

    - #### getColumnScale

          public double getColumnScale()

      Returns the columnScale value.
      Returns:
      columnScale value.

    <!-- -->

    - #### setColumnScale

          public void setColumnScale(double columnScale)

      Sets the columnScale value.
      Parameters:
      `columnScale` - columnScale value

    <!-- -->

    - #### getXScale

          public double getXScale()

      Returns the xScale value.
      Returns:
      xScale value.

    <!-- -->

    - #### setXScale

          public void setXScale(double xScale)

      Sets the xScale value.
      Parameters:
      `xScale` - xScale value

    <!-- -->

    - #### getYScale

          public double getYScale()

      Returns the yScale value.
      Returns:
      yScale value.

    <!-- -->

    - #### setYScale

          public void setYScale(double yScale)

      Sets the yScale value.
      Parameters:
      `yScale` - yScale value

    <!-- -->

    - #### getZScale

          public double getZScale()

      Returns the zScale value.
      Returns:
      zScale value.

    <!-- -->

    - #### setZScale

          public void setZScale(double zScale)

      Sets the zScale value.
      Parameters:
      `zScale` - zScale value

    <!-- -->

    - #### getRowRMS

          public java.lang.Double getRowRMS()

      Returns the rowRMS value.
      Returns:
      rowRMS value.

    <!-- -->

    - #### setRowRMS

          public void setRowRMS(java.lang.Double rowRMS)

      Sets the rowRMS value.
      Parameters:
      `rowRMS` - rowRMS value

    <!-- -->

    - #### getColumnRMS

          public java.lang.Double getColumnRMS()

      Returns the columnRMS value.
      Returns:
      columnRMS value.

    <!-- -->

    - #### setColumnRMS

          public void setColumnRMS(java.lang.Double columnRMS)

      Sets the columnRMS value.
      Parameters:
      `columnRMS` - columnRMS value

    <!-- -->

    - #### getTotalRMS

          public java.lang.Double getTotalRMS()

      Returns the totalRMS value.
      Returns:
      totalRMS value.

    <!-- -->

    - #### setTotalRMS

          public void setTotalRMS(java.lang.Double totalRMS)

      Sets the totalRMS value.
      Parameters:
      `totalRMS` - totalRMS value

    <!-- -->

    - #### getRowNumerator

          public java.util.Vector getRowNumerator()

      Returns the rowNumerator vector.
      Returns:
      rowNumerator vector.

    <!-- -->

    - #### setRowNumerator

          public void setRowNumerator(java.util.Vector rowNumerator)

      Sets the rowNumerator vector.
      Parameters:
      `rowNumerator` - rowNumerator vector

    <!-- -->

    - #### getRowDenominator

          public java.util.Vector getRowDenominator()

      Returns the rowDenominator vector.
      Returns:
      rowDenominator vector.

    <!-- -->

    - #### setRowDenominator

          public void setRowDenominator(java.util.Vector rowDenominator)

      Sets the rowDenominator vector.
      Parameters:
      `rowDenominator` - rowDenominator vector

    <!-- -->

    - #### getColNumerator

          public java.util.Vector getColNumerator()

      Returns the colNumerator vector.
      Returns:
      colNumerator vector.

    <!-- -->

    - #### setColNumerator

          public void setColNumerator(java.util.Vector colNumerator)

      Sets the colNumerator vector.
      Parameters:
      `colNumerator` - colNumerator vector

    <!-- -->

    - #### getColDenominator

          public java.util.Vector getColDenominator()

      Returns the colDenominator vector.
      Returns:
      colDenominator vector.

    <!-- -->

    - #### setColDenominator

          public void setColDenominator(java.util.Vector colDenominator)

      Sets the colDenominator vector.
      Parameters:
      `colDenominator` - colDenominator vector

    <!-- -->

    - #### directTransform2D

          public double[] directTransform2D(double x,
                                            double y)

      Given (X,Y) model coordinates, computes its (row, column) cell coordinates.
      Parameters:
      `x` - input x.

      `y` - input y.

      Returns:
      return (row,column) array.

    <!-- -->

    - #### directTransform3D

          public double[] directTransform3D(double x,
                                            double y,
                                            double z)

      Given (X,Y,Z) model coordinates, computes its (row, column) cell coordinates.
      Parameters:
      `x` - input x.

      `y` - input y.

      `z` - input z.

      Returns:
      return (row,column) array.

    <!-- -->

    - #### inverseTransform2D

          public double[] inverseTransform2D(double row,
                                             double column)

      Given (row, column) cell coordinates, computes the (X,Y) model coordinates.
      Parameters:
      `row` - input row

      `column` - input column

      Returns:
      return (x,y)array.

    <!-- -->

    - #### inverseTransform3D

          public double[] inverseTransform3D(double row,
                                             double column,
                                             double z)

      Given (row, column) cell coordinates and z, computes the (X,Y) model coordinates.
      Parameters:
      `row` - input row

      `column` - input column

      `z` - input z

      Returns:
      return (x,y)array.

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

- [Prev Class](GeorColormapEntry.md)
- [Next Class](GeorGrayscale.md)

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
