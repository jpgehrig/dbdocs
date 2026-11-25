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
- [Next Class](GeoRasterImage.NodataMapping.md)

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

oracle.spatial.georaster.image

## Class GeoRasterImage

- java.lang.Object

- - oracle.spatial.georaster.image.GeoRasterImage

<!-- -->

-

  ------------------------------------------------------------------------



      public class GeoRasterImage
      extends java.lang.Object

  GeoRasterImage is a GeoRaster image engine, which is used to generate Java images from a GeoRaster object or a subset of a GeoRaster object based on the metadata of the GeoRaster object and different query conditions.
  When a GeoRasterImage object is initiated from a JGeoRaster object, r/g/b mappings of the GeoRasterImage object are set automatically based on the metadata of the JGeoRaster object, and then these settings can be changed manually by the following methods:

             public void setRed(int red)
             public void setGreen(int green)
             public void setBlue(int blue)


  Once r/g/b mappings are set, all later calls to the following methods will use these mappings to construct Java images from GeoRaster objects:
             public RenderedImage  getRasterImage(int pyramidLevel)
             public RenderedImage  getRasterImage(int pyramidLevel,JGeometry window)
             public RenderedImage  getRasterImage(int pyramidLevel,long startRow,long startColumn,long endRow,long endColumn)
             public RenderedImage  getRasterImage(int pyramidLevel,String transportationType,int quality)
             public RenderedImage  getRasterImageWithMask(int pyramidLevel,JGeometry window,Vector layerNo,int zeroMapping,int oneMapping)
             public RenderedImage  getRasterImageWithMask(int pyramidLevel,JGeometry window,Vector layerNo,int zeroMapping,int oneMapping,String transportationType,int quality)
             public RenderedImage  getRasterImageWithMask(int pyramidLevel,long startRow,long startColumn,long endRow,long endColumn,Vector layerNo,int zeroMapping,int oneMapping)
             public RenderedImage  getRasterImageWithMask(int pyramidLevel,long startRow,long startColumn,long endRow,long endColumn,Vector layerNo,int zeroMapping,int oneMapping,String transportationType,nt quality)


  A GeoRasterImage object is constructed from a JGeoRaster object as follows:

            public GeoRasterImage(JGeoRaster georaster) throws GeoRasterException


  or you can get a GeoRasterImage instance through the method defined in the JGeoRaster object:
          public GeoRasterImage getGeoRasterImageObject()

  Note: the preceding method is a singleton operation, which means that for each JGeoRaster object, the GeoRasterImage instance is just initiated once. After that, the JGeoRaster will keep returning the same GeoRasterImage instance created by the first invocation, so that the JGeoRaster object can keep red/green/blue mapping across calls.
  The following is an example of how to use this class to visualize a GeoRaster object:

         ...
         //reading a GeoRaster object from database based on a query
         ResultSet rs = statement.executeQuery("SELECT a.georaster FROM georaster_table a where a.georaster.rasterdatatable='RDT' and a.georaster.rasterid=1");
         STRUCT geor = (oracle.sql.STRUCT) rs.getObject(1);
         //construct a JGeoRaster object
         JGeoRaster geoRaster = new JGeoRaster(geor);
         //get GeoRasterImage instance
         GeoRasterImage geoRasterImage=geoRaster.getGeoRasterImageObject();
         //fetch a subset of GeoRaster object as a Java image
         RenderedImage image=geoRasterImage.getRasterImage(0,0,0,100,100);
         ...


<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                              |
    |-------------------|--------------------------------------------------------------------|
    | `class `          | [`GeoRasterImage.NodataMapping`](GeoRasterImage.NodataMapping.md)  |

  <!-- -->

  - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description          |
    |-------------------|--------------------------------|
    | `static int`      | `IP_AUTOMATIC_LINEAR_STRETCH`  |
    | `static int`      | `IP_EQUALIZATION`              |
    | `static int`      | `IP_MANUAL_LINEAR_STRETCH`     |
    | `static int`      | `IP_NONE`                      |
    | `static int`      | `IP_NORMALIZATION`             |
    | `static int`      | `IP_PIECEWISE_LINEAR_STRETCH`  |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                        |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `GeoRasterImage``(`[`JGeoRaster`](../JGeoRaster.md)` georaster)`<br>Constructs a `GeoRasterImage` object with the given JGeoRaster object.                                                                         |
    | `GeoRasterImage``(`[`JGeoRasterVM`](../JGeoRasterVM.md)` geoRasterVM, `[`MosaicParameters`](../util/MosaicParameters.md)` mosaicParam)`<br>Constructs a `GeoRasterImage` object with the given JGeoRasterVM object |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                          | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    |--------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                  | `addNodataMapping``(double nodata, java.lang.Double newValue, boolean isTransparent)`<br>This function will add nodata(value) mapping to current image, so that all pixel values, which equal to the nodata value, will be changed to newValue and it's alpha channel value is changed too based on transparent setting by parameter isTransparent.                                                                                                                                                                                                                                                                          |
    | `boolean`                                  | `addNodataMapping``(double nodataStart, double nodataEnd, java.lang.Double newValue, boolean isTransparent)`<br>This function will add nodata(range) mapping to current image, so that all pixel values, which fall into the nodata range, will be changed to newValue and it's alpha channel value is changed too based on transparent setting by parameter isTransparent.                                                                                                                                                                                                                                                  |
    | `int`                                      | `getAlpha``()`<br>Returns the band number mapped to the alpha channel.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `int`                                      | `getBlue``()`<br>Returns the band number mapped to blue.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `int`                                      | `getGlobalIPOperation``()`<br>This method will return current selected global image processing operation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `int`                                      | `getGreen``()`<br>Returns the band number mapped to green.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `java.awt.image.RenderedImage`             | `getMaskImage``(int pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` window, java.util.Vector layerNo, int zeroMapping, int oneMapping, long[] outWindow)`<br>Returns the specified portion of the GeoRaster mask in the specified pyramidLevel and layer as a Java Image.                                                                                                                                                                                                                                                                                                                                         |
    | `java.awt.image.RenderedImage`             | `getMaskImage``(int pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` window, java.util.Vector layerNo, int zeroMapping, int oneMapping, java.lang.String transportationType, long[] outWindow)`<br>Returns the specified portion of the GeoRaster mask in the specified pyramidLevel and layer as a Java Image.                                                                                                                                                                                                                                                                                                    |
    | `java.awt.image.RenderedImage`             | `getMaskImage``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, java.util.Vector layerNo, int zeroMapping, int oneMapping, long[] outWindow)`<br>Returns the specified portion of the GeoRaster mask in the specified pyramidLevel and layer as a Java Image.                                                                                                                                                                                                                                                                                                                                |
    | `java.awt.image.RenderedImage`             | `getMaskImage``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, java.util.Vector layerNo, int zeroMapping, int oneMapping, java.lang.String transportationType, long[] outWindow)`<br>Returns the specified portion of the GeoRaster mask in the specified pyramidLevel and layer as a Java Image.                                                                                                                                                                                                                                                                                           |
    | `java.util.Vector`                         | `getNodataMapping``()`<br>This function will return all nodata mappings in a Vector of NodataMapping objects                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | [`JGeometry`](../../geometry/JGeometry.md) | `getOutArea``()`<br>Get a SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object of previous getReprojectedRasterImage call.                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `java.awt.image.RenderedImage`             | `getRasterImage``(int pyramidLevel)`<br>Returns the **entire** GeoRaster in the specified pyramidLevel as a Java Image.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `java.awt.image.RenderedImage`             | `getRasterImage``(int pyramidLevel, double[] bgValues)`<br>Returns the **entire** GeoRaster in the specified pyramidLevel as a Java Image.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `java.awt.image.RenderedImage`             | `getRasterImage``(int pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` window, long[] outWindow)`<br>Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image.                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `java.awt.image.RenderedImage`             | `getRasterImage``(int pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` window, long[] outWindow, double[] bgValues)`<br>Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image.                                                                                                                                                                                                                                                                                                                                                                                              |
    | `java.awt.image.RenderedImage`             | `getRasterImage``(int pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` window, java.lang.String transportationType, int quality, long[] outWindow)`<br>Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image.                                                                                                                                                                                                                                                                                                                                                               |
    | `java.awt.image.RenderedImage`             | `getRasterImage``(int pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` window, java.lang.String transportationType, int quality, long[] outWindow, double[] bgValues)`<br>Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image.                                                                                                                                                                                                                                                                                                                                            |
    | `java.awt.image.RenderedImage`             | `getRasterImage``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, long[] outWindow)`<br>Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image.                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `java.awt.image.RenderedImage`             | `getRasterImage``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, long[] outWindow, double[] bgValues)`<br>Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image.                                                                                                                                                                                                                                                                                                                                                                                     |
    | `java.awt.image.RenderedImage`             | `getRasterImage``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, java.lang.String transportationType, int quality, long[] outWindow)`<br>Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image.                                                                                                                                                                                                                                                                                                                                                      |
    | `java.awt.image.RenderedImage`             | `getRasterImage``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, java.lang.String transportationType, int quality, long[] outWindow, double[] bgValues)`<br>Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image.                                                                                                                                                                                                                                                                                                                                   |
    | `java.awt.image.RenderedImage`             | `getRasterImage``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, java.lang.String bandString, long[] outWindow)`<br>Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image.                                                                                                                                                                                                                                                                                                                                                                           |
    | `java.awt.image.RenderedImage`             | `getRasterImage``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, java.lang.String bandString, long[] outWindow, double[] bgValues)`<br>Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image.                                                                                                                                                                                                                                                                                                                                                        |
    | `java.awt.image.RenderedImage`             | `getRasterImage``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, java.lang.String bandString, java.lang.String transportationType, int quality, long[] outWindow)`<br>Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image.                                                                                                                                                                                                                                                                                                                         |
    | `java.awt.image.RenderedImage`             | `getRasterImage``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, java.lang.String bandString, java.lang.String transportationType, int quality, long[] outWindow, double[] bgValues)`<br>Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image.                                                                                                                                                                                                                                                                                                      |
    | `java.awt.image.RenderedImage`             | `getRasterImage``(int pyramidLevel, java.lang.String transportationType, int quality)`<br>Returns the **entire** GeoRaster in the specified pyramidLevel as a Java Image.                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `java.awt.image.RenderedImage`             | `getRasterImage``(int pyramidLevel, java.lang.String transportationType, int quality, double[] bgValues)`<br>Returns the **entire** GeoRaster in the specified pyramidLevel as a Java Image.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `java.awt.image.RenderedImage`             | `getRasterImageWithMask``(int pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` window, java.util.Vector layerNo, int zeroMapping, int oneMapping, long[] outWindow)`<br>Gets the specified portion of the GeoRaster and mask as a Java Image.                                                                                                                                                                                                                                                                                                                                                                      |
    | `java.awt.image.RenderedImage`             | `getRasterImageWithMask``(int pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` window, java.util.Vector layerNo, int zeroMapping, int oneMapping, java.lang.String transportationType, int quality, long[] outWindow)`<br>Gets the specified portion of the GeoRaster and mask as a Java Image.                                                                                                                                                                                                                                                                                                                    |
    | `java.awt.image.RenderedImage`             | `getRasterImageWithMask``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, java.util.Vector layerNo, int zeroMapping, int oneMapping, long[] outWindow)`<br>Gets the specified portion of the GeoRaster and mask as a Java Image.                                                                                                                                                                                                                                                                                                                                                             |
    | `java.awt.image.RenderedImage`             | `getRasterImageWithMask``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, java.util.Vector layerNo, int zeroMapping, int oneMapping, java.lang.String transportationType, int quality, long[] outWindow)`<br>Gets the specified portion of the GeoRaster and mask as a Java Image.                                                                                                                                                                                                                                                                                                           |
    | `int`                                      | `getRed``()`<br>Returns the band number mapped to red.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `java.awt.image.RenderedImage`             | `getReprojectedRasterImage``(int pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` window, java.lang.String resampleParam, int outSRID, long[] outWindow, double[] bgValues)`<br>Reprojects the specified portion of the GeoRaster in the specified pyramidLevel, and returns it as a Java Image.                                                                                                                                                                                                                                                                                                                   |
    | `java.awt.image.RenderedImage`             | `getReprojectedRasterImage``(int pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` window, java.lang.String resampleParam, java.lang.String transportationType, int quality, int outSRID, long[] outWindow, double[] bgValues)`<br>Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image.                                                                                                                                                                                                                                                                                    |
    | `java.awt.image.RenderedImage`             | `getReprojectedRasterImage``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, java.lang.String resampleParam, int outSRID, long[] outWindow, double[] bgValues)`<br>Reprojects the specified portion of the GeoRaster in the specified pyramidLevel, and returns it as a Java Image.                                                                                                                                                                                                                                                                                                          |
    | `java.awt.image.RenderedImage`             | `getReprojectedRasterImage``(int pyramidLevel, long startRow, long startColumn, long endRow, long endColumn, java.lang.String resampleParam, java.lang.String bandString, java.lang.String transportationType, int quality, int outSRID, long[] outWindow, double[] bgValues)`<br>Reprojects the specified portion of the GeoRaster in the specified pyramidLevel, and returns it as a Java Image.                                                                                                                                                                                                                           |
    | `int`                                      | `getTotalBandNumber``()`<br>Gets the number of bands in the current geoRasterImage based on the current setting for red/green/blue if (red=blue=green) then returns 1; otherwise, return 3.                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `boolean`                                  | `hasColormap``()`<br>Returns whether a colormap is associated with the current RGB band.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `boolean`                                  | `hasGrayscale``()`<br>Returns whether a gray scale mapping is associated with the current RGB band.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `boolean`                                  | `isVirtualMosaic``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                     | `removeNodataMapping``(double nodata)`<br>This function will remove nodata(value) mapping from existing nodata setting, which should exactly match parameter nodata.                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `boolean`                                  | `removeNodataMapping``(double nodataStart, double nodataEnd)`<br>This function will remove nodata(range) mapping from existing nodata setting, which exactly matchs parameter nodataStart and nodataEnd.                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `void`                                     | `setAlpha``(int alpha)`<br>Sets the band number mapped to the alpha channel.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `void`                                     | `setBlue``(int blue)`<br>Sets the band number mapped to blue.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `boolean`                                  | `setGlobalIPOperation``(int operation, java.lang.Double src_min, java.lang.Double src_max)`<br>This method will set global image processing operations, which includes: automatical linear stretch manual linear stretch piecewise linear stretch normalization equalization Not like image processing methods defined in the class GeoRasterImageProcessUtil, this method will use statistics data(for whole GeoRaster object) stored in the GeoRaster metadata to do image processing for each getRasterImage call, instead of using "local" statistics data calculated based on returning image from getRasterImage call. |
    | `void`                                     | `setGreen``(int green)`<br>Sets the band number mapped to green.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `void`                                     | `setRed``(int red)`<br>Sets the band number mapped to red.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### IP_NONE

          public static final int IP_NONE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### IP_AUTOMATIC_LINEAR_STRETCH

          public static final int IP_AUTOMATIC_LINEAR_STRETCH

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### IP_MANUAL_LINEAR_STRETCH

          public static final int IP_MANUAL_LINEAR_STRETCH

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### IP_PIECEWISE_LINEAR_STRETCH

          public static final int IP_PIECEWISE_LINEAR_STRETCH

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### IP_NORMALIZATION

          public static final int IP_NORMALIZATION

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### IP_EQUALIZATION

          public static final int IP_EQUALIZATION

      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### GeoRasterImage

          public GeoRasterImage(JGeoRaster georaster)
                         throws GeoRasterException

      Constructs a `GeoRasterImage` object with the given JGeoRaster object.
      Parameters:
      `georaster` - a GeoRaster object

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

    <!-- -->

    - #### GeoRasterImage

          public GeoRasterImage(JGeoRasterVM geoRasterVM,
                                MosaicParameters mosaicParam)
                         throws GeoRasterException

      Constructs a `GeoRasterImage` object with the given JGeoRasterVM object
      Parameters:
      `geoRasterVM` - a JGeoRasterVM object

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

  <!-- -->

  - ### Method Detail

    - #### setGlobalIPOperation

          public boolean setGlobalIPOperation(int operation,
                                              java.lang.Double src_min,
                                              java.lang.Double src_max)
                                       throws GeoRasterException

      This method will set global image processing operations, which includes: automatical linear stretch manual linear stretch piecewise linear stretch normalization equalization Not like image processing methods defined in the class GeoRasterImageProcessUtil, this method will use statistics data(for whole GeoRaster object) stored in the GeoRaster metadata to do image processing for each getRasterImage call, instead of using "local" statistics data calculated based on returning image from getRasterImage call.
      Parameters:
      `operation` - the image processing operations, the following are valid values: IP_NONE IP_AUTOMATIC_LINEAR_STRETCH IP_MANUAL_LINEAR_STRETCH IP_PIECEWISE_LINEAR_STRETCH IP_NORMALIZATION IP_EQUALIZATION

      `src_min` - the min value of source data range, which will be streched in the manual linear strech operation

      `src_max` - the max value of source data range, which will be streched in the manual linear strech operation

      Returns:
      false if any parameter is invalid, otherwise true.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

    <!-- -->

    - #### getGlobalIPOperation

          public int getGlobalIPOperation()

      This method will return current selected global image processing operation.
      Returns:
      current selected global image processing operation.

    <!-- -->

    - #### addNodataMapping

          public boolean addNodataMapping(double nodataStart,
                                          double nodataEnd,
                                          java.lang.Double newValue,
                                          boolean isTransparent)

      This function will add nodata(range) mapping to current image, so that all pixel values, which fall into the nodata range, will be changed to newValue and it's alpha channel value is changed too based on transparent setting by parameter isTransparent.
      Parameters:
      `nodataStart` - the lower bound of nodata range, which is inclusive

      `nodataEnd` - the upper bound of nodata range, which is exclusive

      `newValue` - new value for any pixel value in this no data range, if newValue==null then it means original data value is kept.

      `isTransparent` - set nodata pixels to transparent or opaque

      Returns:
      false if any parameter is invalid, otherwise true. Note: if current image has colorMap or grayScale, then transparent setting doesn't take effect.

    <!-- -->

    - #### addNodataMapping

          public boolean addNodataMapping(double nodata,
                                          java.lang.Double newValue,
                                          boolean isTransparent)

      This function will add nodata(value) mapping to current image, so that all pixel values, which equal to the nodata value, will be changed to newValue and it's alpha channel value is changed too based on transparent setting by parameter isTransparent.
      Parameters:
      `nodata` - nodata value

      `newValue` - new value for this no data, if newValue==null then it means original data value is kept

      `isTransparent` - set nodata pixels to transparent or opaque

      Returns:
      false if any parameter is invalid, otherwise true. Note: if current image has colorMap or grayScale, then transparent setting doesn't take effect.

    <!-- -->

    - #### removeNodataMapping

          public boolean removeNodataMapping(double nodataStart,
                                             double nodataEnd)

      This function will remove nodata(range) mapping from existing nodata setting, which exactly matchs parameter nodataStart and nodataEnd.
      Parameters:
      `nodataStart` - the lower bound of nodata range, which is inclusive

      `nodataEnd` - the upper bound of nodata range, which is exclusive

      Returns:
      false if any parameter is invalid, otherwise true.

    <!-- -->

    - #### removeNodataMapping

          public void removeNodataMapping(double nodata)

      This function will remove nodata(value) mapping from existing nodata setting, which should exactly match parameter nodata.
      Parameters:
      `nodata` - nodata value

    <!-- -->

    - #### getNodataMapping

          public java.util.Vector getNodataMapping()

      This function will return all nodata mappings in a Vector of NodataMapping objects
      Returns:
      a Vector of NodataMapping objects

    <!-- -->

    - #### getAlpha

          public int getAlpha()

      Returns the band number mapped to the alpha channel. Note that value 0 indicates no alpha channel.
      Returns:
      band number mapped to the alpha channel.

    <!-- -->

    - #### setAlpha

          public void setAlpha(int alpha)

      Sets the band number mapped to the alpha channel. Note that value 0 indicates no alpha channel. If a colormap or grayscale is associated with the current R/G/B setting, then the alpha channel will not take effect. Methods hasColormap() and hasgrayscale() can be used to check if a colormap or grayscale is associated with the current R/G/B setting.
      Parameters:
      `alpha` - band number

    <!-- -->

    - #### getRed

          public int getRed()

      Returns the band number mapped to red.
      Returns:
      band number mapped to red.

    <!-- -->

    - #### setRed

          public void setRed(int red)

      Sets the band number mapped to red.
      Parameters:
      `red` - band number

    <!-- -->

    - #### getGreen

          public int getGreen()

      Returns the band number mapped to green.
      Returns:
      band number mapped to green.

    <!-- -->

    - #### setGreen

          public void setGreen(int green)

      Sets the band number mapped to green.
      Parameters:
      `green` - band number

    <!-- -->

    - #### getBlue

          public int getBlue()

      Returns the band number mapped to blue.
      Returns:
      band number mapped to blue.

    <!-- -->

    - #### setBlue

          public void setBlue(int blue)

      Sets the band number mapped to blue.
      Parameters:
      `blue` - band number

    <!-- -->

    - #### hasColormap

          public boolean hasColormap()

      Returns whether a colormap is associated with the current RGB band.
      Returns:
      a boolean value to indicate if a colormap is associated with the current RGB band.

    <!-- -->

    - #### hasGrayscale

          public boolean hasGrayscale()

      Returns whether a gray scale mapping is associated with the current RGB band.
      Returns:
      a boolean value to indicate if a gray scale mapping is associated with the current RGB band.

    <!-- -->

    - #### getRasterImage

          public java.awt.image.RenderedImage getRasterImage(int pyramidLevel)
                                                      throws java.lang.Exception

      Returns the **entire** GeoRaster in the specified pyramidLevel as a Java Image. The Java image is generated based on r/g/b band settings in the current instance.
      Parameters:
      `pyramidLevel` - pyramid level

      Returns:
      a RenderedImage.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getRasterImage

          public java.awt.image.RenderedImage getRasterImage(int pyramidLevel,
                                                             double[] bgValues)
                                                      throws java.lang.Exception

      Returns the **entire** GeoRaster in the specified pyramidLevel as a Java Image. The Java image is generated based on r/g/b band settings in the current instance.
      Parameters:
      `pyramidLevel` - pyramid level

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      a RenderedImage.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getRasterImage

          public java.awt.image.RenderedImage getRasterImage(int pyramidLevel,
                                                             java.lang.String transportationType,
                                                             int quality)
                                                      throws java.lang.Exception

      Returns the **entire** GeoRaster in the specified pyramidLevel as a Java Image. The Java image is generated based on r/g/b band settings in the current instance. Parameter transportationType is provided to reduce network traffic.
      Parameters:
      `pyramidLevel` - pyramid level

      `transportationType` - specify whether or not to fetch data in compression from the server side; must be one of the following values:

                                     RasterInfo.COMPRESSION_NONE
                                     RasterInfo.COMPRESSION_JPEG_F
                                     RasterInfo.COMPRESSION_DEFLATE

      `quality` - JPEG compression quality, which is the degree of lossiness caused by the compression. Must be an integer from 0 (lowest quality) through 100 (highest quality).

      Returns:
      a RenderedImage.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getRasterImage

          public java.awt.image.RenderedImage getRasterImage(int pyramidLevel,
                                                             java.lang.String transportationType,
                                                             int quality,
                                                             double[] bgValues)
                                                      throws java.lang.Exception

      Returns the **entire** GeoRaster in the specified pyramidLevel as a Java Image. The Java image is generated based on r/g/b band settings in the current instance. Parameter transportationType is provided to reduce network traffic.
      Parameters:
      `pyramidLevel` - pyramid level

      `transportationType` - specify whether or not to fetch data in compression from the server side; must be one of the following values:

                                     RasterInfo.COMPRESSION_NONE
                                     RasterInfo.COMPRESSION_JPEG_F
                                     RasterInfo.COMPRESSION_DEFLATE

      `quality` - JPEG compression quality, which is the degree of lossiness caused by the compression. Must be an integer from 0 (lowest quality) through 100 (highest quality).

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      a RenderedImage.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getRasterImage

          public java.awt.image.RenderedImage getRasterImage(int pyramidLevel,
                                                             JGeometry window,
                                                             long[] outWindow)
                                                      throws GeoRasterException,
                                                             java.io.IOException

      Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image. The Java image is generated based on r/g/b band settings in the current instance.
      Parameters:
      `pyramidLevel` - pyramid level

      `window` - a JGeometry object which represents the area of interest

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      Returns:
      a RenderedImage constructed by the specified portion of the GeoRaster data.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

      `java.io.IOException`

    <!-- -->

    - #### getRasterImage

          public java.awt.image.RenderedImage getRasterImage(int pyramidLevel,
                                                             JGeometry window,
                                                             long[] outWindow,
                                                             double[] bgValues)
                                                      throws GeoRasterException,
                                                             java.io.IOException

      Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image. The Java image is generated based on r/g/b band settings in the current instance.
      Parameters:
      `pyramidLevel` - pyramid level

      `window` - a JGeometry object which represents the area of interest

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      a RenderedImage constructed by the specified portion of the GeoRaster data.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

      `java.io.IOException`

    <!-- -->

    - #### getRasterImage

          public java.awt.image.RenderedImage getRasterImage(int pyramidLevel,
                                                             JGeometry window,
                                                             java.lang.String transportationType,
                                                             int quality,
                                                             long[] outWindow)
                                                      throws GeoRasterException,
                                                             java.io.IOException

      Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image. The Java image is generated based on r/g/b band settings in the current instance.
      Parameters:
      `pyramidLevel` - pyramid level

      `window` - a JGeometry object which represents the area of interest.

      `transportationType` - specify whether or not to fetch data in compression from the server side; must be one of the following values:

                                     RasterInfo.COMPRESSION_NONE
                                     RasterInfo.COMPRESSION_JPEG_F
                                     RasterInfo.COMPRESSION_DEFLATE

      `quality` - JPEG compression quality, which is the degree of lossiness caused by the compression. Must be an integer from 0 (lowest quality) through 100 (highest quality).

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      Returns:
      a RenderedImage constructed by the specified portion of the GeoRaster data.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

      `java.io.IOException`

    <!-- -->

    - #### getRasterImage

          public java.awt.image.RenderedImage getRasterImage(int pyramidLevel,
                                                             JGeometry window,
                                                             java.lang.String transportationType,
                                                             int quality,
                                                             long[] outWindow,
                                                             double[] bgValues)
                                                      throws GeoRasterException,
                                                             java.io.IOException

      Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image. The Java image is generated based on r/g/b band settings in the current instance.
      Parameters:
      `pyramidLevel` - pyramid level

      `window` - a JGeometry object which represents the area of interest.

      `transportationType` - specify whether or not to fetch data in compression from the server side; must be one of the following values:

                                     RasterInfo.COMPRESSION_NONE
                                     RasterInfo.COMPRESSION_JPEG_F
                                     RasterInfo.COMPRESSION_DEFLATE

      `quality` - JPEG compression quality, which is the degree of lossiness caused by the compression. Must be an integer from 0 (lowest quality) through 100 (highest quality).

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      a RenderedImage constructed by the specified portion of the GeoRaster data.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

      `java.io.IOException`

    <!-- -->

    - #### getRasterImage

          public java.awt.image.RenderedImage getRasterImage(int pyramidLevel,
                                                             long startRow,
                                                             long startColumn,
                                                             long endRow,
                                                             long endColumn,
                                                             long[] outWindow)
                                                      throws GeoRasterException,
                                                             java.io.IOException

      Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image. The Java image is generated based on r/g/b band settings in the current instance.
      This method is usually used by applications to visualize the Georaster object.

      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - start row number, not including ULTCoordinate.

      `startColumn` - start column number, not including ULTCoordinate.

      `endRow` - end row number, not including ULTCoordinate.

      `endColumn` - end column number, not including ULTCoordinate.

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      Returns:
      a Java image constructed by the specified portion of the GeoRaster data.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

      `java.io.IOException`

    <!-- -->

    - #### getRasterImage

          public java.awt.image.RenderedImage getRasterImage(int pyramidLevel,
                                                             long startRow,
                                                             long startColumn,
                                                             long endRow,
                                                             long endColumn,
                                                             long[] outWindow,
                                                             double[] bgValues)
                                                      throws GeoRasterException,
                                                             java.io.IOException

      Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image. The Java image is generated based on r/g/b band settings in the current instance.
      This method is usually used by applications to visualize the Georaster object.

      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - start row number, not including ULTCoordinate.

      `startColumn` - start column number, not including ULTCoordinate.

      `endRow` - end row number, not including ULTCoordinate.

      `endColumn` - end column number, not including ULTCoordinate.

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      a Java image constructed by the specified portion of the GeoRaster data.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

      `java.io.IOException`

    <!-- -->

    - #### getRasterImage

          public java.awt.image.RenderedImage getRasterImage(int pyramidLevel,
                                                             long startRow,
                                                             long startColumn,
                                                             long endRow,
                                                             long endColumn,
                                                             java.lang.String transportationType,
                                                             int quality,
                                                             long[] outWindow)
                                                      throws GeoRasterException,
                                                             java.io.IOException

      Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image. The Java image is generated based on r/g/b band settings in the current instance.
      This method is usually used by applications to visualize the Georaster object.

      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - start row number, not including ULTCoordinate.

      `startColumn` - start column number, not including ULTCoordinate.

      `endRow` - end row number, not including ULTCoordinate.

      `endColumn` - end column number, not including ULTCoordinate.

      `transportationType` - specify whether or not to fetch data in compression from the server side; must be one of the following values:

                                     RasterInfo.COMPRESSION_NONE
                                     RasterInfo.COMPRESSION_JPEG_F
                                     RasterInfo.COMPRESSION_DEFLATE

      `quality` - JPEG compression quality, which is the degree of lossiness caused by the compression. Must be an integer from 0 (lowest quality) through 100 (highest quality).

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      Returns:
      a Java image constructed by the specified portion of the GeoRaster data.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

      `java.io.IOException`

    <!-- -->

    - #### getRasterImage

          public java.awt.image.RenderedImage getRasterImage(int pyramidLevel,
                                                             long startRow,
                                                             long startColumn,
                                                             long endRow,
                                                             long endColumn,
                                                             java.lang.String transportationType,
                                                             int quality,
                                                             long[] outWindow,
                                                             double[] bgValues)
                                                      throws GeoRasterException,
                                                             java.io.IOException

      Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image. The Java image is generated based on r/g/b band settings in the current instance.
      This method is usually used by applications to visualize the Georaster object.

      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - start row number, not including ULTCoordinate.

      `startColumn` - start column number, not including ULTCoordinate.

      `endRow` - end row number, not including ULTCoordinate.

      `endColumn` - end column number, not including ULTCoordinate.

      `transportationType` - specify whether or not to fetch data in compression from the server side; must be one of the following values:

                                     RasterInfo.COMPRESSION_NONE
                                     RasterInfo.COMPRESSION_JPEG_F
                                     RasterInfo.COMPRESSION_DEFLATE

      `quality` - JPEG compression quality, which is the degree of lossiness caused by the compression. Must be an integer from 0 (lowest quality) through 100 (highest quality).

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      a Java image constructed by the specified portion of the GeoRaster data.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

      `java.io.IOException`

    <!-- -->

    - #### getRasterImage

          public java.awt.image.RenderedImage getRasterImage(int pyramidLevel,
                                                             long startRow,
                                                             long startColumn,
                                                             long endRow,
                                                             long endColumn,
                                                             java.lang.String bandString,
                                                             long[] outWindow)
                                                      throws GeoRasterException,
                                                             java.io.IOException

      Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image. The Java image is generated based on parameter bandString, instead of r/g/b band settings in the current instance; thus, that Java image might have more than 3 bands.
      This method can be used by applications to export a GeoRaster object into an image file through Java image I/O.

      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - start row number, not including ULTCoordinate.

      `startColumn` - start column number, not including ULTCoordinate.

      `endRow` - end row number, not including ULTCoordinate.

      `endColumn` - end column number, not including ULTCoordinate.

      `bandString` - a string to specify which band will be included in the image.

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      Returns:
      a Java image constructed by the specified portion of the GeoRaster data.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

      `java.io.IOException`

    <!-- -->

    - #### getRasterImage

          public java.awt.image.RenderedImage getRasterImage(int pyramidLevel,
                                                             long startRow,
                                                             long startColumn,
                                                             long endRow,
                                                             long endColumn,
                                                             java.lang.String bandString,
                                                             long[] outWindow,
                                                             double[] bgValues)
                                                      throws GeoRasterException,
                                                             java.io.IOException

      Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image. The Java image is generated based on parameter bandString, instead of r/g/b band settings in the current instance; thus, that Java image might have more than 3 bands.
      This method can be used by applications to export a GeoRaster object into an image file through Java image I/O.

      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - start row number, not including ULTCoordinate.

      `startColumn` - start column number, not including ULTCoordinate.

      `endRow` - end row number, not including ULTCoordinate.

      `endColumn` - end column number, not including ULTCoordinate.

      `bandString` - a string to specify which band will be included in the image.

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      a Java image constructed by the specified portion of the GeoRaster data.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

      `java.io.IOException`

    <!-- -->

    - #### getRasterImage

          public java.awt.image.RenderedImage getRasterImage(int pyramidLevel,
                                                             long startRow,
                                                             long startColumn,
                                                             long endRow,
                                                             long endColumn,
                                                             java.lang.String bandString,
                                                             java.lang.String transportationType,
                                                             int quality,
                                                             long[] outWindow)
                                                      throws GeoRasterException,
                                                             java.io.IOException

      Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image. The Java image is generated based on parameter bandString, instead of r/g/b band settings in the current instance; thus, that Java image might have more than 3 bands.
      This method can be used by applications to export a GeoRaster object into an image file through Java image I/O.

      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - start row number, not including ULTCoordinate.

      `startColumn` - start column number, not including ULTCoordinate.

      `endRow` - end row number, not including ULTCoordinate.

      `endColumn` - end column number, not including ULTCoordinate.

      `bandString` - a string to specify which band will be included in the image.

      `transportationType` - specify whether or not to fetch data in compression from the server side; must be one of the following values:

                                     RasterInfo.COMPRESSION_NONE
                                     RasterInfo.COMPRESSION_JPEG_F
                                     RasterInfo.COMPRESSION_DEFLATE

      `quality` - JPEG compression quality, which is the degree of lossiness caused by the compression. Must be an integer from 0 (lowest quality) through 100 (highest quality).

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      Returns:
      a Java image constructed by the specified portion of the GeoRaster data.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

      `java.io.IOException`

    <!-- -->

    - #### getRasterImage

          public java.awt.image.RenderedImage getRasterImage(int pyramidLevel,
                                                             long startRow,
                                                             long startColumn,
                                                             long endRow,
                                                             long endColumn,
                                                             java.lang.String bandString,
                                                             java.lang.String transportationType,
                                                             int quality,
                                                             long[] outWindow,
                                                             double[] bgValues)
                                                      throws GeoRasterException,
                                                             java.io.IOException

      Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image. The Java image is generated based on parameter bandString, instead of r/g/b band settings in the current instance; thus, that Java image might have more than 3 bands.
      This method can be used by applications to export a GeoRaster object into an image file through Java image I/O.

      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - start row number, not including ULTCoordinate.

      `startColumn` - start column number, not including ULTCoordinate.

      `endRow` - end row number, not including ULTCoordinate.

      `endColumn` - end column number, not including ULTCoordinate.

      `bandString` - a string to specify which band will be included in the image.

      `transportationType` - specify whether or not to fetch data in compression from the server side; must be one of the following values:

                                     RasterInfo.COMPRESSION_NONE
                                     RasterInfo.COMPRESSION_JPEG_F
                                     RasterInfo.COMPRESSION_DEFLATE

      `quality` - JPEG compression quality, which is the degree of lossiness caused by the compression. Must be an integer from 0 (lowest quality) through 100 (highest quality).

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      a Java image constructed by the specified portion of the GeoRaster data.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

      `java.io.IOException`

    <!-- -->

    - #### getOutArea

          public JGeometry getOutArea()

      Get a SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object of previous getReprojectedRasterImage call.
      Returns:
      a SDO_GEOMETRY object containing the MBR of the resulting object of previous getReprojectedRasterImage call.

    <!-- -->

    - #### getReprojectedRasterImage

          public java.awt.image.RenderedImage getReprojectedRasterImage(int pyramidLevel,
                                                                        JGeometry window,
                                                                        java.lang.String resampleParam,
                                                                        int outSRID,
                                                                        long[] outWindow,
                                                                        double[] bgValues)
                                                                 throws GeoRasterException,
                                                                        java.io.IOException

      Reprojects the specified portion of the GeoRaster in the specified pyramidLevel, and returns it as a Java Image. The Java image is generated based on r/g/b band settings in the current instance. The immediately following getOutArea() call will return a SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.
      Parameters:
      `pyramidLevel` - pyramid level

      `window` - a JGeometry object which represents the area of interest

      `resampleParam` - a string containing the resampling parameters.

      `outSRID` - target srid number

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      a RenderedImage constructed by the specified portion of the GeoRaster data after reprojection.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

      `java.io.IOException`

    <!-- -->

    - #### getReprojectedRasterImage

          public java.awt.image.RenderedImage getReprojectedRasterImage(int pyramidLevel,
                                                                        JGeometry window,
                                                                        java.lang.String resampleParam,
                                                                        java.lang.String transportationType,
                                                                        int quality,
                                                                        int outSRID,
                                                                        long[] outWindow,
                                                                        double[] bgValues)
                                                                 throws GeoRasterException,
                                                                        java.io.IOException

      Returns the specified portion of the GeoRaster in the specified pyramidLevel as a Java Image. The Java image is generated based on r/g/b band settings in the current instance.The immediately following getOutArea() call will return a SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.
      Parameters:
      `pyramidLevel` - pyramid level

      `window` - a JGeometry object which represents the area of interest.

      `transportationType` - specify whether or not to fetch data in compression from the server side; must be one of the following values:

                                     RasterInfo.COMPRESSION_NONE
                                     RasterInfo.COMPRESSION_JPEG_F
                                     RasterInfo.COMPRESSION_DEFLATE

      `quality` - JPEG compression quality, which is the degree of lossiness caused by the compression. Must be an integer from 0 (lowest quality) through 100 (highest quality).

      `resampleParam` - a string containing the resampling parameters.

      `outSRID` - target srid number

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      a RenderedImage constructed by the specified portion of the GeoRaster data after reprojection.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

      `java.io.IOException`

    <!-- -->

    - #### getReprojectedRasterImage

          public java.awt.image.RenderedImage getReprojectedRasterImage(int pyramidLevel,
                                                                        long startRow,
                                                                        long startColumn,
                                                                        long endRow,
                                                                        long endColumn,
                                                                        java.lang.String resampleParam,
                                                                        int outSRID,
                                                                        long[] outWindow,
                                                                        double[] bgValues)
                                                                 throws GeoRasterException,
                                                                        java.io.IOException

      Reprojects the specified portion of the GeoRaster in the specified pyramidLevel, and returns it as a Java Image. The Java image is generated based on r/g/b band settings in the current instance. The immediately following getOutArea() call will return a SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.
      This method is usually used by applications to visualize the Georaster object.

      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - start row number, not including ULTCoordinate.

      `startColumn` - start column number, not including ULTCoordinate.

      `endRow` - end row number, not including ULTCoordinate.

      `endColumn` - end column number, not including ULTCoordinate.

      `resampleParam` - a string containing the resampling parameters.

      `outSRID` - target srid number

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      a Java image constructed by the specified portion of the GeoRaster data after reprojection.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

      `java.io.IOException`

    <!-- -->

    - #### getReprojectedRasterImage

          public java.awt.image.RenderedImage getReprojectedRasterImage(int pyramidLevel,
                                                                        long startRow,
                                                                        long startColumn,
                                                                        long endRow,
                                                                        long endColumn,
                                                                        java.lang.String resampleParam,
                                                                        java.lang.String bandString,
                                                                        java.lang.String transportationType,
                                                                        int quality,
                                                                        int outSRID,
                                                                        long[] outWindow,
                                                                        double[] bgValues)
                                                                 throws GeoRasterException,
                                                                        java.io.IOException

      Reprojects the specified portion of the GeoRaster in the specified pyramidLevel, and returns it as a Java Image. The Java image is generated based on parameter bandString, instead of r/g/b band settings in the current instance; thus, that Java image might have more than 3 bands.The immediately following getOutArea() call will return a SDO_GEOMETRY object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.
      This method can be used by applications to export a GeoRaster object into an image file through Java image I/O.

      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - start row number, not including ULTCoordinate.

      `startColumn` - start column number, not including ULTCoordinate.

      `endRow` - end row number, not including ULTCoordinate.

      `endColumn` - end column number, not including ULTCoordinate.

      `resampleParam` - a string containing the resampling parameters.

      `bandString` - a string to specify which band will be included in the image.

      `transportationType` - specify whether or not to fetch data in compression from the server side; must be one of the following values:

                                     RasterInfo.COMPRESSION_NONE
                                     RasterInfo.COMPRESSION_JPEG_F
                                     RasterInfo.COMPRESSION_DEFLATE

      `quality` - JPEG compression quality, which is the degree of lossiness caused by the compression. Must be an integer from 0 (lowest quality) through 100 (highest quality).

      `outSRID` - target srid number

      `outWindow` - an SDO_NUMBER_ARRAY object identifying the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `bgValues` - background values for filling sparse data. The number of elements in the array must be either one (same filing value used for all bands) or the band dimension size (a different filling value for each band, respectively). This parameter is useful when the source has empty raster blocks and the output window intersects any empty raster blocks. If this parameter is null, any cells in the output window that are derived from an empty raster block are filled with the value 0 in the output BLOB. Note that this parameter only works in version 11 or later.

      Returns:
      a Java image constructed by the specified portion of the GeoRaster data after reprojection.

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

      `java.io.IOException`

    <!-- -->

    - #### getMaskImage

          public java.awt.image.RenderedImage getMaskImage(int pyramidLevel,
                                                           JGeometry window,
                                                           java.util.Vector layerNo,
                                                           int zeroMapping,
                                                           int oneMapping,
                                                           long[] outWindow)
                                                    throws java.lang.Exception

      Returns the specified portion of the GeoRaster mask in the specified pyramidLevel and layer as a Java Image. In order to generate a Java image, this method will extend mask data from 1 bit to 8 bits unsign, and use parameters zeroMapping and oneMapping to constuct a Java IndexColorModel object to map values 0 and 1 to different color values. zeroMapping and oneMapping must be in the range \[0,255\]
      Parameters:
      `pyramidLevel` - pyramid level

      `window` - a JGeometry object which represents the area of interest

      `layerNo` - layer number; note: 0 for object layer

      `zeroMapping` - the value to which the bitmap mask value 0 is mapped

      `oneMapping` - the value to which the bitmap mask value 1 is mapped

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      Returns:
      a Java image constructed by the specified portion of the GeoRaster data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getMaskImage

          public java.awt.image.RenderedImage getMaskImage(int pyramidLevel,
                                                           JGeometry window,
                                                           java.util.Vector layerNo,
                                                           int zeroMapping,
                                                           int oneMapping,
                                                           java.lang.String transportationType,
                                                           long[] outWindow)
                                                    throws java.lang.Exception

      Returns the specified portion of the GeoRaster mask in the specified pyramidLevel and layer as a Java Image. In order to generate a Java image, this method will extend mask data from 1 bit to 8 bits unsign, and use parameters zeroMapping and oneMapping to constuct a Java IndexColorModel object to map values 0 and 1 to different color values. zeroMapping and oneMapping must be in the range \[0,255\]
      Parameters:
      `pyramidLevel` - pyramid level

      `window` - a JGeometry object which represents the area of interest

      `layerNo` - layer number; note: 0 for object layer

      `zeroMapping` - the value to which the bitmap mask value 0 is mapped

      `oneMapping` - the value to which the bitmap mask value 1 is mapped

      `transportationType` - specify whether or not to fetch data in compression from the server side; must be one of the following values:

                                     RasterInfo.COMPRESSION_NONE
                                     RasterInfo.COMPRESSION_DEFLATE

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      Returns:
      a Java image constructed by the specified portion of the GeoRaster data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getMaskImage

          public java.awt.image.RenderedImage getMaskImage(int pyramidLevel,
                                                           long startRow,
                                                           long startColumn,
                                                           long endRow,
                                                           long endColumn,
                                                           java.util.Vector layerNo,
                                                           int zeroMapping,
                                                           int oneMapping,
                                                           long[] outWindow)
                                                    throws java.lang.Exception

      Returns the specified portion of the GeoRaster mask in the specified pyramidLevel and layer as a Java Image. In order to generate a Java image, this method will extend mask data from 1 bit to 8 bits unsign, and use parameters zeroMapping and oneMapping to constuct a Java IndexColorModel object to map values 0 and 1 to different color values. zeroMapping and oneMapping must be in the range \[0,255\]
      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - start row number, not including ULTCoordinate.

      `startColumn` - start column number, not including ULTCoordinate.

      `endRow` - end row number, not including ULTCoordinate.

      `endColumn` - end column number, not including ULTCoordinate.

      `layerNo` - layer number; note: 0 for object layer

      `zeroMapping` - the value to which the bitmap mask value 0 is mapped

      `oneMapping` - the value to which the bitmap mask value 1 is mapped

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      Returns:
      a Java image constructed by the specified portion of the GeoRaster data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getMaskImage

          public java.awt.image.RenderedImage getMaskImage(int pyramidLevel,
                                                           long startRow,
                                                           long startColumn,
                                                           long endRow,
                                                           long endColumn,
                                                           java.util.Vector layerNo,
                                                           int zeroMapping,
                                                           int oneMapping,
                                                           java.lang.String transportationType,
                                                           long[] outWindow)
                                                    throws java.lang.Exception

      Returns the specified portion of the GeoRaster mask in the specified pyramidLevel and layer as a Java Image. In order to generate a Java image, this method will extend mask data from 1 bit to 8 bits unsign, and use parameters zeroMapping and oneMapping to constuct a Java IndexColorModel object to map values 0 and 1 to different color values. zeroMapping and oneMapping must be in the range \[0,255\]
      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - start row number, not including ULTCoordinate.

      `startColumn` - start column number, not including ULTCoordinate.

      `endRow` - end row number, not including ULTCoordinate.

      `endColumn` - end column number, not including ULTCoordinate.

      `layerNo` - layer number; note: 0 for object layer

      `zeroMapping` - the value to which the bitmap mask value 0 is mapped

      `oneMapping` - the value to which the bitmap mask value 1 is mapped

      `transportationType` - specify whether or not to fetch data in compression from the server side; must be one of the following values:

                                     RasterInfo.COMPRESSION_NONE
                                     RasterInfo.COMPRESSION_DEFLATE

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      Returns:
      a Java image constructed by the specified portion of the GeoRaster data.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getRasterImageWithMask

          public java.awt.image.RenderedImage getRasterImageWithMask(int pyramidLevel,
                                                                     JGeometry window,
                                                                     java.util.Vector layerNo,
                                                                     int zeroMapping,
                                                                     int oneMapping,
                                                                     long[] outWindow)

      Gets the specified portion of the GeoRaster and mask as a Java Image. This method will generate raster image and mask image first, and then apply a JAI composite operation on both images to generate the returned Java image.
      Parameters:
      `pyramidLevel` - pyramid level

      `window` - a JGeometry object which represents the area of interest.

      `layerNo` - layer number; note: 0 for object layer

      `zeroMapping` - the value to which the bitmap mask value 0 is mapped

      `oneMapping` - the value to which the bitmap mask value 1 is mapped

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      Returns:
      a Java image constructed by the specified portion of the GeoRaster data and mask.

    <!-- -->

    - #### getRasterImageWithMask

          public java.awt.image.RenderedImage getRasterImageWithMask(int pyramidLevel,
                                                                     JGeometry window,
                                                                     java.util.Vector layerNo,
                                                                     int zeroMapping,
                                                                     int oneMapping,
                                                                     java.lang.String transportationType,
                                                                     int quality,
                                                                     long[] outWindow)

      Gets the specified portion of the GeoRaster and mask as a Java Image. This method will generate raster image and mask image first, and then apply a JAI composite operation on both images to generate the returned Java image.
      Parameters:
      `pyramidLevel` - pyramid level

      `window` - a JGeometry object which represents the area of interest.

      `layerNo` - layer number; note: 0 for object layer

      `zeroMapping` - the value to which the bitmap mask value 0 is mapped

      `oneMapping` - the value to which the bitmap mask value 1 is mapped

      `transportationType` - specify whether or not to fetch data in compression from the server side; must be one of the following values:

                                     RasterInfo.COMPRESSION_NONE
                                     RasterInfo.COMPRESSION_JPEG_F
                                     RasterInfo.COMPRESSION_DEFLATE

      `quality` - JPEG compression quality, which is the degree of lossiness caused by the compression. Must be an integer from 0 (lowest quality) through 100 (highest quality).

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      Returns:
      a Java image constructed by the specified portion of the GeoRaster data. and mask.

    <!-- -->

    - #### getRasterImageWithMask

          public java.awt.image.RenderedImage getRasterImageWithMask(int pyramidLevel,
                                                                     long startRow,
                                                                     long startColumn,
                                                                     long endRow,
                                                                     long endColumn,
                                                                     java.util.Vector layerNo,
                                                                     int zeroMapping,
                                                                     int oneMapping,
                                                                     long[] outWindow)

      Gets the specified portion of the GeoRaster and mask as a Java Image. This method will generate raster image and mask image first, and then apply a JAI composite operation on both images to generate the returned Java image.
      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - start row number, not including ULTCoordinate

      `startColumn` - start column number, not including ULTCoordinate

      `endRow` - end row number, not including ULTCoordinate

      `endColumn` - end column number, not including ULTCoordinate

      `layerNo` - layer number; note: 0 for object layer

      `zeroMapping` - the value to which the bitmap mask value 0 is mapped

      `oneMapping` - the value to which the bitmap mask value 1 is mapped

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      Returns:
      a Java image constructed by the specified portion of the GeoRaster data and mask.

    <!-- -->

    - #### getRasterImageWithMask

          public java.awt.image.RenderedImage getRasterImageWithMask(int pyramidLevel,
                                                                     long startRow,
                                                                     long startColumn,
                                                                     long endRow,
                                                                     long endColumn,
                                                                     java.util.Vector layerNo,
                                                                     int zeroMapping,
                                                                     int oneMapping,
                                                                     java.lang.String transportationType,
                                                                     int quality,
                                                                     long[] outWindow)

      Gets the specified portion of the GeoRaster and mask as a Java Image. This method will generate raster image and mask image first, and then apply a JAI composite operation on both images to generate the returned Java image.
      Parameters:
      `pyramidLevel` - pyramid level

      `startRow` - start row number, not including ULTCoordinate

      `startColumn` - start column number, not including ULTCoordinate

      `endRow` - end row number, not including ULTCoordinate

      `endColumn` - end column number, not including ULTCoordinate

      `layerNo` - layer number; note: 0 for object layer

      `zeroMapping` - the value to which the bitmap mask value 0 is mapped

      `oneMapping` - the value to which the bitmap mask value 1 is mapped

      `transportationType` - specify whether or not to fetch data in compression from the server side; must be one of the following values:

                                     RasterInfo.COMPRESSION_NONE
                                     RasterInfo.COMPRESSION_JPEG_F
                                     RasterInfo.COMPRESSION_DEFLATE

      `quality` - JPEG compression quality, which is the degree of lossiness caused by the compression. Must be an integer from 0 (lowest quality) through 100 (highest quality).

      `outWindow` - a long array returning the coordinates of the upper-left and lower-right corners of the output window in the cell space. Note that the caller must pass in a long array, and the length of the array should be 4. The method getModelCoordinate(...) defined in the class SpatialReferenceInfo can be used to transform this outWindow into model space.

      Returns:
      a Java image constructed by the specified portion of the GeoRaster data and mask.

    <!-- -->

    - #### getTotalBandNumber

          public int getTotalBandNumber()

      Gets the number of bands in the current geoRasterImage based on the current setting for red/green/blue if (red=blue=green) then returns 1; otherwise, return 3. Note: for celldepth 32BIT_REAL, the method always returns 3, because Java image does not support indexColorModel with this cell depth.
      Returns:
      the number of bands in the current geoRasterImage.

    <!-- -->

    - #### isVirtualMosaic

          public boolean isVirtualMosaic()

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
- [Next Class](GeoRasterImage.NodataMapping.md)

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
