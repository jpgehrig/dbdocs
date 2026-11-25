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

- Prev Class
- Next Class

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

oracle.spatial.georaster.util

## Class MosaicParameters

- java.lang.Object

- - oracle.spatial.georaster.util.MosaicParameters

<!-- -->

-

  ------------------------------------------------------------------------



      public class MosaicParameters
      extends java.lang.Object

  `MosaicParameters` class provides the parameters for JGeoRasterVM
  The `MosaicParameters` should be initiated and the individual paramters should be set before passed to `JGeoRasterVM`:

           MosaicParameters param = new MosaicParameters();

           param.setFillGap(true);
           param.setIncludeNODATA(true);

           JGeoRasterVM geoRasterVM = new JGeoRasterVM( connection,
                        tables_or_views, georaster_columns, null, "4326",
                        param );


  Passed to an existing `JGeoRasterVM` object:

           MosaicParameters param = new MosaicParameters();

           param.setFillGap(true);
           param.setIncludeNODATA(true);

           geoRasterVM.setMosaicParam(param);


  Or retrived from an existing `JGeoRasterVM` object:

           MosaicParameters param = geoRasterVM.getMosaicParam();


<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description             |
    |---------------------------|-----------------------------------|
    | `static java.lang.String` | `CBREFEREBCE_IMAGE`               |
    | `static java.lang.String` | `CBREFERENCE_OVERLAP`             |
    | `static java.lang.String` | `CBREFERENCE_VALUE`               |
    | `static java.lang.String` | `COLORBALANCE_HISTOGRAMMATCHING`  |
    | `static java.lang.String` | `COLORBALANCE_LINEARSTRETCHING`   |
    | `static java.lang.String` | `COLORBALANCE_NONE`               |
    | `static java.lang.String` | `COLORBALANCE_NORMALIZATION`      |
    | `static java.lang.String` | `COLORBALANCE_STATISTICMATCHING`  |
    | `static java.lang.String` | `COMMONPOINTRULE_AVERAGE`         |
    | `static java.lang.String` | `COMMONPOINTRULE_CTC`             |
    | `static java.lang.String` | `COMMONPOINTRULE_END`             |
    | `static java.lang.String` | `COMMONPOINTRULE_HIGH`            |
    | `static java.lang.String` | `COMMONPOINTRULE_HIGHRES`         |
    | `static java.lang.String` | `COMMONPOINTRULE_LATEST`          |
    | `static java.lang.String` | `COMMONPOINTRULE_LOW`             |
    | `static java.lang.String` | `COMMONPOINTRULE_OLDEST`          |
    | `static java.lang.String` | `COMMONPOINTRULE_START`           |
    | `static java.lang.String` | `RESAMPLING_AVERAGE16`            |
    | `static java.lang.String` | `RESAMPLING_AVERAGE4`             |
    | `static java.lang.String` | `RESAMPLING_BILINEAR`             |
    | `static java.lang.String` | `RESAMPLING_BIQUADRATIC`          |
    | `static java.lang.String` | `RESAMPLING_CUBIC`                |
    | `static java.lang.String` | `RESAMPLING_NN`                   |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `MosaicParameters``()`      |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                 |
    |--------------------|----------------------------------------------------------------------------------------|
    | `boolean`          | `getApplyResolutionFilter``()`                                                         |
    | `java.lang.String` | `getCBReference``()`                                                                   |
    | `java.lang.String` | `getColorBalance``()`                                                                  |
    | `java.lang.String` | `getCommonPointRule``()`                                                               |
    | `boolean`          | `getFillGap``()`                                                                       |
    | `boolean`          | `getIncludeNODATA``()`                                                                 |
    | `int`              | `getMaxStretchValue``()`                                                               |
    | `double`           | `getMean``()`                                                                          |
    | `int`              | `getMinStretchValue``()`                                                               |
    | `double`           | `getReferecenValue1``()`                                                               |
    | `double`           | `getReferecenValue2``()`                                                               |
    | `java.lang.String` | `getResamplingMode``()`                                                                |
    | `double`           | `getResamplingTolerance``()`                                                           |
    | `boolean`          | `getResFilter``()`                                                                     |
    | `double`           | `getStandardDeviation``()`                                                             |
    | `java.lang.String` | `getVmElevationParam``()`<br>Get elevation parameters.                                 |
    | `void`             | `setApplyResolutionFilter``(boolean filter)`                                           |
    | `void`             | `setCBReference``(java.lang.String cbReference)`                                       |
    | `void`             | `setColorBalance``(java.lang.String color)`                                            |
    | `void`             | `setCommonPointRule``(java.lang.String rule)`                                          |
    | `void`             | `setFillGap``(boolean fillGap)`                                                        |
    | `void`             | `setIncludeNODATA``(boolean nodata)`                                                   |
    | `void`             | `setMaxStretchValue``(int maxValue)`                                                   |
    | `void`             | `setMean``(double mean)`                                                               |
    | `void`             | `setMinStretchValue``(int minValue)`                                                   |
    | `void`             | `setReferenceValue1``(double value)`                                                   |
    | `void`             | `setReferenceValue2``(double value)`                                                   |
    | `void`             | `setResamplingMode``(java.lang.String resampling)`                                     |
    | `void`             | `setResamplingTolerance``(double tolerance)`                                           |
    | `void`             | `setResFilter``(boolean resFilter)`                                                    |
    | `void`             | `setStandardDeviation``(double stdDev)`                                                |
    | `void`             | `setVmElevationParam``(java.lang.String vmElevationParam)`<br>Set elevation paramters. |
    | `java.lang.String` | `toStrings``()`                                                                        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### COLORBALANCE_NONE

          public static java.lang.String COLORBALANCE_NONE

    <!-- -->

    - #### COLORBALANCE_LINEARSTRETCHING

          public static java.lang.String COLORBALANCE_LINEARSTRETCHING

    <!-- -->

    - #### COLORBALANCE_NORMALIZATION

          public static java.lang.String COLORBALANCE_NORMALIZATION

    <!-- -->

    - #### COLORBALANCE_STATISTICMATCHING

          public static java.lang.String COLORBALANCE_STATISTICMATCHING

    <!-- -->

    - #### COLORBALANCE_HISTOGRAMMATCHING

          public static java.lang.String COLORBALANCE_HISTOGRAMMATCHING

    <!-- -->

    - #### COMMONPOINTRULE_START

          public static java.lang.String COMMONPOINTRULE_START

    <!-- -->

    - #### COMMONPOINTRULE_END

          public static java.lang.String COMMONPOINTRULE_END

    <!-- -->

    - #### COMMONPOINTRULE_LATEST

          public static java.lang.String COMMONPOINTRULE_LATEST

    <!-- -->

    - #### COMMONPOINTRULE_OLDEST

          public static java.lang.String COMMONPOINTRULE_OLDEST

    <!-- -->

    - #### COMMONPOINTRULE_CTC

          public static java.lang.String COMMONPOINTRULE_CTC

    <!-- -->

    - #### COMMONPOINTRULE_HIGH

          public static java.lang.String COMMONPOINTRULE_HIGH

    <!-- -->

    - #### COMMONPOINTRULE_LOW

          public static java.lang.String COMMONPOINTRULE_LOW

    <!-- -->

    - #### COMMONPOINTRULE_AVERAGE

          public static java.lang.String COMMONPOINTRULE_AVERAGE

    <!-- -->

    - #### COMMONPOINTRULE_HIGHRES

          public static java.lang.String COMMONPOINTRULE_HIGHRES

    <!-- -->

    - #### RESAMPLING_NN

          public static java.lang.String RESAMPLING_NN

    <!-- -->

    - #### RESAMPLING_BILINEAR

          public static java.lang.String RESAMPLING_BILINEAR

    <!-- -->

    - #### RESAMPLING_BIQUADRATIC

          public static java.lang.String RESAMPLING_BIQUADRATIC

    <!-- -->

    - #### RESAMPLING_CUBIC

          public static java.lang.String RESAMPLING_CUBIC

    <!-- -->

    - #### RESAMPLING_AVERAGE4

          public static java.lang.String RESAMPLING_AVERAGE4

    <!-- -->

    - #### RESAMPLING_AVERAGE16

          public static java.lang.String RESAMPLING_AVERAGE16

    <!-- -->

    - #### CBREFERENCE_VALUE

          public static java.lang.String CBREFERENCE_VALUE

    <!-- -->

    - #### CBREFEREBCE_IMAGE

          public static java.lang.String CBREFEREBCE_IMAGE

    <!-- -->

    - #### CBREFERENCE_OVERLAP

          public static java.lang.String CBREFERENCE_OVERLAP

  <!-- -->

  - ### Constructor Detail

    - #### MosaicParameters

          public MosaicParameters()

  <!-- -->

  - ### Method Detail

    - #### getColorBalance

          public java.lang.String getColorBalance()

      Returns:
      vmColorBalance

    <!-- -->

    - #### setColorBalance

          public void setColorBalance(java.lang.String color)

      Parameters:
      `color` - Specifies the method for color balancing. Can have one of the following values:

           NONE (the default): No color balancing is performed.

           LINEARSTRETCHING: Use the linear stretching method to stretch the source image's cell values to the reference minimum and maximum value.
               If the cbreference parameter is VALUE, then parameter referenceValue1 has the reference minimum values and parameter referenceValue2 has the reference maximum values. If the referenceValue1 or referenceValue2 is null, default values 0 and 255 are used, respectively. If the referenceValue1 or referenceValue2 has only one value, it is applied to all the bands; otherwise, the reference values are corresponding to each band. Thus, the number of values in the SDO_NUMBER_ARRAY must be the same as the number of bands in the source images.
               If the cbreference parameter is IMAGE, then the minimum and maximum values of referenceImage are used as the reference.
               If the cbreference parameter is not specified, the minVal and maxVal parameters are used to specify the minimum and maximum reference values, respectively.

           STATISTICMATCHING: Stretch the source images to match the reference statistics.
               If the cbreference parameter is VALUE, then parameter referenceValue1 has the reference mean value and parameter referenceValue2 has the reference standard deviation value. If the referenceValue1 or referenceValue2 is null, default values 128 and 100 are used, respectively. If the referenceValue1 or referenceValue2 has only one value, it is applied to all the bands; otherwise, the reference values are corresponding to each band. Thus, the number of values in the SDO_NUMBER_ARRAY must be the same as the number of bands in the source images.
               If the cbreference parameter is IMAGE, then the reference image's mean and standard deviation values are used for the matching.
               If the cbreference parameter is OVERLAP, then the mean and standard deviation values are derived from the overlapping area.
               If the cbreference parameter is not specified, the std and mean parameters are used to specify the reference statistics.

           HISTOGRAMMATCHING: Use the reference histogram as the source image's histogram.
               If the cbreference parameter is VALUE, then parameter referenceHistogram defines the reference histograms for each band. If only one reference histogram is specified, it is applied to all the bands.
               If the cbreference parameter is IMAGE, then the referencce image's histograms for each band are used as the reference for matching
               If the cbreference parameter is OVERLAP, then histograms at the overlapping area are used to derive the matching.


    <!-- -->

    - #### getFillGap

          public boolean getFillGap()

      Returns:
      vmFillGap

    <!-- -->

    - #### setFillGap

          public void setFillGap(boolean fillGap)

      Parameters:
      `fillGap` - Specifies whether or not to fill the narrow gap between source images. TRUE causes any gap that is less than or equal to 2 pixels wide to be filled with the nearest-neighbor pixel value. FALSE causes any gaps to be filled with zero or bgValue.

    <!-- -->

    - #### getIncludeNODATA

          public boolean getIncludeNODATA()

      Returns:
      vmNODATA

    <!-- -->

    - #### setIncludeNODATA

          public void setIncludeNODATA(boolean nodata)

      Parameters:
      `nodata` - Specifies whether or not to consider NODATA (NODATA value or NODATA bitmap mask) when handling the overlap area or when resampling is performed. The default value is FALSE. When handling the overlap area, nodata=TRUE causes any NODATA values cells not to be involved in the overlap area calculation; nodata=FALSE causes all the overlapped cells to be involved in the overlap area calculation. When resampling is performed and the resampling method is BILINEAR, BIQUADRATIC, CUBIC, AVERAGE4, or AVERAGE16, if any of the cells involved in the resampling has a NODATA value, then nodata=TRUE causes the result of the resampling to be a NODATA value.

    <!-- -->

    - #### getResamplingMode

          public java.lang.String getResamplingMode()

      Returns:
      vmResampling

    <!-- -->

    - #### setResamplingMode

          public void setResamplingMode(java.lang.String resampling)

      Parameters:
      `resampling` - Specifies the resampling method (if resampling is involved or rectification is needed) to be used during the mosaic operation. Can have one of the following values: NN (the default), BILINEAR, BIQUADRATIC, CUBIC, AVERAGE4, or AVERAGE16. For more information, see Resampling and Interpolation.

    <!-- -->

    - #### getResamplingTolerance

          public double getResamplingTolerance()

      Returns:
      vmResamplingTolerance

    <!-- -->

    - #### setResamplingTolerance

          public void setResamplingTolerance(double tolerance)

      Parameters:
      `tolerance` - Specifies the tolerance for not doing resampling when the source GeoRaster objects are not perfectly aligned. The value should be between 0 and 0.5, where the unit is pixel or cell (for example, 0.5 meaning one-half pixel or cell). If not specified, 0.5 is used, which means no resampling will occur.

    <!-- -->

    - #### getApplyResolutionFilter

          public boolean getApplyResolutionFilter()

      Returns:
      vmResolutionFilter

    <!-- -->

    - #### setApplyResolutionFilter

          public void setApplyResolutionFilter(boolean filter)

      Parameters:
      `filter` - Specifies whether or not to filter the source GeoRaster objects to select only the GeoRaster object that is in the range of the output resolution (outResolution parameter). TRUE (the default) enables resolution filtering. FALSE disables resolution filtering, causing all the source GeoRaster objects to be involved in the mosaicking process. (Always ignored if specified in appendParam for SDO_GEOR_AGGR.append.)

    <!-- -->

    - #### getMinStretchValue

          public int getMinStretchValue()

      Returns:
      vmMinStretchValue

    <!-- -->

    - #### setMinStretchValue

          public void setMinStretchValue(int minValue)

      Parameters:
      `minValue` - Ignored if colorBalance is not LINEARSTRETCHING or if the cbreference keyword is specified; otherwise, specifies the lowest value in the range of the linear stretching method. Defaults to 0. (Always ignored if specified in appendParam for SDO_GEOR_AGGR.append.)

    <!-- -->

    - #### getMaxStretchValue

          public int getMaxStretchValue()

      Returns:
      vmMaxStretchValue

    <!-- -->

    - #### setMaxStretchValue

          public void setMaxStretchValue(int maxValue)

      Parameters:
      `maxValue` - Ignored if colorBalance is not LINEARSTRETCHING or if the cbreference keyword is specified; otherwise, specifies the highest value in the range of the linear stretching method. Defaults to 255. (Always ignored if specified in appendParam for SDO_GEOR_AGGR.append.)

    <!-- -->

    - #### getMean

          public double getMean()

      Returns:
      vmMean

    <!-- -->

    - #### setMean

          public void setMean(double mean)

      Parameters:
      `mean` - Ignored if colorBalance is not STATISTICMATCHING or if the cbreference keyword is specified; otherwise, specifies the reference mean of the statistic matching method. (Always ignored if specified in appendParam for SDO_GEOR_AGGR.append.)

    <!-- -->

    - #### getStandardDeviation

          public double getStandardDeviation()

      Returns:
      vmStandardDeviation

    <!-- -->

    - #### setStandardDeviation

          public void setStandardDeviation(double stdDev)

      Parameters:
      `stdDev` - Ignored if colorBalance is not STATISTICMATCHING or if the cbreference keyword is specified; otherwise, specifies the reference standard deviation for the statistic matching method. (Always ignored if specified in appendParam for SDO_GEOR_AGGR.append.)

    <!-- -->

    - #### getReferecenValue1

          public double getReferecenValue1()

      Returns:
      vmReferenceValue1

    <!-- -->

    - #### setReferenceValue1

          public void setReferenceValue1(double value)

      Parameters:
      `value` - Ignored if CBReference is not VALUE

    <!-- -->

    - #### getReferecenValue2

          public double getReferecenValue2()

      Returns:
      vmReferenceValue2

    <!-- -->

    - #### setReferenceValue2

          public void setReferenceValue2(double value)

      Parameters:
      `value` - Ignored if CBReference is not VALUE

    <!-- -->

    - #### getCommonPointRule

          public java.lang.String getCommonPointRule()

      Returns:
      CommonPointRule

    <!-- -->

    - #### getVmElevationParam

          public java.lang.String getVmElevationParam()

      Get elevation parameters.
      Returns:

    <!-- -->

    - #### setVmElevationParam

          public void setVmElevationParam(java.lang.String vmElevationParam)

      Set elevation paramters.
      Parameters:
      `vmElevationParam` -

    <!-- -->

    - #### setCommonPointRule

          public void setCommonPointRule(java.lang.String rule)

      Parameters:
      `rule` - Specifies the method for getting the cell value at the overlapping area. Can have one of the following values:

           START: The value from the first encountered GeoRaster object is used.
           END: The value from the last encountered GeoRaster object is used.
           LATEST: The value from the GeoRaster object that has the most recent EndDateTime in the metadata is used.
           OLDEST: The value from the GeoRaster object that has the oldest BeginDateTime in the metadata is used.
           CTC: The call value from the GeoRaster object that is closest to the center of the output window is used.
           HIGH: The maximum cell value of all the overlapping GeoRaster objects is used.
           LOW: The minimum cell value of all the overlapping GeoRaster objects is used.
           AVERAGE: The average of all cell values from the overlapping GeoRaster objects is used.
           HIGHRES: The value from the GeoRaster object that has the highest spatial resolution is used.


    <!-- -->

    - #### setCBReference

          public void setCBReference(java.lang.String cbReference)

      Parameters:
      `cbReference` - (Supported with the procedure formats that include the referenceImage, referenceValue1, /referenceValue2, and refHistograms parameters.) Specifies the source of the reference value used in colorBalance. Can have one of the following values:

           VALUE: The reference value is specified in the referenceValue1 and referenceValue2 parameters.
           IMAGE: The reference value is retrieved from the referenceImage parameter.
           OVERLAP: the reference value is derived from the overlapping area of the source images. (Always ignored if specified in appendParam for SDO_GEOR_AGGR.append.)


    <!-- -->

    - #### getCBReference

          public java.lang.String getCBReference()

      Returns:
      vmCBReference

    <!-- -->

    - #### getResFilter

          public boolean getResFilter()

      Returns:
      vmResFilter

    <!-- -->

    - #### setResFilter

          public void setResFilter(boolean resFilter)

      Parameters:
      `resFilter` - Specifies whether or not to filter the source GeoRaster objects to select only the GeoRaster object that is in the range of the output resolution (outResolution parameter). TRUE (the default) enables resolution filtering. FALSE disables resolution filtering, causing all the source GeoRaster objects to be involved in the mosaicking process. (Always ignored if specified in appendParam for SDO_GEOR_AGGR.append.)

    <!-- -->

    - #### toStrings

          public java.lang.String toStrings()

      Returns:
      result

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

- Prev Class
- Next Class

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
