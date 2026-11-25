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

- [Prev Class](GeorHistogramEntry.md)
- [Next Class](JGeoRaster.md)

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

## Class GeorSpatialReference

- java.lang.Object

- - oracle.spatial.georaster.GeorSpatialReference

<!-- -->

-

  ------------------------------------------------------------------------



      public class GeorSpatialReference
      extends java.lang.Object

  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                           |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `GeorSpatialReference``()`                                                                                                                                                                                                            |
    | `GeorSpatialReference``(`[`SpatialReferenceInfo`](SpatialReferenceInfo.md)` srs)`<br>GeorSpatialReference support the representation of a SDO_GEOR_SRS type and can be instantiated from a SpatialRerenceInfo object or from scracth. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type             | Method and Description                                                                                                                                                                                    |
    |-------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Double[]`          | `getColDenominator``()`<br>Get Column Denominator                                                                                                                                                         |
    | `java.lang.Double[]`          | `getColNumerator``()`<br>Get Column Numerator                                                                                                                                                             |
    | `java.lang.Double`            | `getColumnOff``()`<br>Get column offset                                                                                                                                                                   |
    | `java.lang.Double`            | `getColumnRMS``()`<br>Get column RMS                                                                                                                                                                      |
    | `java.lang.Double`            | `getColumnScale``()`<br>Get column scale                                                                                                                                                                  |
    | `java.lang.String`            | `getModelCoordinateLocation``()`<br>Get model coordinate location                                                                                                                                         |
    | `java.lang.Integer`           | `getModelSRID``()`<br>Get model SRID                                                                                                                                                                      |
    | `java.lang.Double`            | `getModelTotalRMS``()`<br>Get model total RMS                                                                                                                                                             |
    | `java.lang.Double[]`          | `getRowDenominator``()`<br>Get Row Denominator                                                                                                                                                            |
    | `java.lang.Double[]`          | `getRowNumerator``()`<br>Get row numerator                                                                                                                                                                |
    | `java.lang.Double`            | `getRowOff``()`<br>Get row offset                                                                                                                                                                         |
    | `java.lang.Double`            | `getRowRMS``()`<br>Get row RMS                                                                                                                                                                            |
    | `java.lang.Double`            | `getRowScale``()`<br>Get row scale                                                                                                                                                                        |
    | `java.lang.Double[]`          | `getSpatialResolutions``()`<br>Get Spatial Resolution of all dimensions:                                                                                                                                  |
    | `java.lang.Double`            | `getSpatialTolerance``()`<br>Get spatial tolerance                                                                                                                                                        |
    | `java.lang.Double`            | `getTotalRMS``()`<br>Get total RMS                                                                                                                                                                        |
    | `java.lang.Double`            | `getXOff``()`<br>Get x offset                                                                                                                                                                             |
    | `java.lang.Double`            | `getXRMS``()`<br>Get x RMS                                                                                                                                                                                |
    | `java.lang.Double`            | `getXScale``()`<br>Get x scale                                                                                                                                                                            |
    | `java.lang.Double`            | `getYOff``()`<br>Get x offset                                                                                                                                                                             |
    | `java.lang.Double`            | `getYRMS``()`<br>Get y RMS                                                                                                                                                                                |
    | `java.lang.Double`            | `getYScale``()`<br>Get y scale                                                                                                                                                                            |
    | `java.lang.Double`            | `getZOff``()`<br>Get z offset                                                                                                                                                                             |
    | `java.lang.Double`            | `getZRMS``()`<br>Get z RMS                                                                                                                                                                                |
    | `java.lang.Double`            | `getZScale``()`<br>Get z scale                                                                                                                                                                            |
    | `java.lang.Boolean`           | `isOrthoRectified``()`<br>Get true if spatial orthorectified is orthorectified, false if is not                                                                                                           |
    | `java.lang.Boolean`           | `isRectified``()`<br>Get true if spatial reference is rectified, false if is not                                                                                                                          |
    | `java.lang.Boolean`           | `isReferenced``()`<br>Get true if spatial reference is referenced, false if is not                                                                                                                        |
    | `static GeorSpatialReference` | `loadJS``(java.sql.Struct srs)`                                                                                                                                                                           |
    | `void`                        | `setColDenominator``(java.lang.Integer pType, java.lang.Integer nVars, java.lang.Integer order, java.util.Vector coefficients)`<br>Create an array with Column Denominator                                |
    | `void`                        | `setColNumerator``(java.lang.Integer pType, java.lang.Integer nVars, java.lang.Integer order, java.util.Vector coefficients)`<br>Create an array with Column Numerator                                    |
    | `void`                        | `setColumnOff``(java.lang.Double value)`<br>Set column offset                                                                                                                                             |
    | `void`                        | `setColumnRMS``(java.lang.Double value)`<br>Set column RMS                                                                                                                                                |
    | `void`                        | `setColumnScale``(java.lang.Double value)`<br>Set column scale                                                                                                                                            |
    | `void`                        | `setModelCoordinateLocation``(java.lang.String value)`<br>Set model coordinate location                                                                                                                   |
    | `void`                        | `setModelSRID``(java.lang.Integer value)`<br>Set model SRID                                                                                                                                               |
    | `void`                        | `setModelTotalRMS``(java.lang.Double value)`<br>Set model total RMS                                                                                                                                       |
    | `void`                        | `setOrthoRectified``(java.lang.Boolean value)`<br>Set true if spatial orthorectified is referenced, false if is not                                                                                       |
    | `void`                        | `setRectified``(java.lang.Boolean value)`<br>Set true if spatial reference is referenced, false if is not                                                                                                 |
    | `void`                        | `setReferenced``(java.lang.Boolean value)`<br>Set true if spatial reference is referenced, false if is not                                                                                                |
    | `void`                        | `setRowDenominator``(java.lang.Integer pType, java.lang.Integer nVars, java.lang.Integer order, java.util.Vector coefficients)`<br>Create an array with Row Denominator                                   |
    | `void`                        | `setRowNumerator``(java.lang.Integer pType, java.lang.Integer nVars, java.lang.Integer order, java.util.Vector coefficients)`<br>Create an array with Row Numerator                                       |
    | `void`                        | `setRowOff``(java.lang.Double value)`<br>Set row offset                                                                                                                                                   |
    | `void`                        | `setRowRMS``(java.lang.Double value)`<br>Set row RMS                                                                                                                                                      |
    | `void`                        | `setRowScale``(java.lang.Double value)`<br>Set row scale                                                                                                                                                  |
    | `void`                        | `setSpatialResolutions``(java.lang.Double xResolution, java.lang.Double yResolution, java.lang.Double tResolution, java.lang.Double zResolution)`<br>Set Spatial X, Y, T (time) and Z (hight) Resolutions |
    | `void`                        | `setSpatialTolerance``(java.lang.Double value)`<br>Set spatial tolerance                                                                                                                                  |
    | `void`                        | `setTotalRMS``(java.lang.Double value)`<br>Set total RMS                                                                                                                                                  |
    | `void`                        | `setXOff``(java.lang.Double value)`<br>Set z offset                                                                                                                                                       |
    | `void`                        | `setXRMS``(java.lang.Double value)`<br>Set x RMS                                                                                                                                                          |
    | `void`                        | `setXScale``(java.lang.Double value)`<br>Set x scale                                                                                                                                                      |
    | `void`                        | `setYOff``(java.lang.Double value)`<br>Set y offset                                                                                                                                                       |
    | `void`                        | `setYRMS``(java.lang.Double value)`<br>Set y RMS                                                                                                                                                          |
    | `void`                        | `setYScale``(java.lang.Double value)`<br>Set y scale                                                                                                                                                      |
    | `void`                        | `setZOff``(java.lang.Double value)`<br>Set z offset                                                                                                                                                       |
    | `void`                        | `setZRMS``(java.lang.Double value)`<br>Set z RMS                                                                                                                                                          |
    | `void`                        | `setZScale``(java.lang.Double value)`<br>St z scale                                                                                                                                                       |
    | `java.sql.Struct`             | `toSTRUCT``(java.sql.Connection conn)`<br>Converts the Spatial Reference information into an Oracle JDBC Struct object.                                                                                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GeorSpatialReference

          public GeorSpatialReference()

    <!-- -->

    - #### GeorSpatialReference

          public GeorSpatialReference(SpatialReferenceInfo srs)
                               throws GeoRasterException

      GeorSpatialReference support the representation of a SDO_GEOR_SRS type and can be instantiated from a SpatialRerenceInfo object or from scracth.
      Parameters:
      `srs` - an SpatialReferenceInfo object

      Throws:
      [`GeoRasterException`](GeoRasterException.md)

  <!-- -->

  - ### Method Detail

    - #### isRectified

          public java.lang.Boolean isRectified()

      Get true if spatial reference is rectified, false if is not
      Returns:

    <!-- -->

    - #### setRectified

          public void setRectified(java.lang.Boolean value)

      Set true if spatial reference is referenced, false if is not
      Parameters:
      `value` -

    <!-- -->

    - #### isReferenced

          public java.lang.Boolean isReferenced()

      Get true if spatial reference is referenced, false if is not
      Returns:

    <!-- -->

    - #### setReferenced

          public void setReferenced(java.lang.Boolean value)

      Set true if spatial reference is referenced, false if is not
      Parameters:
      `value` -

    <!-- -->

    - #### isOrthoRectified

          public java.lang.Boolean isOrthoRectified()

      Get true if spatial orthorectified is orthorectified, false if is not
      Returns:

    <!-- -->

    - #### setOrthoRectified

          public void setOrthoRectified(java.lang.Boolean value)

      Set true if spatial orthorectified is referenced, false if is not
      Parameters:
      `value` -

    <!-- -->

    - #### getModelCoordinateLocation

          public java.lang.String getModelCoordinateLocation()

      Get model coordinate location
      Returns:

    <!-- -->

    - #### setModelCoordinateLocation

          public void setModelCoordinateLocation(java.lang.String value)

      Set model coordinate location
      Parameters:
      `value` - "CENTER" "UPPERLEFT"

    <!-- -->

    - #### getModelSRID

          public java.lang.Integer getModelSRID()

      Get model SRID
      Returns:

    <!-- -->

    - #### setModelSRID

          public void setModelSRID(java.lang.Integer value)

      Set model SRID
      Parameters:
      `value` -

    <!-- -->

    - #### getSpatialTolerance

          public java.lang.Double getSpatialTolerance()

      Get spatial tolerance
      Returns:

    <!-- -->

    - #### setSpatialTolerance

          public void setSpatialTolerance(java.lang.Double value)

      Set spatial tolerance
      Parameters:
      `value` -

    <!-- -->

    - #### setSpatialResolutions

          public void setSpatialResolutions(java.lang.Double xResolution,
                                            java.lang.Double yResolution,
                                            java.lang.Double tResolution,
                                            java.lang.Double zResolution)

      Set Spatial X, Y, T (time) and Z (hight) Resolutions
      Parameters:
      `xResolution` -

      `yResolution` -

      `tResolution` -

      `zResolution` -

    <!-- -->

    - #### getSpatialResolutions

          public java.lang.Double[] getSpatialResolutions()

      Get Spatial Resolution of all dimensions:
      Returns:
      on return\[0\] X Resolution on return\[1\] Y Resolution on return\[2\] T (time) Resolution on return\[3\] Z (hight) Resolution

    <!-- -->

    - #### getRowOff

          public java.lang.Double getRowOff()

      Get row offset
      Returns:

    <!-- -->

    - #### setRowOff

          public void setRowOff(java.lang.Double value)

      Set row offset
      Parameters:
      `value` -

    <!-- -->

    - #### getColumnOff

          public java.lang.Double getColumnOff()

      Get column offset
      Returns:

    <!-- -->

    - #### setColumnOff

          public void setColumnOff(java.lang.Double value)

      Set column offset
      Parameters:
      `value` -

    <!-- -->

    - #### getXOff

          public java.lang.Double getXOff()

      Get x offset
      Returns:

    <!-- -->

    - #### setXOff

          public void setXOff(java.lang.Double value)

      Set z offset
      Parameters:
      `value` -

    <!-- -->

    - #### getYOff

          public java.lang.Double getYOff()

      Get x offset
      Returns:

    <!-- -->

    - #### setYOff

          public void setYOff(java.lang.Double value)

      Set y offset
      Parameters:
      `value` -

    <!-- -->

    - #### getZOff

          public java.lang.Double getZOff()

      Get z offset
      Returns:

    <!-- -->

    - #### setZOff

          public void setZOff(java.lang.Double value)

      Set z offset
      Parameters:
      `value` -

    <!-- -->

    - #### getRowScale

          public java.lang.Double getRowScale()

      Get row scale
      Returns:

    <!-- -->

    - #### setRowScale

          public void setRowScale(java.lang.Double value)

      Set row scale
      Parameters:
      `value` -

    <!-- -->

    - #### getColumnScale

          public java.lang.Double getColumnScale()

      Get column scale
      Returns:

    <!-- -->

    - #### setColumnScale

          public void setColumnScale(java.lang.Double value)

      Set column scale
      Parameters:
      `value` -

    <!-- -->

    - #### getXScale

          public java.lang.Double getXScale()

      Get x scale
      Returns:

    <!-- -->

    - #### setXScale

          public void setXScale(java.lang.Double value)

      Set x scale
      Parameters:
      `value` -

    <!-- -->

    - #### getYScale

          public java.lang.Double getYScale()

      Get y scale
      Returns:

    <!-- -->

    - #### setYScale

          public void setYScale(java.lang.Double value)

      Set y scale
      Parameters:
      `value` -

    <!-- -->

    - #### getZScale

          public java.lang.Double getZScale()

      Get z scale
      Returns:

    <!-- -->

    - #### setZScale

          public void setZScale(java.lang.Double value)

      St z scale
      Parameters:
      `value` -

    <!-- -->

    - #### getRowRMS

          public java.lang.Double getRowRMS()

      Get row RMS
      Returns:

    <!-- -->

    - #### setRowRMS

          public void setRowRMS(java.lang.Double value)

      Set row RMS
      Parameters:
      `value` -

    <!-- -->

    - #### getColumnRMS

          public java.lang.Double getColumnRMS()

      Get column RMS
      Returns:

    <!-- -->

    - #### setColumnRMS

          public void setColumnRMS(java.lang.Double value)

      Set column RMS
      Parameters:
      `value` -

    <!-- -->

    - #### getTotalRMS

          public java.lang.Double getTotalRMS()

      Get total RMS
      Returns:

    <!-- -->

    - #### setTotalRMS

          public void setTotalRMS(java.lang.Double value)

      Set total RMS
      Parameters:
      `value` -

    <!-- -->

    - #### getRowNumerator

          public java.lang.Double[] getRowNumerator()

      Get row numerator
      Returns:

    <!-- -->

    - #### setRowNumerator

          public void setRowNumerator(java.lang.Integer pType,
                                      java.lang.Integer nVars,
                                      java.lang.Integer order,
                                      java.util.Vector coefficients)
                               throws GeoRasterException

      Create an array with Row Numerator
      Parameters:
      `pType` - polynomial type

      `nVars` - polynomial number of variables

      `order` - polynomial order

      `coefficients` - polynomial coeeficients

      Throws:
      [`GeoRasterException`](GeoRasterException.md)

    <!-- -->

    - #### getColNumerator

          public java.lang.Double[] getColNumerator()

      Get Column Numerator
      Returns:
      on return\[0\] polynomial type on return\[1\] polynomial number of variables on return\[2\] polynomial order on return\[3..N\] coefficients polynomial coeeficients

    <!-- -->

    - #### setColNumerator

          public void setColNumerator(java.lang.Integer pType,
                                      java.lang.Integer nVars,
                                      java.lang.Integer order,
                                      java.util.Vector coefficients)
                               throws GeoRasterException

      Create an array with Column Numerator
      Parameters:
      `pType` - polynomial type

      `nVars` - polynomial number of variables

      `order` - polynomial order

      `coefficients` - polynomial coeeficients

      Throws:
      [`GeoRasterException`](GeoRasterException.md)

    <!-- -->

    - #### getRowDenominator

          public java.lang.Double[] getRowDenominator()

      Get Row Denominator
      Returns:
      on return\[0\] polynomial type on return\[1\] polynomial number of variables on return\[2\] polynomial order on return\[3..N\] coefficients polynomial coeeficients

    <!-- -->

    - #### setRowDenominator

          public void setRowDenominator(java.lang.Integer pType,
                                        java.lang.Integer nVars,
                                        java.lang.Integer order,
                                        java.util.Vector coefficients)
                                 throws GeoRasterException

      Create an array with Row Denominator
      Parameters:
      `pType` - polynomial type

      `nVars` - polynomial number of variables

      `order` - polynomial order

      `coefficients` - polynomial coeeficients

      Throws:
      [`GeoRasterException`](GeoRasterException.md)

    <!-- -->

    - #### getColDenominator

          public java.lang.Double[] getColDenominator()

      Get Column Denominator
      Returns:
      on return\[0\] polynomial type on return\[1\] polynomial number of variables on return\[2\] polynomial order on return\[3..N\] coefficients polynomial coeeficients

    <!-- -->

    - #### setColDenominator

          public void setColDenominator(java.lang.Integer pType,
                                        java.lang.Integer nVars,
                                        java.lang.Integer order,
                                        java.util.Vector coefficients)
                                 throws GeoRasterException

      Create an array with Column Denominator
      Parameters:
      `pType` - polynomial type

      `nVars` - polynomial number of variables

      `order` - polynomial order

      `coefficients` - polynomial coeeficients

      Throws:
      [`GeoRasterException`](GeoRasterException.md)

    <!-- -->

    - #### getXRMS

          public java.lang.Double getXRMS()

      Get x RMS
      Returns:

    <!-- -->

    - #### setXRMS

          public void setXRMS(java.lang.Double value)

      Set x RMS
      Parameters:
      `value` -

    <!-- -->

    - #### getYRMS

          public java.lang.Double getYRMS()

      Get y RMS
      Returns:

    <!-- -->

    - #### setYRMS

          public void setYRMS(java.lang.Double value)

      Set y RMS
      Parameters:
      `value` -

    <!-- -->

    - #### getZRMS

          public java.lang.Double getZRMS()

      Get z RMS
      Returns:

    <!-- -->

    - #### setZRMS

          public void setZRMS(java.lang.Double value)

      Set z RMS
      Parameters:
      `value` -

    <!-- -->

    - #### getModelTotalRMS

          public java.lang.Double getModelTotalRMS()

      Get model total RMS
      Returns:

    <!-- -->

    - #### setModelTotalRMS

          public void setModelTotalRMS(java.lang.Double value)

      Set model total RMS
      Parameters:
      `value` -

    <!-- -->

    - #### toSTRUCT

          public java.sql.Struct toSTRUCT(java.sql.Connection conn)
                                   throws java.sql.SQLException

      Converts the Spatial Reference information into an Oracle JDBC Struct object. You can then bind the Struct object to a SQL statment that inserts or updates the SDO_GEOR_SRS in the database.
      Parameters:
      `conn` - the connection to use.

      Returns:
      a java.sql.Struct object when successful; otherwise null

      Throws:
      `java.sql.SQLException` - on error

    <!-- -->

    - #### loadJS

          public static final GeorSpatialReference loadJS(java.sql.Struct srs)
                                                   throws java.sql.SQLException,
                                                          GeoRasterException

      Throws:
      `java.sql.SQLException`

      [`GeoRasterException`](GeoRasterException.md)

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

- [Prev Class](GeorHistogramEntry.md)
- [Next Class](JGeoRaster.md)

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
