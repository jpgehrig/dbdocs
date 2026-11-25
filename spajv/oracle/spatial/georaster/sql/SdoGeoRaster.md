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

- [Prev Class](SdoGeorAggrPKG.md)
- [Next Class](SdoGeorIpPKG.md)

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

## Class SdoGeoRaster

- java.lang.Object

- - oracle.spatial.georaster.sql.SdoGeoRaster

<!-- -->

-

  ------------------------------------------------------------------------



      public class SdoGeoRaster
      extends java.lang.Object

  SdoGeoRaster is a Java class which contains a pair of rasterID and rasterDataTable information. Combined with a connection (a database), SdoGeoRaster can uniquely identify a GeoRaster object in the target database.
  SdoGeoRaster can be constructed from a STRUCT object.

          public SdoGeoRaster(STRUCT georaster) throws Exception

       or from a pair of rasterID and rasterDataTable.

          public SdoGeoRaster(String rasterDataTable, NUMBER rasterID)

       SdoGeoRaster can also be constructed from a JGeoRaster object:

          public SdoGeoRaster(JGeoRaster jeor)


  Compared with JGeoRaster object, SdoGeoRaster is a lightweight Java mapping of a GeoRaster object, because it only contains a pair of rasterID and rasterDataTable information without any other overhead; instead, when a JGeoRaster object is constructed, it needs to fetch and parse a GeoRaster metadata XML string, construct internal metadata objects structure, and initialize some necessary attributes for later data and image processing.

  SdoGeoRaster is usually used with class SdoGeorPKG to wrap the GeoRaster PL/SQL API on the Java side. For example:

           public void changeFormatCopy(SdoGeoRaster source,String storageParam,SdoGeoRaster target,double[] bgValues) throws Exception


<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                              |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `SdoGeoRaster``(java.lang.String rasterDataTable, NUMBER rasterID)`<br>Constructs an `SdoGeoRaster` object using the given rasterDataTable and rasterID. |
    | `SdoGeoRaster``(STRUCT georaster)`<br>Constructs an `SdoGeoRaster` object using the given STRUCT.                                                        |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                  |
    |--------------------|-------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getRasterDataTable``()`<br>Returns the raster data table where the current GeoRaster object is stored.                 |
    | `NUMBER`           | `getRasterID``()`<br>Returns the raster ID assigned to the current GeoRaster object.                                    |
    | `void`             | `setRasterDataTable``(java.lang.String rasterDataTable)`<br>Sets the raster data table of the current GeoRaster object. |
    | `void`             | `setRasterID``(NUMBER rasterID)`<br>Sets the raster ID of the current GeoRaster object.                                 |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SdoGeoRaster

          public SdoGeoRaster(STRUCT georaster)
                       throws java.lang.Exception

      Constructs an `SdoGeoRaster` object using the given STRUCT.
      Parameters:
      `georaster` - a STRUCT object, which is used to initiate the SdoGeoRaster object

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### SdoGeoRaster

          public SdoGeoRaster(java.lang.String rasterDataTable,
                              NUMBER rasterID)

      Constructs an `SdoGeoRaster` object using the given rasterDataTable and rasterID.
      Parameters:
      `rasterDataTable` - raster data table

      `rasterID` - raster ID number

  <!-- -->

  - ### Method Detail

    - #### getRasterDataTable

          public java.lang.String getRasterDataTable()

      Returns the raster data table where the current GeoRaster object is stored.
      Returns:
      the raster data table where the current GeoRaster object is stored.

    <!-- -->

    - #### getRasterID

          public NUMBER getRasterID()

      Returns the raster ID assigned to the current GeoRaster object.
      Returns:
      the raster ID assigned to the current GeoRaster object.

    <!-- -->

    - #### setRasterID

          public void setRasterID(NUMBER rasterID)
                           throws GeoRasterException

      Sets the raster ID of the current GeoRaster object.
      Parameters:
      `rasterID` - the raster ID assigned to the current GeoRaster object

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

    <!-- -->

    - #### setRasterDataTable

          public void setRasterDataTable(java.lang.String rasterDataTable)
                                  throws GeoRasterException

      Sets the raster data table of the current GeoRaster object.
      Parameters:
      `rasterDataTable` - the raster data table where the current GeoRaster object is stored

      Throws:
      [`GeoRasterException`](../GeoRasterException.md)

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

- [Prev Class](SdoGeorAggrPKG.md)
- [Next Class](SdoGeorIpPKG.md)

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
