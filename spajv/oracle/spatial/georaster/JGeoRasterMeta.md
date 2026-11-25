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

- [Prev Class](JGeoRaster.md)
- [Next Class](JGeoRasterVM.md)

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

## Class JGeoRasterMeta

- java.lang.Object

- - oracle.spatial.georaster.JGeoRasterMeta

<!-- -->

-

  ------------------------------------------------------------------------



      public class JGeoRasterMeta
      extends java.lang.Object

  The GeoRaster Java library defines a full set of Java classes to store and represent all metadata of a GeoRaster object. A hierarchical mapping is built between these Java classes and major XML elements defined in the GeoRaster XML schema as below:
                                           JGeoRasterMeta
                                         (georasterMetadata)
                                                  |
            ----------------------------------------------------------------------------------------------
            |            |             |                        |                         |              |
        ObjectInfo   RasterInfo  SpatialReferenceInfo    TemporalReferenceInfo    bandReferenceInfo   LayerInfo
       (objectInfo) (rasterInfo)(spatialReferenceInfo)  (temporalReferenceInfo)  (bandReferenceInfo) (layerInfo)
                                                                                                         |
                                                                                                   --------------
                                                                                                   |             |
                                                                                               SubLayerInfo    Vector of SubLayerInfo
                                                                                              (objectLayer)    (subLayer)


  In these Java classes, all necessary methods are created to allow you to get/set value of each attribute defined in the specific mapped XML element, and through hierarchical structure above, you can easily manipulate all metadata, for example, the following sample code is used to get NODATA value defined in the objectLayer
         ...
         //reading a GeoRaster object from database based on a query
         ResultSet rs = statement.executeQuery("SELECT a.georaster FROM georaster_table a where a.georaster.rasterdatatable='RDT' and a.georaster.rasterid=1");
         STRUCT geor = (oracle.sql.STRUCT) rs.getObject(1);
         //construct a JGeoRaster object
         JGeoRaster geoRaster = new JGeoRaster(geor);
         //get GeoRasterImage instance
         JGeoRasterMeta geoRasterMeta=geoRaster.getMetadataObject();
         //get NODATA value defined in the objectLayer
         Vector nodata=geoRasterMeta.getLayerInfo().getObjectLayer().getNODATAValue();
         ...


  JGeoRasterMeta is a Java class mapped to the XML element georasterMetadata in the Oracle Spatial GeoRaster metadata, and it is the root access point of the whole hierarchical structure above.
  A JGeoRasterMeta object is always associated with a JGeoRaster object; it cannot be constructed directly. When a JGeoRaster is initiated, the metadata XML string will be retrieved from the database server and populated into the JGeoRasterMeta object and other related Java objects. After the JGeoRaster is initiated successfully, the following method defined in the JGeoRaster is used to retrieve an instance of JGeoRasterMeta:

            public JGeoRasterMeta getMetadataObject()


  Inside the JGeoRasterMeta class, all get\*\*\*Info() methods are used to get instances of second level XML elements, but there is possibility that the return value is null, because some second level elements are optional in the XML schema, such as bandReferenceInfo. In this case, if you want to add a missing second level element into metadata, all init\*\*\*Info() methods are designed to construct and add an empty second level element based on default value defined in the XML schema.

  In order to avoid mistaken modification on some critical metadata attributes, which might result in raster data corruption, the following attributes are not allowed to be changed in each second level XML element directly:

              DimensionSize
              CellDepth
              Interleaving
              Blocking
              BlockSize
              PyramidLevel
              PyramidResampling
              Compression


  However, a method init() is defined in the JGeoRasterMeta class, and provides a way to initiate these critical metadata. The init() method actually is a mapping of the server side PL/SQL function createTemplate(), which takes the rasterSpec string to initialize basic metadata.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description     |
    |-------------------|---------------------------|
    | `static short`    | `BANDREFERENCE_INFO`      |
    | `static short`    | `LAYER_INFO`              |
    | `static short`    | `OBJECT_INFO`             |
    | `static short`    | `RASTER_INFO`             |
    | `static short`    | `SOURCE_INFO`             |
    | `static short`    | `SPATIALREFERENCE_INFO`   |
    | `static short`    | `TEMPORALREFERENCE_INFO`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                   | Method and Description                                                                                                                                                                                                                               |
    |-----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object[][]`                              | `display``()`<br>Returns a two-dimensional array to list all metadata information.                                                                                                                                                                   |
    | [`BandReferenceInfo`](BandReferenceInfo.md)         | `getBandReferenceInfo``()`<br>Returns an BandReferenceInfo object, which represents the XML BandReferenceInfo element, contained in the current instance.                                                                                            |
    | `java.lang.String`                                  | `getJSONString``(int component)`<br>Returns an JSON string represented by this GeoRasterMetadata object.                                                                                                                                             |
    | [`LayerInfo`](LayerInfo.md)                         | `getLayerInfo``()`<br>Returns an LayerInfo object, which represents the XML LayerInfo element, contained in the current instance.                                                                                                                    |
    | [`ObjectInfo`](ObjectInfo.md)                       | `getObjectInfo``()`<br>Returns an ObjectInfo object, which represents the XML objectInfo element, contained in the current instance.                                                                                                                 |
    | [`RasterInfo`](RasterInfo.md)                       | `getRasterInfo``()`<br>Returns an RasterInfo object, which represents the XML RasterInfo element, contained in the current instance.                                                                                                                 |
    | `java.lang.String[]`                                | `getSourceInfo``()`<br>Returns an array of string, which represents the XML SourceInfo nodes, contained in the current instance.                                                                                                                     |
    | [`SpatialReferenceInfo`](SpatialReferenceInfo.md)   | `getSpatialReferenceInfo``()`<br>Returns an SpatialReferenceInfo object, which represents the XML SpatialReferenceInfo element, contained in the current instance.                                                                                   |
    | [`TemporalReferenceInfo`](TemporalReferenceInfo.md) | `getTemporalReferenceInfo``()`<br>Returns an TemporalReferenceInfo object, which represents the XML TemporalReferenceInfo element, contained in the current instance.                                                                                |
    | `java.lang.String`                                  | `getXMLString``()`<br>Returns an XML string represented by this GeoRasterMetadata object.                                                                                                                                                            |
    | `boolean`                                           | `hasBitmapMask``(int layerNo)`<br>Returns `true` if the GeoRaster object has a bitmapMask defined in the layer `layerNo`                                                                                                                             |
    | `void`                                              | `init``(int rasterType, java.lang.String rasterSpec)`<br>Initiates a JGeoRasterMeta object based on a general pattern of metadata of a JGeoRaster object.                                                                                            |
    | [`BandReferenceInfo`](BandReferenceInfo.md)         | `initBandReferenceInfo``()`<br>If the current instance does not contain a BandReferenceInfo instance, then an empty BandReferenceInfo is created and added to the current instance, otherwise just return current BandReferenceInfo.                 |
    | [`LayerInfo`](LayerInfo.md)                         | `initLayerInfo``()`<br>If the current instance does not contain a LayerInfo instance, then an empty LayerInfo is created and added to the current instance, otherwise just return current LayerInfo.                                                 |
    | [`ObjectInfo`](ObjectInfo.md)                       | `initObjectInfo``()`<br>If the current instance does not contain an ObjectInfo instance, then an empty ObjectInfo is created and added to the current instance; otherwise, just return the current ObjectInfo.                                       |
    | [`RasterInfo`](RasterInfo.md)                       | `initRasterInfo``()`<br>If the current instance does not contain a RasterInfo instance, then an empty RasterInfo is created and added to the current instance; otherwise, just return the current RasterInfo.                                        |
    | [`SpatialReferenceInfo`](SpatialReferenceInfo.md)   | `initSpatialReferenceInfo``()`<br>If the current instance does not contain a SpatialReferenceInfo instance, then an empty SpatialReferenceInfo is created and added to the current instance, otherwise just return current SpatialReferenceInfo.     |
    | [`TemporalReferenceInfo`](TemporalReferenceInfo.md) | `initTemporalReferenceInfo``()`<br>If the current instance does not contain a TemporalReferenceInfo instance, then an empty TemporalReferenceInfo is created and added to the current instance, otherwise just return current TemporalReferenceInfo. |
    | `void`                                              | `setSourceInfo``(java.lang.String[] sourceInfo)`<br>set sourceInfo by a given array of string                                                                                                                                                        |
    | `oracle.sql.STRUCT`                                 | `storeToDB``()`<br>Deprecated.                                                                                                                                                                                                                       |
    | `java.sql.Struct`                                   | `storeToDBJS``()`<br>Updates server-side metadata by the XML string generated from this class.                                                                                                                                                       |
    | `boolean`                                           | `validate``()`<br>Validates GeoRaster metadata represented by current instance                                                                                                                                                                       |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### OBJECT_INFO

          public static final short OBJECT_INFO

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### RASTER_INFO

          public static final short RASTER_INFO

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SPATIALREFERENCE_INFO

          public static final short SPATIALREFERENCE_INFO

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TEMPORALREFERENCE_INFO

          public static final short TEMPORALREFERENCE_INFO

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### BANDREFERENCE_INFO

          public static final short BANDREFERENCE_INFO

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LAYER_INFO

          public static final short LAYER_INFO

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SOURCE_INFO

          public static final short SOURCE_INFO

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getObjectInfo

          public ObjectInfo getObjectInfo()

      Returns an ObjectInfo object, which represents the XML objectInfo element, contained in the current instance.
      Returns:
      ObjectInfo object, or `null`.

      See Also:
      [`ObjectInfo`](ObjectInfo.md), `initObjectInfo()`

    <!-- -->

    - #### initObjectInfo

          public ObjectInfo initObjectInfo()

      If the current instance does not contain an ObjectInfo instance, then an empty ObjectInfo is created and added to the current instance; otherwise, just return the current ObjectInfo.
      Returns:
      the contained ObjectInfo object.

      See Also:
      [`ObjectInfo`](ObjectInfo.md), `getObjectInfo()`

    <!-- -->

    - #### getRasterInfo

          public RasterInfo getRasterInfo()

      Returns an RasterInfo object, which represents the XML RasterInfo element, contained in the current instance.
      Returns:
      RasterInfo object, or `null`.

      See Also:
      [`RasterInfo`](RasterInfo.md), `initRasterInfo()`

    <!-- -->

    - #### initRasterInfo

          public RasterInfo initRasterInfo()

      If the current instance does not contain a RasterInfo instance, then an empty RasterInfo is created and added to the current instance; otherwise, just return the current RasterInfo.
      Returns:
      the contained RasterInfo object.

      See Also:
      [`RasterInfo`](RasterInfo.md), `getRasterInfo()`

    <!-- -->

    - #### getSpatialReferenceInfo

          public SpatialReferenceInfo getSpatialReferenceInfo()

      Returns an SpatialReferenceInfo object, which represents the XML SpatialReferenceInfo element, contained in the current instance.
      Returns:
      SpatialReferenceInfo object, or `null`.

      See Also:
      [`SpatialReferenceInfo`](SpatialReferenceInfo.md), `initSpatialReferenceInfo()`

    <!-- -->

    - #### initSpatialReferenceInfo

          public SpatialReferenceInfo initSpatialReferenceInfo()

      If the current instance does not contain a SpatialReferenceInfo instance, then an empty SpatialReferenceInfo is created and added to the current instance, otherwise just return current SpatialReferenceInfo.
      Returns:
      the contained SpatialReferenceInfo object.

      See Also:
      [`SpatialReferenceInfo`](SpatialReferenceInfo.md), `getSpatialReferenceInfo()`

    <!-- -->

    - #### getTemporalReferenceInfo

          public TemporalReferenceInfo getTemporalReferenceInfo()

      Returns an TemporalReferenceInfo object, which represents the XML TemporalReferenceInfo element, contained in the current instance.
      Returns:
      TemporalReferenceInfo object, or `null`.

      See Also:
      [`TemporalReferenceInfo`](TemporalReferenceInfo.md), `initTemporalReferenceInfo()`

    <!-- -->

    - #### initTemporalReferenceInfo

          public TemporalReferenceInfo initTemporalReferenceInfo()

      If the current instance does not contain a TemporalReferenceInfo instance, then an empty TemporalReferenceInfo is created and added to the current instance, otherwise just return current TemporalReferenceInfo.
      Returns:
      the contained TemporalReferenceInfo object.

      See Also:
      [`TemporalReferenceInfo`](TemporalReferenceInfo.md), `getTemporalReferenceInfo()`

    <!-- -->

    - #### getBandReferenceInfo

          public BandReferenceInfo getBandReferenceInfo()

      Returns an BandReferenceInfo object, which represents the XML BandReferenceInfo element, contained in the current instance.
      Returns:
      BandReferenceInfo object, or `null`.

      See Also:
      [`BandReferenceInfo`](BandReferenceInfo.md), `initBandReferenceInfo()`

    <!-- -->

    - #### initBandReferenceInfo

          public BandReferenceInfo initBandReferenceInfo()

      If the current instance does not contain a BandReferenceInfo instance, then an empty BandReferenceInfo is created and added to the current instance, otherwise just return current BandReferenceInfo.
      Returns:
      the contained TemporalReferenceInfo object.

      See Also:
      [`BandReferenceInfo`](BandReferenceInfo.md), `getBandReferenceInfo()`

    <!-- -->

    - #### getLayerInfo

          public LayerInfo getLayerInfo()

      Returns an LayerInfo object, which represents the XML LayerInfo element, contained in the current instance.
      Returns:
      LayerInfo object, or `null`.

      See Also:
      [`LayerInfo`](LayerInfo.md), `initLayerInfo()`

    <!-- -->

    - #### initLayerInfo

          public LayerInfo initLayerInfo()

      If the current instance does not contain a LayerInfo instance, then an empty LayerInfo is created and added to the current instance, otherwise just return current LayerInfo.
      Returns:
      the contained LayerInfo object.

      See Also:
      [`LayerInfo`](LayerInfo.md), `getLayerInfo()`

    <!-- -->

    - #### getSourceInfo

          public java.lang.String[] getSourceInfo()

      Returns an array of string, which represents the XML SourceInfo nodes, contained in the current instance.
      Returns:
      array of sourceInfo string, or `null`.

      See Also:
      `setSourceInfo(java.lang.String[])`

    <!-- -->

    - #### setSourceInfo

          public void setSourceInfo(java.lang.String[] sourceInfo)

      set sourceInfo by a given array of string
      Parameters:
      `sourceInfo` - a array of string, which represents sourceInfo.

      See Also:
      `getSourceInfo()`

    <!-- -->

    - #### hasBitmapMask

          public boolean hasBitmapMask(int layerNo)

      Returns `true` if the GeoRaster object has a bitmapMask defined in the layer `layerNo`
      Parameters:
      `layerNo` - a string, which represents layer number.

      Returns:
      true, or `false`.

    <!-- -->

    - #### validate

          public boolean validate()
                           throws java.lang.Exception

      Validates GeoRaster metadata represented by current instance
      Returns:
      true or false to indicate if metadata is valid.

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getJSONString

          public java.lang.String getJSONString(int component)
                                         throws GeoRasterException

      Returns an JSON string represented by this GeoRasterMetadata object.
      Returns:
      a GeoRaster metadata JSON string.

      Throws:
      [`GeoRasterException`](GeoRasterException.md)

    <!-- -->

    - #### getXMLString

          public java.lang.String getXMLString()
                                        throws GeoRasterException

      Returns an XML string represented by this GeoRasterMetadata object.
      Returns:
      a GeoRaster metadata XML string.

      Throws:
      [`GeoRasterException`](GeoRasterException.md)

    <!-- -->

    - #### init

          public void init(int rasterType,
                           java.lang.String rasterSpec)
                    throws GeoRasterException

      Initiates a JGeoRasterMeta object based on a general pattern of metadata of a JGeoRaster object.
      Parameters:
      `rasterType` - a 5-digit rasterType attribute value

      `rasterSpec` - a string with raster specification parameters. The rasterSpec parameter must be a string that contains one or more of the following keyword-value pairs:

      dimSize (for example, dimSize=(256,256,3)): Specifies the row, column, and band dimension sizes. This keyword must be specified and must be consistent with the rasterType parameter.

      ultCoord (for example, ultCoord=(0,0,0)): Specifies the upper-left coordinate integer values for the GeoRaster object. The default value is 0 for all the dimensions. The value for the band dimension must be 0.

      cellDepth (for example, cellDepth=8BIT_S): Specifies the cell depth of the GeoRaster object. Must be one of the following values (with \_U indicating unsigned and \_S indicating signed): 1BIT, 2BIT, 4BIT, 8BIT_U, 8BIT_S, 16BIT_U, 16BIT_S, 32BIT_U, 32BIT_S, 32BIT_REAL, or 64BIT_REAL. The default value is 8BIT_U.

      interleaving (for example, interleaving=BIP): Specifies the interleaving type. Must be one of the following values: BSQ, BIL, or BIP. The default value is BSQ.

      blocking (for example, blocking=TRUE): Specified whether the GeoRaster object is blocked. Must be either TRUE or FALSE. The default value is FALSE if blocksize is not specified.

      blocksize (for example, blocksize=(128,128,3)): Specifies the block size for each dimension of the GeoRaster object. The values must be non-negative integers. A zero block size value means the corresponding dimension size is the real value. Is blocking is set to TRUE but blocksize is not specified, the GeoRaster object's blocksize is (256,256,B), where B is the band dimension size.

      rLevel (for example, rLevel=2): Specifies the maximum pyramid reduction level. Must be a positive integer. If you specify this keyword, the pyramid type is set to DECREASE in the metadata; otherwise the pyramid type is set to NONE.

      resampling (for example, resampling=NN): Specifies the resampling method. Must be one of the following: NN (value of the nearest neighbor cell in the original GeoRaster object), BILINEAR (distance-weighted average of the 4 nearest cells in the original GeoRaster object), AVERAGE4 (simple average of the 4 nearest cells in the original GeoRaster object), AVERAGE16 (simple average of the 16 nearest cells in the original GeoRaster object), CUBIC (cubic convolution of the 16 nearest cells in the original GeoRaster object). This keyword is ignored if rLevel is not set.

      compression (for example, compression=JPEG-F): Specifies the compression type of the GeoRaster object. Must be one of the following: NONE, DEFLATE or JPEG-F. The default value is NONE.

      quality (for example, quality=75): Specifies the JPEG compression quality, which is the degree of lossiness caused by the compression. Must be an integer from 0 (lowest quality) through 100 (highest quality). This keyword is ignored when the compression keyword is not specified or is not set to one of the JPEG types.

      Throws:
      [`GeoRasterException`](GeoRasterException.md)

    <!-- -->

    - #### storeToDB

          @Deprecated
          public oracle.sql.STRUCT storeToDB()
                                                   throws java.lang.Exception

      Deprecated. 
      Updates server-side metadata by the XML string generated from this class.
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### storeToDBJS

          public java.sql.Struct storeToDBJS()
                                      throws java.lang.Exception

      Updates server-side metadata by the XML string generated from this class.
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### display

          public java.lang.Object[][] display()

      Returns a two-dimensional array to list all metadata information.
      Returns:
      a two-dimensional array.

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

- [Prev Class](JGeoRaster.md)
- [Next Class](JGeoRasterVM.md)

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
