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

- [Prev Class](SdoGeoRaster.md)
- [Next Class](SdoGeorPKG.md)

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

oracle.spatial.georaster.sql

## Class SdoGeorIpPKG

- java.lang.Object

- - oracle.spatial.georaster.sql.SdoGeorIpPKG

<!-- -->

-

  ------------------------------------------------------------------------



      public class SdoGeorIpPKG
      extends java.lang.Object

  SdoGeorIpPKG is a Java class which wraps PL/SQL functions and procedures defined in the server-side package SDO_GEOR_IP. When a method defined in the class is invoked, a corresponding PL/SQL block is generated and submitted to the target Oracle database through a JDBC connection, so that equivalent result by PL/SQL can be achieved from the Java side.
  Note that all methods in this class are transactional, which means that no commit statement is issued implicitly in each method.

  The following is an example of how to use this class:

         //initialize an instance of SdoGeorRaPKG
         SdoGeorRaPKG  pkg=new SdoGeorIpPKG(connection);
         //reading a GeoRaster object from database based on a query
         Statement stmt = connection.createStatement();
         ResultSet rs = statement.executeQuery("SELECT a.georaster FROM georaster_table a where a.georaster.rasterdatatable='RDT' and a.georaster.rasterid=1");
         rs.next();
         STRUCT geor = (oracle.sql.STRUCT) rs.getObject(1);
         //convert STRUCT into SdoGeoRaster
         SdoGeoRaster sdoGeoRaster = new SdoGeoRaster(geor);
         rs = statement.executeQuery("SELECT a.georaster FROM georaster_table a where a.georaster.rasterdatatable='RDT' and a.georaster.rasterid=2");
         rs.next();
         geor = (oracle.sql.STRUCT) rs.getObject(1);
         //convert STRUCT into SdoGeoRaster
         SdoGeoRaster sdoGeoRaster1 = new SdoGeoRaster(geor);
         pkg.dodge(sdoGeoRaster,new double[]{512,512},'samplingFactor=3',new double[]{125},new double[]{80},null,sdoGeoRaster1);

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                   |
    |---------------------------------------------------------------------------------------------------------------|
    | `SdoGeorIpPKG``(java.sql.Connection conn)`<br>Constructs an `SdoGeorIpPKG` object using the given connection. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    |-----------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                | `dodge``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, double[] gridSize, int samplingFactor, double[] means, double[] standardDeviations, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, int parallelDegree)`<br>Apply a dodging algorithm on the input GeoRaster object to color balance the image..                                                                                                                                                                                                                           |
    | `void`                | `dodge``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, double[] gridSize, int samplingFactor, `[`SdoGeoRaster`](SdoGeoRaster.md)` refGeoRaster, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, int parallelDegree)`<br>Apply a dodging algorithm on the input GeoRaster object to color balance the image..                                                                                                                                                                                                                      |
    | `void`                | `equalize``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, java.math.BigDecimal[] cropArea, java.lang.String bandNumbers, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow)`<br>Process the input GeoRaster object by using histogram equalization method.                                                                                                                                                                                     |
    | `void`                | `equalize``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, java.math.BigDecimal[] cropArea, java.lang.String bandNumbers, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, int parallelDegree)`<br>Process the input GeoRaster object by using histogram equalization method.                                                                                                                                                                                                                       |
    | `void`                | `equalize``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String layerNumbers, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow)`<br>Process the input GeoRaster object by using histogram equalization method.                                                                                                                                                              |
    | `void`                | `equalize``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String layerNumbers, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, int parallelDegree)`<br>Process the input GeoRaster object by using histogram equalization method.                                                                                                                                                                                                |
    | `void`                | `filter``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, java.math.BigDecimal[] cropArea, java.lang.String bandNumbers, java.lang.String filterParam, double[] filterKernel, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow)`<br>Applies the convolution filter on the input GeoRaster object.                                                                                                                                               |
    | `void`                | `filter``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, java.math.BigDecimal[] cropArea, java.lang.String bandNumbers, java.lang.String filterParam, double[] filterKernel, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, int parallelDegree)`<br>Applies the convolution filter on the input GeoRaster object.                                                                                                                                                                                 |
    | `void`                | `filter``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String layerNumbers, java.lang.String filterParam, double[] filterKernel, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow)`<br>Applies the convolution filter on the input GeoRaster object.                                                                                                                        |
    | `void`                | `filter``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String layerNumbers, java.lang.String filterParam, double[] filterKernel, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, int parallelDegree)`<br>Applies the convolution filter on the input GeoRaster object.                                                                                                                                                          |
    | `java.sql.Connection` | `getConnection``()`<br>Returns a connection which points to target database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                | `histogramMatch``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, java.math.BigDecimal[] cropArea, java.lang.String bandNumbers, `[`GeorHistogram`](../GeorHistogram.md)`[] refHistograms, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, int parallelDegree)`<br>Processes the input GeoRaster object so that the histograms of the output GeoRaster object matches the histogram of a reference GeoRaster object (refGeoRaster) or a reference histogram (refHistograms).                        |
    | `void`                | `histogramMatch``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, java.math.BigDecimal[] cropArea, java.lang.String bandNumbers, `[`SdoGeoRaster`](SdoGeoRaster.md)` refGeoRaster, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, int parallelDegree)`<br>Processes the input GeoRaster object so that the histograms of the output GeoRaster object matches the histogram of a reference GeoRaster object (refGeoRaster) or a reference histogram (refHistograms).                                |
    | `void`                | `histogramMatch``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String layerNumbers, `[`GeorHistogram`](../GeorHistogram.md)`[] refHistograms, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, int parallelDegree)`<br>Processes the input GeoRaster object so that the histograms of the output GeoRaster object matches the histogram of a reference GeoRaster object (refGeoRaster) or a reference histogram (refHistograms). |
    | `void`                | `histogramMatch``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String layerNumbers, `[`SdoGeoRaster`](SdoGeoRaster.md)` refGeoRaster, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, int parallelDegree)`<br>Processes the input GeoRaster object so that the histograms of the output GeoRaster object matches the histogram of a reference GeoRaster object (refGeoRaster) or a reference histogram (refHistograms).         |
    | `void`                | `normalize``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, java.math.BigDecimal[] cropArea, java.lang.String bandNumbers, double[] means, double[] standardDeviations, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow)`<br>Normalizes the input GeoRaster object using the specified mean and standard deviation.                                                                                                                           |
    | `void`                | `normalize``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, java.math.BigDecimal[] cropArea, java.lang.String bandNumbers, double[] means, double[] standardDeviations, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, int parallelDegree)`<br>Normalizes the input GeoRaster object using the specified mean and standard deviation.                                                                                                                                                             |
    | `void`                | `normalize``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, java.math.BigDecimal[] cropArea, java.lang.String bandNumbers, `[`SdoGeoRaster`](SdoGeoRaster.md)` refGeoRaster, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, int parallelDegree)`<br>Normalizes the input GeoRaster object using the specified mean and standard deviation.                                                                                                                                                        |
    | `void`                | `normalize``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String layerNumbers, double[] means, double[] standardDeviations, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow)`<br>Normalizes the input GeoRaster object using the specified mean and standard deviation.                                                                                                    |
    | `void`                | `normalize``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String layerNumbers, double[] means, double[] standardDeviations, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, int parallelDegree)`<br>Normalizes the input GeoRaster object using the specified mean and standard deviation.                                                                                                                                      |
    | `void`                | `normalize``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String layerNumbers, `[`SdoGeoRaster`](SdoGeoRaster.md)` refGeoRaster, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, int parallelDegree)`<br>Normalizes the input GeoRaster object using the specified mean and standard deviation.                                                                                                                                 |
    | `void`                | `piecewiseStretch``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, java.math.BigDecimal[] cropArea, java.lang.String bandNumbers, double[][] inValues, double[][] outValues, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow)`<br>Performs a linear stretch on the input GeoRaster object using the minimum and maximum values.                                                                                                               |
    | `void`                | `piecewiseStretch``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, java.math.BigDecimal[] cropArea, java.lang.String bandNumbers, double[][] inValues, double[][] outValues, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, int parallelDegree)`<br>Performs a linear stretch on the input GeoRaster object using the minimum and maximum values.                                                                                                                                                 |
    | `void`                | `piecewiseStretch``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String layerNumbers, double[][] inValues, double[][] outValues, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow)`<br>Performs a linear stretch on the input GeoRaster object using the minimum and maximum values.                                                                                        |
    | `void`                | `piecewiseStretch``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String layerNumbers, double[][] inValues, double[][] outValues, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, int parallelDegree)`<br>Performs a linear stretch on the input GeoRaster object using the minimum and maximum values.                                                                                                                          |
    | `void`                | `setConnection``(java.sql.Connection conn)`<br>Sets the connection which points to the target database.                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `void`                | `stretch``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, java.math.BigDecimal[] cropArea, java.lang.String bandNumbers, double[] minValues, double[] maxValues, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow)`<br>Performs a min-max linear stretch on the input GeoRaster object using the minimum and maximum values.                                                                                                                   |
    | `void`                | `stretch``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, java.math.BigDecimal[] cropArea, java.lang.String bandNumbers, double[] minValues, double[] maxValues, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, int parallelDegree)`<br>Performs a min-max linear stretch on the input GeoRaster object using the minimum and maximum values.                                                                                                                                                     |
    | `void`                | `stretch``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String layerNumbers, double[] minValues, double[] maxValues, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow)`<br>Performs a min-max linear stretch on the input GeoRaster object using the minimum and maximum values.                                                                                            |
    | `void`                | `stretch``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String layerNumbers, double[] minValues, double[] maxValues, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, int parallelDegree)`<br>Performs a min-max linear stretch on the input GeoRaster object using the minimum and maximum values.                                                                                                                              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SdoGeorIpPKG

          public SdoGeorIpPKG(java.sql.Connection conn)

      Constructs an `SdoGeorIpPKG` object using the given connection.
      Parameters:
      `conn` - a JDBC connection.

  <!-- -->

  - ### Method Detail

    - #### setConnection

          public void setConnection(java.sql.Connection conn)

      Sets the connection which points to the target database.
      Parameters:
      `conn` - a JDBC connection

    <!-- -->

    - #### getConnection

          public java.sql.Connection getConnection()

      Returns a connection which points to target database.
      Returns:
      a connection which points to target database.

    <!-- -->

    - #### dodge

          public void dodge(SdoGeoRaster inGeoRaster,
                            double[] gridSize,
                            int samplingFactor,
                            double[] means,
                            double[] standardDeviations,
                            java.lang.String storageParam,
                            SdoGeoRaster outGeoRaster,
                            int parallelDegree)
                     throws java.lang.Exception

      Apply a dodging algorithm on the input GeoRaster object to color balance the image..
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be dodged.

      `gridSize` - The size of each grid in x and y direction, respectively. It is an array of one or two numbers. If only one number is specified, then it is for both x and y direction.

      `samplingFactor` - Sampling factor, used to control the calculation of the statistics,with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example,if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1,all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed. samplingFactor cannot be greater than or equal to one-half (0.5) of gridSize.

      `means` - The target mean values for each output bands. If only one value is specified, it is applied to all the output bands; otherwise, it must have the same number of values as the number bands of the output GeoRaster object. If null, it is calculated as the average mean value over all the grids.

      `standardDeviations` - The target standard deviation values for each output bands. If only one value is specified, it is applied to all the output bands; otherwise, it must have the same number of values as the number of bands of the output GeoRaster object. If null, it is calculated as the average standard deviation over all the grids.

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### dodge

          public void dodge(SdoGeoRaster inGeoRaster,
                            double[] gridSize,
                            int samplingFactor,
                            SdoGeoRaster refGeoRaster,
                            java.lang.String storageParam,
                            SdoGeoRaster outGeoRaster,
                            int parallelDegree)
                     throws java.lang.Exception

      Apply a dodging algorithm on the input GeoRaster object to color balance the image..
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be dodged.

      `gridSize` - The size of each grid in x and y direction, respectively. It is an array of one or two numbers. If only one number is specified, then it is for both x and y direction.

      `samplingFactor` - Sampling factor, used to control the calculation of the statistics,with the denominator n in 1/(n\*n) representing the number of cells skipped in both row and column dimensions in computing the statistics. For example,if samplingFactor is 4, one-sixteenth of the cells are sampled; but if samplingFactor is 1,all cells are sampled. The higher the value, the less accurate the statistics are likely to be, but the more quickly they will be computed. samplingFactor cannot be greater than or equal to one-half (0.5) of gridSize.

      `refGeoRaster` - The reference GeoRaster object. Instead of giving the target mean and standard deviation, the mean and standard deviation of refGeoRaster are used as the target. The reference GeoRaster object must have the same number of bands as the input GeoRaster object.

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### equalize

          public void equalize(SdoGeoRaster inGeoRaster,
                               java.lang.Integer pyramidLevel,
                               java.math.BigDecimal[] cropArea,
                               java.lang.String bandNumbers,
                               java.lang.String storageParam,
                               SdoGeoRaster outGeoRaster,
                               int parallelDegree)
                        throws java.lang.Exception

      Process the input GeoRaster object by using histogram equalization method. The processed image is stored in the output GeoRaster object.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be equalized.

      `pyramidLevel` - A number specifying the pyramid level to be equalized in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `bandNumbers` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `outGeoRaster` - The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### equalize

          public void equalize(SdoGeoRaster inGeoRaster,
                               java.lang.Integer pyramidLevel,
                               JGeometry cropArea,
                               java.lang.String layerNumbers,
                               java.lang.String storageParam,
                               SdoGeoRaster outGeoRaster,
                               int parallelDegree)
                        throws java.lang.Exception

      Process the input GeoRaster object by using histogram equalization method. The processed image is stored in the output GeoRaster object.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be equalized.

      `pyramidLevel` - A number specifying the pyramid level to be equalized in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The minimum bounding rectangle (MBR) of the geometry object is used as the crop area.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `outGeoRaster` - The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### equalize

          public void equalize(SdoGeoRaster inGeoRaster,
                               java.lang.Integer pyramidLevel,
                               java.math.BigDecimal[] cropArea,
                               java.lang.String bandNumbers,
                               java.lang.String storageParam,
                               java.sql.Blob[] rasterBlob,
                               JGeometry[] outArea,
                               double[] outWindow)
                        throws java.lang.Exception

      Process the input GeoRaster object by using histogram equalization method. The processed image is stored in the output GeoRaster object.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be equalized.

      `pyramidLevel` - A number specifying the pyramid level to be equalized in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `bandNumbers` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### equalize

          public void equalize(SdoGeoRaster inGeoRaster,
                               java.lang.Integer pyramidLevel,
                               JGeometry cropArea,
                               java.lang.String layerNumbers,
                               java.lang.String storageParam,
                               java.sql.Blob[] rasterBlob,
                               JGeometry[] outArea,
                               double[] outWindow)
                        throws java.lang.Exception

      Process the input GeoRaster object by using histogram equalization method. The processed image is stored in the output GeoRaster object.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be equalized.

      `pyramidLevel` - A number specifying the pyramid level to be equalized in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The minimum bounding rectangle (MBR) of the geometry object is used as the crop area.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### filter

          public void filter(SdoGeoRaster inGeoRaster,
                             java.lang.Integer pyramidLevel,
                             java.math.BigDecimal[] cropArea,
                             java.lang.String bandNumbers,
                             java.lang.String filterParam,
                             double[] filterKernel,
                             java.lang.String storageParam,
                             SdoGeoRaster outGeoRaster,
                             int parallelDegree)
                      throws java.lang.Exception

      Applies the convolution filter on the input GeoRaster object. The processed image is stored in the output GeoRaster object.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object for the filter operation.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `bandNumbers` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `filterParam` - The type of the filter to be applied on the input GeoRaster. It is in the format 'filterType=value' where value can be one of the following: LPF (low-pass filter, the default), HPF (high-pass filter), HBF (high-boost filter), MIN (minimum filter), MAX (maximum filter), MEDIAN (median filter), MODE (mode filter), or CUSTOM (user-provided filter kernel). filterParam can also include: 'kernelSize=(kx, ky)' where kx, ky are the size of the kernel on the x and y direction. For a filter type other than CUSTOM, the kx and ky should be odd numbers greater than or equal to 3. 'p1 = value', used by the HBF filter to indicate the degree of boost.

      `filterKernel` - Required only when filterType=CUSTOM. It is the kx \* ky numbers in an array.

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `outGeoRaster` - The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### filter

          public void filter(SdoGeoRaster inGeoRaster,
                             java.lang.Integer pyramidLevel,
                             JGeometry cropArea,
                             java.lang.String layerNumbers,
                             java.lang.String filterParam,
                             double[] filterKernel,
                             java.lang.String storageParam,
                             SdoGeoRaster outGeoRaster,
                             int parallelDegree)
                      throws java.lang.Exception

      Applies the convolution filter on the input GeoRaster object. The processed image is stored in the output GeoRaster object.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object for the filter operation.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The minimum bounding rectangle (MBR) of the geometry object is used as the crop area.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `filterParam` - The type of the filter to be applied on the input GeoRaster. It is in the format 'filterType=value' where value can be one of the following: LPF (low-pass filter, the default), HPF (high-pass filter), HBF (high-boost filter), MIN (minimum filter), MAX (maximum filter), MEDIAN (median filter), MODE (mode filter), or CUSTOM (user-provided filter kernel). filterParam can also include: 'kernelSize=(kx, ky)' where kx, ky are the size of the kernel on the x and y direction. For a filter type other than CUSTOM, the kx and ky should be odd numbers greater than or equal to 3. 'p1 = value', used by the HBF filter to indicate the degree of boost.

      `filterKernel` - Required only when filterType=CUSTOM. It is the kx \* ky numbers in an array.

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `outGeoRaster` - The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### filter

          public void filter(SdoGeoRaster inGeoRaster,
                             java.lang.Integer pyramidLevel,
                             java.math.BigDecimal[] cropArea,
                             java.lang.String bandNumbers,
                             java.lang.String filterParam,
                             double[] filterKernel,
                             java.lang.String storageParam,
                             java.sql.Blob[] rasterBlob,
                             JGeometry[] outArea,
                             double[] outWindow)
                      throws java.lang.Exception

      Applies the convolution filter on the input GeoRaster object. The processed image is stored in the output GeoRaster object.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object for the filter operation.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `bandNumbers` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `filterParam` - The type of the filter to be applied on the input GeoRaster. It is in the format 'filterType=value' where value can be one of the following: LPF (low-pass filter, the default), HPF (high-pass filter), HBF (high-boost filter), MIN (minimum filter), MAX (maximum filter), MEDIAN (median filter), MODE (mode filter), or CUSTOM (user-provided filter kernel). filterParam can also include: 'kernelSize=(kx, ky)' where kx, ky are the size of the kernel on the x and y direction. For a filter type other than CUSTOM, the kx and ky should be odd numbers greater than or equal to 3. 'p1 = value', used by the HBF filter to indicate the degree of boost.

      `filterKernel` - Required only when filterType=CUSTOM. It is the kx \* ky numbers in an array.

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### filter

          public void filter(SdoGeoRaster inGeoRaster,
                             java.lang.Integer pyramidLevel,
                             JGeometry cropArea,
                             java.lang.String layerNumbers,
                             java.lang.String filterParam,
                             double[] filterKernel,
                             java.lang.String storageParam,
                             java.sql.Blob[] rasterBlob,
                             JGeometry[] outArea,
                             double[] outWindow)
                      throws java.lang.Exception

      Applies the convolution filter on the input GeoRaster object. The processed image is stored in the output GeoRaster object.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object for the filter operation.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The minimum bounding rectangle (MBR) of the geometry object is used as the crop area.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `filterParam` - The type of the filter to be applied on the input GeoRaster. It is in the format 'filterType=value' where value can be one of the following: LPF (low-pass filter, the default), HPF (high-pass filter), HBF (high-boost filter), MIN (minimum filter), MAX (maximum filter), MEDIAN (median filter), MODE (mode filter), or CUSTOM (user-provided filter kernel). filterParam can also include: 'kernelSize=(kx, ky)' where kx, ky are the size of the kernel on the x and y direction. For a filter type other than CUSTOM, the kx and ky should be odd numbers greater than or equal to 3. 'p1 = value', used by the HBF filter to indicate the degree of boost.

      `filterKernel` - Required only when filterType=CUSTOM. It is the kx \* ky numbers in an array.

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### histogramMatch

          public void histogramMatch(SdoGeoRaster inGeoRaster,
                                     java.lang.Integer pyramidLevel,
                                     java.math.BigDecimal[] cropArea,
                                     java.lang.String bandNumbers,
                                     GeorHistogram[] refHistograms,
                                     java.lang.String storageParam,
                                     SdoGeoRaster outGeoRaster,
                                     int parallelDegree)
                              throws java.lang.Exception

      Processes the input GeoRaster object so that the histograms of the output GeoRaster object matches the histogram of a reference GeoRaster object (refGeoRaster) or a reference histogram (refHistograms).
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object for the histogram matching operation.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `bandNumbers` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `refHistograms` - An array of reference histograms. If there is only one element in the array, all the output bands match to this histogram; otherwise, the length of the array must be the same as the number of the bands in the output GeoRaster object.

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `outGeoRaster` - The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### histogramMatch

          public void histogramMatch(SdoGeoRaster inGeoRaster,
                                     java.lang.Integer pyramidLevel,
                                     JGeometry cropArea,
                                     java.lang.String layerNumbers,
                                     GeorHistogram[] refHistograms,
                                     java.lang.String storageParam,
                                     SdoGeoRaster outGeoRaster,
                                     int parallelDegree)
                              throws java.lang.Exception

      Processes the input GeoRaster object so that the histograms of the output GeoRaster object matches the histogram of a reference GeoRaster object (refGeoRaster) or a reference histogram (refHistograms).
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object for the histogram matching operation.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The minimum bounding rectangle (MBR) of the geometry object is used as the crop area.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `refHistograms` - An array of reference histograms. If there is only one element in the array, all the output bands match to this histogram; otherwise, the length of the array must be the same as the number of the bands in the output GeoRaster object.

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `outGeoRaster` - The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### histogramMatch

          public void histogramMatch(SdoGeoRaster inGeoRaster,
                                     java.lang.Integer pyramidLevel,
                                     java.math.BigDecimal[] cropArea,
                                     java.lang.String bandNumbers,
                                     SdoGeoRaster refGeoRaster,
                                     java.lang.String storageParam,
                                     SdoGeoRaster outGeoRaster,
                                     int parallelDegree)
                              throws java.lang.Exception

      Processes the input GeoRaster object so that the histograms of the output GeoRaster object matches the histogram of a reference GeoRaster object (refGeoRaster) or a reference histogram (refHistograms).
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object for the histogram matching operation.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `bandNumbers` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `refGeoRaster` - The reference GeoRaster object. Instead of giving the target mean and standard deviation, the mean and standard deviation of refGeoRaster are used as the target. The reference GeoRaster object must have the same number of bands as the input GeoRaster object.

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `outGeoRaster` - The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### histogramMatch

          public void histogramMatch(SdoGeoRaster inGeoRaster,
                                     java.lang.Integer pyramidLevel,
                                     JGeometry cropArea,
                                     java.lang.String layerNumbers,
                                     SdoGeoRaster refGeoRaster,
                                     java.lang.String storageParam,
                                     SdoGeoRaster outGeoRaster,
                                     int parallelDegree)
                              throws java.lang.Exception

      Processes the input GeoRaster object so that the histograms of the output GeoRaster object matches the histogram of a reference GeoRaster object (refGeoRaster) or a reference histogram (refHistograms).
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object for the histogram matching operation.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The minimum bounding rectangle (MBR) of the geometry object is used as the crop area.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `refGeoRaster` - The reference GeoRaster object. Instead of giving the target mean and standard deviation, the mean and standard deviation of refGeoRaster are used as the target. The reference GeoRaster object must have the same number of bands as the input GeoRaster object.

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `outGeoRaster` - The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### normalize

          public void normalize(SdoGeoRaster inGeoRaster,
                                java.lang.Integer pyramidLevel,
                                java.math.BigDecimal[] cropArea,
                                java.lang.String bandNumbers,
                                double[] means,
                                double[] standardDeviations,
                                java.lang.String storageParam,
                                SdoGeoRaster outGeoRaster,
                                int parallelDegree)
                         throws java.lang.Exception

      Normalizes the input GeoRaster object using the specified mean and standard deviation.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be stretched.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `bandNumbers` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `means` - The target mean values for each output band. If only one value is specified, it is applied to all the output bands; otherwise, it must have the same number of values as the number of bands of the output GeoRaster object. The target mean values must be in the range of the cell depth of the outGeoRaster object. If null, it defaults to 128.

      `standardDeviations` - The target standard deviation values for each output band. If only one value is specified, it is applied to all the output bands; otherwise, it must have the same number of values as the number of bands of the output GeoRaster object. The target standard deviation values must be in the range of the cell depth of the outGeoRaster object. If null, it defaults to 100.

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `outGeoRaster` - The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### normalize

          public void normalize(SdoGeoRaster inGeoRaster,
                                java.lang.Integer pyramidLevel,
                                JGeometry cropArea,
                                java.lang.String layerNumbers,
                                double[] means,
                                double[] standardDeviations,
                                java.lang.String storageParam,
                                SdoGeoRaster outGeoRaster,
                                int parallelDegree)
                         throws java.lang.Exception

      Normalizes the input GeoRaster object using the specified mean and standard deviation.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be stretched.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The minimum bounding rectangle (MBR) of the geometry object is used as the crop area.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `means` - The target mean values for each output band. If only one value is specified, it is applied to all the output bands; otherwise, it must have the same number of values as the number of bands of the output GeoRaster object. The target mean values must be in the range of the cell depth of the outGeoRaster object. If null, it defaults to 128.

      `standardDeviations` - The target standard deviation values for each output band. If only one value is specified, it is applied to all the output bands; otherwise, it must have the same number of values as the number of bands of the output GeoRaster object. The target standard deviation values must be in the range of the cell depth of the outGeoRaster object. If null, it defaults to 100.

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `outGeoRaster` - The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### normalize

          public void normalize(SdoGeoRaster inGeoRaster,
                                java.lang.Integer pyramidLevel,
                                java.math.BigDecimal[] cropArea,
                                java.lang.String bandNumbers,
                                double[] means,
                                double[] standardDeviations,
                                java.lang.String storageParam,
                                java.sql.Blob[] rasterBlob,
                                JGeometry[] outArea,
                                double[] outWindow)
                         throws java.lang.Exception

      Normalizes the input GeoRaster object using the specified mean and standard deviation.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be stretched.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `bandNumbers` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `means` - The target mean values for each output band. If only one value is specified, it is applied to all the output bands; otherwise, it must have the same number of values as the number of bands of the output GeoRaster object. The target mean values must be in the range of the cell depth of the outGeoRaster object. If null, it defaults to 128.

      `standardDeviations` - The target standard deviation values for each output band. If only one value is specified, it is applied to all the output bands; otherwise, it must have the same number of values as the number of bands of the output GeoRaster object. The target standard deviation values must be in the range of the cell depth of the outGeoRaster object. If null, it defaults to 100.

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### normalize

          public void normalize(SdoGeoRaster inGeoRaster,
                                java.lang.Integer pyramidLevel,
                                JGeometry cropArea,
                                java.lang.String layerNumbers,
                                double[] means,
                                double[] standardDeviations,
                                java.lang.String storageParam,
                                java.sql.Blob[] rasterBlob,
                                JGeometry[] outArea,
                                double[] outWindow)
                         throws java.lang.Exception

      Normalizes the input GeoRaster object using the specified mean and standard deviation.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be stretched.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The minimum bounding rectangle (MBR) of the geometry object is used as the crop area.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `means` - The target mean values for each output band. If only one value is specified, it is applied to all the output bands; otherwise, it must have the same number of values as the number of bands of the output GeoRaster object. The target mean values must be in the range of the cell depth of the outGeoRaster object. If null, it defaults to 128.

      `standardDeviations` - The target standard deviation values for each output band. If only one value is specified, it is applied to all the output bands; otherwise, it must have the same number of values as the number of bands of the output GeoRaster object. The target standard deviation values must be in the range of the cell depth of the outGeoRaster object. If null, it defaults to 100.

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### normalize

          public void normalize(SdoGeoRaster inGeoRaster,
                                java.lang.Integer pyramidLevel,
                                java.math.BigDecimal[] cropArea,
                                java.lang.String bandNumbers,
                                SdoGeoRaster refGeoRaster,
                                java.lang.String storageParam,
                                SdoGeoRaster outGeoRaster,
                                int parallelDegree)
                         throws java.lang.Exception

      Normalizes the input GeoRaster object using the specified mean and standard deviation.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be stretched.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `bandNumbers` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `refGeoRaster` - The reference GeoRaster object. Instead of giving the target mean and standard deviation, the mean and standard deviation of refGeoRaster are used as the target. The reference GeoRaster object must have the same number of bands as the input GeoRaster object.

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `outGeoRaster` - The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### normalize

          public void normalize(SdoGeoRaster inGeoRaster,
                                java.lang.Integer pyramidLevel,
                                JGeometry cropArea,
                                java.lang.String layerNumbers,
                                SdoGeoRaster refGeoRaster,
                                java.lang.String storageParam,
                                SdoGeoRaster outGeoRaster,
                                int parallelDegree)
                         throws java.lang.Exception

      Normalizes the input GeoRaster object using the specified mean and standard deviation.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be stretched.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The minimum bounding rectangle (MBR) of the geometry object is used as the crop area.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `refGeoRaster` - The reference GeoRaster object. Instead of giving the target mean and standard deviation, the mean and standard deviation of refGeoRaster are used as the target. The reference GeoRaster object must have the same number of bands as the input GeoRaster object.

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `outGeoRaster` - The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### piecewiseStretch

          public void piecewiseStretch(SdoGeoRaster inGeoRaster,
                                       java.lang.Integer pyramidLevel,
                                       java.math.BigDecimal[] cropArea,
                                       java.lang.String bandNumbers,
                                       double[][] inValues,
                                       double[][] outValues,
                                       java.lang.String storageParam,
                                       SdoGeoRaster outGeoRaster,
                                       int parallelDegree)
                                throws java.lang.Exception

      Performs a linear stretch on the input GeoRaster object using the minimum and maximum values. The processed image is stored in the output GeoRaster object.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be stretched.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `bandNumbers` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `inValues` - A 2-dimentional array corresponding to the input cell value range of each band. For example, if there are 3 bands, and each band has 3 ranges, the inValues would be: double\[\]\[\] inValues ={ {0, 20, 180, 255}, {0, 50, 100, 255}, {0, 20, 200, 255}}; If only one array is specified, all the bands are stretched in the same way. For Example, double\[\]\[\] inValues = {{0, 20, 180,, 255}};

      `outValues` - A 2-dimentional array corresponding to the output cell value range of each band. For example, if there are 3 bands, and each band has 3 ranges, the outValues would be: double\[\]\[\] outValues ={ {0, 10, 250, 255}, {0, 10, 200, 255}, {0, 10, 250, 255}}; If only one array is specified, all the bands are stretched in the same way. For Example, double\[\]\[\] outValues = {{0, 10, 250,, 255}}; This parameter must have the same dimension size as the inValues parameter

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `outGeoRaster` - The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### piecewiseStretch

          public void piecewiseStretch(SdoGeoRaster inGeoRaster,
                                       java.lang.Integer pyramidLevel,
                                       JGeometry cropArea,
                                       java.lang.String layerNumbers,
                                       double[][] inValues,
                                       double[][] outValues,
                                       java.lang.String storageParam,
                                       SdoGeoRaster outGeoRaster,
                                       int parallelDegree)
                                throws java.lang.Exception

      Performs a linear stretch on the input GeoRaster object using the minimum and maximum values. The processed image is stored in the output GeoRaster object.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be stretched.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The minimum bounding rectangle (MBR) of the geometry object is used as the crop area.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `inValues` - A 2-dimentional array corresponding to the input cell value range of each band. For example, if there are 3 bands, and each band has 3 ranges, the inValues would be: double\[\]\[\] inValues ={ {0, 20, 180, 255}, {0, 50, 100, 255}, {0, 20, 200, 255}}; If only one array is specified, all the bands are stretched in the same way. For Example, double\[\]\[\] inValues = {{0, 20, 180,, 255}};

      `outValues` - A 2-dimentional array corresponding to the output cell value range of each band. For example, if there are 3 bands, and each band has 3 ranges, the outValues would be: double\[\]\[\] outValues ={ {0, 10, 250, 255}, {0, 10, 200, 255}, {0, 10, 250, 255}}; If only one array is specified, all the bands are stretched in the same way. For Example, double\[\]\[\] outValues = {{0, 10, 250,, 255}}; This parameter must have the same dimension size as the inValues parameter

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `outGeoRaster` - The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### piecewiseStretch

          public void piecewiseStretch(SdoGeoRaster inGeoRaster,
                                       java.lang.Integer pyramidLevel,
                                       java.math.BigDecimal[] cropArea,
                                       java.lang.String bandNumbers,
                                       double[][] inValues,
                                       double[][] outValues,
                                       java.lang.String storageParam,
                                       java.sql.Blob[] rasterBlob,
                                       JGeometry[] outArea,
                                       double[] outWindow)
                                throws java.lang.Exception

      Performs a linear stretch on the input GeoRaster object using the minimum and maximum values. The processed image is stored in the output GeoRaster object.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be stretched.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `bandNumbers` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `inValues` - A 2-dimentional array corresponding to the input cell value range of each band. For example, if there are 3 bands, and each band has 3 ranges, the inValues would be: double\[\]\[\] inValues ={ {0, 20, 180, 255}, {0, 50, 100, 255}, {0, 20, 200, 255}}; If only one array is specified, all the bands are stretched in the same way. For Example, double\[\]\[\] inValues = {{0, 20, 180,, 255}};

      `outValues` - A 2-dimentional array corresponding to the output cell value range of each band. For example, if there are 3 bands, and each band has 3 ranges, the outValues would be: double\[\]\[\] outValues ={ {0, 10, 250, 255}, {0, 10, 200, 255}, {0, 10, 250, 255}}; If only one array is specified, all the bands are stretched in the same way. For Example, double\[\]\[\] outValues = {{0, 10, 250,, 255}}; This parameter must have the same dimension size as the inValues parameter

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### piecewiseStretch

          public void piecewiseStretch(SdoGeoRaster inGeoRaster,
                                       java.lang.Integer pyramidLevel,
                                       JGeometry cropArea,
                                       java.lang.String layerNumbers,
                                       double[][] inValues,
                                       double[][] outValues,
                                       java.lang.String storageParam,
                                       java.sql.Blob[] rasterBlob,
                                       JGeometry[] outArea,
                                       double[] outWindow)
                                throws java.lang.Exception

      Performs a linear stretch on the input GeoRaster object using the minimum and maximum values. The processed image is stored in the output GeoRaster object.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be stretched.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The minimum bounding rectangle (MBR) of the geometry object is used as the crop area.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `inValues` - A 2-dimentional array corresponding to the input cell value range of each band. For example, if there are 3 bands, and each band has 3 ranges, the inValues would be: double\[\]\[\] inValues ={ {0, 20, 180, 255}, {0, 50, 100, 255}, {0, 20, 200, 255}}; If only one array is specified, all the bands are stretched in the same way. For Example, double\[\]\[\] inValues = {{0, 20, 180,, 255}};

      `outValues` - A 2-dimentional array corresponding to the output cell value range of each band. For example, if there are 3 bands, and each band has 3 ranges, the outValues would be: double\[\]\[\] outValues ={ {0, 10, 250, 255}, {0, 10, 200, 255}, {0, 10, 250, 255}}; If only one array is specified, all the bands are stretched in the same way. For Example, double\[\]\[\] outValues = {{0, 10, 250,, 255}}; This parameter must have the same dimension size as the inValues parameter

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### stretch

          public void stretch(SdoGeoRaster inGeoRaster,
                              java.lang.Integer pyramidLevel,
                              java.math.BigDecimal[] cropArea,
                              java.lang.String bandNumbers,
                              double[] minValues,
                              double[] maxValues,
                              java.lang.String storageParam,
                              SdoGeoRaster outGeoRaster,
                              int parallelDegree)
                       throws java.lang.Exception

      Performs a min-max linear stretch on the input GeoRaster object using the minimum and maximum values. The processed image is stored in the output GeoRaster object.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be stretched.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `bandNumbers` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `minValues` - The minimum values of the bands to be stretched. If it is null, the minimum value of the input GeoRaster object that is stored in the layer metadata is used. If there is only one value in the array, it is used as the minimum value of all the input bands; otherwise, the number of values in the array must be the same as the number of bands of the output GeoRaster object.

      `maxValues` - The maximum values of the bands to be stretched. If it is null, the maximum value of the input GeoRaster object that is stored in the layer metadata is used. If there is only one value in the array, it is used as the maximum value of all the input bands; otherwise, the number of values in the array must be the same as the number of bands of the output GeoRaster object.

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `outGeoRaster` - The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### stretch

          public void stretch(SdoGeoRaster inGeoRaster,
                              java.lang.Integer pyramidLevel,
                              JGeometry cropArea,
                              java.lang.String layerNumbers,
                              double[] minValues,
                              double[] maxValues,
                              java.lang.String storageParam,
                              SdoGeoRaster outGeoRaster,
                              int parallelDegree)
                       throws java.lang.Exception

      Performs a min-max linear stretch on the input GeoRaster object using the minimum and maximum values. The processed image is stored in the output GeoRaster object.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be stretched.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The minimum bounding rectangle (MBR) of the geometry object is used as the crop area.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `minValues` - The minimum values of the bands to be stretched. If it is null, the minimum value of the input GeoRaster object that is stored in the layer metadata is used. If there is only one value in the array, it is used as the minimum value of all the input bands; otherwise, the number of values in the array must be the same as the number of bands of the output GeoRaster object.

      `maxValues` - The maximum values of the bands to be stretched. If it is null, the maximum value of the input GeoRaster object that is stored in the layer metadata is used. If there is only one value in the array, it is used as the maximum value of all the input bands; otherwise, the number of values in the array must be the same as the number of bands of the output GeoRaster object.

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `outGeoRaster` - The output SDO_GEORASTER object that reflects the results of the operation. Must be either a valid existing GeoRaster object or an empty GeoRaster object. (Empty GeoRaster objects are explained in Blank and Empty GeoRaster Objects.) Cannot be the same GeoRaster object as inGeoRaster.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if parallelism specified, the procedure performs an internal commit operation. error occurs (even it raised by oracle server), you must delete resulting mosaicked object explicitly order to roll back operation.\< dd\>

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### stretch

          public void stretch(SdoGeoRaster inGeoRaster,
                              java.lang.Integer pyramidLevel,
                              java.math.BigDecimal[] cropArea,
                              java.lang.String bandNumbers,
                              double[] minValues,
                              double[] maxValues,
                              java.lang.String storageParam,
                              java.sql.Blob[] rasterBlob,
                              JGeometry[] outArea,
                              double[] outWindow)
                       throws java.lang.Exception

      Performs a min-max linear stretch on the input GeoRaster object using the minimum and maximum values. The processed image is stored in the output GeoRaster object.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be stretched.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `bandNumbers` - A string identifying the physical band numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 1-3 for bands 1, 2, and 3).

      `minValues` - The minimum values of the bands to be stretched. If it is null, the minimum value of the input GeoRaster object that is stored in the layer metadata is used. If there is only one value in the array, it is used as the minimum value of all the input bands; otherwise, the number of values in the array must be the same as the number of bands of the output GeoRaster object.

      `maxValues` - The maximum values of the bands to be stretched. If it is null, the maximum value of the input GeoRaster object that is stored in the layer metadata is used. If there is only one value in the array, it is used as the maximum value of all the input bands; otherwise, the number of values in the array must be the same as the number of bands of the output GeoRaster object.

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### stretch

          public void stretch(SdoGeoRaster inGeoRaster,
                              java.lang.Integer pyramidLevel,
                              JGeometry cropArea,
                              java.lang.String layerNumbers,
                              double[] minValues,
                              double[] maxValues,
                              java.lang.String storageParam,
                              java.sql.Blob[] rasterBlob,
                              JGeometry[] outArea,
                              double[] outWindow)
                       throws java.lang.Exception

      Performs a min-max linear stretch on the input GeoRaster object using the minimum and maximum values. The processed image is stored in the output GeoRaster object.
      Parameters:
      `inGeoRaster` - The SDO_GEORASTER object to be stretched.

      `pyramidLevel` - A number specifying the pyramid level for the filter operation in the source GeoRaster object. If null, the default is 0.

      `cropArea` - Crop area definition. The minimum bounding rectangle (MBR) of the geometry object is used as the crop area.

      `layerNumbers` - A string identifying the logical layer numbers on which the operation is to be performed. Use commas to delimit the values, and a hyphen to indicate a range (for example, 2-4 for layers 2, 3, and 4).

      `minValues` - The minimum values of the bands to be stretched. If it is null, the minimum value of the input GeoRaster object that is stored in the layer metadata is used. If there is only one value in the array, it is used as the minimum value of all the input bands; otherwise, the number of values in the array must be the same as the number of bands of the output GeoRaster object.

      `maxValues` - The maximum values of the bands to be stretched. If it is null, the maximum value of the input GeoRaster object that is stored in the layer metadata is used. If there is only one value in the array, it is used as the maximum value of all the input bands; otherwise, the number of values in the array must be the same as the number of bands of the output GeoRaster object.

      `storageParam` - A string specifying storage parameters, as explained in Storage Parameters.

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      Throws:
      `java.lang.Exception`

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

- [Prev Class](SdoGeoRaster.md)
- [Next Class](SdoGeorPKG.md)

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
