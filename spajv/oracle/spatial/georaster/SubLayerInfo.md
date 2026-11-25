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

- [Prev Class](SpatialReferenceInfo.md)
- [Next Class](TemporalReferenceInfo.md)

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

## Class SubLayerInfo

- java.lang.Object

- - oracle.spatial.georaster.SubLayerInfo

<!-- -->

-

  ------------------------------------------------------------------------



      public class SubLayerInfo
      extends java.lang.Object

  SubLayerInfo is a Java class mapped to the XML element subLayer or objectLayer in the Oracle Spatial GeoRaster metadata.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                              |
    |---------------------------|------------------------------------------------------------------------------------|
    | `static java.lang.String` | `BIN_TYPE_EXPLICIT`<br>A string indicating EXPLICIT value bin function definition. |
    | `static java.lang.String` | `BIN_TYPE_LINEAR`<br>A string indicating LINEAR bin function definition.           |
    | `static java.lang.String` | `BIN_TYPE_LOGARITHM`<br>A string indicating LOGARITHM bin function definition.     |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                   | Method and Description                                                                                                                                                                                          |
    |-------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                              | `addNODATARange``(java.lang.Double min, java.lang.Double max)`<br>Adds a new NODATA range.                                                                                                                      |
    | `void`                              | `addNODATAValue``(double nodata)`<br>Adds a NODATA value.                                                                                                                                                       |
    | `void`                              | `deleteNODATARange``(java.lang.Double min, java.lang.Double max)`<br>Removes a new NODATA range.                                                                                                                |
    | `void`                              | `deleteNODATAValue``(double nodata)`<br>Removes a NODATA value.                                                                                                                                                 |
    | `java.util.Vector`                  | `getBinFunctionData``()`<br>Returns the bin function data as a vector, which stores four elements in the following order: totalSegNumber(Integer),firstSegNumber(Integer),Extent_Min(Double),Extent_Max(Double) |
    | `java.lang.String`                  | `getBinFunctionTableName``()`<br>Returns the bin function table name.                                                                                                                                           |
    | `java.lang.String`                  | `getBinFunctionType``()`<br>Returns the bin function type.                                                                                                                                                      |
    | [`GeorColormap`](GeorColormap.md)   | `getColormap``()`<br>Returns a georColormap instance which is constructed by colormap data associated with the specific layer of the current JGeoRaster object.                                                 |
    | `java.lang.String`                  | `getColormapTableName``()`<br>Returns the color map table name.                                                                                                                                                 |
    | `java.util.Vector`                  | `getDescription``()`<br>Returns the description.                                                                                                                                                                |
    | [`GeorGrayscale`](GeorGrayscale.md) | `getGrayscale``()`<br>Returns the gray scale as a GeorGrayscale object.                                                                                                                                         |
    | `java.lang.String`                  | `getGrayscaleTableName``()`<br>Returns the gray scale table name.                                                                                                                                               |
    | [`GeorHistogram`](GeorHistogram.md) | `getHistogram``()`<br>Returns the histogram as a GeorHistogram object.                                                                                                                                          |
    | `java.lang.String`                  | `getHistogramTableName``()`<br>Returns the histogram table name.                                                                                                                                                |
    | `java.lang.Integer`                 | `getLayerDimensionOrdinate``()`<br>Returns the layer dimension ordinate.                                                                                                                                        |
    | `java.lang.String`                  | `getLayerID``()`<br>Returns the layer ID.                                                                                                                                                                       |
    | `java.lang.Integer`                 | `getLayerNumber``()`<br>Returns the layer number.                                                                                                                                                               |
    | `java.lang.Double`                  | `getMax``()`<br>Returns the statistics maximum value.                                                                                                                                                           |
    | `java.lang.Double`                  | `getMean``()`<br>Returns the statistics mean value.                                                                                                                                                             |
    | `java.lang.Double`                  | `getMedian``()`<br>Returns the statistics median value.                                                                                                                                                         |
    | `java.lang.Double`                  | `getMin``()`<br>Returns the statistics minimum value.                                                                                                                                                           |
    | `java.lang.Double`                  | `getModeValue``()`<br>Returns the statistics mode value.                                                                                                                                                        |
    | `java.lang.Boolean`                 | `getNODATAMask``()`<br>Returns true if NODATA is mask.                                                                                                                                                          |
    | `java.util.Vector`                  | `getNODATARange``()`<br>Returns the NODATA range vector.                                                                                                                                                        |
    | `java.util.Vector`                  | `getNODATAValue``()`<br>Returns the NODATA value vector.                                                                                                                                                        |
    | `java.lang.Integer`                 | `getSamplingFactor``()`<br>Returns the sampling factor.                                                                                                                                                         |
    | `java.lang.Integer`                 | `getSamplingWindowColumnWidth``()`<br>Returns the sampling window column width.                                                                                                                                 |
    | `java.lang.Long`                    | `getSamplingWindowOrigin``(int dimension)`<br>Returns the sampling window origin point for the specified dimension.                                                                                             |
    | `java.lang.Integer`                 | `getSamplingWindowRowHeight``()`<br>Returns the sampling window row height.                                                                                                                                     |
    | `java.util.Vector`                  | `getScalingFunction``()`<br>Returns the scaling function as a vector, and coefficients are stored in the vector in the following order: a0,a1,b0,b1                                                             |
    | `java.lang.Double`                  | `getSTD``()`<br>Returns the statistics STD value.                                                                                                                                                               |
    | `java.lang.String`                  | `getVATName``()`<br>Returns the VAT table name.                                                                                                                                                                 |
    | `java.lang.Boolean`                 | `hasBitmapMask``()`<br>Returns true if there is a bitmap mask associated with this layer.                                                                                                                       |
    | `void`                              | `setBinFunctionTableName``(java.lang.String binTableName)`<br>Sets the bin function table name.                                                                                                                 |
    | `void`                              | `setBinFunctionType``(java.lang.String binFunctionType)`<br>Sets the bin function type.                                                                                                                         |
    | `void`                              | `setBitmapMask``(java.lang.Boolean isBitmapMask)`<br>Sets true if there is a bitmap mask associated with this layer.                                                                                            |
    | `void`                              | `setBitmapMaskAsNODATA``(java.lang.Boolean mask)`<br>Sets true if NODATA is mask.                                                                                                                               |
    | `void`                              | `setColormap``(`[`GeorColormap`](GeorColormap.md)` colormap)`<br>Sets the colormap information for the specific layer in the metadata based on data stored in the GeorColormap object.                          |
    | `void`                              | `setColormapTableName``(java.lang.String name)`<br>Sets the color map table name.                                                                                                                               |
    | `void`                              | `setDescription``(java.util.Vector description)`<br>Sets the description.                                                                                                                                       |
    | `void`                              | `setGrayscale``(`[`GeorGrayscale`](GeorGrayscale.md)` grayscale)`<br>Sets the gray scale by specifying a GeorGrayscale object.                                                                                  |
    | `void`                              | `setGrayscaleTableName``(java.lang.String name)`<br>Sets the gray scale table name.                                                                                                                             |
    | `void`                              | `setHistogram``(`[`GeorHistogram`](GeorHistogram.md)` histogram)`<br>Sets the histogram by specifying a GeorHistogram object.                                                                                   |
    | `void`                              | `setHistogramTableName``(java.lang.String name)`<br>Sets the histogram table name.                                                                                                                              |
    | `void`                              | `setLayerDimensionOrdinate``(java.lang.Integer layerDimensionOrdinate)`<br>Sets the layer dimension ordinate.                                                                                                   |
    | `void`                              | `setLayerID``(java.lang.String layerID)`<br>Sets the layer ID.                                                                                                                                                  |
    | `void`                              | `setLayerNumber``(java.lang.Integer layerNumber)`<br>Sets the layer number.                                                                                                                                     |
    | `void`                              | `setMax``(java.lang.Double max)`<br>Sets the statistics maximum value.                                                                                                                                          |
    | `void`                              | `setMean``(java.lang.Double mean)`<br>Sets the statistics mean value.                                                                                                                                           |
    | `void`                              | `setMedian``(java.lang.Double median)`<br>Sets the statistics median value.                                                                                                                                     |
    | `void`                              | `setMin``(java.lang.Double min)`<br>Sets the statistics minimum value.                                                                                                                                          |
    | `void`                              | `setModeValue``(java.lang.Double mode)`<br>Sets the statistics mode value.                                                                                                                                      |
    | `void`                              | `setSamplingFactor``(java.lang.Integer factor)`<br>Sets the sampling factor.                                                                                                                                    |
    | `void`                              | `setSamplingWindowColumnWidth``(java.lang.Integer width)`<br>Sets the sampling window column width.                                                                                                             |
    | `void`                              | `setSamplingWindowOrigin``(int dimension, java.lang.Long origin)`<br>Sets the sampling window origin point for the specified dimension.                                                                         |
    | `void`                              | `setSamplingWindowRowHeight``(java.lang.Integer height)`<br>Sets the sampling window row height.                                                                                                                |
    | `void`                              | `setScalingFunction``(double a0, double a1, double b0, double b1)`<br>Sets the scaling function coefficient a0,a1,b0,b1.                                                                                        |
    | `void`                              | `setSTD``(java.lang.Double STD)`<br>Sets the statistics STD value.                                                                                                                                              |
    | `void`                              | `setVATName``(java.lang.String name)`<br>Sets the VAT table name.                                                                                                                                               |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### BIN_TYPE_LINEAR

          public static final java.lang.String BIN_TYPE_LINEAR

      A string indicating LINEAR bin function definition.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### BIN_TYPE_LOGARITHM

          public static final java.lang.String BIN_TYPE_LOGARITHM

      A string indicating LOGARITHM bin function definition.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### BIN_TYPE_EXPLICIT

          public static final java.lang.String BIN_TYPE_EXPLICIT

      A string indicating EXPLICIT value bin function definition.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getLayerNumber

          public java.lang.Integer getLayerNumber()

      Returns the layer number.
      Returns:
      layer number.

    <!-- -->

    - #### setLayerNumber

          public void setLayerNumber(java.lang.Integer layerNumber)

      Sets the layer number.
      Parameters:
      `layerNumber` - layer number

    <!-- -->

    - #### getLayerDimensionOrdinate

          public java.lang.Integer getLayerDimensionOrdinate()

      Returns the layer dimension ordinate.
      Returns:
      layer dimension ordinate.

    <!-- -->

    - #### setLayerDimensionOrdinate

          public void setLayerDimensionOrdinate(java.lang.Integer layerDimensionOrdinate)

      Sets the layer dimension ordinate.
      Parameters:
      `layerDimensionOrdinate` - layer dimension ordinate

    <!-- -->

    - #### getLayerID

          public java.lang.String getLayerID()

      Returns the layer ID.
      Returns:
      layer ID.

    <!-- -->

    - #### setLayerID

          public void setLayerID(java.lang.String layerID)

      Sets the layer ID.
      Parameters:
      `layerID` - layer ID

    <!-- -->

    - #### getDescription

          public java.util.Vector getDescription()

      Returns the description.
      Returns:
      description.

    <!-- -->

    - #### setDescription

          public void setDescription(java.util.Vector description)

      Sets the description.
      Parameters:
      `description` - description

    <!-- -->

    - #### hasBitmapMask

          public java.lang.Boolean hasBitmapMask()

      Returns true if there is a bitmap mask associated with this layer.
      Returns:
      true if there is a bitmap mask associated with this layer.

    <!-- -->

    - #### setBitmapMask

          public void setBitmapMask(java.lang.Boolean isBitmapMask)

      Sets true if there is a bitmap mask associated with this layer.
      Parameters:
      `isBitmapMask` - true if there is a bitmap mask associated with this layer

    <!-- -->

    - #### getNODATAValue

          public java.util.Vector getNODATAValue()

      Returns the NODATA value vector.
      Returns:
      NODATA value vector.

    <!-- -->

    - #### addNODATAValue

          public void addNODATAValue(double nodata)

      Adds a NODATA value.
      Parameters:
      `nodata` - NODATA value

    <!-- -->

    - #### deleteNODATAValue

          public void deleteNODATAValue(double nodata)

      Removes a NODATA value.
      Parameters:
      `nodata` - NODATA value

    <!-- -->

    - #### getNODATARange

          public java.util.Vector getNODATARange()

      Returns the NODATA range vector.
      Returns:
      NODATA range vector.

    <!-- -->

    - #### addNODATARange

          public void addNODATARange(java.lang.Double min,
                                     java.lang.Double max)

      Adds a new NODATA range.
      Parameters:
      `min` - minimum value

      `max` - maximum value

    <!-- -->

    - #### deleteNODATARange

          public void deleteNODATARange(java.lang.Double min,
                                        java.lang.Double max)

      Removes a new NODATA range.
      Parameters:
      `min` - minimum value

      `max` - maximum value

    <!-- -->

    - #### getNODATAMask

          public java.lang.Boolean getNODATAMask()

      Returns true if NODATA is mask.
      Returns:
      true if NODATA is mask.

    <!-- -->

    - #### setBitmapMaskAsNODATA

          public void setBitmapMaskAsNODATA(java.lang.Boolean mask)

      Sets true if NODATA is mask.
      Parameters:
      `mask` - true if NODATA is mask

    <!-- -->

    - #### getScalingFunction

          public java.util.Vector getScalingFunction()

      Returns the scaling function as a vector, and coefficients are stored in the vector in the following order: a0,a1,b0,b1
      Pixel value is scaled as:

          value = (a0 + a1 * cellValue)/(b0 + b1 * cellValue)


      Returns:
      scaling function.

    <!-- -->

    - #### setScalingFunction

          public void setScalingFunction(double a0,
                                         double a1,
                                         double b0,
                                         double b1)

      Sets the scaling function coefficient a0,a1,b0,b1.
      Parameters:
      `a0` - coefficient a0.

      `a1` - coefficient a1.

      `b0` - coefficient b0.

      `b1` - coefficient b1.

    <!-- -->

    - #### getBinFunctionType

          public java.lang.String getBinFunctionType()

      Returns the bin function type.
      Returns:
      bin function type.

    <!-- -->

    - #### setBinFunctionType

          public void setBinFunctionType(java.lang.String binFunctionType)

      Sets the bin function type.
      Parameters:
      `binFunctionType` - bin function type

    <!-- -->

    - #### getBinFunctionData

          public java.util.Vector getBinFunctionData()

      Returns the bin function data as a vector, which stores four elements in the following order: totalSegNumber(Integer),firstSegNumber(Integer),Extent_Min(Double),Extent_Max(Double)
      Returns:
      bin function data.

    <!-- -->

    - #### getBinFunctionTableName

          public java.lang.String getBinFunctionTableName()

      Returns the bin function table name.
      Returns:
      bin function table name.

    <!-- -->

    - #### setBinFunctionTableName

          public void setBinFunctionTableName(java.lang.String binTableName)

      Sets the bin function table name.
      Parameters:
      `binTableName` - bin function table name

    <!-- -->

    - #### getSamplingFactor

          public java.lang.Integer getSamplingFactor()

      Returns the sampling factor.
      Returns:
      sampling factor.

    <!-- -->

    - #### setSamplingFactor

          public void setSamplingFactor(java.lang.Integer factor)

      Sets the sampling factor.
      Parameters:
      `factor` - sampling factor

    <!-- -->

    - #### getSamplingWindowOrigin

          public java.lang.Long getSamplingWindowOrigin(int dimension)

      Returns the sampling window origin point for the specified dimension.
      Parameters:
      `dimension` - specified dimension

      Returns:
      sampling window origin point for the specified dimension.

    <!-- -->

    - #### setSamplingWindowOrigin

          public void setSamplingWindowOrigin(int dimension,
                                              java.lang.Long origin)

      Sets the sampling window origin point for the specified dimension.
      Parameters:
      `dimension` - specified dimension

      `origin` - sampling window origin point for the specified dimension

    <!-- -->

    - #### getSamplingWindowRowHeight

          public java.lang.Integer getSamplingWindowRowHeight()

      Returns the sampling window row height.
      Returns:
      sampling window row height.

    <!-- -->

    - #### setSamplingWindowRowHeight

          public void setSamplingWindowRowHeight(java.lang.Integer height)

      Sets the sampling window row height.
      Parameters:
      `height` - sampling window row height

    <!-- -->

    - #### getSamplingWindowColumnWidth

          public java.lang.Integer getSamplingWindowColumnWidth()

      Returns the sampling window column width.
      Returns:
      sampling window column width.

    <!-- -->

    - #### setSamplingWindowColumnWidth

          public void setSamplingWindowColumnWidth(java.lang.Integer width)

      Sets the sampling window column width.
      Parameters:
      `width` - sampling window column width

    <!-- -->

    - #### getMin

          public java.lang.Double getMin()

      Returns the statistics minimum value.
      Returns:
      statistics minimum value.

    <!-- -->

    - #### setMin

          public void setMin(java.lang.Double min)

      Sets the statistics minimum value.
      Parameters:
      `min` - statistics minimum value

    <!-- -->

    - #### getMax

          public java.lang.Double getMax()

      Returns the statistics maximum value.
      Returns:
      statistics maximum value.

    <!-- -->

    - #### setMax

          public void setMax(java.lang.Double max)

      Sets the statistics maximum value.
      Parameters:
      `max` - statistics maximum value

    <!-- -->

    - #### getMean

          public java.lang.Double getMean()

      Returns the statistics mean value.
      Returns:
      statistics mean value.

    <!-- -->

    - #### setMean

          public void setMean(java.lang.Double mean)

      Sets the statistics mean value.
      Parameters:
      `mean` - statistics mean value

    <!-- -->

    - #### getMedian

          public java.lang.Double getMedian()

      Returns the statistics median value.
      Returns:
      statistics median value.

    <!-- -->

    - #### setMedian

          public void setMedian(java.lang.Double median)

      Sets the statistics median value.
      Parameters:
      `median` - statistics median value

    <!-- -->

    - #### getModeValue

          public java.lang.Double getModeValue()

      Returns the statistics mode value.
      Returns:
      statistics mode value.

    <!-- -->

    - #### setModeValue

          public void setModeValue(java.lang.Double mode)

      Sets the statistics mode value.
      Parameters:
      `mode` - statistics mode value

    <!-- -->

    - #### getSTD

          public java.lang.Double getSTD()

      Returns the statistics STD value.
      Returns:
      statistics STD value.

    <!-- -->

    - #### setSTD

          public void setSTD(java.lang.Double STD)

      Sets the statistics STD value.
      Parameters:
      `STD` - statistics STD value

    <!-- -->

    - #### getHistogramTableName

          public java.lang.String getHistogramTableName()

      Returns the histogram table name.
      Returns:
      histogram table name.

    <!-- -->

    - #### setHistogramTableName

          public void setHistogramTableName(java.lang.String name)

      Sets the histogram table name.
      Parameters:
      `name` - histogram table name

    <!-- -->

    - #### getHistogram

          public GeorHistogram getHistogram()

      Returns the histogram as a GeorHistogram object.
      Returns:
      GeorHistogram object.

    <!-- -->

    - #### setHistogram

          public void setHistogram(GeorHistogram histogram)

      Sets the histogram by specifying a GeorHistogram object.
      Parameters:
      `histogram` - GeorHistogram object.

    <!-- -->

    - #### getGrayscaleTableName

          public java.lang.String getGrayscaleTableName()

      Returns the gray scale table name.
      Returns:
      gray scale table name.

    <!-- -->

    - #### setGrayscaleTableName

          public void setGrayscaleTableName(java.lang.String name)

      Sets the gray scale table name.
      Parameters:
      `name` - gray scale table name

    <!-- -->

    - #### getGrayscale

          public GeorGrayscale getGrayscale()

      Returns the gray scale as a GeorGrayscale object.
      Returns:
      gray scale.

    <!-- -->

    - #### setGrayscale

          public void setGrayscale(GeorGrayscale grayscale)

      Sets the gray scale by specifying a GeorGrayscale object.
      Parameters:
      `grayscale` - GeorGrayscale object

    <!-- -->

    - #### getColormapTableName

          public java.lang.String getColormapTableName()

      Returns the color map table name.
      Returns:
      color map table name.

    <!-- -->

    - #### setColormapTableName

          public void setColormapTableName(java.lang.String name)

      Sets the color map table name.
      Parameters:
      `name` - color map table name

    <!-- -->

    - #### getColormap

          public GeorColormap getColormap()

      Returns a georColormap instance which is constructed by colormap data associated with the specific layer of the current JGeoRaster object.
      Returns:
      a GeorColormap instance or null.

    <!-- -->

    - #### setColormap

          public void setColormap(GeorColormap colormap)

      Sets the colormap information for the specific layer in the metadata based on data stored in the GeorColormap object.
      Parameters:
      `colormap` - GeorColormap object

    <!-- -->

    - #### getVATName

          public java.lang.String getVATName()

      Returns the VAT table name.
      Returns:
      VAT table name.

    <!-- -->

    - #### setVATName

          public void setVATName(java.lang.String name)

      Sets the VAT table name.
      Parameters:
      `name` - VAT table name

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

- [Prev Class](SpatialReferenceInfo.md)
- [Next Class](TemporalReferenceInfo.md)

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
