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

- [Prev Class](SdoGeorPKG.SdoGeorGCPRefType.md)
- [Next Class](SdoGeorUtlPKG.md)

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

## Class SdoGeorRaPKG

- java.lang.Object

- - oracle.spatial.georaster.sql.SdoGeorRaPKG

<!-- -->

-

  ------------------------------------------------------------------------



      public class SdoGeorRaPKG
      extends java.lang.Object

  SdoGeorRaPKG is a Java class which wraps PL/SQL functions and procedures defined in the server-side package SDO_GEOR_RA. When a method defined in the class is invoked, a corresponding PL/SQL block is generated and submitted to the target Oracle database through a JDBC connection, so that equivalent result by PL/SQL can be achieved from the Java side.
  Note that all methods in this class are transactional, which means that no commit statement is issued implicitly in each method.

  The following is an example of how to use this class:

         //initialize an instance of SdoGeorRaPKG
         SdoGeorRaPKG  pkg=new SdoGeorRaPKG(connection);
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
         //check overlap of two GeoRaster Objects
         boolean m_isOverlap=pkg.isOverlap(geoRaster,geoRaster1,new Double(0.5));

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description     |
    |-------------------|---------------------------|
    | `static int`      | `OPERATOR_ABSOLUTE`       |
    | `static int`      | `OPERATOR_ADD`            |
    | `static int`      | `OPERATOR_ADDCONST`       |
    | `static int`      | `OPERATOR_DIVIDE`         |
    | `static int`      | `OPERATOR_DIVIDECONST`    |
    | `static int`      | `OPERATOR_EXP`            |
    | `static int`      | `OPERATOR_INVERT`         |
    | `static int`      | `OPERATOR_LOG`            |
    | `static int`      | `OPERATOR_MULTIPLY`       |
    | `static int`      | `OPERATOR_MULTIPLYCONST`  |
    | `static int`      | `OPERATOR_SUBTRACT`       |
    | `static int`      | `OPERATOR_SUBTRACTCONST`  |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                   |
    |---------------------------------------------------------------------------------------------------------------|
    | `SdoGeorRaPKG``(java.sql.Connection conn)`<br>Constructs an `SdoGeorRaPKG` object using the given connection. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type     | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    |-----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                | `classify``(`[`SdoGeoRaster`](SdoGeoRaster.md)`[] inGeoRasters, double[] cropArea, java.lang.String expression, double[] rangeArray, double[] valueArray, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, boolean nodata, double nodataValue)`<br>Generates a new raster object stored in a BLOB after applying the specified classification operation on the input GeoRaster object or objects.                                                                                                                                                                 |
    | `void`                | `classify``(`[`SdoGeoRaster`](SdoGeoRaster.md)`[] inGeoRasters, double[] cropArea, java.lang.String expression, double[] rangeArray, double[] valueArray, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, double nodataValue, int parallelDegree)`<br>Generates a new GeoRaster object after applying the specified classification operation on the input GeoRaster object or objects.                                                                                                                                                                                                                 |
    | `void`                | `classify``(`[`SdoGeoRaster`](SdoGeoRaster.md)`[] inGeoRasters, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String expression, double[] rangeArray, double[] valueArray, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, boolean nodata, double nodataValue, java.lang.String polygonClip)`<br>Generates a new raster stored in BLOB after applying the specified classification operation on the input GeoRaster object or objects.                                                                                                        |
    | `void`                | `classify``(`[`SdoGeoRaster`](SdoGeoRaster.md)`[] inGeoRasters, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String expression, double[] rangeArray, double[] valueArray, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, double nodataValue, java.lang.String polygonClip, int parallelDegree)`<br>Generates a new GeoRaster object after applying the specified classification operation on the input GeoRaster object or objects.                                                                                                                                               |
    | `void`                | `classify``(`[`SdoGeoRaster`](SdoGeoRaster.md)`[] inGeoRasters, java.lang.String expression, double[] rangeArray, double[] valueArray, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, double nodataValue, int parallelDegree)`<br>Generates a new GeoRaster object after applying the specified classification operation on the input GeoRaster object or objects.                                                                                                                                                                                                                                    |
    | `void`                | `classify``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, double[] cropArea, java.lang.String expression, double[] rangeArray, double[] valueArray, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, boolean nodata, double nodataValue)`<br>Generates a new raster in BLOB after applying the specified classification operation on the input GeoRaster object or objects.                                                                                                                                                                                    |
    | `void`                | `classify``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, double[] cropArea, java.lang.String expression, double[] rangeArray, double[] valueArray, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, double nodataValue, int parallelDegree)`<br>Generates a new GeoRaster object after applying the specified classification operation on the input GeoRaster object or objects.                                                                                                                                                                                                                    |
    | `void`                | `classify``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String expression, double[] rangeArray, double[] valueArray, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, boolean nodata, double nodataValue, java.lang.String polygonClip)`<br>Generates a new raster in BLOB after applying the specified classification operation on the input GeoRaster object or objects.                                                                                                                  |
    | `void`                | `classify``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String expression, double[] rangeArray, double[] valueArray, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, double nodataValue, java.lang.String polygonClip, int parallelDegree)`<br>Generates a new GeoRaster object after applying the specified classification operation on the input GeoRaster object or objects.                                                                                                                                                  |
    | `void`                | `classify``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.String expression, double[] rangeArray, double[] valueArray, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, double nodataValue, int parallelDegree)`<br>Generates a new GeoRaster object after applying the specified classification operation on the input GeoRaster object or objects.                                                                                                                                                                                                                                       |
    | `void`                | `classify``(java.lang.String inGeoRasters, double[] cropArea, java.lang.String expression, double[] rangeArray, double[] valueArray, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, boolean nodata, double nodataValue)`<br>Generates a new raster stored in a BLOB after applying the specified classification operation on the input GeoRaster object or objects.                                                                                                                                                                                             |
    | `void`                | `classify``(java.lang.String inGeoRasters, double[] cropArea, java.lang.String expression, double[] rangeArray, double[] valueArray, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, double nodataValue, int parallelDegree)`<br>Generates a new GeoRaster object after applying the specified classification operation on the input GeoRaster object or objects.                                                                                                                                                                                                                                      |
    | `void`                | `classify``(java.lang.String inGeoRasters, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String expression, double[] rangeArray, double[] valueArray, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, boolean nodata, double nodataValue, java.lang.String polygonClip)`<br>Generates a new raster stored in a BLOB after applying the specified classification operation on the input GeoRaster object or objects.                                                                                                                           |
    | `void`                | `classify``(java.lang.String inGeoRasters, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String expression, double[] rangeArray, double[] valueArray, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, double nodataValue, java.lang.String polygonClip, int parallelDegree)`<br>Generates a new GeoRaster object after applying the specified classification operation on the input GeoRaster object or objects.                                                                                                                                                                    |
    | `void`                | `classify``(java.lang.String inGeoRasters, java.lang.String expression, double[] rangeArray, double[] valueArray, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, double nodataValue, int parallelDegree)`<br>Generates a new GeoRaster object after applying the specified classification operation on the input GeoRaster object or objects.                                                                                                                                                                                                                                                         |
    | `void`                | `diff``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster1, `[`SdoGeoRaster`](SdoGeoRaster.md)` georaster2, double[] cropArea, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, boolean nodata, java.lang.Double nodataValue)`<br>Generates a new raster stored in a BLOB by performing the diff operation (explained in the Usage Notes).                                                                                                                                                                                                                            |
    | `void`                | `diff``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster1, `[`SdoGeoRaster`](SdoGeoRaster.md)` georaster2, double[] cropArea, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, java.lang.Double nodataValue, int parallelDegree)`<br>Generates a new GeoRaster object by performing the diff operation (explained in the Usage Notes).                                                                                                                                                                                                                                                                     |
    | `void`                | `diff``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster1, `[`SdoGeoRaster`](SdoGeoRaster.md)` georaster2, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, boolean nodata, java.lang.Double nodataValue, boolean polygonClip)`<br>Generates a new raster stored in a BLOB by performing the diff operation (explained in the Usage Notes).                                                                                                                                                                   |
    | `void`                | `diff``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster1, `[`SdoGeoRaster`](SdoGeoRaster.md)` georaster2, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, java.lang.Double nodataValue, boolean polygonClip, int parallelDegree)`<br>Generates a new GeoRaster object by performing the diff operation (explained in the Usage Notes).                                                                                                                                                                                                            |
    | `void`                | `findCells``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, double[] cropArea, java.lang.String condition, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, double[] bgValues, boolean nodata)`<br>Generates a new raster stored in a BLOB based on the input GeoRaster object, but masking all cells that do not satisfy the condition parameter specification.                                                                                                                                                                                                |
    | `void`                | `findCells``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, double[] cropArea, java.lang.String condition, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, double[] bgValues, boolean nodata, int parallelDegree)`<br>Generates a new GeoRaster object based on the input GeoRaster object, but masking all cells that do not satisfy the condition parameter specification.                                                                                                                                                                                                                                         |
    | `void`                | `findCells``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String condition, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, double[] bgValues, boolean nodata, java.lang.String polygonClip)`<br>Generates a new raster stored in a BLOB based on the input GeoRaster object, but masking all cells that do not satisfy the condition parameter specification.                                                                                                                              |
    | `void`                | `findCells``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String condition, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, double[] bgValues, boolean nodata, java.lang.String polygonClip, int parallelDegree)`<br>Generates a new GeoRaster object based on the input GeoRaster object, but masking all cells that do not satisfy the condition parameter specification.                                                                                                                                                                       |
    | `void`                | `findCells``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.String condition, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, double[] bgValues, boolean nodata, int parallelDegree)`<br>Generates a new GeoRaster object based on the input GeoRaster object, but masking all cells that do not satisfy the condition parameter specification.                                                                                                                                                                                                                                                            |
    | `java.sql.Connection` | `getConnection``()`<br>Returns a connection which points to target database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `boolean`             | `isOverlap``(`[`SdoGeoRaster`](SdoGeoRaster.md)`[] inGeoRasters, java.lang.Double tolerance)`<br>Returns the string TRUE if two or more GeoRaster objects overlap, or FALSE if two or more GeoRaster objects do not overlap.                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `boolean`             | `isOverlap``(`[`SdoGeoRaster`](SdoGeoRaster.md)` geoRaster1, `[`SdoGeoRaster`](SdoGeoRaster.md)` geoRaster2, java.lang.Double tolerance)`<br>Returns the string TRUE if two or more GeoRaster objects overlap, or FALSE if two or more GeoRaster objects do not overlap.                                                                                                                                                                                                                                                                                                                                                                                |
    | `boolean`             | `isOverlap``(java.lang.String inGeoRasters, java.lang.Double tolerance)`<br>Returns the string TRUE if two or more GeoRaster objects overlap, or FALSE if two or more GeoRaster objects do not overlap.                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `void`                | `over``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster1, `[`SdoGeoRaster`](SdoGeoRaster.md)` georaster2, double[] cropArea, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, boolean nodata, java.lang.Double nodataValue)`<br>Generates a new raster stored in a BLOB by performing the over operation (explained in the Usage Notes).                                                                                                                                                                                                                            |
    | `void`                | `over``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster1, `[`SdoGeoRaster`](SdoGeoRaster.md)` georaster2, double[] cropArea, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, java.lang.Double nodataValue, int parallelDegree)`<br>Generates a new GeoRaster object by performing the over operation (explained in the Usage Notes).                                                                                                                                                                                                                                                                     |
    | `void`                | `over``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster1, `[`SdoGeoRaster`](SdoGeoRaster.md)` georaster2, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, boolean nodata, java.lang.Double nodataValue, boolean polygonClip)`<br>Generates a new raster stored in a BLOB by performing the over operation (explained in the Usage Notes).                                                                                                                                                                   |
    | `void`                | `over``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster1, `[`SdoGeoRaster`](SdoGeoRaster.md)` georaster2, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, java.lang.Double nodataValue, boolean polygonClip, int parallelDegree)`<br>Generates a new GeoRaster object by performing the over operation (explained in the Usage Notes).                                                                                                                                                                                                            |
    | `void`                | `rasterMathOp``(`[`SdoGeoRaster`](SdoGeoRaster.md)`[] inGeoRasters, double[] cropArea, java.lang.String[] operation, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, boolean nodata, java.lang.Double nodataValue)`<br>Generate a new raster stored in BLOB from layers of one or more input GeoRaster objects based on the operation parameter specification.                                                                                                                                                                                                   |
    | `void`                | `rasterMathOp``(`[`SdoGeoRaster`](SdoGeoRaster.md)`[] inGeoRasters, double[] cropArea, java.lang.String[] operation, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, java.lang.Double nodataValue, int parallelDegree)`<br>Generate a new GeoRaster object from layers of one or more input GeoRaster objects based on the operation parameter specification.                                                                                                                                                                                                                                          |
    | `void`                | `rasterMathOp``(`[`SdoGeoRaster`](SdoGeoRaster.md)`[] inGeoRasters, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String[] operation, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, boolean nodata, java.lang.Double nodataValue, java.lang.String polygonClip)`<br>Generate a new raster stored in BLOB from layers of one or more input GeoRaster objects based on the operation parameter specification.                                                                                                                                 |
    | `void`                | `rasterMathOp``(`[`SdoGeoRaster`](SdoGeoRaster.md)`[] inGeoRasters, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String[] operation, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, java.lang.Double nodataValue, java.lang.String polygonClip, int parallelDegree)`<br>Generate a new GeoRaster object from layers of one or more input GeoRaster objects based on the operation parameter specification.                                                                                                                                                                        |
    | `void`                | `rasterMathOp``(`[`SdoGeoRaster`](SdoGeoRaster.md)`[] inGeoRasters, java.lang.String[] operation, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, java.lang.Double nodataValue, int parallelDegree)`<br>Generate a new GeoRaster object from layers of one or more input GeoRaster objects based on the operation parameter specification.                                                                                                                                                                                                                                                             |
    | `void`                | `rasterMathOp``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, double[] cropArea, java.lang.String[] operation, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, boolean nodata, java.lang.Double nodataValue)`<br>Generate a new raster stored in a BLOB from layers of one or more input GeoRaster objects based on the operation parameter specification.                                                                                                                                                                                                    |
    | `void`                | `rasterMathOp``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, double[] cropArea, java.lang.String[] operation, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, java.lang.Double nodataValue, int parallelDegree)`<br>Generate a new GeoRaster object from layers of one or more input GeoRaster objects based on the operation parameter specification.                                                                                                                                                                                                                                             |
    | `void`                | `rasterMathOp``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String[] operation, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, boolean nodata, java.lang.Double nodataValue, java.lang.String polygonClip)`<br>Generate a new raster stored in a BLOB from layers of one or more input GeoRaster objects based on the operation parameter specification.                                                                                                                                  |
    | `void`                | `rasterMathOp``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String[] operation, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, java.lang.Double nodataValue, java.lang.String polygonClip, int parallelDegree)`<br>Generate a new GeoRaster object from layers of one or more input GeoRaster objects based on the operation parameter specification.                                                                                                                                                                           |
    | `void`                | `rasterMathOp``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster0, `[`SdoGeoRaster`](SdoGeoRaster.md)` georaster1, double[] cropArea, java.lang.Double constant, int operartor, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, double[] bgValues, boolean nodata, java.lang.Double nodataValue)`<br>Applies a mathematical operation on all corresponding cells of each layer of one or two input GeoRaster objects and generate a new raster stored in a BLOB.                                                                                                    |
    | `void`                | `rasterMathOp``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster0, `[`SdoGeoRaster`](SdoGeoRaster.md)` georaster1, double[] cropArea, java.lang.Double constant, int operartor, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, double[] bgValues, boolean nodata, java.lang.Double nodataValue, int parallelDegree)`<br>Applies a mathematical operation on all corresponding cells of each layer of one or two input GeoRaster objects.                                                                                                                                                                                 |
    | `void`                | `rasterMathOp``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster0, `[`SdoGeoRaster`](SdoGeoRaster.md)` georaster1, java.lang.Double constant, int operartor, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, double[] bgValues, boolean nodata, java.lang.Double nodataValue, int parallelDegree)`<br>Applies a mathematical operation on all corresponding cells of each layer of one or two input GeoRaster objects.                                                                                                                                                                                                    |
    | `void`                | `rasterMathOp``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster0, `[`SdoGeoRaster`](SdoGeoRaster.md)` georaster1, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.Double constant, int operartor, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, double[] bgValues, boolean nodata, java.lang.Double nodataValue, java.lang.String polygonClip)`<br>Applies a mathematical operation on all corresponding cells of each layer of one or two input GeoRaster objects and create a new raster stored in a BLOB.                                    |
    | `void`                | `rasterMathOp``(`[`SdoGeoRaster`](SdoGeoRaster.md)` georaster0, `[`SdoGeoRaster`](SdoGeoRaster.md)` georaster1, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.Double constant, int operartor, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, double[] bgValues, boolean nodata, java.lang.Double nodataValue, java.lang.String polygonClip, int parallelDegree)`<br>Applies a mathematical operation on all corresponding cells of each layer of one or two input GeoRaster objects.                                                                                                               |
    | `void`                | `rasterMathOp``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.String[] operation, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, java.lang.Double nodataValue, int parallelDegree)`<br>Generate a new GeoRaster object from layers of one or more input GeoRaster objects based on the operation parameter specification.                                                                                                                                                                                                                                                                |
    | `void`                | `rasterMathOp``(java.lang.String inGeoRasters, double[] cropArea, java.lang.String[] operation, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, boolean nodata, java.lang.Double nodataValue)`<br>Generate a new raster stored in a BLOB from layers of one or more input GeoRaster objects based on the operation parameter specification.                                                                                                                                                                                                                      |
    | `void`                | `rasterMathOp``(java.lang.String inGeoRasters, double[] cropArea, java.lang.String[] operation, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, java.lang.Double nodataValue, int parallelDegree)`<br>Generate a new GeoRaster object from layers of one or more input GeoRaster objects based on the operation parameter specification.                                                                                                                                                                                                                                                               |
    | `void`                | `rasterMathOp``(java.lang.String inGeoRasters, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String[] operation, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, boolean nodata, java.lang.Double nodataValue, java.lang.String polygonClip)`<br>Generate a new raster stored in BLOB from layers of one or more input GeoRaster objects based on the operation parameter specification.                                                                                                                                                      |
    | `void`                | `rasterMathOp``(java.lang.String inGeoRasters, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, java.lang.String[] operation, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, java.lang.Double nodataValue, java.lang.String polygonClip, int parallelDegree)`<br>Generate a new GeoRaster object from layers of one or more input GeoRaster objects based on the operation parameter specification.                                                                                                                                                                                             |
    | `void`                | `rasterMathOp``(java.lang.String inGeoRasters, java.lang.String[] operation, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, java.lang.Double nodataValue, int parallelDegree)`<br>Generate a new GeoRaster object from layers of one or more input GeoRaster objects based on the operation parameter specification.                                                                                                                                                                                                                                                                                  |
    | `void`                | `rasterUpdate``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, double[] targetArea, java.lang.String[] conditions, java.lang.String[][] vals, double[] bgValues, boolean nodata, int parallelDegree)`<br>Updates all cells for which the conditions specification is true, using values calculated from the vals specification.                                                                                                                                                                                                                                                                                       |
    | `void`                | `rasterUpdate``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, `[`JGeometry`](../../geometry/JGeometry.md)` targetArea, java.lang.String[] conditions, java.lang.String[][] vals, double[] bgValues, boolean nodata, java.lang.String polygonClip, int parallelDegree)`<br>Updates all cells for which the conditions specification is true, using values calculated from the vals specification.                                                                                                                                                                                                                     |
    | `void`                | `rasterUpdate``(`[`SdoGeoRaster`](SdoGeoRaster.md)` inGeoRaster, java.lang.Integer pyramidLevel, java.lang.String[] conditions, java.lang.String[][] vals, double[] bgValues, boolean nodata, int parallelDegree)`<br>Updates all cells for which the conditions specification is true, using values calculated from the vals specification.                                                                                                                                                                                                                                                                                                            |
    | `void`                | `setConnection``(java.sql.Connection conn)`<br>Sets the connection which points to the target database.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `void`                | `stack``(`[`SdoGeoRaster`](SdoGeoRaster.md)`[] inGeoRasters, double[] cropArea, int[] layerList, java.lang.String method, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, boolean nodata, java.lang.Double nodataValue)`<br>Generates a single-layer raster stored in a BLOB whose cell values are a local statistics value of a list of layers of the input GeoRaster array.The input layers are specified by the layerList parameter, and the statistics method is specified by the method parameter.                                                          |
    | `void`                | `stack``(`[`SdoGeoRaster`](SdoGeoRaster.md)`[] inGeoRasters, double[] cropArea, int[] layerList, java.lang.String method, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, java.lang.Double nodataValue, int parallelDegree)`<br>Generates a single-layer GeoRaster object whose cell values are a local statistics value of a list of layers of the input GeoRaster array.The input layers are specified by the layerList parameter, and the statistics method is specified by the method parameter.                                                                                                   |
    | `void`                | `stack``(`[`SdoGeoRaster`](SdoGeoRaster.md)`[] inGeoRasters, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, int[] layerList, java.lang.String method, java.lang.String storageParam, java.sql.Blob[] rasterBlob, `[`JGeometry`](../../geometry/JGeometry.md)`[] outArea, double[] outWindow, boolean nodata, java.lang.Double nodataValue, boolean polygonClip)`<br>Generates a single-layer raster stored in a BLOB whose cell values are a local statistics value of a list of layers of the input GeoRaster array.The input layers are specified by the layerList parameter, and the statistics method is specified by the method parameter. |
    | `void`                | `stack``(`[`SdoGeoRaster`](SdoGeoRaster.md)`[] inGeoRasters, `[`JGeometry`](../../geometry/JGeometry.md)` cropArea, int[] layerList, java.lang.String method, java.lang.String storageParam, `[`SdoGeoRaster`](SdoGeoRaster.md)` outGeoRaster, boolean nodata, java.lang.Double nodataValue, boolean polygonClip, int parallelDegree)`<br>Generates a single-layer GeoRaster object whose cell values are a local statistics value of a list of layers of the input GeoRaster array.The input layers are specified by the layerList parameter, and the statistics method is specified by the method parameter.                                          |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### OPERATOR_ABSOLUTE

          public static final int OPERATOR_ABSOLUTE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### OPERATOR_ADD

          public static final int OPERATOR_ADD

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### OPERATOR_ADDCONST

          public static final int OPERATOR_ADDCONST

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### OPERATOR_DIVIDE

          public static final int OPERATOR_DIVIDE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### OPERATOR_DIVIDECONST

          public static final int OPERATOR_DIVIDECONST

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### OPERATOR_EXP

          public static final int OPERATOR_EXP

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### OPERATOR_INVERT

          public static final int OPERATOR_INVERT

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### OPERATOR_LOG

          public static final int OPERATOR_LOG

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### OPERATOR_MULTIPLY

          public static final int OPERATOR_MULTIPLY

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### OPERATOR_MULTIPLYCONST

          public static final int OPERATOR_MULTIPLYCONST

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### OPERATOR_SUBTRACT

          public static final int OPERATOR_SUBTRACT

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### OPERATOR_SUBTRACTCONST

          public static final int OPERATOR_SUBTRACTCONST

      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### SdoGeorRaPKG

          public SdoGeorRaPKG(java.sql.Connection conn)

      Constructs an `SdoGeorRaPKG` object using the given connection.
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

    - #### classify

          public void classify(SdoGeoRaster inGeoRaster,
                               java.lang.String expression,
                               double[] rangeArray,
                               double[] valueArray,
                               java.lang.String storageParam,
                               SdoGeoRaster outGeoRaster,
                               boolean nodata,
                               double nodataValue,
                               int parallelDegree)
                        throws java.lang.Exception

      Generates a new GeoRaster object after applying the specified classification operation on the input GeoRaster object or objects. This procedure generates a one-layer GeoRaster object based on the input GeoRaster object or objects and the expression parameter, which is an arithmetic expression string. For each cell in the output GeoRaster object, expression is evaluated against corresponding cell values in the input GeoRaster object, and the following algorithm is used to calculate cell values of the output GeoRaster object: if (value of expression \< rangeArray\[0\]) cellValue=valueArray\[0\] else if (value of expression \>= rangeArray\[n-1\]) cellValue=valueArray\[n\] else if rangeArray\[m-1\] \<= 0 value of expression \< rangearray\[m\] cellvalue="valueArray\[m\]" in the calculation: length rangearray is n valuearray n+1 m n-1 if paralleldegree\>1, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If parallelDegree\<=1, you can roll back all changes.\< div\>
      Parameters:
      `inGeoRaster` - Input GeoRaster object.

      `expression` - An arithmetic expression used to classify cell values. See the Usage Notes for more information about specifying this parameter.

      `rangeArray` - A number array that defines ranges for classifying cell values. The array must contain at least one element.

      `valueArray` - A number array that defines the target cell value for each range. The number of elements must be 1 greater than the elements in rangeArray (that is, its length must be rangeArray+1).

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies that for any NODATA cells in an input GeoRaster object, the corresponding cells in the output GeoRaster object are to be set to the value specified for the nodataValue parameter. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### classify

          public void classify(SdoGeoRaster inGeoRaster,
                               double[] cropArea,
                               java.lang.String expression,
                               double[] rangeArray,
                               double[] valueArray,
                               java.lang.String storageParam,
                               SdoGeoRaster outGeoRaster,
                               boolean nodata,
                               double nodataValue,
                               int parallelDegree)
                        throws java.lang.Exception

      Generates a new GeoRaster object after applying the specified classification operation on the input GeoRaster object or objects. This procedure generates a one-layer GeoRaster object based on the input GeoRaster object or objects and the expression parameter, which is an arithmetic expression string. For each cell in the output GeoRaster object, expression is evaluated against corresponding cell values in the input GeoRaster object, and the following algorithm is used to calculate cell values of the output GeoRaster object: if (value of expression \< rangeArray\[0\]) cellValue=valueArray\[0\] else if (value of expression \>= rangeArray\[n-1\]) cellValue=valueArray\[n\] else if rangeArray\[m-1\] \<= 0 value of expression \< rangearray\[m\] cellvalue="valueArray\[m\]" in the calculation: length rangearray is n valuearray n+1 m n-1 if paralleldegree\>1, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If parallelDegree\<=1, you can roll back all changes.\< div\>
      Parameters:
      `inGeoRaster` - Input GeoRaster object.

      `cropArea` - crop area definition in cell space by a long array

      `expression` - An arithmetic expression used to classify cell values. See the Usage Notes for more information about specifying this parameter.

      `rangeArray` - A number array that defines ranges for classifying cell values. The array must contain at least one element.

      `valueArray` - A number array that defines the target cell value for each range. The number of elements must be 1 greater than the elements in rangeArray (that is, its length must be rangeArray+1).

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies that for any NODATA cells in an input GeoRaster object, the corresponding cells in the output GeoRaster object are to be set to the value specified for the nodataValue parameter. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### classify

          public void classify(SdoGeoRaster inGeoRaster,
                               double[] cropArea,
                               java.lang.String expression,
                               double[] rangeArray,
                               double[] valueArray,
                               java.lang.String storageParam,
                               java.sql.Blob[] rasterBlob,
                               JGeometry[] outArea,
                               double[] outWindow,
                               boolean nodata,
                               double nodataValue)
                        throws java.lang.Exception

      Generates a new raster in BLOB after applying the specified classification operation on the input GeoRaster object or objects. This procedure generates a one-layer raster stored in a single BLOB based on the input GeoRaster object or objects and the expression parameter, which is an arithmetic expression string. For each cell in the output GeoRaster object, expression is evaluated against corresponding cell values in the input GeoRaster object, and the following algorithm is used to calculate cell values of the output GeoRaster object: if (value of expression \< rangeArray\[0\]) cellValue=valueArray\[0\] else if (value of expression \>= rangeArray\[n-1\]) cellValue=valueArray\[n\] else if rangeArray\[m-1\] \<= 0 value of expression \< rangearray\[m\] cellvalue="valueArray\[m\]" in the calculation: length rangearray is n valuearray n+1 m n-1 if paralleldegree\>1, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If parallelDegree\<=1, you can roll back all changes.\< div\>
      Parameters:
      `inGeoRaster` - Input GeoRaster object.

      `cropArea` - crop area definition in cell space by a long array

      `expression` - An arithmetic expression used to classify cell values. See the Usage Notes for more information about specifying this parameter.

      `rangeArray` - A number array that defines ranges for classifying cell values. The array must contain at least one element.

      `valueArray` - A number array that defines the target cell value for each range. The number of elements must be 1 greater than the elements in rangeArray (that is, its length must be rangeArray+1).

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `nodata` - The string TRUE specifies that for any NODATA cells in an input GeoRaster object, the corresponding cells in the output GeoRaster object are to be set to the value specified for the nodataValue parameter. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### classify

          public void classify(SdoGeoRaster inGeoRaster,
                               JGeometry cropArea,
                               java.lang.String expression,
                               double[] rangeArray,
                               double[] valueArray,
                               java.lang.String storageParam,
                               SdoGeoRaster outGeoRaster,
                               boolean nodata,
                               double nodataValue,
                               java.lang.String polygonClip,
                               int parallelDegree)
                        throws java.lang.Exception

      Generates a new GeoRaster object after applying the specified classification operation on the input GeoRaster object or objects. This procedure generates a one-layer GeoRaster object based on the input GeoRaster object or objects and the expression parameter, which is an arithmetic expression string. For each cell in the output GeoRaster object, expression is evaluated against corresponding cell values in the input GeoRaster object, and the following algorithm is used to calculate cell values of the output GeoRaster object: if (value of expression \< rangeArray\[0\]) cellValue=valueArray\[0\] else if (value of expression \>= rangeArray\[n-1\]) cellValue=valueArray\[n\] else if rangeArray\[m-1\] \<= 0 value of expression \< rangearray\[m\] cellvalue="valueArray\[m\]" in the calculation: length rangearray is n valuearray n+1 m n-1 if paralleldegree\>1, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If parallelDegree\<=1, you can roll back all changes.\< div\>
      Parameters:
      `inGeoRaster` - Input GeoRaster object.

      `cropArea` - crop area definition in model space by a JGeometry object

      `expression` - An arithmetic expression used to classify cell values. See the Usage Notes for more information about specifying this parameter.

      `rangeArray` - A number array that defines ranges for classifying cell values. The array must contain at least one element.

      `valueArray` - A number array that defines the target cell value for each range. The number of elements must be 1 greater than the elements in rangeArray (that is, its length must be rangeArray+1).

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies that for any NODATA cells in an input GeoRaster object, the corresponding cells in the output GeoRaster object are to be set to the value specified for the nodataValue parameter. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `polygonClip` - The string TRUE causes the clipping window (cropArea geometry object) to be used for the operation; the string FALSE or a null value causes the MBR (minimum bounding rectangle) of the clipping window to be used for the operation.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### classify

          public void classify(SdoGeoRaster inGeoRaster,
                               JGeometry cropArea,
                               java.lang.String expression,
                               double[] rangeArray,
                               double[] valueArray,
                               java.lang.String storageParam,
                               java.sql.Blob[] rasterBlob,
                               JGeometry[] outArea,
                               double[] outWindow,
                               boolean nodata,
                               double nodataValue,
                               java.lang.String polygonClip)
                        throws java.lang.Exception

      Generates a new raster in BLOB after applying the specified classification operation on the input GeoRaster object or objects. This procedure generates a one-layer raster stored in a single BLOB based on the input GeoRaster object or objects and the expression parameter, which is an arithmetic expression string. For each cell in the output GeoRaster object, expression is evaluated against corresponding cell values in the input GeoRaster object, and the following algorithm is used to calculate cell values of the output GeoRaster object: if (value of expression \< rangeArray\[0\]) cellValue=valueArray\[0\] else if (value of expression \>= rangeArray\[n-1\]) cellValue=valueArray\[n\] else if rangeArray\[m-1\] \<= 0 value of expression \< rangearray\[m\] cellvalue="valueArray\[m\]" in the calculation: length rangearray is n valuearray n+1 m n-1 if paralleldegree\>1, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If parallelDegree\<=1, you can roll back all changes.\< div\>
      Parameters:
      `inGeoRaster` - Input GeoRaster object.

      `cropArea` - crop area definition in model space by a JGeometry object

      `expression` - An arithmetic expression used to classify cell values. See the Usage Notes for more information about specifying this parameter.

      `rangeArray` - A number array that defines ranges for classifying cell values. The array must contain at least one element.

      `valueArray` - A number array that defines the target cell value for each range. The number of elements must be 1 greater than the elements in rangeArray (that is, its length must be rangeArray+1).

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `nodata` - The string TRUE specifies that for any NODATA cells in an input GeoRaster object, the corresponding cells in the output GeoRaster object are to be set to the value specified for the nodataValue parameter. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `polygonClip` - The string TRUE causes the clipping window (cropArea geometry object) to be used for the operation; the string FALSE or a null value causes the MBR (minimum bounding rectangle) of the clipping window to be used for the operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### classify

          public void classify(SdoGeoRaster[] inGeoRasters,
                               java.lang.String expression,
                               double[] rangeArray,
                               double[] valueArray,
                               java.lang.String storageParam,
                               SdoGeoRaster outGeoRaster,
                               boolean nodata,
                               double nodataValue,
                               int parallelDegree)
                        throws java.lang.Exception

      Generates a new GeoRaster object after applying the specified classification operation on the input GeoRaster object or objects. This procedure generates a one-layer GeoRaster object based on the input GeoRaster object or objects and the expression parameter, which is an arithmetic expression string. For each cell in the output GeoRaster object, expression is evaluated against corresponding cell values in the input GeoRaster object, and the following algorithm is used to calculate cell values of the output GeoRaster object: if (value of expression \< rangeArray\[0\]) cellValue=valueArray\[0\] else if (value of expression \>= rangeArray\[n-1\]) cellValue=valueArray\[n\] else if rangeArray\[m-1\] \<= 0 value of expression \< rangearray\[m\] cellvalue="valueArray\[m\]" in the calculation: length rangearray is n valuearray n+1 m n-1 if paralleldegree\>1, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If parallelDegree\<=1, you can roll back all changes.\< div\>
      Parameters:
      `inGeoRasters` - An array of SdoGeoRaster objects. The maximum number of GeoRaster objects in the array is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `expression` - An arithmetic expression used to classify cell values. See the Usage Notes for more information about specifying this parameter.

      `rangeArray` - A number array that defines ranges for classifying cell values. The array must contain at least one element.

      `valueArray` - A number array that defines the target cell value for each range. The number of elements must be 1 greater than the elements in rangeArray (that is, its length must be rangeArray+1).

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies that for any NODATA cells in an input GeoRaster object, the corresponding cells in the output GeoRaster object are to be set to the value specified for the nodataValue parameter. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### classify

          public void classify(SdoGeoRaster[] inGeoRasters,
                               double[] cropArea,
                               java.lang.String expression,
                               double[] rangeArray,
                               double[] valueArray,
                               java.lang.String storageParam,
                               SdoGeoRaster outGeoRaster,
                               boolean nodata,
                               double nodataValue,
                               int parallelDegree)
                        throws java.lang.Exception

      Generates a new GeoRaster object after applying the specified classification operation on the input GeoRaster object or objects. This procedure generates a one-layer GeoRaster object based on the input GeoRaster object or objects and the expression parameter, which is an arithmetic expression string. For each cell in the output GeoRaster object, expression is evaluated against corresponding cell values in the input GeoRaster object, and the following algorithm is used to calculate cell values of the output GeoRaster object: if (value of expression \< rangeArray\[0\]) cellValue=valueArray\[0\] else if (value of expression \>= rangeArray\[n-1\]) cellValue=valueArray\[n\] else if rangeArray\[m-1\] \<= 0 value of expression \< rangearray\[m\] cellvalue="valueArray\[m\]" in the calculation: length rangearray is n valuearray n+1 m n-1 if paralleldegree\>1, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If parallelDegree\<=1, you can roll back all changes.\< div\>
      Parameters:
      `inGeoRasters` - An array of SdoGeoRaster objects. The maximum number of GeoRaster objects in the array is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `cropArea` - crop area definition in cell space by a long array

      `expression` - An arithmetic expression used to classify cell values. See the Usage Notes for more information about specifying this parameter.

      `rangeArray` - A number array that defines ranges for classifying cell values. The array must contain at least one element.

      `valueArray` - A number array that defines the target cell value for each range. The number of elements must be 1 greater than the elements in rangeArray (that is, its length must be rangeArray+1).

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies that for any NODATA cells in an input GeoRaster object, the corresponding cells in the output GeoRaster object are to be set to the value specified for the nodataValue parameter. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### classify

          public void classify(SdoGeoRaster[] inGeoRasters,
                               double[] cropArea,
                               java.lang.String expression,
                               double[] rangeArray,
                               double[] valueArray,
                               java.lang.String storageParam,
                               java.sql.Blob[] rasterBlob,
                               JGeometry[] outArea,
                               double[] outWindow,
                               boolean nodata,
                               double nodataValue)
                        throws java.lang.Exception

      Generates a new raster object stored in a BLOB after applying the specified classification operation on the input GeoRaster object or objects. This procedure generates a one-layer raster in a single BLOB based on the input GeoRaster object or objects and the expression parameter, which is an arithmetic expression string. For each cell in the output GeoRaster object, expression is evaluated against corresponding cell values in the input GeoRaster object, and the following algorithm is used to calculate cell values of the output GeoRaster object: if (value of expression \< rangeArray\[0\]) cellValue=valueArray\[0\] else if (value of expression \>= rangeArray\[n-1\]) cellValue=valueArray\[n\] else if rangeArray\[m-1\] \<= 0 value of expression \< rangearray\[m\] cellvalue="valueArray\[m\]" in the calculation: length rangearray is n valuearray n+1 m n-1 if paralleldegree\>1, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If parallelDegree\<=1, you can roll back all changes.\< div\>
      Parameters:
      `inGeoRasters` - An array of SdoGeoRaster objects. The maximum number of GeoRaster objects in the array is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `cropArea` - crop area definition in cell space by a long array

      `expression` - An arithmetic expression used to classify cell values. See the Usage Notes for more information about specifying this parameter.

      `rangeArray` - A number array that defines ranges for classifying cell values. The array must contain at least one element.

      `valueArray` - A number array that defines the target cell value for each range. The number of elements must be 1 greater than the elements in rangeArray (that is, its length must be rangeArray+1).

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `nodata` - The string TRUE specifies that for any NODATA cells in an input GeoRaster object, the corresponding cells in the output GeoRaster object are to be set to the value specified for the nodataValue parameter. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### classify

          public void classify(SdoGeoRaster[] inGeoRasters,
                               JGeometry cropArea,
                               java.lang.String expression,
                               double[] rangeArray,
                               double[] valueArray,
                               java.lang.String storageParam,
                               SdoGeoRaster outGeoRaster,
                               boolean nodata,
                               double nodataValue,
                               java.lang.String polygonClip,
                               int parallelDegree)
                        throws java.lang.Exception

      Generates a new GeoRaster object after applying the specified classification operation on the input GeoRaster object or objects. This procedure generates a one-layer GeoRaster object based on the input GeoRaster object or objects and the expression parameter, which is an arithmetic expression string. For each cell in the output GeoRaster object, expression is evaluated against corresponding cell values in the input GeoRaster object, and the following algorithm is used to calculate cell values of the output GeoRaster object: if (value of expression \< rangeArray\[0\]) cellValue=valueArray\[0\] else if (value of expression \>= rangeArray\[n-1\]) cellValue=valueArray\[n\] else if rangeArray\[m-1\] \<= 0 value of expression \< rangearray\[m\] cellvalue="valueArray\[m\]" in the calculation: length rangearray is n valuearray n+1 m n-1 if paralleldegree\>1, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If parallelDegree\<=1, you can roll back all changes.\< div\>
      Parameters:
      `inGeoRasters` - An array of SdoGeoRaster objects. The maximum number of GeoRaster objects in the array is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `cropArea` - crop area definition in model space by a JGeometry object

      `expression` - An arithmetic expression used to classify cell values. See the Usage Notes for more information about specifying this parameter.

      `rangeArray` - A number array that defines ranges for classifying cell values. The array must contain at least one element.

      `valueArray` - A number array that defines the target cell value for each range. The number of elements must be 1 greater than the elements in rangeArray (that is, its length must be rangeArray+1).

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies that for any NODATA cells in an input GeoRaster object, the corresponding cells in the output GeoRaster object are to be set to the value specified for the nodataValue parameter. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `polygonClip` - The string TRUE causes the clipping window (cropArea geometry object) to be used for the operation; the string FALSE or a null value causes the MBR (minimum bounding rectangle) of the clipping window to be used for the operation.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### classify

          public void classify(SdoGeoRaster[] inGeoRasters,
                               JGeometry cropArea,
                               java.lang.String expression,
                               double[] rangeArray,
                               double[] valueArray,
                               java.lang.String storageParam,
                               java.sql.Blob[] rasterBlob,
                               JGeometry[] outArea,
                               double[] outWindow,
                               boolean nodata,
                               double nodataValue,
                               java.lang.String polygonClip)
                        throws java.lang.Exception

      Generates a new raster stored in BLOB after applying the specified classification operation on the input GeoRaster object or objects. This procedure generates a one-layer raster in a single BLOB based on the input GeoRaster object or objects and the expression parameter, which is an arithmetic expression string. For each cell in the output GeoRaster object, expression is evaluated against corresponding cell values in the input GeoRaster object, and the following algorithm is used to calculate cell values of the output GeoRaster object: if (value of expression \< rangeArray\[0\]) cellValue=valueArray\[0\] else if (value of expression \>= rangeArray\[n-1\]) cellValue=valueArray\[n\] else if rangeArray\[m-1\] \<= 0 value of expression \< rangearray\[m\] cellvalue="valueArray\[m\]" in the calculation: length rangearray is n valuearray n+1 m n-1 if paralleldegree\>1, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If parallelDegree\<=1, you can roll back all changes.\< div\>
      Parameters:
      `inGeoRasters` - An array of SdoGeoRaster objects. The maximum number of GeoRaster objects in the array is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `cropArea` - crop area definition in model space by a JGeometry object

      `expression` - An arithmetic expression used to classify cell values. See the Usage Notes for more information about specifying this parameter.

      `rangeArray` - A number array that defines ranges for classifying cell values. The array must contain at least one element.

      `valueArray` - A number array that defines the target cell value for each range. The number of elements must be 1 greater than the elements in rangeArray (that is, its length must be rangeArray+1).

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `nodata` - The string TRUE specifies that for any NODATA cells in an input GeoRaster object, the corresponding cells in the output GeoRaster object are to be set to the value specified for the nodataValue parameter. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `polygonClip` - The string TRUE causes the clipping window (cropArea geometry object) to be used for the operation; the string FALSE or a null value causes the MBR (minimum bounding rectangle) of the clipping window to be used for the operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### classify

          public void classify(java.lang.String inGeoRasters,
                               java.lang.String expression,
                               double[] rangeArray,
                               double[] valueArray,
                               java.lang.String storageParam,
                               SdoGeoRaster outGeoRaster,
                               boolean nodata,
                               double nodataValue,
                               int parallelDegree)
                        throws java.lang.Exception

      Generates a new GeoRaster object after applying the specified classification operation on the input GeoRaster object or objects. This procedure generates a one-layer GeoRaster object based on the input GeoRaster object or objects and the expression parameter, which is an arithmetic expression string. For each cell in the output GeoRaster object, expression is evaluated against corresponding cell values in the input GeoRaster object, and the following algorithm is used to calculate cell values of the output GeoRaster object: if (value of expression \< rangeArray\[0\]) cellValue=valueArray\[0\] else if (value of expression \>= rangeArray\[n-1\]) cellValue=valueArray\[n\] else if rangeArray\[m-1\] \<= 0 value of expression \< rangearray\[m\] cellvalue="valueArray\[m\]" in the calculation: length rangearray is n valuearray n+1 m n-1 if paralleldegree\>1, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If parallelDegree\<=1, you can roll back all changes.\< div\>
      Parameters:
      `inGeoRasters` - PL/SQL query for the input GeoRaster objects. The maximum number of GeoRaster objects in the cursor is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `expression` - An arithmetic expression used to classify cell values. See the Usage Notes for more information about specifying this parameter.

      `rangeArray` - A number array that defines ranges for classifying cell values. The array must contain at least one element.

      `valueArray` - A number array that defines the target cell value for each range. The number of elements must be 1 greater than the elements in rangeArray (that is, its length must be rangeArray+1).

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies that for any NODATA cells in an input GeoRaster object, the corresponding cells in the output GeoRaster object are to be set to the value specified for the nodataValue parameter. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### classify

          public void classify(java.lang.String inGeoRasters,
                               double[] cropArea,
                               java.lang.String expression,
                               double[] rangeArray,
                               double[] valueArray,
                               java.lang.String storageParam,
                               SdoGeoRaster outGeoRaster,
                               boolean nodata,
                               double nodataValue,
                               int parallelDegree)
                        throws java.lang.Exception

      Generates a new GeoRaster object after applying the specified classification operation on the input GeoRaster object or objects. This procedure generates a one-layer GeoRaster object based on the input GeoRaster object or objects and the expression parameter, which is an arithmetic expression string. For each cell in the output GeoRaster object, expression is evaluated against corresponding cell values in the input GeoRaster object, and the following algorithm is used to calculate cell values of the output GeoRaster object: if (value of expression \< rangeArray\[0\]) cellValue=valueArray\[0\] else if (value of expression \>= rangeArray\[n-1\]) cellValue=valueArray\[n\] else if rangeArray\[m-1\] \<= 0 value of expression \< rangearray\[m\] cellvalue="valueArray\[m\]" in the calculation: length rangearray is n valuearray n+1 m n-1 if paralleldegree\>1, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If parallelDegree\<=1, you can roll back all changes.\< div\>
      Parameters:
      `inGeoRasters` - PL/SQL query for the input GeoRaster objects. The maximum number of GeoRaster objects in the cursor is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `cropArea` - crop area definition in cell space by a long array

      `expression` - An arithmetic expression used to classify cell values. See the Usage Notes for more information about specifying this parameter.

      `rangeArray` - A number array that defines ranges for classifying cell values. The array must contain at least one element.

      `valueArray` - A number array that defines the target cell value for each range. The number of elements must be 1 greater than the elements in rangeArray (that is, its length must be rangeArray+1).

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies that for any NODATA cells in an input GeoRaster object, the corresponding cells in the output GeoRaster object are to be set to the value specified for the nodataValue parameter. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### classify

          public void classify(java.lang.String inGeoRasters,
                               double[] cropArea,
                               java.lang.String expression,
                               double[] rangeArray,
                               double[] valueArray,
                               java.lang.String storageParam,
                               java.sql.Blob[] rasterBlob,
                               JGeometry[] outArea,
                               double[] outWindow,
                               boolean nodata,
                               double nodataValue)
                        throws java.lang.Exception

      Generates a new raster stored in a BLOB after applying the specified classification operation on the input GeoRaster object or objects. This procedure generates a one-layer raster in a single BLOB based on the input GeoRaster object or objects and the expression parameter, which is an arithmetic expression string. For each cell in the output GeoRaster object, expression is evaluated against corresponding cell values in the input GeoRaster object, and the following algorithm is used to calculate cell values of the output GeoRaster object: if (value of expression \< rangeArray\[0\]) cellValue=valueArray\[0\] else if (value of expression \>= rangeArray\[n-1\]) cellValue=valueArray\[n\] else if rangeArray\[m-1\] \<= 0 value of expression \< rangearray\[m\] cellvalue="valueArray\[m\]" in the calculation: length rangearray is n valuearray n+1 m n-1 if paralleldegree\>1, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If parallelDegree\<=1, you can roll back all changes.\< div\>
      Parameters:
      `inGeoRasters` - PL/SQL query for the input GeoRaster objects. The maximum number of GeoRaster objects in the cursor is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `cropArea` - crop area definition in cell space by a long array

      `expression` - An arithmetic expression used to classify cell values. See the Usage Notes for more information about specifying this parameter.

      `rangeArray` - A number array that defines ranges for classifying cell values. The array must contain at least one element.

      `valueArray` - A number array that defines the target cell value for each range. The number of elements must be 1 greater than the elements in rangeArray (that is, its length must be rangeArray+1).

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `nodata` - The string TRUE specifies that for any NODATA cells in an input GeoRaster object, the corresponding cells in the output GeoRaster object are to be set to the value specified for the nodataValue parameter. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### classify

          public void classify(java.lang.String inGeoRasters,
                               JGeometry cropArea,
                               java.lang.String expression,
                               double[] rangeArray,
                               double[] valueArray,
                               java.lang.String storageParam,
                               SdoGeoRaster outGeoRaster,
                               boolean nodata,
                               double nodataValue,
                               java.lang.String polygonClip,
                               int parallelDegree)
                        throws java.lang.Exception

      Generates a new GeoRaster object after applying the specified classification operation on the input GeoRaster object or objects. This procedure generates a one-layer GeoRaster object based on the input GeoRaster object or objects and the expression parameter, which is an arithmetic expression string. For each cell in the output GeoRaster object, expression is evaluated against corresponding cell values in the input GeoRaster object, and the following algorithm is used to calculate cell values of the output GeoRaster object: if (value of expression \< rangeArray\[0\]) cellValue=valueArray\[0\] else if (value of expression \>= rangeArray\[n-1\]) cellValue=valueArray\[n\] else if rangeArray\[m-1\] \<= 0 value of expression \< rangearray\[m\] cellvalue="valueArray\[m\]" in the calculation: length rangearray is n valuearray n+1 m n-1 if paralleldegree\>1, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If parallelDegree\<=1, you can roll back all changes.\< div\>
      Parameters:
      `inGeoRasters` - PL/SQL query for the input GeoRaster objects. The maximum number of GeoRaster objects in the cursor is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `cropArea` - crop area definition in model space by a JGeometry object

      `expression` - An arithmetic expression used to classify cell values. See the Usage Notes for more information about specifying this parameter.

      `rangeArray` - A number array that defines ranges for classifying cell values. The array must contain at least one element.

      `valueArray` - A number array that defines the target cell value for each range. The number of elements must be 1 greater than the elements in rangeArray (that is, its length must be rangeArray+1).

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies that for any NODATA cells in an input GeoRaster object, the corresponding cells in the output GeoRaster object are to be set to the value specified for the nodataValue parameter. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `polygonClip` - The string TRUE causes the clipping window (cropArea geometry object) to be used for the operation; the string FALSE or a null value causes the MBR (minimum bounding rectangle) of the clipping window to be used for the operation.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### classify

          public void classify(java.lang.String inGeoRasters,
                               JGeometry cropArea,
                               java.lang.String expression,
                               double[] rangeArray,
                               double[] valueArray,
                               java.lang.String storageParam,
                               java.sql.Blob[] rasterBlob,
                               JGeometry[] outArea,
                               double[] outWindow,
                               boolean nodata,
                               double nodataValue,
                               java.lang.String polygonClip)
                        throws java.lang.Exception

      Generates a new raster stored in a BLOB after applying the specified classification operation on the input GeoRaster object or objects. This procedure generates a one-layer raster in a single BLOB based on the input GeoRaster object or objects and the expression parameter, which is an arithmetic expression string. For each cell in the output GeoRaster object, expression is evaluated against corresponding cell values in the input GeoRaster object, and the following algorithm is used to calculate cell values of the output GeoRaster object: if (value of expression \< rangeArray\[0\]) cellValue=valueArray\[0\] else if (value of expression \>= rangeArray\[n-1\]) cellValue=valueArray\[n\] else if rangeArray\[m-1\] \<= 0 value of expression \< rangearray\[m\] cellvalue="valueArray\[m\]" in the calculation: length rangearray is n valuearray n+1 m n-1 if paralleldegree\>1, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If parallelDegree\<=1, you can roll back all changes.\< div\>
      Parameters:
      `inGeoRasters` - PL/SQL query for the input GeoRaster objects. The maximum number of GeoRaster objects in the cursor is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `cropArea` - crop area definition in model space by a JGeometry object

      `expression` - An arithmetic expression used to classify cell values. See the Usage Notes for more information about specifying this parameter.

      `rangeArray` - A number array that defines ranges for classifying cell values. The array must contain at least one element.

      `valueArray` - A number array that defines the target cell value for each range. The number of elements must be 1 greater than the elements in rangeArray (that is, its length must be rangeArray+1).

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `nodata` - The string TRUE specifies that for any NODATA cells in an input GeoRaster object, the corresponding cells in the output GeoRaster object are to be set to the value specified for the nodataValue parameter. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `polygonClip` - The string TRUE causes the clipping window (cropArea geometry object) to be used for the operation; the string FALSE or a null value causes the MBR (minimum bounding rectangle) of the clipping window to be used for the operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### findCells

          public void findCells(SdoGeoRaster inGeoRaster,
                                java.lang.String condition,
                                java.lang.String storageParam,
                                SdoGeoRaster outGeoRaster,
                                double[] bgValues,
                                boolean nodata,
                                int parallelDegree)
                         throws java.lang.Exception

      Generates a new GeoRaster object based on the input GeoRaster object, but masking all cells that do not satisfy the condition parameter specification. This procedure generates a new GeoRaster object based on the input GeoRaster object and the condition parameter, which is booleanExpr, a Boolean expression string. For each cell in the output GeoRaster object, condition is evaluated against corresponding cell values in the input GeoRaster object. If condition is true for a cell, the original cell value is kept in the output GeoRaster object; otherwise, bgValues are filled for the cell in the output GeoRaster object
      Parameters:
      `inGeoRaster` - PL/SQL query for the input GeoRaster objects. The maximum number of GeoRaster objects in the cursor is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `condition` - An expression string used to filter out cells.

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `bgValues` - Background values to represent values of cells in the empty raster blocks of the input GeoRaster object. The number of elements in the bgValues array must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, (1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### findCells

          public void findCells(SdoGeoRaster inGeoRaster,
                                double[] cropArea,
                                java.lang.String condition,
                                java.lang.String storageParam,
                                SdoGeoRaster outGeoRaster,
                                double[] bgValues,
                                boolean nodata,
                                int parallelDegree)
                         throws java.lang.Exception

      Generates a new GeoRaster object based on the input GeoRaster object, but masking all cells that do not satisfy the condition parameter specification. This procedure generates a new GeoRaster object based on the input GeoRaster object and the condition parameter, which is booleanExpr, a Boolean expression string. For each cell in the output GeoRaster object, condition is evaluated against corresponding cell values in the input GeoRaster object. If condition is true for a cell, the original cell value is kept in the output GeoRaster object; otherwise, bgValues are filled for the cell in the output GeoRaster object
      Parameters:
      `inGeoRaster` - PL/SQL query for the input GeoRaster objects. The maximum number of GeoRaster objects in the cursor is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `cropArea` - crop area definition in cell space by a long array

      `condition` - An expression string used to filter out cells.

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `bgValues` - Background values to represent values of cells in the empty raster blocks of the input GeoRaster object. The number of elements in the bgValues array must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, (1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### findCells

          public void findCells(SdoGeoRaster inGeoRaster,
                                double[] cropArea,
                                java.lang.String condition,
                                java.lang.String storageParam,
                                java.sql.Blob[] rasterBlob,
                                JGeometry[] outArea,
                                double[] outWindow,
                                double[] bgValues,
                                boolean nodata)
                         throws java.lang.Exception

      Generates a new raster stored in a BLOB based on the input GeoRaster object, but masking all cells that do not satisfy the condition parameter specification. This procedure generates a new raster in a single BLOB based on the input GeoRaster object and the condition parameter, which is booleanExpr, a Boolean expression string. For each cell in the output GeoRaster object, condition is evaluated against corresponding cell values in the input GeoRaster object. If condition is true for a cell, the original cell value is kept in the output GeoRaster object; otherwise, bgValues are filled for the cell in the output GeoRaster object
      Parameters:
      `inGeoRaster` - PL/SQL query for the input GeoRaster objects. The maximum number of GeoRaster objects in the cursor is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `cropArea` - crop area definition in cell space by a long array

      `condition` - An expression string used to filter out cells.

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `bgValues` - Background values to represent values of cells in the empty raster blocks of the input GeoRaster object. The number of elements in the bgValues array must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, (1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### findCells

          public void findCells(SdoGeoRaster inGeoRaster,
                                JGeometry cropArea,
                                java.lang.String condition,
                                java.lang.String storageParam,
                                SdoGeoRaster outGeoRaster,
                                double[] bgValues,
                                boolean nodata,
                                java.lang.String polygonClip,
                                int parallelDegree)
                         throws java.lang.Exception

      Generates a new GeoRaster object based on the input GeoRaster object, but masking all cells that do not satisfy the condition parameter specification. This procedure generates a new GeoRaster object based on the input GeoRaster object and the condition parameter, which is booleanExpr, a Boolean expression string. For each cell in the output GeoRaster object, condition is evaluated against corresponding cell values in the input GeoRaster object. If condition is true for a cell, the original cell value is kept in the output GeoRaster object; otherwise, bgValues are filled for the cell in the output GeoRaster object
      Parameters:
      `inGeoRaster` - PL/SQL query for the input GeoRaster objects. The maximum number of GeoRaster objects in the cursor is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `cropArea` - crop area definition in model space by a JGeometry object

      `condition` - An expression string used to filter out cells.

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `bgValues` - Background values to represent values of cells in the empty raster blocks of the input GeoRaster object. The number of elements in the bgValues array must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, (1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `polygonClip` - The string TRUE causes the clipping window (cropArea geometry object) to be used for the operation; the string FALSE or a null value causes the MBR (minimum bounding rectangle) of the clipping window to be used for the operation.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### findCells

          public void findCells(SdoGeoRaster inGeoRaster,
                                JGeometry cropArea,
                                java.lang.String condition,
                                java.lang.String storageParam,
                                java.sql.Blob[] rasterBlob,
                                JGeometry[] outArea,
                                double[] outWindow,
                                double[] bgValues,
                                boolean nodata,
                                java.lang.String polygonClip)
                         throws java.lang.Exception

      Generates a new raster stored in a BLOB based on the input GeoRaster object, but masking all cells that do not satisfy the condition parameter specification. This procedure generates a new raster in a single BLOB based on the input GeoRaster object and the condition parameter, which is booleanExpr, a Boolean expression string. For each cell in the output GeoRaster object, condition is evaluated against corresponding cell values in the input GeoRaster object. If condition is true for a cell, the original cell value is kept in the output GeoRaster object; otherwise, bgValues are filled for the cell in the output GeoRaster object
      Parameters:
      `inGeoRaster` - PL/SQL query for the input GeoRaster objects. The maximum number of GeoRaster objects in the cursor is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `cropArea` - crop area definition in model space by a JGeometry object

      `condition` - An expression string used to filter out cells.

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `bgValues` - Background values to represent values of cells in the empty raster blocks of the input GeoRaster object. The number of elements in the bgValues array must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, (1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `polygonClip` - The string TRUE causes the clipping window (cropArea geometry object) to be used for the operation; the string FALSE or a null value causes the MBR (minimum bounding rectangle) of the clipping window to be used for the operation.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### isOverlap

          public boolean isOverlap(SdoGeoRaster geoRaster1,
                                   SdoGeoRaster geoRaster2,
                                   java.lang.Double tolerance)
                            throws java.lang.Exception

      Returns the string TRUE if two or more GeoRaster objects overlap, or FALSE if two or more GeoRaster objects do not overlap. The GeoRaster objects being compared for overlap must be either all georeferenced or all non-georeferenced. The following logic is applied to determine if two GeoRaster objects overlap: If the row or column dimension size of two GeoRaster objects is different, then return 'FALSE'. Otherwise, continue to the next step. Check if both GeoRaster objects are georeferenced.If one is georeferenced and the other one is not, then return 'FALSE'.If both are non-georeferenced, and if the ultCoordinate of both GeoRaster objects is the same, then return 'TRUE'; else, return 'FALSE'.If both are georeferenced, go to the next step. Check the pType, nVars, order, and nCoefficients values (explained in Section 1.6.1, "Functional Fitting Georeferencing Model") of the p, q, r, and s polynomials. If any are different, then return 'FALSE'; else, go to the next step. Calculate the upper-left, upper-right, lower-left, and lower-right four points from cell space to model space. If the distance of corresponding points of the two GeoRaster objects is within the tolerance value (converted from cell space to model space), then return 'TRUE'; else, return 'FALSE'. The raster algebra functions of GeoRaster require the raster layers from different GeoRaster objects have the same size and completely overlap each other. Before you apply raster algebra operations over two or more GeoRaster objects or perform other operations, you can use the SDO_GEOR_RA.isOverlap function to determine if the GeoRaster objects are of the same size and cover the same ground area.
      Parameters:
      `geoRaster1` - Input GeoRaster object

      `geoRaster2` - Input GeoRaster object

      `tolerance` - Tolerance value used to determine if two cells in the cell space overlap in the model space. The value should be between 0 and 1, and the unit is cell. For example, 0.5 (the default) means one-half cell, namely, that two cells overlap if the distance between them in 0.5 cell or less.

      Returns:
      a boolean value to indicate if two or more GeoRaster objects overlap

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### isOverlap

          public boolean isOverlap(SdoGeoRaster[] inGeoRasters,
                                   java.lang.Double tolerance)
                            throws java.lang.Exception

      Returns the string TRUE if two or more GeoRaster objects overlap, or FALSE if two or more GeoRaster objects do not overlap. The GeoRaster objects being compared for overlap must be either all georeferenced or all non-georeferenced. The following logic is applied to determine if two GeoRaster objects overlap: If the row or column dimension size of two GeoRaster objects is different, then return 'FALSE'. Otherwise, continue to the next step. Check if both GeoRaster objects are georeferenced.If one is georeferenced and the other one is not, then return 'FALSE'.If both are non-georeferenced, and if the ultCoordinate of both GeoRaster objects is the same, then return 'TRUE'; else, return 'FALSE'.If both are georeferenced, go to the next step. Check the pType, nVars, order, and nCoefficients values (explained in Section 1.6.1, "Functional Fitting Georeferencing Model") of the p, q, r, and s polynomials. If any are different, then return 'FALSE'; else, go to the next step. Calculate the upper-left, upper-right, lower-left, and lower-right four points from cell space to model space. If the distance of corresponding points of the two GeoRaster objects is within the tolerance value (converted from cell space to model space), then return 'TRUE'; else, return 'FALSE'. The raster algebra functions of GeoRaster require the raster layers from different GeoRaster objects have the same size and completely overlap each other. Before you apply raster algebra operations over two or more GeoRaster objects or perform other operations, you can use the SDO_GEOR_RA.isOverlap function to determine if the GeoRaster objects are of the same size and cover the same ground area.
      Parameters:
      `inGeoRasters` - An array of SdoGeoRaster objects. The maximum number of GeoRaster objects in the array is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `tolerance` - Tolerance value used to determine if two cells in the cell space overlap in the model space. The value should be between 0 and 1, and the unit is cell. For example, 0.5 (the default) means one-half cell, namely, that two cells overlap if the distance between them in 0.5 cell or less.

      Returns:
      a boolean value to indicate if two or more GeoRaster objects overlap

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### isOverlap

          public boolean isOverlap(java.lang.String inGeoRasters,
                                   java.lang.Double tolerance)
                            throws java.lang.Exception

      Returns the string TRUE if two or more GeoRaster objects overlap, or FALSE if two or more GeoRaster objects do not overlap. The GeoRaster objects being compared for overlap must be either all georeferenced or all non-georeferenced. The following logic is applied to determine if two GeoRaster objects overlap: If the row or column dimension size of two GeoRaster objects is different, then return 'FALSE'. Otherwise, continue to the next step. Check if both GeoRaster objects are georeferenced.If one is georeferenced and the other one is not, then return 'FALSE'.If both are non-georeferenced, and if the ultCoordinate of both GeoRaster objects is the same, then return 'TRUE'; else, return 'FALSE'.If both are georeferenced, go to the next step. Check the pType, nVars, order, and nCoefficients values (explained in Section 1.6.1, "Functional Fitting Georeferencing Model") of the p, q, r, and s polynomials. If any are different, then return 'FALSE'; else, go to the next step. Calculate the upper-left, upper-right, lower-left, and lower-right four points from cell space to model space. If the distance of corresponding points of the two GeoRaster objects is within the tolerance value (converted from cell space to model space), then return 'TRUE'; else, return 'FALSE'. The raster algebra functions of GeoRaster require the raster layers from different GeoRaster objects have the same size and completely overlap each other. Before you apply raster algebra operations over two or more GeoRaster objects or perform other operations, you can use the SDO_GEOR_RA.isOverlap function to determine if the GeoRaster objects are of the same size and cover the same ground area.
      Parameters:
      `inGeoRasters` - PL/SQL query for the input GeoRaster objects. The maximum number of GeoRaster objects in the cursor is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `tolerance` - Tolerance value used to determine if two cells in the cell space overlap in the model space. The value should be between 0 and 1, and the unit is cell. For example, 0.5 (the default) means one-half cell, namely, that two cells overlap if the distance between them in 0.5 cell or less.

      Returns:
      a boolean value to indicate if two or more GeoRaster objects overlap

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterMathOp

          public void rasterMathOp(java.lang.String inGeoRasters,
                                   JGeometry cropArea,
                                   java.lang.String[] operation,
                                   java.lang.String storageParam,
                                   SdoGeoRaster outGeoRaster,
                                   boolean nodata,
                                   java.lang.Double nodataValue,
                                   java.lang.String polygonClip,
                                   int parallelDegree)
                            throws java.lang.Exception

      Generate a new GeoRaster object from layers of one or more input GeoRaster objects based on the operation parameter specification.
      Parameters:
      `inGeoRasters` - PL/SQL query for the input GeoRaster objects. The maximum number of GeoRaster objects in the cursor is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `cropArea` - crop area definition in model space by a JGeometry object

      `operation` - An array of arithmeticExpr expression strings used to calculate raster cell values in the output GeoRaster object. Each element of the array corresponds to a layer in the output GeoRaster object. The syntax for the arithmeticExpr expressions is explained in Section 4.1, "Raster Algebra Language".

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterMathOp

          public void rasterMathOp(java.lang.String inGeoRasters,
                                   JGeometry cropArea,
                                   java.lang.String[] operation,
                                   java.lang.String storageParam,
                                   java.sql.Blob[] rasterBlob,
                                   JGeometry[] outArea,
                                   double[] outWindow,
                                   boolean nodata,
                                   java.lang.Double nodataValue,
                                   java.lang.String polygonClip)
                            throws java.lang.Exception

      Generate a new raster stored in BLOB from layers of one or more input GeoRaster objects based on the operation parameter specification.
      Parameters:
      `inGeoRasters` - PL/SQL query for the input GeoRaster objects. The maximum number of GeoRaster objects in the cursor is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `cropArea` - crop area definition in model space by a JGeometry object

      `operation` - An array of arithmeticExpr expression strings used to calculate raster cell values in the output GeoRaster object. Each element of the array corresponds to a layer in the output GeoRaster object. The syntax for the arithmeticExpr expressions is explained in Section 4.1, "Raster Algebra Language".

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterMathOp

          public void rasterMathOp(java.lang.String inGeoRasters,
                                   double[] cropArea,
                                   java.lang.String[] operation,
                                   java.lang.String storageParam,
                                   SdoGeoRaster outGeoRaster,
                                   boolean nodata,
                                   java.lang.Double nodataValue,
                                   int parallelDegree)
                            throws java.lang.Exception

      Generate a new GeoRaster object from layers of one or more input GeoRaster objects based on the operation parameter specification.
      Parameters:
      `inGeoRasters` - PL/SQL query for the input GeoRaster objects. The maximum number of GeoRaster objects in the cursor is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `cropArea` - crop area definition in cell space by a long array

      `operation` - An array of arithmeticExpr expression strings used to calculate raster cell values in the output GeoRaster object. Each element of the array corresponds to a layer in the output GeoRaster object. The syntax for the arithmeticExpr expressions is explained in Section 4.1, "Raster Algebra Language".

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterMathOp

          public void rasterMathOp(java.lang.String inGeoRasters,
                                   double[] cropArea,
                                   java.lang.String[] operation,
                                   java.lang.String storageParam,
                                   java.sql.Blob[] rasterBlob,
                                   JGeometry[] outArea,
                                   double[] outWindow,
                                   boolean nodata,
                                   java.lang.Double nodataValue)
                            throws java.lang.Exception

      Generate a new raster stored in a BLOB from layers of one or more input GeoRaster objects based on the operation parameter specification.
      Parameters:
      `inGeoRasters` - PL/SQL query for the input GeoRaster objects. The maximum number of GeoRaster objects in the cursor is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `cropArea` - crop area definition in cell space by a long array

      `operation` - An array of arithmeticExpr expression strings used to calculate raster cell values in the output GeoRaster object. Each element of the array corresponds to a layer in the output GeoRaster object. The syntax for the arithmeticExpr expressions is explained in Section 4.1, "Raster Algebra Language".

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterMathOp

          public void rasterMathOp(java.lang.String inGeoRasters,
                                   java.lang.String[] operation,
                                   java.lang.String storageParam,
                                   SdoGeoRaster outGeoRaster,
                                   boolean nodata,
                                   java.lang.Double nodataValue,
                                   int parallelDegree)
                            throws java.lang.Exception

      Generate a new GeoRaster object from layers of one or more input GeoRaster objects based on the operation parameter specification.
      Parameters:
      `inGeoRasters` - PL/SQL query for the input GeoRaster objects. The maximum number of GeoRaster objects in the cursor is 8, but there is no limit on the total number of layers for all the GeoRaster objects.

      `operation` - An array of arithmeticExpr expression strings used to calculate raster cell values in the output GeoRaster object. Each element of the array corresponds to a layer in the output GeoRaster object. The syntax for the arithmeticExpr expressions is explained in Section 4.1, "Raster Algebra Language".

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterMathOp

          public void rasterMathOp(SdoGeoRaster[] inGeoRasters,
                                   JGeometry cropArea,
                                   java.lang.String[] operation,
                                   java.lang.String storageParam,
                                   SdoGeoRaster outGeoRaster,
                                   boolean nodata,
                                   java.lang.Double nodataValue,
                                   java.lang.String polygonClip,
                                   int parallelDegree)
                            throws java.lang.Exception

      Generate a new GeoRaster object from layers of one or more input GeoRaster objects based on the operation parameter specification.
      Parameters:
      `inGeoRasters` - An array of SdoGeoRaster objects.

      `cropArea` - crop area definition in model space by a JGeometry object

      `operation` - An array of arithmeticExpr expression strings used to calculate raster cell values in the output GeoRaster object. Each element of the array corresponds to a layer in the output GeoRaster object. The syntax for the arithmeticExpr expressions is explained in Section 4.1, "Raster Algebra Language".

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterMathOp

          public void rasterMathOp(SdoGeoRaster[] inGeoRasters,
                                   JGeometry cropArea,
                                   java.lang.String[] operation,
                                   java.lang.String storageParam,
                                   java.sql.Blob[] rasterBlob,
                                   JGeometry[] outArea,
                                   double[] outWindow,
                                   boolean nodata,
                                   java.lang.Double nodataValue,
                                   java.lang.String polygonClip)
                            throws java.lang.Exception

      Generate a new raster stored in BLOB from layers of one or more input GeoRaster objects based on the operation parameter specification.
      Parameters:
      `inGeoRasters` - An array of SdoGeoRaster objects.

      `cropArea` - crop area definition in model space by a JGeometry object

      `operation` - An array of arithmeticExpr expression strings used to calculate raster cell values in the output GeoRaster object. Each element of the array corresponds to a layer in the output GeoRaster object. The syntax for the arithmeticExpr expressions is explained in Section 4.1, "Raster Algebra Language".

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterMathOp

          public void rasterMathOp(SdoGeoRaster[] inGeoRasters,
                                   double[] cropArea,
                                   java.lang.String[] operation,
                                   java.lang.String storageParam,
                                   SdoGeoRaster outGeoRaster,
                                   boolean nodata,
                                   java.lang.Double nodataValue,
                                   int parallelDegree)
                            throws java.lang.Exception

      Generate a new GeoRaster object from layers of one or more input GeoRaster objects based on the operation parameter specification.
      Parameters:
      `inGeoRasters` - An array of SdoGeoRaster objects.

      `cropArea` - crop area definition in cell space by a long array

      `operation` - An array of arithmeticExpr expression strings used to calculate raster cell values in the output GeoRaster object. Each element of the array corresponds to a layer in the output GeoRaster object. The syntax for the arithmeticExpr expressions is explained in Section 4.1, "Raster Algebra Language".

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterMathOp

          public void rasterMathOp(SdoGeoRaster[] inGeoRasters,
                                   double[] cropArea,
                                   java.lang.String[] operation,
                                   java.lang.String storageParam,
                                   java.sql.Blob[] rasterBlob,
                                   JGeometry[] outArea,
                                   double[] outWindow,
                                   boolean nodata,
                                   java.lang.Double nodataValue)
                            throws java.lang.Exception

      Generate a new raster stored in BLOB from layers of one or more input GeoRaster objects based on the operation parameter specification.
      Parameters:
      `inGeoRasters` - An array of SdoGeoRaster objects.

      `cropArea` - crop area definition in cell space by a long array

      `operation` - An array of arithmeticExpr expression strings used to calculate raster cell values in the output GeoRaster object. Each element of the array corresponds to a layer in the output GeoRaster object. The syntax for the arithmeticExpr expressions is explained in Section 4.1, "Raster Algebra Language".

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterMathOp

          public void rasterMathOp(SdoGeoRaster[] inGeoRasters,
                                   java.lang.String[] operation,
                                   java.lang.String storageParam,
                                   SdoGeoRaster outGeoRaster,
                                   boolean nodata,
                                   java.lang.Double nodataValue,
                                   int parallelDegree)
                            throws java.lang.Exception

      Generate a new GeoRaster object from layers of one or more input GeoRaster objects based on the operation parameter specification.
      Parameters:
      `inGeoRasters` - An array of SdoGeoRaster objects.

      `operation` - An array of arithmeticExpr expression strings used to calculate raster cell values in the output GeoRaster object. Each element of the array corresponds to a layer in the output GeoRaster object. The syntax for the arithmeticExpr expressions is explained in Section 4.1, "Raster Algebra Language".

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterMathOp

          public void rasterMathOp(SdoGeoRaster inGeoRaster,
                                   JGeometry cropArea,
                                   java.lang.String[] operation,
                                   java.lang.String storageParam,
                                   SdoGeoRaster outGeoRaster,
                                   boolean nodata,
                                   java.lang.Double nodataValue,
                                   java.lang.String polygonClip,
                                   int parallelDegree)
                            throws java.lang.Exception

      Generate a new GeoRaster object from layers of one or more input GeoRaster objects based on the operation parameter specification.
      Parameters:
      `inGeoRaster` - Input GeoRaster object.

      `cropArea` - crop area definition in model space by a JGeometry object

      `operation` - An array of arithmeticExpr expression strings used to calculate raster cell values in the output GeoRaster object. Each element of the array corresponds to a layer in the output GeoRaster object. The syntax for the arithmeticExpr expressions is explained in Section 4.1, "Raster Algebra Language".

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterMathOp

          public void rasterMathOp(SdoGeoRaster inGeoRaster,
                                   JGeometry cropArea,
                                   java.lang.String[] operation,
                                   java.lang.String storageParam,
                                   java.sql.Blob[] rasterBlob,
                                   JGeometry[] outArea,
                                   double[] outWindow,
                                   boolean nodata,
                                   java.lang.Double nodataValue,
                                   java.lang.String polygonClip)
                            throws java.lang.Exception

      Generate a new raster stored in a BLOB from layers of one or more input GeoRaster objects based on the operation parameter specification.
      Parameters:
      `inGeoRaster` - Input GeoRaster object.

      `cropArea` - crop area definition in model space by a JGeometry object

      `operation` - An array of arithmeticExpr expression strings used to calculate raster cell values in the output GeoRaster object. Each element of the array corresponds to a layer in the output GeoRaster object. The syntax for the arithmeticExpr expressions is explained in Section 4.1, "Raster Algebra Language".

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterMathOp

          public void rasterMathOp(SdoGeoRaster inGeoRaster,
                                   double[] cropArea,
                                   java.lang.String[] operation,
                                   java.lang.String storageParam,
                                   SdoGeoRaster outGeoRaster,
                                   boolean nodata,
                                   java.lang.Double nodataValue,
                                   int parallelDegree)
                            throws java.lang.Exception

      Generate a new GeoRaster object from layers of one or more input GeoRaster objects based on the operation parameter specification.
      Parameters:
      `inGeoRaster` - Input GeoRaster object.

      `cropArea` - crop area definition in cell space by a long array

      `operation` - An array of arithmeticExpr expression strings used to calculate raster cell values in the output GeoRaster object. Each element of the array corresponds to a layer in the output GeoRaster object. The syntax for the arithmeticExpr expressions is explained in Section 4.1, "Raster Algebra Language".

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterMathOp

          public void rasterMathOp(SdoGeoRaster inGeoRaster,
                                   double[] cropArea,
                                   java.lang.String[] operation,
                                   java.lang.String storageParam,
                                   java.sql.Blob[] rasterBlob,
                                   JGeometry[] outArea,
                                   double[] outWindow,
                                   boolean nodata,
                                   java.lang.Double nodataValue)
                            throws java.lang.Exception

      Generate a new raster stored in a BLOB from layers of one or more input GeoRaster objects based on the operation parameter specification.
      Parameters:
      `inGeoRaster` - Input GeoRaster object.

      `cropArea` - crop area definition in cell space by a long array

      `operation` - An array of arithmeticExpr expression strings used to calculate raster cell values in the output GeoRaster object. Each element of the array corresponds to a layer in the output GeoRaster object. The syntax for the arithmeticExpr expressions is explained in Section 4.1, "Raster Algebra Language".

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterMathOp

          public void rasterMathOp(SdoGeoRaster inGeoRaster,
                                   java.lang.String[] operation,
                                   java.lang.String storageParam,
                                   SdoGeoRaster outGeoRaster,
                                   boolean nodata,
                                   java.lang.Double nodataValue,
                                   int parallelDegree)
                            throws java.lang.Exception

      Generate a new GeoRaster object from layers of one or more input GeoRaster objects based on the operation parameter specification.
      Parameters:
      `inGeoRaster` - Input GeoRaster object.

      `operation` - An array of arithmeticExpr expression strings used to calculate raster cell values in the output GeoRaster object. Each element of the array corresponds to a layer in the output GeoRaster object. The syntax for the arithmeticExpr expressions is explained in Section 4.1, "Raster Algebra Language".

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterMathOp

          public void rasterMathOp(SdoGeoRaster georaster0,
                                   SdoGeoRaster georaster1,
                                   double[] cropArea,
                                   java.lang.Double constant,
                                   int operartor,
                                   java.lang.String storageParam,
                                   SdoGeoRaster outGeoRaster,
                                   double[] bgValues,
                                   boolean nodata,
                                   java.lang.Double nodataValue,
                                   int parallelDegree)
                            throws java.lang.Exception

      Applies a mathematical operation on all corresponding cells of each layer of one or two input GeoRaster objects. For this method, all pyramids are removed in the resulting GeoRaster object, but masks of the first input GeoRaster object are kept in the resulting GeoRaster object. For the operator parameter, the operators have the following definitions: OPERATOR_ABSOLUTE : if (src\[x\]\[y\]\[b\] \< 0) { dst\[x\]\[y\]\[b\] = -src\[x\]\[y\]\[b\]; } else { dst\[x\]\[y\]\[b\] = src\[x\]\[y\]\[b\]; } OPERATOR_ADD dst\[x\]\[y\]\[b\]=src1\[x\]\[y\]\[b\]+src2\[x\]\[y\]\[b\] OPERATOR_ADDCONST dst\[x\]\[y\]\[b\]=src\[x\]\[y\]\[b\] +constant --constant is the third parameter OPERATOR_DIVIDE dst\[x\]\[y\]\[b\]=src1\[x\]\[y\]\[b\]/src2\[x\]\[y\]\[b\] OPERATOR_DIVIDECONST dst\[x\]\[y\]\[b\]=src\[x\]\[y\]\[b\]/constant --constant is the third parameter OPERATOR_EXP dst\[x\]\[y\]\[b\]=exp(src\[x\]\[y\]\[b\]) OPERATOR_INVERT : Inverts the cell values: dst\[x\]\[y\]\[b\]=-src\[x\]\[y\]\[b\] OPERATOR_LOG : dst\[x\]\[y\]\[b\]=log(src\[x\]\[y\]\[b\]) OPERATOR_MULTIPLY dst\[x\]\[y\]\[b\]=src1\[x\]\[y\]\[b\]\*src2\[x\]\[y\]\[b\] OPERATOR_MULTIPLYCONST dst\[x\]\[y\]\[b\]=src\[x\]\[y\]\[b\]\*constant --constant is the third parameter OPERATOR_SUBTRACT dst\[x\]\[y\]\[b\]=src1\[x\]\[y\]\[b\]-src2\[x\]\[y\]\[b\] OPERATOR_SUBTRACTCONST dst\[x\]\[y\]\[b\]=src\[x\]\[y\]\[b\]-constant --constant is the third parameter
      Parameters:
      `georaster0` - The left operand.

      `georaster1` - The right operand.

      `cropArea` - crop area definition in cell space by a long array

      `constant` - Constant value for some operators , such as addConst and divConstant.

      `operator` - One of the following math operators, which are defined in this class: OPERATOR_ABSOLUTE OPERATOR_ADD OPERATOR_ADDCONST OPERATOR_DIVIDE OPERATOR_DIVIDECONST OPERATOR_EXP OPERATOR_INVERT OPERATOR_LOG OPERATOR_MULTIPLY OPERATOR_MULTIPLYCONST OPERATOR_SUBTRACT OPERATOR_SUBTRACTCONST

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `bgValues` - Background values to represent values of cells in the empty raster blocks of the input GeoRaster object. The number of elements in the bgValues array must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, (1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterMathOp

          public void rasterMathOp(SdoGeoRaster georaster0,
                                   SdoGeoRaster georaster1,
                                   double[] cropArea,
                                   java.lang.Double constant,
                                   int operartor,
                                   java.lang.String storageParam,
                                   java.sql.Blob[] rasterBlob,
                                   JGeometry[] outArea,
                                   double[] outWindow,
                                   double[] bgValues,
                                   boolean nodata,
                                   java.lang.Double nodataValue)
                            throws java.lang.Exception

      Applies a mathematical operation on all corresponding cells of each layer of one or two input GeoRaster objects and generate a new raster stored in a BLOB. For this method, all pyramids are removed in the resulting GeoRaster object, but masks of the first input GeoRaster object are kept in the resulting GeoRaster object. For the operator parameter, the operators have the following definitions: OPERATOR_ABSOLUTE : if (src\[x\]\[y\]\[b\] \< 0) { dst\[x\]\[y\]\[b\] = -src\[x\]\[y\]\[b\]; } else { dst\[x\]\[y\]\[b\] = src\[x\]\[y\]\[b\]; } OPERATOR_ADD dst\[x\]\[y\]\[b\]=src1\[x\]\[y\]\[b\]+src2\[x\]\[y\]\[b\] OPERATOR_ADDCONST dst\[x\]\[y\]\[b\]=src\[x\]\[y\]\[b\] +constant --constant is the third parameter OPERATOR_DIVIDE dst\[x\]\[y\]\[b\]=src1\[x\]\[y\]\[b\]/src2\[x\]\[y\]\[b\] OPERATOR_DIVIDECONST dst\[x\]\[y\]\[b\]=src\[x\]\[y\]\[b\]/constant --constant is the third parameter OPERATOR_EXP dst\[x\]\[y\]\[b\]=exp(src\[x\]\[y\]\[b\]) OPERATOR_INVERT : Inverts the cell values: dst\[x\]\[y\]\[b\]=-src\[x\]\[y\]\[b\] OPERATOR_LOG : dst\[x\]\[y\]\[b\]=log(src\[x\]\[y\]\[b\]) OPERATOR_MULTIPLY dst\[x\]\[y\]\[b\]=src1\[x\]\[y\]\[b\]\*src2\[x\]\[y\]\[b\] OPERATOR_MULTIPLYCONST dst\[x\]\[y\]\[b\]=src\[x\]\[y\]\[b\]\*constant --constant is the third parameter OPERATOR_SUBTRACT dst\[x\]\[y\]\[b\]=src1\[x\]\[y\]\[b\]-src2\[x\]\[y\]\[b\] OPERATOR_SUBTRACTCONST dst\[x\]\[y\]\[b\]=src\[x\]\[y\]\[b\]-constant --constant is the third parameter
      Parameters:
      `georaster0` - The left operand.

      `georaster1` - The right operand.

      `cropArea` - crop area definition in cell space by a long array

      `constant` - Constant value for some operators , such as addConst and divConstant.

      `operator` - One of the following math operators, which are defined in this class: OPERATOR_ABSOLUTE OPERATOR_ADD OPERATOR_ADDCONST OPERATOR_DIVIDE OPERATOR_DIVIDECONST OPERATOR_EXP OPERATOR_INVERT OPERATOR_LOG OPERATOR_MULTIPLY OPERATOR_MULTIPLYCONST OPERATOR_SUBTRACT OPERATOR_SUBTRACTCONST

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `bgValues` - Background values to represent values of cells in the empty raster blocks of the input GeoRaster object. The number of elements in the bgValues array must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, (1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterMathOp

          public void rasterMathOp(SdoGeoRaster georaster0,
                                   SdoGeoRaster georaster1,
                                   JGeometry cropArea,
                                   java.lang.Double constant,
                                   int operartor,
                                   java.lang.String storageParam,
                                   SdoGeoRaster outGeoRaster,
                                   double[] bgValues,
                                   boolean nodata,
                                   java.lang.Double nodataValue,
                                   java.lang.String polygonClip,
                                   int parallelDegree)
                            throws java.lang.Exception

      Applies a mathematical operation on all corresponding cells of each layer of one or two input GeoRaster objects. For this method, all pyramids are removed in the resulting GeoRaster object, but masks of the first input GeoRaster object are kept in the resulting GeoRaster object. For the operator parameter, the operators have the following definitions: OPERATOR_ABSOLUTE : if (src\[x\]\[y\]\[b\] \< 0) { dst\[x\]\[y\]\[b\] = -src\[x\]\[y\]\[b\]; } else { dst\[x\]\[y\]\[b\] = src\[x\]\[y\]\[b\]; } OPERATOR_ADD dst\[x\]\[y\]\[b\]=src1\[x\]\[y\]\[b\]+src2\[x\]\[y\]\[b\] OPERATOR_ADDCONST dst\[x\]\[y\]\[b\]=src\[x\]\[y\]\[b\] +constant --constant is the third parameter OPERATOR_DIVIDE dst\[x\]\[y\]\[b\]=src1\[x\]\[y\]\[b\]/src2\[x\]\[y\]\[b\] OPERATOR_DIVIDECONST dst\[x\]\[y\]\[b\]=src\[x\]\[y\]\[b\]/constant --constant is the third parameter OPERATOR_EXP dst\[x\]\[y\]\[b\]=exp(src\[x\]\[y\]\[b\]) OPERATOR_INVERT : Inverts the cell values: dst\[x\]\[y\]\[b\]=-src\[x\]\[y\]\[b\] OPERATOR_LOG : dst\[x\]\[y\]\[b\]=log(src\[x\]\[y\]\[b\]) OPERATOR_MULTIPLY dst\[x\]\[y\]\[b\]=src1\[x\]\[y\]\[b\]\*src2\[x\]\[y\]\[b\] OPERATOR_MULTIPLYCONST dst\[x\]\[y\]\[b\]=src\[x\]\[y\]\[b\]\*constant --constant is the third parameter OPERATOR_SUBTRACT dst\[x\]\[y\]\[b\]=src1\[x\]\[y\]\[b\]-src2\[x\]\[y\]\[b\] OPERATOR_SUBTRACTCONST dst\[x\]\[y\]\[b\]=src\[x\]\[y\]\[b\]-constant --constant is the third parameter
      Parameters:
      `georaster0` - The left operand.

      `georaster1` - The right operand.

      `cropArea` - crop area definition in model space by a JGeometry object

      `constant` - Constant value for some operators , such as addConst and divConstant.

      `operator` - One of the following math operators, which are defined in this class: OPERATOR_ABSOLUTE OPERATOR_ADD OPERATOR_ADDCONST OPERATOR_DIVIDE OPERATOR_DIVIDECONST OPERATOR_EXP OPERATOR_INVERT OPERATOR_LOG OPERATOR_MULTIPLY OPERATOR_MULTIPLYCONST OPERATOR_SUBTRACT OPERATOR_SUBTRACTCONST

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `bgValues` - Background values to represent values of cells in the empty raster blocks of the input GeoRaster object. The number of elements in the bgValues array must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, (1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterMathOp

          public void rasterMathOp(SdoGeoRaster georaster0,
                                   SdoGeoRaster georaster1,
                                   JGeometry cropArea,
                                   java.lang.Double constant,
                                   int operartor,
                                   java.lang.String storageParam,
                                   java.sql.Blob[] rasterBlob,
                                   JGeometry[] outArea,
                                   double[] outWindow,
                                   double[] bgValues,
                                   boolean nodata,
                                   java.lang.Double nodataValue,
                                   java.lang.String polygonClip)
                            throws java.lang.Exception

      Applies a mathematical operation on all corresponding cells of each layer of one or two input GeoRaster objects and create a new raster stored in a BLOB. For this method, all pyramids are removed in the resulting GeoRaster object, but masks of the first input GeoRaster object are kept in the resulting GeoRaster object. For the operator parameter, the operators have the following definitions: OPERATOR_ABSOLUTE : if (src\[x\]\[y\]\[b\] \< 0) { dst\[x\]\[y\]\[b\] = -src\[x\]\[y\]\[b\]; } else { dst\[x\]\[y\]\[b\] = src\[x\]\[y\]\[b\]; } OPERATOR_ADD dst\[x\]\[y\]\[b\]=src1\[x\]\[y\]\[b\]+src2\[x\]\[y\]\[b\] OPERATOR_ADDCONST dst\[x\]\[y\]\[b\]=src\[x\]\[y\]\[b\] +constant --constant is the third parameter OPERATOR_DIVIDE dst\[x\]\[y\]\[b\]=src1\[x\]\[y\]\[b\]/src2\[x\]\[y\]\[b\] OPERATOR_DIVIDECONST dst\[x\]\[y\]\[b\]=src\[x\]\[y\]\[b\]/constant --constant is the third parameter OPERATOR_EXP dst\[x\]\[y\]\[b\]=exp(src\[x\]\[y\]\[b\]) OPERATOR_INVERT : Inverts the cell values: dst\[x\]\[y\]\[b\]=-src\[x\]\[y\]\[b\] OPERATOR_LOG : dst\[x\]\[y\]\[b\]=log(src\[x\]\[y\]\[b\]) OPERATOR_MULTIPLY dst\[x\]\[y\]\[b\]=src1\[x\]\[y\]\[b\]\*src2\[x\]\[y\]\[b\] OPERATOR_MULTIPLYCONST dst\[x\]\[y\]\[b\]=src\[x\]\[y\]\[b\]\*constant --constant is the third parameter OPERATOR_SUBTRACT dst\[x\]\[y\]\[b\]=src1\[x\]\[y\]\[b\]-src2\[x\]\[y\]\[b\] OPERATOR_SUBTRACTCONST dst\[x\]\[y\]\[b\]=src\[x\]\[y\]\[b\]-constant --constant is the third parameter
      Parameters:
      `georaster0` - The left operand.

      `georaster1` - The right operand.

      `cropArea` - crop area definition in model space by a JGeometry object

      `constant` - Constant value for some operators , such as addConst and divConstant.

      `operator` - One of the following math operators, which are defined in this class: OPERATOR_ABSOLUTE OPERATOR_ADD OPERATOR_ADDCONST OPERATOR_DIVIDE OPERATOR_DIVIDECONST OPERATOR_EXP OPERATOR_INVERT OPERATOR_LOG OPERATOR_MULTIPLY OPERATOR_MULTIPLYCONST OPERATOR_SUBTRACT OPERATOR_SUBTRACTCONST

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `bgValues` - Background values to represent values of cells in the empty raster blocks of the input GeoRaster object. The number of elements in the bgValues array must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, (1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterMathOp

          public void rasterMathOp(SdoGeoRaster georaster0,
                                   SdoGeoRaster georaster1,
                                   java.lang.Double constant,
                                   int operartor,
                                   java.lang.String storageParam,
                                   SdoGeoRaster outGeoRaster,
                                   double[] bgValues,
                                   boolean nodata,
                                   java.lang.Double nodataValue,
                                   int parallelDegree)
                            throws java.lang.Exception

      Applies a mathematical operation on all corresponding cells of each layer of one or two input GeoRaster objects. For this method, all pyramids are removed in the resulting GeoRaster object, but masks of the first input GeoRaster object are kept in the resulting GeoRaster object. For the operator parameter, the operators have the following definitions: OPERATOR_ABSOLUTE : if (src\[x\]\[y\]\[b\] \< 0) { dst\[x\]\[y\]\[b\] = -src\[x\]\[y\]\[b\]; } else { dst\[x\]\[y\]\[b\] = src\[x\]\[y\]\[b\]; } OPERATOR_ADD dst\[x\]\[y\]\[b\]=src1\[x\]\[y\]\[b\]+src2\[x\]\[y\]\[b\] OPERATOR_ADDCONST dst\[x\]\[y\]\[b\]=src\[x\]\[y\]\[b\] +constant --constant is the third parameter OPERATOR_DIVIDE dst\[x\]\[y\]\[b\]=src1\[x\]\[y\]\[b\]/src2\[x\]\[y\]\[b\] OPERATOR_DIVIDECONST dst\[x\]\[y\]\[b\]=src\[x\]\[y\]\[b\]/constant --constant is the third parameter OPERATOR_EXP dst\[x\]\[y\]\[b\]=exp(src\[x\]\[y\]\[b\]) OPERATOR_INVERT : Inverts the cell values: dst\[x\]\[y\]\[b\]=-src\[x\]\[y\]\[b\] OPERATOR_LOG : dst\[x\]\[y\]\[b\]=log(src\[x\]\[y\]\[b\]) OPERATOR_MULTIPLY dst\[x\]\[y\]\[b\]=src1\[x\]\[y\]\[b\]\*src2\[x\]\[y\]\[b\] OPERATOR_MULTIPLYCONST dst\[x\]\[y\]\[b\]=src\[x\]\[y\]\[b\]\*constant --constant is the third parameter OPERATOR_SUBTRACT dst\[x\]\[y\]\[b\]=src1\[x\]\[y\]\[b\]-src2\[x\]\[y\]\[b\] OPERATOR_SUBTRACTCONST dst\[x\]\[y\]\[b\]=src\[x\]\[y\]\[b\]-constant --constant is the third parameter
      Parameters:
      `georaster0` - The left operand.

      `georaster1` - The right operand.

      `constant` - Constant value for some operators , such as addConst and divConstant.

      `operator` - One of the following math operators, which are defined in this class: OPERATOR_ABSOLUTE OPERATOR_ADD OPERATOR_ADDCONST OPERATOR_DIVIDE OPERATOR_DIVIDECONST OPERATOR_EXP OPERATOR_INVERT OPERATOR_LOG OPERATOR_MULTIPLY OPERATOR_MULTIPLYCONST OPERATOR_SUBTRACT OPERATOR_SUBTRACTCONST

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `bgValues` - Background values to represent values of cells in the empty raster blocks of the input GeoRaster object. The number of elements in the bgValues array must be either one (same filling value used for all bands) or the band dimension size (a different filling value for each band, respectively). For example, (1,5,10) fills the first band with 1, the second band with 5, and the third band with 10. The default bgValues are zero (0). The filling values must be valid cell values as specified by the target cell depth background values for filling sparse data.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterUpdate

          public void rasterUpdate(SdoGeoRaster inGeoRaster,
                                   java.lang.Integer pyramidLevel,
                                   double[] targetArea,
                                   java.lang.String[] conditions,
                                   java.lang.String[][] vals,
                                   double[] bgValues,
                                   boolean nodata,
                                   int parallelDegree)
                            throws java.lang.Exception

      Updates all cells for which the conditions specification is true, using values calculated from the vals specification. Because this procedure overwrites data in the input GeoRaster object, you should make a copy of the original GeoRaster object and use this procedure on the copied object. After you are satisfied with the result of this procedure, you can discard the original GeoRaster object if you wish. This procedure selects cells from the specified GeoRaster object based on booleanExpr strings specified in the conditions parameter, and updates corresponding cell values by calculating arithmeticExpr expression strings specified in the vals parameter. For example, if: conditions = SDO_STRING2_ARRAY('{0}=48','{0}=108') vals = SDO_STRING2_ARRAYSET(SDO_STRING2_ARRAY('123','54','89'),SDO_STRING2_ARRAY('98','56','123')) Then: For all cells whose first layer value equals 48, their first, second, and third layer values are set to 123,54,89, respectively. For all cells whose first layer value equals 108, their first, second, and third layer values are set to 98,56,123, respectively. For more information, see Section 4.1, "Raster Algebra Language". If you specify parallelParam, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If you do not specify this parameter, you can roll back all changes.
      Parameters:
      `geoRaster` - GeoRaster object that is used for input and for output (updating based on specified conditions).

      `pyramidLevel` - Pyramid level to be updated. If this parameter is null, all pyramid levels are updated.

      `targetArea` - Target area definition in cell space by a long array

      `conditions` - An array of booleanExpr expression strings used to select cells.

      `vals` - An array or arrays of arithmeticExpr expressions, with the outer array corresponding to each condition and the inner array corresponding to each layer.

      `bgValues` - Background value array

      `nodata` - The TRUE specifies that any NODATA cells in the GeoRaster object are not to be updated. The FALSE (the default) causes cells with NODATA values to be considered as regular cells and thus eligible for updating. NODATA values and value ranges are discussed in Section 1.10.of Spatial GeoRaster Developer's Guide.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterUpdate

          public void rasterUpdate(SdoGeoRaster inGeoRaster,
                                   java.lang.Integer pyramidLevel,
                                   JGeometry targetArea,
                                   java.lang.String[] conditions,
                                   java.lang.String[][] vals,
                                   double[] bgValues,
                                   boolean nodata,
                                   java.lang.String polygonClip,
                                   int parallelDegree)
                            throws java.lang.Exception

      Updates all cells for which the conditions specification is true, using values calculated from the vals specification. Because this procedure overwrites data in the input GeoRaster object, you should make a copy of the original GeoRaster object and use this procedure on the copied object. After you are satisfied with the result of this procedure, you can discard the original GeoRaster object if you wish. This procedure selects cells from the specified GeoRaster object based on booleanExpr strings specified in the conditions parameter, and updates corresponding cell values by calculating arithmeticExpr expression strings specified in the vals parameter. For example, if: conditions = SDO_STRING2_ARRAY('{0}=48','{0}=108') vals = SDO_STRING2_ARRAYSET(SDO_STRING2_ARRAY('123','54','89'),SDO_STRING2_ARRAY('98','56','123')) Then: For all cells whose first layer value equals 48, their first, second, and third layer values are set to 123,54,89, respectively. For all cells whose first layer value equals 108, their first, second, and third layer values are set to 98,56,123, respectively. For more information, see Section 4.1, "Raster Algebra Language". If you specify parallelParam, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If you do not specify this parameter, you can roll back all changes.
      Parameters:
      `geoRaster` - GeoRaster object that is used for input and for output (updating based on specified conditions).

      `pyramidLevel` - Pyramid level to be updated. If this parameter is null, all pyramid levels are updated.

      `targetArea` - crop area definition in model space by a JGeometry object

      `conditions` - An array of booleanExpr expression strings used to select cells.

      `vals` - An array or arrays of arithmeticExpr expressions, with the outer array corresponding to each condition and the inner array corresponding to each layer.

      `bgValues` - Background value array

      `nodata` - The TRUE specifies that any NODATA cells in the GeoRaster object are not to be updated. The FALSE (the default) causes cells with NODATA values to be considered as regular cells and thus eligible for updating. NODATA values and value ranges are discussed in Section 1.10.of Spatial GeoRaster Developer's Guide.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### rasterUpdate

          public void rasterUpdate(SdoGeoRaster inGeoRaster,
                                   java.lang.Integer pyramidLevel,
                                   java.lang.String[] conditions,
                                   java.lang.String[][] vals,
                                   double[] bgValues,
                                   boolean nodata,
                                   int parallelDegree)
                            throws java.lang.Exception

      Updates all cells for which the conditions specification is true, using values calculated from the vals specification. Because this procedure overwrites data in the input GeoRaster object, you should make a copy of the original GeoRaster object and use this procedure on the copied object. After you are satisfied with the result of this procedure, you can discard the original GeoRaster object if you wish. This procedure selects cells from the specified GeoRaster object based on booleanExpr strings specified in the conditions parameter, and updates corresponding cell values by calculating arithmeticExpr expression strings specified in the vals parameter. For example, if: conditions = SDO_STRING2_ARRAY('{0}=48','{0}=108') vals = SDO_STRING2_ARRAYSET(SDO_STRING2_ARRAY('123','54','89'),SDO_STRING2_ARRAY('98','56','123')) Then: For all cells whose first layer value equals 48, their first, second, and third layer values are set to 123,54,89, respectively. For all cells whose first layer value equals 108, their first, second, and third layer values are set to 98,56,123, respectively. For more information, see Section 4.1, "Raster Algebra Language". If you specify parallelParam, some execution units of the procedure run as autonomous transactions, which means that some changes are committed while the procedure is running and therefore you cannot roll back those changes. If you do not specify this parameter, you can roll back all changes.
      Parameters:
      `geoRaster` - GeoRaster object that is used for input and for output (updating based on specified conditions).

      `pyramidLevel` - Pyramid level to be updated. If this parameter is null, all pyramid levels are updated.

      `conditions` - An array of booleanExpr expression strings used to select cells.

      `vals` - An array or arrays of arithmeticExpr expressions, with the outer array corresponding to each condition and the inner array corresponding to each layer.

      `bgValues` - Background value array

      `nodata` - The TRUE specifies that any NODATA cells in the GeoRaster object are not to be updated. The FALSE (the default) causes cells with NODATA values to be considered as regular cells and thus eligible for updating. NODATA values and value ranges are discussed in Section 1.10.of Spatial GeoRaster Developer's Guide.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### diff

          public void diff(SdoGeoRaster georaster1,
                           SdoGeoRaster georaster2,
                           double[] cropArea,
                           java.lang.String storageParam,
                           SdoGeoRaster outGeoRaster,
                           boolean nodata,
                           java.lang.Double nodataValue,
                           int parallelDegree)
                    throws java.lang.Exception

      Generates a new GeoRaster object by performing the diff operation (explained in the Usage Notes).
      Parameters:
      `georaster1` - First input GeoRaster object.

      `georaster2` - Second input GeoRaster object.

      `cropArea` - Crop area definition,the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### diff

          public void diff(SdoGeoRaster georaster1,
                           SdoGeoRaster georaster2,
                           double[] cropArea,
                           java.lang.String storageParam,
                           java.sql.Blob[] rasterBlob,
                           JGeometry[] outArea,
                           double[] outWindow,
                           boolean nodata,
                           java.lang.Double nodataValue)
                    throws java.lang.Exception

      Generates a new raster stored in a BLOB by performing the diff operation (explained in the Usage Notes).
      Parameters:
      `georaster1` - First input GeoRaster object.

      `georaster2` - Second input GeoRaster object.

      `cropArea` - Crop area definition,the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### diff

          public void diff(SdoGeoRaster georaster1,
                           SdoGeoRaster georaster2,
                           JGeometry cropArea,
                           java.lang.String storageParam,
                           SdoGeoRaster outGeoRaster,
                           boolean nodata,
                           java.lang.Double nodataValue,
                           boolean polygonClip,
                           int parallelDegree)
                    throws java.lang.Exception

      Generates a new GeoRaster object by performing the diff operation (explained in the Usage Notes).
      Parameters:
      `georaster1` - First input GeoRaster object.

      `georaster2` - Second input GeoRaster object.

      `cropArea` - Crop area definition

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `polygonClip` - Ignored if cropArea is null. Otherwise, the string TRUE causes the cropArea value to be used to crop the data; the string FALSE or a null value causes the MBR of cropArea to be used to crop the output image.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### diff

          public void diff(SdoGeoRaster georaster1,
                           SdoGeoRaster georaster2,
                           JGeometry cropArea,
                           java.lang.String storageParam,
                           java.sql.Blob[] rasterBlob,
                           JGeometry[] outArea,
                           double[] outWindow,
                           boolean nodata,
                           java.lang.Double nodataValue,
                           boolean polygonClip)
                    throws java.lang.Exception

      Generates a new raster stored in a BLOB by performing the diff operation (explained in the Usage Notes).
      Parameters:
      `georaster1` - First input GeoRaster object.

      `georaster2` - Second input GeoRaster object.

      `cropArea` - Crop area definition

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `polygonClip` - Ignored if cropArea is null. Otherwise, the string TRUE causes the cropArea value to be used to crop the data; the string FALSE or a null value causes the MBR of cropArea to be used to crop the output image.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### over

          public void over(SdoGeoRaster georaster1,
                           SdoGeoRaster georaster2,
                           double[] cropArea,
                           java.lang.String storageParam,
                           SdoGeoRaster outGeoRaster,
                           boolean nodata,
                           java.lang.Double nodataValue,
                           int parallelDegree)
                    throws java.lang.Exception

      Generates a new GeoRaster object by performing the over operation (explained in the Usage Notes).
      Parameters:
      `georaster1` - First input GeoRaster object.

      `georaster2` - Second input GeoRaster object.

      `cropArea` - Crop area definition,the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### over

          public void over(SdoGeoRaster georaster1,
                           SdoGeoRaster georaster2,
                           double[] cropArea,
                           java.lang.String storageParam,
                           java.sql.Blob[] rasterBlob,
                           JGeometry[] outArea,
                           double[] outWindow,
                           boolean nodata,
                           java.lang.Double nodataValue)
                    throws java.lang.Exception

      Generates a new raster stored in a BLOB by performing the over operation (explained in the Usage Notes).
      Parameters:
      `georaster1` - First input GeoRaster object.

      `georaster2` - Second input GeoRaster object.

      `cropArea` - Crop area definition,the parameter identifies the upper-left (row, column) and lower-right (row, column) coordinates of a rectangular window, and raster space is assumed.

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### over

          public void over(SdoGeoRaster georaster1,
                           SdoGeoRaster georaster2,
                           JGeometry cropArea,
                           java.lang.String storageParam,
                           SdoGeoRaster outGeoRaster,
                           boolean nodata,
                           java.lang.Double nodataValue,
                           boolean polygonClip,
                           int parallelDegree)
                    throws java.lang.Exception

      Generates a new GeoRaster object by performing the over operation (explained in the Usage Notes).
      Parameters:
      `georaster1` - First input GeoRaster object.

      `georaster2` - Second input GeoRaster object.

      `cropArea` - Crop area definition

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `polygonClip` - Ignored if cropArea is null. Otherwise, the string TRUE causes the cropArea value to be used to crop the data; the string FALSE or a null value causes the MBR of cropArea to be used to crop the output image.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### over

          public void over(SdoGeoRaster georaster1,
                           SdoGeoRaster georaster2,
                           JGeometry cropArea,
                           java.lang.String storageParam,
                           java.sql.Blob[] rasterBlob,
                           JGeometry[] outArea,
                           double[] outWindow,
                           boolean nodata,
                           java.lang.Double nodataValue,
                           boolean polygonClip)
                    throws java.lang.Exception

      Generates a new raster stored in a BLOB by performing the over operation (explained in the Usage Notes).
      Parameters:
      `georaster1` - First input GeoRaster object.

      `georaster2` - Second input GeoRaster object.

      `cropArea` - Crop area definition

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `polygonClip` - Ignored if cropArea is null. Otherwise, the string TRUE causes the cropArea value to be used to crop the data; the string FALSE or a null value causes the MBR of cropArea to be used to crop the output image.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### stack

          public void stack(SdoGeoRaster[] inGeoRasters,
                            double[] cropArea,
                            int[] layerList,
                            java.lang.String method,
                            java.lang.String storageParam,
                            SdoGeoRaster outGeoRaster,
                            boolean nodata,
                            java.lang.Double nodataValue,
                            int parallelDegree)
                     throws java.lang.Exception

      Generates a single-layer GeoRaster object whose cell values are a local statistics value of a list of layers of the input GeoRaster array.The input layers are specified by the layerList parameter, and the statistics method is specified by the method parameter.
      Parameters:
      `inGeoRasters` - An array of SdoGeoRaster objects.

      `cropArea` - Crop area definition

      `layerList` - A number array to specify which bands of the input GeoRaster objects are used to compute statistics value for output. For example, if georArray specifies three GeoRaster objects geor1,geor2,geor3, which have 2,3,4 bands respectively, a layer list {0,3,7} is used to specify three bands as follows: The first band of the first GeoRaster object geor1 The second band of the second GeoRaster object geor2 The third band of the third GeoRaster object geor3

      `method` - A string to specify what local statistics value should be returned. It should be one of the following values: max, min, median, mean, std, sum, minority, majority, diversity.

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### stack

          public void stack(SdoGeoRaster[] inGeoRasters,
                            double[] cropArea,
                            int[] layerList,
                            java.lang.String method,
                            java.lang.String storageParam,
                            java.sql.Blob[] rasterBlob,
                            JGeometry[] outArea,
                            double[] outWindow,
                            boolean nodata,
                            java.lang.Double nodataValue)
                     throws java.lang.Exception

      Generates a single-layer raster stored in a BLOB whose cell values are a local statistics value of a list of layers of the input GeoRaster array.The input layers are specified by the layerList parameter, and the statistics method is specified by the method parameter.
      Parameters:
      `inGeoRasters` - An array of SdoGeoRaster objects.

      `cropArea` - Crop area definition

      `layerList` - A number array to specify which bands of the input GeoRaster objects are used to compute statistics value for output. For example, if georArray specifies three GeoRaster objects geor1,geor2,geor3, which have 2,3,4 bands respectively, a layer list {0,3,7} is used to specify three bands as follows: The first band of the first GeoRaster object geor1 The second band of the second GeoRaster object geor2 The third band of the third GeoRaster object geor3

      `method` - A string to specify what local statistics value should be returned. It should be one of the following values: max, min, median, mean, std, sum, minority, majority, diversity.

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### stack

          public void stack(SdoGeoRaster[] inGeoRasters,
                            JGeometry cropArea,
                            int[] layerList,
                            java.lang.String method,
                            java.lang.String storageParam,
                            SdoGeoRaster outGeoRaster,
                            boolean nodata,
                            java.lang.Double nodataValue,
                            boolean polygonClip,
                            int parallelDegree)
                     throws java.lang.Exception

      Generates a single-layer GeoRaster object whose cell values are a local statistics value of a list of layers of the input GeoRaster array.The input layers are specified by the layerList parameter, and the statistics method is specified by the method parameter.
      Parameters:
      `inGeoRasters` - An array of SdoGeoRaster objects.

      `cropArea` - Crop area definition

      `layerList` - A number array to specify which bands of the input GeoRaster objects are used to compute statistics value for output. For example, if georArray specifies three GeoRaster objects geor1,geor2,geor3, which have 2,3,4 bands respectively, a layer list {0,3,7} is used to specify three bands as follows: The first band of the first GeoRaster object geor1 The second band of the second GeoRaster object geor2 The third band of the third GeoRaster object geor3

      `method` - A string to specify what local statistics value should be returned. It should be one of the following values: max, min, median, mean, std, sum, minority, majority, diversity.

      `storageParam` - A string specifying storage parameters

      `outGeoRaster` - Output GeoRaster object.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `polygonClip` - Ignored if cropArea is null. Otherwise, the string TRUE causes the cropArea value to be used to crop the data; the string FALSE or a null value causes the MBR of cropArea to be used to crop the output image.

      `parallelDegree` - Specifies the degree of parallelism for the operation. If \>1. The database optimizer uses the degree of parallelism specified by this parameter. If \<=1, then there is no parallel processing. (for more information,see section 1.13 of spatial georaster developer's guide, "parallel processing in georaster"). if paralleldegree\>1 then it means that you cannot roll back the results of this procedure.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### stack

          public void stack(SdoGeoRaster[] inGeoRasters,
                            JGeometry cropArea,
                            int[] layerList,
                            java.lang.String method,
                            java.lang.String storageParam,
                            java.sql.Blob[] rasterBlob,
                            JGeometry[] outArea,
                            double[] outWindow,
                            boolean nodata,
                            java.lang.Double nodataValue,
                            boolean polygonClip)
                     throws java.lang.Exception

      Generates a single-layer raster stored in a BLOB whose cell values are a local statistics value of a list of layers of the input GeoRaster array.The input layers are specified by the layerList parameter, and the statistics method is specified by the method parameter.
      Parameters:
      `inGeoRasters` - An array of SdoGeoRaster objects.

      `cropArea` - Crop area definition

      `layerList` - A number array to specify which bands of the input GeoRaster objects are used to compute statistics value for output. For example, if georArray specifies three GeoRaster objects geor1,geor2,geor3, which have 2,3,4 bands respectively, a layer list {0,3,7} is used to specify three bands as follows: The first band of the first GeoRaster object geor1 The second band of the second GeoRaster object geor2 The third band of the third GeoRaster object geor3

      `method` - A string to specify what local statistics value should be returned. It should be one of the following values: max, min, median, mean, std, sum, minority, majority, diversity.

      `storageParam` - A string specifying storage parameters

      `rasterBlob` - The BLOB to hold the output reflecting the results of the operation.

      `outArea` - An JGeometry object containing the MBR (minimum bounding rectangle) in the model coordinate system of the resulting object.

      `outWindow` - An array to hold the the coordinates of the upper-left and lower-right corners of the output window in the cell space.

      `nodata` - The string TRUE specifies to keep the original values for any NODATA cells in the GeoRaster object. The string FALSE (the default) causes cells with NODATA values to be considered as regular data. NODATA values and value ranges are discussed in Section 1.10 of Spatial GeoRaster Developer's Guide.

      `nodataValue` - The value used to set NODATA cells if the nodata parameter value is the string TRUE.

      `polygonClip` - Ignored if cropArea is null. Otherwise, the string TRUE causes the cropArea value to be used to crop the data; the string FALSE or a null value causes the MBR of cropArea to be used to crop the output image.

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

- [Prev Class](SdoGeorPKG.SdoGeorGCPRefType.md)
- [Next Class](SdoGeorUtlPKG.md)

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
