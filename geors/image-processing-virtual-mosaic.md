## 6  Image Processing and Virtual Mosaic

This chapter describes advanced image processing capabilities, including GCP georeferencing, reprojection, rectification, orthorectification, warping, image scaling, stretching, filtering, masking, segmentation, NDVI computation, Tasseled Cap Transformation, image appending, bands merging, and large-scale advanced image mosaicking.

This chapter also describes the concept and application of virtual mosaic within the context of a large-scale image database and on-the-fly spatial queries over it.

The operations in this chapter are most commonly used to process geospatial images, particularly raw satellite imagery and airborne photographs. However, those operations, just like the GeoRaster raster algebra, apply to all raster data types.

This chapter contains the following major sections.

- Advanced Georeferencing
  In addition to spatial referencing capability, advanced georeferencing capabilities are available.
- Image Reprojection
  Image reprojection is the process of transforming an image from one SRS (spatial reference system, or coordinate system) to another.
- Image Rectification
  Most raster data originating from remote sensors above the ground is usually subject to distortion caused by the terrain, the view angles of the instrument, and the irregular shape of the Earth. Image rectification as explained in this section is the process of transforming the images to reduce some of that distortion.
- Image Orthorectification
  Orthorectification is a rectification transformation process where information about the elevation, the terrain, and the shape of the Earth is used to improve the quality of the output rectified image. Oracle GeoRaster supports single image orthorectification with average height value or DEM.
- Image Warping
  Image warping transforms an input GeoRaster object to an output GeoRaster object using the spatial reference information from a specified SDO_GEOR_SRS object.
- Image Affine Transformation and Scaling
  Affine transformation is the process of using geometric transformations of translation, scaling, rotation, shearing, and reflection on an image to produce another image.
- Image Stretching, Normalization, Equalization, Histogram Matching, and Dodging
  The color and contrast of images can be enhanced to improve their visual quality. The SDO_GEOR_IP package (“IP” for image processing) provides a set of subprograms for image enhancement, including performing image stretching, image normalization, image equalization, histogram matching, and image dodging.
- Image Filtering
  Image filtering is the process of applying a convolution filter on an image to achieve a specific purpose. For example, applying a low-pass filter on an image can smooth and reduce noise in an image, while applying a high-pass filter on an image can enhance the details of the image or even detect the edges inside the image.
- Image Segmentation
  Segmentation is a simple type of classification algorithm, and can be useful in classifying certain types of images into larger ground feature categories, such as land, cloud, water, or snow.
- Image Pyramiding: Parallel Generation and Partial Update
  Image pyramiding is one of the most commonly used processes in building large-scale image databases.
- Bitmap Pyramiding
  Bitmap pyramiding can produce high-quality pyramids in certain cases where traditional pyramiding is not adequate.
- Vegetation Index Computation
  In remote sensing, the Normalized Difference Vegetation Index (NDVI) is a widely used vegetation index, enabling users to quickly identify vegetated areas and monitor the growth and "condition" of plants.
- Tasseled Cap Transformation
  Tasseled Cap Transformation (TCT) is a useful tool for analyzing physical ground features using remotely sensed imagery.
- Image Masking
  To perform image masking, an application can query the GeoRaster database for bitmap masks, retrieve the desired bitmap mask or masks, and apply the masking operation on the target GeoRaster object for the purpose of displaying the object or performing some other processing.
- Band Merging
  For image classification, time series analysis, and raster GIS modeling, multiple bands or layers of different GeoRaster objects may need to be merged into a single GeoRaster object.
- Image Appending
  You can append one image to another image when the two images have the same number of bands.
- Large-Scale Image Mosaicking
  A large geospatial area typically consists of many smaller aerial photographs or satellite images. Large-scale image mosaicking can stitch these small geospatial images into one large image to get a better view of the whole spatial area.
- Virtual Mosaic
  A virtual mosaic treats a set of GeoRaster images as one large virtually mosaicked image.
- Image Serving
  Serving of image and raster data to clients or applications is supported through many features of the GeoRaster PL/SQL and Java APIs.

### 6.1 Advanced Georeferencing

In addition to spatial referencing capability, advanced georeferencing capabilities are available.

In GeoRaster, the spatial referencing capability is called SRS (spatial reference system) or georeferencing, which may or may not be related to geography or a geospatial scheme. Georeferencing is a key feature of GeoRaster and is the foundation of spatial query and operations over geospatial image and gridded raster data. See [Georeferencing](georaster-overview-and-concepts.md) for a detailed description of the SRS models.

GeoRaster supports non-geospatial images, fine art photos, and multi-dimensional arrays, which might not be associated with any coordinate system. For those images and rasters, there is generally no need for georeferencing, but most of the GeoRaster operations still work on them, such as pyramiding, scaling, subsetting, band merging, stretching, and algebraic operations. In these cases, you address the pixels (cells) using the raster's cell space coordinates (that is, row, column, and band).

You can also create a user-defined coordinate system (a new SRID) that is not related to geography, and you can use that SRID as the model coordinate system for the rasters. Then, you can spatially reference these rasters to that SRID; that is, an SRS metadata component will be created for each of those rasters. Doing this causes those rasters to be spatially referenced, and thus co-located in that user-defined model coordinate system. After this is done for all related rasters, GeoRaster operations will work on those rasters as if they are georeferenced to a geographic coordinate system. For example, assume that an artist has painted a large mural on a wall, and that you want to be able to take many high-resolution photographs of different tiles of this wall and then stitch them together. You can spatially reference the tile images and then use the GeoRaster mosaicking capability to do the stitching.

If you do not define a new coordinate system, you can still co-locate the images in the cell space. That is, you can set up different ULT coordinates for the images by calling the [SDO_GEOR.setULTCoordinate](SDO_GEOR-reference.md) procedure, so that the images are aligned in the same coordinate system and then can be mosaicked.

Most geospatial image and raster files that you have are probably already georeferenced by other software tools, and thus they may come with georeferencing information. In those cases, the georeferencing information can be directly loaded with the rasters or afterward by using [SDO_GEOR.importFrom](SDO_GEOR-reference.md), [SDO_GEOR.setSRS](SDO_GEOR-reference.md), the GeoRaster loader tool, GDAL, or other third-party ETL tools. For more information, check [GeoRaster Tools: Viewer\_ Loader\_ Exporter](georaster-overview-and-concepts.md) and [Georeferencing GeoRaster Objects](georaster-database-creation-management.md).

If a geospatial image does not have spatial reference information, you can use the GeoRaster Ground Control Point (GCP) support to georeference the image. GCPs are collected either automatically by the remote sensing system or manually afterward. For an image without GCP information, you can use a GeoRaster visualization tool to collection GCPs for the GeoRaster object. GCPs are described in [Ground Control Point (GCP) Georeferencing Model](georaster-overview-and-concepts.md).

After you have the GCPs and want to store them in the GeoRaster metadata, you can get and set the GCP-based georeferencing mode by using the [SDO_GEOR.getGCPGeorefModel](SDO_GEOR-reference.md) function and the [SDO_GEOR.setGCPGeorefModel](SDO_GEOR-reference.md) procedure. To get, set, and edit only GCPs, use the [SDO_GEOR.getControlPoint](SDO_GEOR-reference.md) function and the [SDO_GEOR.setControlPoint](SDO_GEOR-reference.md) and [SDO_GEOR.deleteControlPoint](SDO_GEOR-reference.md) procedures. The GCPs can also be stored in the GeoRaster metadata when you call [SDO_GEOR.georeference](SDO_GEOR-reference.md).

To get and set only the geometric model, use the [SDO_GEOR.getGCPGeorefMethod](SDO_GEOR-reference.md) function and the [SDO_GEOR.setGCPGeorefMethod](SDO_GEOR-reference.md) procedure. GeoRaster also allows you to store check points (`pointType` = 2), which are treated and manipulated in the same way as control points (`pointType` = 1) except that check points are not used to create the SRS coefficient when [SDO_GEOR.georeference](SDO_GEOR-reference.md) is called with the GCPs.

If you have ground control points (GCPs) that are either stored in the GeoRaster object or not, and if you want to calculate the functional fitting georeferencing model, you can call the [SDO_GEOR.georeference](SDO_GEOR-reference.md) procedure to find the solution. The functional fitting georeferencing model stores all coefficients in the GeoRaster SRS and enables the coordinate transformations between cell space and model space. To generate the functional fitting georeferencing model using GCP, you must specify an appropriate geometric model. The specific geometric models supported by [SDO_GEOR.georeference](SDO_GEOR-reference.md) are Affine Transformation, Quadratic Polynomial, Cubic Polynomial, DLT, Quadratic Rational, and RPC. These models are described in [Functional Fitting Georeferencing Model](georaster-overview-and-concepts.md).

Example 6-1 Setting Up the GCP Georeferencing Model

For example, if you have a Landsat image in a plain area and want to georeference it, you might choose the Quadratic Polynomial geometric model. For that purpose, assuming you have collected 9 GCPs (at least 6 GCPs in this case) and 3 check points, you can set up the GCPs and store them in the GeoRaster's metadata using the code in Example 6-1.

    DECLARE
       gr1         sdo_georaster;
       georefModel SDO_GEOR_GCPGEOREFTYPE;
       GCPs        SDO_GEOR_GCP_COLLECTION;
    BEGIN
       SELECT georaster INTO gr1 from georaster_table WHERE georid=1 FOR UPDATE;
       GCPs := SDO_GEOR_GCP_COLLECTION(
                     SDO_GEOR_GCP('1', '', 1,
                          2, sdo_number_array(25, 73),
                          2, sdo_number_array(237036.9, 897987.2),
                          NULL, NULL),
                     SDO_GEOR_GCP('2', '', 1,
                          2, sdo_number_array(100, 459),
                          2, sdo_number_array(237229.6, 897949.7),
                          NULL, NULL),
                     SDO_GEOR_GCP('3', '', 1,
                          2, sdo_number_array(362, 77),
                          2, sdo_number_array(237038.9, 897818.8),
                          NULL, NULL),
                     SDO_GEOR_GCP('4', '', 1,
                           2, sdo_number_array(478, 402),
                           2, sdo_number_array(237201.06, 897760.56),
                           NULL, NULL),
                     SDO_GEOR_GCP('5', '', 1,
                           2, sdo_number_array(167, 64),
                           2, sdo_number_array(237032.02, 897916.26),
                           NULL, NULL),
                     SDO_GEOR_GCP('6', '', 1,
                           2, sdo_number_array(101, 257),
                           2, sdo_number_array(237128.9, 897949.3),
                           NULL, NULL),
                     SDO_GEOR_GCP('7', '', 1,
                           2, sdo_number_array(235, 501),
                           2, sdo_number_array(237250.9, 897882.2),
                           NULL, NULL),
                     SDO_GEOR_GCP('8', '', 1,
                           2, sdo_number_array(423, 214),
                           2, sdo_number_array(237107.3, 897788.0),
                           NULL, NULL),
                     SDO_GEOR_GCP('9', '', 1,
                           2, sdo_number_array(127, 178),
                           2, sdo_number_array(237089.0, 897936.5),
                           NULL, NULL),
                     SDO_GEOR_GCP('10', '', 2,
                           2, sdo_number_array(131, 425),
                           2, sdo_number_array(237212.8, 897934.2),
                           NULL, NULL),
                     SDO_GEOR_GCP('11', '', 2,
                           2, sdo_number_array(299, 111),
                           2, sdo_number_array(237055.7, 897850.4),
                           NULL, NULL),
                     SDO_GEOR_GCP('12', '', 2,
                           2, sdo_number_array(329, 253),
                           2, sdo_number_array(237126.9,897835.4),
                           NULL, NULL) );
       georefModel := SDO_GEOR_GCPGEOREFTYPE('QuadraticPolynomial', GCPs.count, GCPs, NULL);
       -- Set and store the GCP georeference model into the GeoRaster object's metadata
       sdo_geor.setGCPGeorefModel(gr1, georefModel);
       UPDATE georaster_table SET georaster=gr1 WHERE georid=1;
       COMMIT;
    END;
    /

Example 6-2 Generating the Functional Fitting Model Using GCPs

After using the code in Example 6-1, you can generate the functional fitting model coefficients by using the code in Example 6-2.

    DECLARE
       gr1  sdo_georaster;
       rms  sdo_number_array;
    BEGIN
       SELECT georaster INTO gr1 from georaster_table WHERE georid=1 FOR UPDATE;
       -- georeference the image using the GCPs stored in the image's metadata
       rms := sdo_geor.georeference(gr1, null, 26986, 0, 'TRUE');
       UPDATE georaster_table SET georaster=gr1 WHERE georid=1;
       COMMIT;
    END;
    /

The steps in Example 6-1 and Example 6-2 can be combined without the need to pre-set the GCPs into the GeoRaster object's metadata (see the example for [SDO_GEOR.georeference](SDO_GEOR-reference.md) in [SDO_GEOR Package Reference](SDO_GEOR-reference.md)). The returned value array of [SDO_GEOR.georeference](SDO_GEOR-reference.md) in Example 6-2 contains RMS values and residuals for each GCP. Using these, you can examine the solution accuracy and identify erratic GCPs. If the accuracy is not satisfactory, recheck all GCPs to make sure they are accurate and add more GCPs as necessary, and then run the script or scripts again.

The GCP support in GeoRaster enables you to spatially reference any non-geospatial images and rasters also.

After geospatial images are georeferenced, you can process those images, such as applying rectification, reprojection, and mosaicking, and spatially querying and subsetting the rasters using geometry polygons in different coordinate systems.

**Parent topic:** Image Processing and Virtual Mosaic

### 6.2 Image Reprojection

Image reprojection is the process of transforming an image from one SRS (spatial reference system, or coordinate system) to another.

Reprojection is particularly useful with certain GeoRaster operations that combine two or more objects, because it requires that all the GeoRaster objects involved be in the same SRS.

Basic reprojection in GeoRaster is performed by the [SDO_GEOR.reproject](SDO_GEOR-reference.md) procedure and requires that the source GeoRaster SRID be different from the output SRID.

Example 6-3 Image Reprojection

Example 6-3 reprojects a raster image that had been loaded into a GeoRaster object with SRID 4326, but needs to be reprojected to have the same SRID as other images previously stored with SRID 23619.

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
    BEGIN
      select raster into gr1 from georaster_load_table where georid = 10;
      delete from georaster_table where georid = 54;
      insert into georaster_table
             values(54,'reprojected', sdo_geor.init())
             returning georaster into gr2;
      sdo_geor.reproject(inGeoRaster   => gr1,
                         pyramidLevel  => 0,
                         cropArea      => null,
                         layerNumbers  => null,
                         resampleParam => 'resampling=BILINEAR',
                         storageParam  => null,
                         outSRID       => 32619,
                         outGeoraster  => gr2);
      update georaster_table set georaster = gr2 where georid = 54;
      commit;
    END;

The same operation can be accomplished by the [SDO_GEOR.rectify](SDO_GEOR-reference.md) procedure, producing similar results. The [SDO_GEOR.rectify](SDO_GEOR-reference.md) procedure offers more capabilities and flexibility than [SDO_GEOR.reproject](SDO_GEOR-reference.md); for example, the input and output SRID can be the same and users can specify the precise resolution of the output (see Image Rectification).

If a GeoRaster object does not have an associated SRS, the process for georeferencing and rectifying it is explained in [Georeferencing GeoRaster Objects](georaster-database-creation-management.md) and Image Rectification.

Parallel reprojection is supported with the [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) procedure.

**Parent topic:** Image Processing and Virtual Mosaic

### 6.3 Image Rectification

Most raster data originating from remote sensors above the ground is usually subject to distortion caused by the terrain, the view angles of the instrument, and the irregular shape of the Earth. Image rectification as explained in this section is the process of transforming the images to reduce some of that distortion.

Rectification is performed by the [SDO_GEOR.rectify](SDO_GEOR-reference.md) procedure, and requires that the source GeoRaster object have at least a functional fitting georeferencing model. This means that the image does not need to be rectified, but it needs to have georeference information in the metadata (see [Georeferencing GeoRaster Objects](georaster-database-creation-management.md)).

The [SDO_GEOR.rectify](SDO_GEOR-reference.md) procedure can use the information available in the source GeoRaster object to automatically establish the spatial extents, dimension, and SRID of the output GeoRaster, and users can also specify different values by using the appropriate parameters.

Example 6-4 Image Rectification

Example 6-3 rectifies an aerial image that had been loaded into GeoRaster and later georeferenced with GCPs (see Advanced Georeferencing). The image is rectified so that the output GeoRaster object has the same SRS and resolution of an existing GeoRaster object. The image is to be restricted to the area of existing GeoRaster object, and the pixels should be perfectly aligned with the existing GeoRaster object.

    DECLARE
      gr_src sdo_georaster;
      gr_ref sdo_georaster;
      gr_out sdo_georaster;
    BEGIN
      select raster into gr_src from georaster_load_table where georid = 15;
      select raster into gr_ref from georaster_table where georid = 1;
      delete from georaster_table where georid = 2;
      insert into georaster_table
             values(2, 'rectified', sdo_geor.init())
             returning georaster into gr_out;
      sdo_geor.rectify(inGeoRaster      => gr_src,
                       pyramidLevel     => null,
                       elevationParam   => null,
                       dem              => null,
                       outSRID          => sdo_geor.getModelSRID(gr_ref),
                       outModelCoordLoc => null,
                       cropArea         => sdo_geor.generateSpatialExtent(gr_ref),
                       polygonClip      => null,
                       layerNumbers     => null,
                       outResolutions   => sdo_geor.getSpatialResolutions(gr_ref),
                       resolutionUnit   => 'unit=meters',
                       referencePoint   => sdo_geor.getModelCoordinate(gr_ref,
                                           0, sdo_number_array(-0.5,-0.5)),
                       resampleParam    => null,
                       storageParam     => null,
                       outGeoraster     => gr_out);
      update georaster_table set georaster = gr_out where georid = 2;
      commit;
    END;

Rectification output can be significantly improved if information about elevation is passed to the [SDO_GEOR.rectify](SDO_GEOR-reference.md) procedure. (See Image Orthorectification for more information about elevation.)

Parallel rectification is supported with the [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) procedure.

**Parent topic:** Image Processing and Virtual Mosaic

### 6.4 Image Orthorectification

Orthorectification is a rectification transformation process where information about the elevation, the terrain, and the shape of the Earth is used to improve the quality of the output rectified image. Oracle GeoRaster supports single image orthorectification with average height value or DEM.

The orthorectification is done by the [SDO_GEOR.rectify](SDO_GEOR-reference.md) procedure and requires that the source GeoRaster have a 3D SRS. The [SDO_GEOR.rectify](SDO_GEOR-reference.md) procedure can execute orthorectification with just the average height of the area or with a detailed Digital Elevation Model (DEM).

- Orthorectification with Average Height
- Orthorectification with DEM

**Parent topic:** Image Processing and Virtual Mosaic

#### 6.4.1 Orthorectification with Average Height

A GeoRaster object with a Digital Elevation Model (DEM) is optional for orthorectification. For relatively flat terrains, the 3D SRS together with the average height value might be sufficient to correct the distortion of the source image.

Example 6-5 Orthorectification with Average Height

Example 6-5 shows orthorectification with average height. For this example, the source image was acquired from DigitalGlobe with RPC. The DEM was not available, but the average elevation of the area is known to be 1748.0 meters.

    DECLARE
      gr_src  sdo_georaster;
      gr_out  sdo_georaster;
    BEGIN
      select georaster into gr_src from georaster_table where georid = 1;
      delete from georaster_table where georid = 3;
      insert into georaster_table values(3, 'orthorectified without DEM',
             sdo_geor.init('rdt_4',3))
             returning georaster into gr_out;
      sdo_geor.rectify(inGeoRaster      => gr_src,
                       pyramidLevel     => null,
                       elevationParam   => 'average=1748.8',
                       dem              => null,
                       outSRID          => 32613,
                       outModelCoordLoc => null,
                       cropArea         => null,
                       polygonClip      => null,
                       layerNumbers     => null,
                       outResolutions   => null,
                       resolutionUnit   => null,
                       referencePoint   => null,
                       resampleParam    => 'resampling=AVERAGE4',
                       storageParam     => null,
                       outGeoraster     => gr_out);
      update georaster_table set georaster = gr_out where georid = 3;
      commit;
    END;

In Example 6-5, the `dem` parameter is null, and the `elevationParam` average elevation must be in the same unit as the SRS. Also, in `elevationParam` the `offset` and scale `keywords` are not specified because they are relevant only if DEM is specified.

**Parent topic:** Image Orthorectification

#### 6.4.2 Orthorectification with DEM

The use of a DEM (Digital Elevation Model) layer improves the accuracy of the rectification process and therefore produces a higher quality output GeoRaster object.

Orthorectification with DEM requires that the source GeoRaster have a 3D SRS. The DEM must cover all the target output area, and it should be in the same SRID as the output. The resolution of the DEM should be similar to the expected resolution of the output GeoRaster object.

For orthorectification with DEM, the `elevationParam` `average` keyword is optional; and if it is not specified, the procedure estimates elevation values based on sample values extracted from the DEM on the target area.

The `elevationParam` `offset` and `scale` values can be used to modify the values from the DEM. For example, `scale` can be used for unit conversion if the DEM values are in a unit other than that of the source GeoRaster SRS, and `offset` can be used to perform geoidal correction or other offsetting. However, these specifications do not apply the changes to DEM values in the GeoRaster object. An alternative is to pre-process the DEM values by applying the scaling and offsetting to the DEM data before the orthorectification, as explained in [Raster Data Scaling and Offsetting](raster-algebra-and-analytics.md).

Example 6-6 Orthorectification with DEM

Example 6-6 example performs orthorectification with DEM. The DEM covers all the output area in a resolution approximated to the resolution of the output GeoRaster. The DEM values are in meters but the source image SRS is in feet. There is also a geoid correction on that area of about -15.3 meters:

    DECLARE
      gr_src  sdo_georaster;
      gr_dem  sdo_georaster;
      gr_out  sdo_georaster;
    BEGIN
      select georaster into gr_src from georaster_table where georid = 1;
      select georaster into gr_dem from georaster_table where georid = 5;
      delete from georaster_table where georid = 6;
      insert into georaster_table values(5, 'orthorectified with DEM',
             sdo_geor.init('rdt_4',6))
             returning georaster into gr_out;
      sdo_geor.rectify(inGeoRaster      => gr_src,
                       pyramidLevel     => null,
                       elevationParam   => 'average=1748.8 offset=-15.3',
                       dem              => gr_dem,
                       outSRID          => 32613,
                       outModelCoordLoc => null,
                       cropArea         => null,
                       polygonClip      => null,
                       layerNumbers     => null,
                       outResolutions   => null,
                       resolutionUnit   => null,
                       referencePoint   => null,
                       resampleParam    => 'resampling=BILINEAR',
                       storageParam     => null,
                       outGeoraster     => gr_out);
      update georaster_table set georaster = gr_out where georid = 6;
      commit;
    END;

Example 6-7 Orthorectification with Cropped DEM

Typically, the DEM covers an area much larger than the target area, and the resolution is coarser than the target resolution of the output GeoRaster object. Using this DEM "as is" would result in poor quality orthorectification. The solution to that common problem is to crop the DEM to the target area and rescale it to the desired resolution, as shown in Example 6-7. This example uses the [SDO_GEOR.rectify](SDO_GEOR-reference.md) procedure to transform the low-resolution DEM GeoRaster object into a second DEM GeoRaster object that has the same resolution as the orthorectified GeoRaster object generated by the second call to the [SDO_GEOR.rectify](SDO_GEOR-reference.md) procedure.

    DECLARE
      height   number := 1748.8;
      gr_src   sdo_georaster;
      gr_out   sdo_georaster;
      gr_dem   sdo_georaster;
      gr_dem2  sdo_georaster;
      gm_area  sdo_geometry;
    begin
      select georaster into gr_src from georaster_table where georid = 1;
      select georaster into gr_dem from georaster_table where georid = 2;
      -- Calculate crop area
      gm_area := sdo_cs.make_2d(
                 sdo_geor.generateSpatialExtent(gr_src,height),
                 sdo_geor.getModelSRID(gr_dem));
      -- Rectify dem ( re-project, crop area, re-escale and resample )
      delete from georaster_table where georid = 4;
      insert into georaster_table values(4,
                  'rectified DEM',
                  sdo_geor.init('rdt_4',4))
                  returning georaster into gr_dem2;
      sdo_geor.rectify(inGeoRaster      => gr_dem,
                       pyramidLevel     => null,
                       elevationParam   => null,
                       dem              => null,
                       outSRID          => 32613,
                       outModelCoordLoc => null,
                       cropArea         => gm_area,
                       polygonClip      => null,
                       layerNumbers     => null,
                       outResolutions   => sdo_number_array(0.6,0.6),
                       resolutionUnit   => null,
                       referencePoint   => null,
                       resampleParam    => 'resampling=CUBIC',
                       storageParam     => null,
                       outGeoraster     => gr_dem2);
      update georaster_table set georaster = gr_dem2 where georid = 4;
      commit;
      -- Orthorectification with DEM
      select georaster into gr_dem2 from georaster_table where georid = 4;
      delete from georaster_table where georid = 5;
      insert into georaster_table
             values(5, 'orthorectified', sdo_geor.init('rdt_4',5))
             returning georaster into gr_out;
      sdo_geor.rectify(inGeoRaster      => gr_src,
                       pyramidLevel     => null,
                       elevationParam   =>
                              'average=' || height || ' offset=-15.588',
                       dem              => gr_dem2,
                       outSRID          => 32613,
                       outModelCoordLoc => null,
                       cropArea         => gm_area,
                       polygonClip      => null,
                       layerNumbers     => null,
                       outResolutions   => sdo_number_array(0.6,0.6),
                       resolutionUnit   => null,
                       referencePoint   => null,
                       resampleParam    => 'resampling=average16',
                       storageParam     => null,
                       outGeoraster     => gr_out);
      update georaster_table set georaster = gr_out where georid = 5;
      commit;
    end;
    /

**Parent topic:** Image Orthorectification

### 6.5 Image Warping

Image warping transforms an input GeoRaster object to an output GeoRaster object using the spatial reference information from a specified SDO_GEOR_SRS object.

The reference SDO_GEOR_SRS object can be copied from an existing GeoRaster object or created using a constructor. (For more information, see [SDO_GEOR_SRS Object Type](georaster-datatypes.md).)

Warping is performed by the [SDO_GEOR.warp](SDO_GEOR-reference.md) procedure, and requires that the source GeoRaster object have at least a functional fitting georeferencing model. This means that the image does not need to be rectified, but it needs to have georeference information in the metadata (see [Georeferencing GeoRaster Objects](georaster-database-creation-management.md)).

Example 6-8 Image Warping

The following example uses the SDO_GEOR_SRS information from one GeoRaster image (`gr1`) as a reference to transform an existing GeoRaster object (`gr2`) into a new (warped) GeoRaster object (`gr3`). Thus, the third GeoRaster object is a “copy” (actually, a transformation) of the second GeoRaster object, but reflects the same georeferencing as the first GeoRaster object.

    DECLARE
      srs sdo_geor_srs;
      gr1 sdo_georaster;
      gr2 sdo_georaster;
      gr3 sdo_georaster;
    BEGIN
      select georaster into gr1 from georaster_table where georid = 1;
      select georaster into gr2 from georaster_table where georid = 2;

      srs := sdo_geor.getSRS(gr1); -- get the SRS from image 1.

      insert into georaster_table values(3, 'Warped Object',
             sdo_geor.init('imagery_rdt'))
             returning georaster  into gr3;

      sdo_geor.warp( inGeoRaster      => gr2,
                     pyramidLevel     => null,
                     outSRS           => srs, -- apply SRS to warp transformation
                     cropArea         => null,
                     dimensionSize    => null,
                     layerNumbers     => null,
                     elevationParam   => null,
                     resampleParam    => ‘resampling=AVERAGE4’,
                     storageParam     => ‘pyramid=true’,
                     outGeoRaster     => gr3,
                     bgValues         => sdo_number_array(0,0,0),
                     parallelParam    => ‘parellel=4’ );

      update georaster_table set georaster = gr3 where georid = 3;
      commit;
    END;

**Parent topic:** Image Processing and Virtual Mosaic

### 6.6 Image Affine Transformation and Scaling

Affine transformation is the process of using geometric transformations of translation, scaling, rotation, shearing, and reflection on an image to produce another image.

For details and examples, see the [SDO_GEOR.affineTransform](SDO_GEOR-reference.md) reference topic.

Image scaling is the process of enlarging or shrinking an image by changing the pixel size for the row and column dimensions of an image. Image scaling resamples the pixel values from the original image to construct the rescaled version of that image. Image scaling can be performed in several ways:

- Use the [SDO_GEOR.scaleCopy](SDO_GEOR-reference.md) procedure and specify for `scaleParam` a `scaleFactor` to be applied to the input image dimensions or a `maxDimSize` for the output image.

- Use the [SDO_GEOR.rectify](SDO_GEOR-reference.md) procedure and specify the resolution of the output image. (This procedure can be executed in parallel.)

- During affine transformation, use the `scales` parameter of the [SDO_GEOR.affineTransform](SDO_GEOR-reference.md) procedure. In that procedure, the `scales` parameter is a two-number array where you can specify a scale factor for rows and for columns independently. (This procedure can be executed in parallel.)

Example 6-9 Image Scaling Using SDO_GEOR.scaleCopy

This example performs rescaling by using [SDO_GEOR.scaleCopy](SDO_GEOR-reference.md) and specifying the `scaleFactor` value as 2. The input image will have 2 times more rows and 2 times more columns than the original, and the values will be resampled by the `average16` algorithm. Note that the image will be 4 times larger than the original.

    DECLARE
      gr_src  sdo_georaster;
      gr_out  sdo_georaster;
    BEGIN
      select georaster into gr_src from georaster_table where georid = 7;
      -- Rescale
      delete from georaster_table where georid = 9;
      insert into georaster_table values(9, 're-scaled by scaleCopy',
                  sdo_geor.init('rdt_4',9))
                  returning georaster into gr_out;
      sdo_geor.scaleCopy(inGeoRaster      => null,
                         scaleFactor      => 'scaleFactor=2',
                         resampleParam    => 'resampling=AVERAGE16',
                         storageParam     => null,
                         outGeoraster     => gr_out);
      update georaster_table set georaster = gr_out where georid = 9;
      commit;
    END;
    /

Example 6-10 Image Scaling Using SDO_GEOR.rectify

This example performs rescaling by using [SDO_GEOR.rectify](SDO_GEOR-reference.md) and specifying the `outResolutions` parameter. The input image is already rectified, and the output will have the same SRID as the input.

    DECLARE
      gr_src     sdo_georaster;
      gr_out     sdo_georaster;
    BEGIN
      select georaster into gr_src from georaster_table where georid = 7;
      -- Rescale
      delete from georaster_table where georid = 10;
      insert into georaster_table values(10, 're-scaled by rectify',
                  sdo_geor.init('rdt_4',10))
                  returning georaster into gr_out;
      sdo_geor.rectify(inGeoRaster      => null,
                       pyramidLevel     => null,
                       elevationParam   => null,
                       dem              => null,
                       outSRID          => null,
                       outModelCoordLoc => null,
                       cropArea         => null,
                       polygonClip      => null,
                       layerNumbers     => null,
                       outResolutions   => sdo_number_array(1.2,1.2),
                       resolutionUnit   => null,
                       referencePoint   => null,
                       resampleParam    => 'resampling=CUBIC',
                       storageParam     => null,
                       outGeoraster     => gr_out,
                       parallelParam    => 'parallel=4');
      update georaster_table set georaster = gr_out where georid = 10;
      commit;
    END;
    /

Example 6-11 Rescaling Using SDO_GEOR.affineTransform

This example performs rescaling by using the [SDO_GEOR.affineTransform](SDO_GEOR-reference.md) procedure and specifying he `scales` parameter as `sdo_number_array(2, 2)`, indicating that the image will be enlarged 2 times on the rows dimension and 2 times on the columns dimension.

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
    BEGIN
      select georaster into gr1 from georaster_table where georid = 1;

      insert into georaster_table values(2, 'Rotated 90 left',
             sdo_geor.init('rdt0',2)) returning georaster into gr2;

      sdo_geor.affineTransform(inGeoRaster   => gr1,
                               translation   => null,
                               scales        => sdo_number_array(2,2),
                               rotatePt      => null,
                               rotateAngle   => null,
                               shear         => null,
                               reflection    => null,
                               storageParam  => null,
                               outGeoraster  => gr2,
                               parallelParam => 'parallel=4');

      update georaster_table set georaster = gr2 where georid = 2;
      commit;
    END;

**Parent topic:** Image Processing and Virtual Mosaic

### 6.7 Image Stretching, Normalization, Equalization, Histogram Matching, and Dodging

The color and contrast of images can be enhanced to improve their visual quality. The SDO_GEOR_IP package (“IP” for image processing) provides a set of subprograms for image enhancement, including performing image stretching, image normalization, image equalization, histogram matching, and image dodging.

Linear stretching and piecewise stretching can stretch the image cell values linearly for all cells values based on the minimum and maximum cell values or at specified value range, to achieve better color and contrast. To perform image stretching, you can use the following procedures:

- [SDO_GEOR_IP.stretch](SDO_GEOR_IP-reference-ref.md) stretches GeoRaster objects in any supported cell depth (1BIT to 64BIT_REAL) to cell depth of 8BIT_U for display purposes.

- [SDO_GEOR_IP.piecewiseStretch](SDO_GEOR_IP-reference-ref.md) stretches GeoRaster objects of any supported cell depth to the GeoRaster objects in higher or lower cell depth, not limited to 8BIT_U.

Image normalization linearly stretches the image based on the statistics (mean and standard deviation) of the image cell values. To perform image normalization, use the [SDO_GEOR_IP.normalize](SDO_GEOR_IP-reference-ref.md).

Image equalization enhances image contrast by equalizaing its histogram. To perform equalization, use the [SDO_GEOR_IP.equalize](SDO_GEOR_IP-reference-ref.md) procedure.

Image histogram matching stretches the image to match the specified histogram or the histogram of a reference image. To perform image histogram matching, use the [SDO_GEOR_IP.histogramMatch](SDO_GEOR_IP-reference-ref.md) procedure.

Image dodging balances image color by stretching the contrast of the image locally instead of globally. To perform image dodging, use the [SDO_GEOR_IP.dodge](SDO_GEOR_IP-reference-ref.md) procedure.

**Parent topic:** Image Processing and Virtual Mosaic

### 6.8 Image Filtering

Image filtering is the process of applying a convolution filter on an image to achieve a specific purpose. For example, applying a low-pass filter on an image can smooth and reduce noise in an image, while applying a high-pass filter on an image can enhance the details of the image or even detect the edges inside the image.

The [SDO_GEOR_IP.filter](SDO_GEOR_IP-reference-ref.md) procedure provides standard filters such as low-pass filter (LPF), high-pass filter (HPF), and high-boost filter (HBF). It also allows you to apply customized filters on images.

The following example performs image filtering by providing a customized 3-by-3 Laplacian filter on the image for edge detection.

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
      cropArea sdo_geometry;
    BEGIN
      INSERT INTO georaster_table (georid, georaster)
        VALUES (41, sdo_geor.init('RDT_1'))
        RETURNING georaster INTO gr2;

      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=4;

      sdo_geor_ip.filter(gr1, 0, cropArea, null, ‘filtertype=CUSTOM, kernelsize=(3,3)’, sdo_number_array(0, 1, 0, 1, -4, 1, 0, 1, 0 ), null, gr2);
      UPDATE georaster_table SET georaster=gr2 WHERE georid=41;
      COMMIT;
    END;
    /

**Parent topic:** Image Processing and Virtual Mosaic

### 6.9 Image Segmentation

Segmentation is a simple type of classification algorithm, and can be useful in classifying certain types of images into larger ground feature categories, such as land, cloud, water, or snow.

You can use the [SDO_GEOR_RA.classify](sdo-geor-ra-ref.md) procedure to apply thresholding to images. Thresholding is the simplest segmentation, which classifies an image into two categories by using a single cell value as the threshold. The resulting image has only two values and can be cast into a binary bitmap mask directly in the same process.

You can also apply more image segmentation operations using the [SDO_GEOR_RA.classify](sdo-geor-ra-ref.md) procedure, by first applying arithmetic operations on multiple bands and then classifying the results into a number of categories.

For examples of using the [SDO_GEOR_RA.classify](sdo-geor-ra-ref.md) procedure, see [Classification Operations](raster-algebra-and-analytics.md).

**Parent topic:** Image Processing and Virtual Mosaic

### 6.10 Image Pyramiding: Parallel Generation and Partial Update

Image pyramiding is one of the most commonly used processes in building large-scale image databases.

This topic discusses some related techniques: pyramid generation in parallel, partial updating of pyramids, and batch and concurrent processing.

For working more efficiently with pyramids, you can generate pyramids in parallel and perform a partial update of a pyramid. (This section assumes you understand the concepts explained in [Pyramids](georaster-overview-and-concepts.md).)

Example 6-12 Parallel Generation of Pyramids

For faster pyramid generation, you can specify the `parallelParam` parameter with the [SDO_GEOR.generatePyramid](SDO_GEOR-reference.md) procedure. In Example 6-12, the degree of parallelism is set to 4. (The actual performance improvement for pyramid generation depends on the number of CPUs available to Oracle Database.)

    DECLARE
      gr sdo_georaster;
    BEGIN

      SELECT georaster INTO gr
        FROM georaster_table WHERE georid = 6 FOR UPDATE;

      -- Generate pyramids.
      sdo_geor.generatePyramid(gr, 'rLevel=5, resampling=NN', null, 'parallel=4');

      -- Update the original GeoRaster object.
      UPDATE georaster_table SET georaster = gr WHERE georid = 6;

      COMMIT;
    END;
    /

To enable parallel processing of the pyramid generation, [SDO_GEOR.generatePyramid](SDO_GEOR-reference.md) performs an implicit commit operation. If an error during the call, the GeoRaster object may in an invalid state. If this occurs, use [SDO_GEOR.deletePyramid](SDO_GEOR-reference.md) to remove the newly generated and upper pyramid levels of the GeoRaster object.

Example 6-13 Partial Updating of Pyramids

You can partially update pyramids by using the [SDO_GEOR.updateRaster](SDO_GEOR-reference.md) procedure. In Example 6-13, the target GeoRaster object at a specified area (`targetArea` is specified as `area`) is updated by another GeoRaster object. The `updateUpperPyramids` parameter is set to `true`, so the upper pyramids of the target GeoRaster object are only partially updated at the specified area. In other words, the upper pyramid levels are not regenerated in full, but only the cells in that targetArea are regenerated, and thus performance is improved.

    DECLARE
      gr1 sdo_georaster;
      gr2 sdo_georaster;
      area sdo_number_array := sdo_number_array(-200,-50,201,162);
    BEGIN
      SELECT georaster INTO gr2 FROM georaster_table WHERE georid=0 FOR UPDATE;
      SELECT georaster INTO gr1 FROM georaster_table WHERE georid=1;
      SDO_GEOR.updateRaster(gr2, 0, null, area, gr1, 0, null, 'true');
      UPDATE GEORASTER_TABLE SET georaster=gr2 WHERE georid=0;
      COMMIT;
    END;
    /

Other techniques to speed up and automate the pyramiding process include batch processing and concurrent processing can be used. To batch pyramid many images in a certain area, see the example in [Querying and Searching GeoRaster Objects](georaster-data-manipulation.md). To process many batches concurrently, you can start different database sessions

**Parent topic:** Image Processing and Virtual Mosaic

### 6.11 Bitmap Pyramiding

Bitmap pyramiding can produce high-quality pyramids in certain cases where traditional pyramiding is not adequate.

For most raster data types, image pyramiding as described in Image Pyramiding: Parallel Generation and Partial Update results in pyramids of great quality. However, for bitmap rasters of points, lines, or polylines, which are typically stored in 1-bit cell depth, the same pyramiding approach may not create high-quality pyramids. Distorted point patterns and dashed lines are commonly seen in those pyramids.

To solve such problems, you can use the [SDO_GEOR.generateBitmapPyramid](SDO_GEOR-reference.md) procedure, instead of [SDOGEOR.generatePyramid](SDO_GEOR-reference.md), to perform pyramiding on bitmap GeoRaster objects. The [SDO_GEOR.generateBitmapPyramid](SDO_GEOR-reference.md) procedure significantly improves the pyramid quality by avoiding distorted patterns, particularly dashed lines or missing lines in a bitmap raster, such as a road raster map or utility network raster map.

**Parent topic:** Image Processing and Virtual Mosaic

### 6.12 Vegetation Index Computation

In remote sensing, the Normalized Difference Vegetation Index (NDVI) is a widely used vegetation index, enabling users to quickly identify vegetated areas and monitor the growth and "condition" of plants.

Using Landsat TM imagery, the standard NDVI computation formula is: (TM4 - TM3) / (TM4 + TM3).

Example 6-14 Vegetation Index Computation

Example 6-14takes a Landsat 7 ETM+ image and computes the NDVI with parallelism. The result is stored as another raster of floating number data type. Note that in the GeoRaster algebra language, band numbering starts with 0, so the formula translates into the expression: ({3}-{2})/({3}+{2}).

    DECLARE
      geor1    SDO_GEORASTER;
      geor2    SDO_GEORASTER;
    EBGIN
      -- Source ETM+ image
      select georaster into geor1 from georaster_table where georid = 2;
      -- Store NDVI
      select georaster into geor2 from georaster_table where georid = 3 for update;
      sdo_geor_ra.rasterMathOp(geor1,
           SDO_STRING2_ARRAY('({3}-{2})/({3}+{2})'),
           'celldepth=32bit_real',geor2, null, null, ‘parallel=4’);
      update georaster_table set georaster = geor2 where georid = 3;
      commit;
    end;
    /

In addition to NDVI, there are many other vegetation indexes in the area of remote sensing. Many of these can be similarly computed using the GeoRaster raster algebra.

**Parent topic:** Image Processing and Virtual Mosaic

### 6.13 Tasseled Cap Transformation

Tasseled Cap Transformation (TCT) is a useful tool for analyzing physical ground features using remotely sensed imagery.

With various Landsat imagery, it uses 5 bands of either original digital number (DN) or reflectance data to generate 6 new bands, each of which represents different ground features. The 6 resulting bands are generally called (soil) brightness, (vegetation) greenness, (soil and canopy) wetness, haze, TC5, and TC6. Each one or a combination of them is useful for different applications, such as crop growth monitoring and analysis, biomass study, and agriculture planning.

Example 6-15 Tasseled Cap Transformation

Example 6-15 takes the DN data of a Landsat 5 TM image as input, executes the TCT using the GeoRaster raster algebra with parallelism, and creates a new image holding the results.

    DECLARE
        gr1 sdo_georaster;
        gr2 sdo_georaster;
        ret varchar2(32);
    BEGIN
        select georaster into gr1 from georaster_table where georid = 2;
        select georaster into gr2 from georaster_table where georid = 4 for update;
        sdo_geor_ra.rasterMathOp(
          gr1,
          SDO_STRING2_ARRAY(
             '0.3561*{0}+0.3972*{1}+0.3904*{2}+0.6966*{3}+0.2286*{4}+0.1596*{6}',
             '(-0.3344)*{0}-0.3544*{1}-0.4556*{2}+0.6966*{3}-0.0242*{4}-0.2630*{6}',
             '0.2626*{0}+0.2141*{1}+0.0926*{2}+0.0656*{3}-0.7629*{4}-0.5388*{6}',
             '0.0805*{0}-0.0498*{1}+0.1950*{2}-0.1327*{3}+0.5752*{4}-0.7775*{6}',
             '(-0.7252)*{0}-0.0202*{1}+0.6683*{2}+0.0631*{3}-0.1494*{4}-0.0274*{6}',
             '0.4000*{0}-0.8172*{1}+0.3832*{2}+0.0602*{3}-0.1095*{4}+0.0985*{6}' ),
          'celldepth=32BIT_REAL',
          gr2, null, null, ‘parallel=4’);
        update georaster_table set georaster = gr2 where georid = 4;
        commit;
    END;
    /

You can also use the same raster algebra language to add code in Example 6-15 to convert the 32-bit floating number image into an 8-bit integer image and to apply image stretching (described in Image Stretching) on the resulting TCT image to generate a new GeoRaster object for visualization and analysis.

In addition to using the optimized implementation of raster algebra algorithms and the embedded parallel processing, you can further take advantage of the Oracle grid computing infrastructure to quickly compute NDVI or apply TCT on thousands of images stored in the GeoRaster database.

**Parent topic:** Image Processing and Virtual Mosaic

### 6.14 Image Masking

To perform image masking, an application can query the GeoRaster database for bitmap masks, retrieve the desired bitmap mask or masks, and apply the masking operation on the target GeoRaster object for the purpose of displaying the object or performing some other processing.

A bitmap mask (described in [Bitmap Masks](georaster-overview-and-concepts.md)) can be stored as an independent GeoRaster object; it can also be stored as metadata inside a GeoRaster object and be associated with a single band or with the whole GeoRaster object.

You can also perform masking operations inside the database to generate new GeoRaster objects, using the [SDO_GEOR.mask](SDO_GEOR-reference.md) procedure.

**Parent topic:** Image Processing and Virtual Mosaic

### 6.15 Band Merging

For image classification, time series analysis, and raster GIS modeling, multiple bands or layers of different GeoRaster objects may need to be merged into a single GeoRaster object.

This operation is called band or layer merging in GeoRaster, and can be performed by using the [SDO_GEOR.mergeLayers](SDO_GEOR-reference.md) procedure or the [SDO_GEOR_RA.rasterMathOp](sdo-geor-ra-ref.md) procedure. You can either append specified bands of a source GeoRaster object to a target GeoRaster object or merge different bands from two GeoRaster objects into a new GeoRaster object. By doing this merging or appending iteratively, you can merge an unlimited number of bands into a single GeoRaster object.

Example 6-16 Band Merging

Example 6-16 includes two examples. The first example assumes there are eight GeoRaster objects, each of which contains only one band loaded from a single-band Landsat ETM+ image file in GeoTIFF format. The number of the band in each GeoRaster object is the same as the GEORID column value for the GeoRaster object. The example merges all bands into a single GeoRaster object to create a complete ETM+ scene.

    DECLARE
        gr1 sdo_georaster;
    BEGIN
        select georaster into gr1 from georaster_table where georid = 1 for update;
        for rec in (select georaster from georaster_table
                         where georid >= 2 and georid <= 8
                         order by georid)
        loop
           sdo_geor.mergelayers(gr1, rec.georaster);
        end loop;
        update georaster_table set georaster = gr1 where georid = 1;
        commit;
    END;
    /

The second example assumes there are eight GeoRaster objects, each of which contains three bands. The example picks up one band from each GeoRaster object and merges them into a single 8-band GeoRaster object in parallel.

    DECLARE
      geor       SDO_GEORASTER;
      geo_array  SDO_GEORASTER_ARRAY;
    BEGIN
      SELECT georaster INTO geor FROM georaster_table WHERE georid = 0 for update;
      geo_array:=SDO_GEORASTER_ARRAY();
      for rec in (select georaster from georaster_table
                         where georid >= 1 and georid <= 8
                         order by georid)
      loop
         geo_array.extend(1);
         geo_array(geo_array.last):=rec.georaster;
      end loop;
      sdo_geor_ra.rasterMathOp(geo_array,SDO_STRING2_ARRAY('{0,0}','{1,1}','{2,2}','{3,0}','{4,1}','{5,2}','{6,0}','{7,1}',),null,geor,'false',null,'parallel=4');
      UPDATE georaster_table SET georaster = geor WHERE georid = 0;
      COMMIT;
    END;
    /

**Parent topic:** Image Processing and Virtual Mosaic

### 6.16 Image Appending

You can append one image to another image when the two images have the same number of bands.

Image appending is useful when the geospatial images are collected at intervals and the captured image later needs to be appended to the existing image to make a large image of the whole spatial area. Image appending is also useful for updating the existing image with a new image.

The [SDO_GEOR_AGGR.append](SDO_GEOR_AGGR-referencer-ref.md) procedure implements image appending by partially updating the existing GeoRaster object with another GeoRaster object. If the existing GeoRaster object contains pyramids, the pyramids with blocking are partially updated with the new data.

Example 6-17 appends one image to another, with pyramids with blocking are updated at the same time. Because the `appendParam` parameter specifies `'nodata=true'`, the NODATA values in the overlapping area are considered transparent.

Example 6-17 Appending One Image to Another Image

    DECLARE
        gr1 sdo_georaster;
        gr1 sdo_georaster;
    BEGIN
         select georaster into gr1 from georaster_table where georid = 1 for update;
         select georaster into gr2 from georaster_table where georid = 2;
         sdo_geor_aggr.append(gr1, gr2, 0, 'nodata=true');
         update georaster_table set georaster = gr1 where georid= 1;
         commit;
    END;
    /

**Parent topic:** Image Processing and Virtual Mosaic

### 6.17 Large-Scale Image Mosaicking

A large geospatial area typically consists of many smaller aerial photographs or satellite images. Large-scale image mosaicking can stitch these small geospatial images into one large image to get a better view of the whole spatial area.

GeoRaster provides large-scale mosaicking functions that allow gaps, overlaps, and missing source GeoRaster objects. It supports both rectified and unrectified images. It supports internal reprojection and rectification, common point rules, and simple color balancing. You can also mosaic at a certain pyramid level. This mosaicking process results in a single GeoRaster object, which is also called a physical mosaic as opposed to virtual mosaic (For information about virtual mosaic, see Virtual Mosaic).

The [SDO_GEOR.mosaic](SDO_GEOR-reference.md) and [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) procedures provide support for image mosaicking; however, you are strongly encouraged to use [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) because it provides much more advanced features and options, and it is also implemented with parallelism. [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) can take a virtual mosaic, such as a list of GeoRaster tables, a database view with a GeoRaster column, or a REF CURSOR, as the source images.

The [SDO_GEOR.mosaic](SDO_GEOR-reference.md) procedure mosaics a set of source GeoRaster images that are rectified, are geospatially aligned under the same SRID, and have the same resolution. The result of the mosaic is another GeoRaster object. If there are overlaps between the source images, the mosaic result will have the last source image's content at the overlapping area. This procedure works well for preprocessed and perfectly aligned source images.

In the examples in this section, the source images are stored in source GeoRaster tables GRTAB, GRTAB1, and GRTAB2, which are defined with the following columns:

      (id          NUMBER PRIMARY KEY,
      cloud_cover  NUMBER     -- percentage of cloud coverage
      last_update  TIMESTAMP  -- GeoRaster object's last update time
      grobj        SDO_GEORASTER )

Oracle Spatial and Graph spatial indexes have been created on the `spatialExtent` attribute of the GeoRaster object in these tables.

In these examples, the mosaicked image is stored in GEORASTER_TABLE, which is defined in [Storage Parameters](georaster-overview-and-concepts.md).

Example 6-18 SDO_GEOR.mosaic (Table and Column Name)

Example 6-18 shows the [SDO_GEOR.mosaic](SDO_GEOR-reference.md) procedure.

    DECLARE
      gr sdo_georaster;
    BEGIN
      INSERT INTO georaster_table (georid, georaster)
          VALUES (12, sdo_geor.init('rdt_1'))
          RETURNING georaster INTO gr;
      sdo_geor.mosaic('grtab', 'grobj', gr, 'blocking=optimalpadding blocksize=(512,512,1)');
      UPDATE georaster_table SET georaster=gr WHERE id=12;
    END;
    /

In the real world, however, the source images are often collected under different circumstances so as to have different resolutions or large areas of overlap, or using a different georeference system. In such cases, you can use the [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) procedure to mosaic these source images into one uniform mosaicked image. Compared to [SDO_GEOR.mosaic](SDO_GEOR-reference.md), the [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) procedure provides more features and options:

- The source images do not have to be in the same coordinate system (SRID) and have the same georeferencing information or resolutions.

- The source images can be mosaicked on a user-specified pyramid level.

- The source images can be mosaicked on user-specified bands.

- The output images can have a different coordinate system and resolution than the input images (`outSRID` and `outResolutions` parameters).

- You have more control on the output of the overlapping area through the `mosaicParam` parameter: `commonPointRule` can specify which cell value to use for the output at the overlapping area, and `NODATA` can indicate whether to consider the NODATA value at the overlapping area.

- The output mosaicked image can be aligned at a specified point (the reference point). The source image can be resampled in order to align with the reference point if the source image is out of alignment more than the `resampleTolerance` value specified in `mosaicParam`.

- If there is small gap between the source images that is less than 2 pixels wide, it can be filled using the neighboring pixel values when `fillGap` is `true` in `mosaicParam`.

- Limited color balancing (linear stretching and normalization) is supported.

- Parallel processing is supported to speed up the mosaicking process.

Example 6-19 SDO_GEOR_AGGR.mosaicSubset

Example 6-19 uses [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) to mosaic all the source images from two GeoRaster tables (GRTAB1 and GRTAB2) into a large mosaicked image in SRID 4326 with a resolution of 30 meters on the x and y dimensions.

    DECLARE
      resolutions sdo_number_array;
      gr sdo_georaster;
    BEGIN
        insert into georaster_table (georid, georaster)
            values (10, sdo_geor.init('RDT_1',10))
             returning georaster into gr;

        resolutions := sdo_number_array(30, 30);
        sdo_geor_aggr.mosaicSubset('grtab1, grtab2', 'grobj, grobj',
                                   0, 4326, null, null, null,
                                   null, null, null, resolutions, 'unit=meter',
                                   'commonPointRule = end, nodata=true, resampleTolerance=0.2, resampling=bilinear, fillGap=true',
                                   'blocking=optimalpadding blocksize=(512, 512, 3)', gr, null, 'parallel=4');

          update georaster_table set georaster = gr where georid=10;
          commit;
    END;
    /

In Example 6-19:

- Any source image that is not rectified is rectified; any source image that is not in SRID 4326 is reprojected to SRID 4326.

- Any source image that has a resolution other than 30 meters is scaled to a resolution of 30 meters.

- The `nodata` keyword in the `mosaicParam` parameter is specified as `true`, which means the NODATA values in the overlapping area are not considered.

- The `resampleTolerance` keyword in the `mosaicParam` parameter is specified as 0.2, which means that if the source image is offset from the target by more than 0.2 pixel, the source image is resampled.

- The resampling method is specified as `bilinear` in the `mosaicParam` parameter.

- The degree of parallelism is specified as 4 in the `parallelParam` parameter.

You can call [SDO_GEOR_AGGR.validateForMosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) before calling [SDO_GEOR_AGGR.getMosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) to make sure that the source images can be mosaicked.

- Color Balancing During Mosaicking
- Parallel Compression, Copying, and Subsetting

**Parent topic:** Image Processing and Virtual Mosaic

#### 6.17.1 Color Balancing During Mosaicking

The source images of the mosaicking operation can have different luminance or colors due to the differences in the lighting conditions, time of day, or other factors when the images were captured. Color balancing minimizes the color differences between the neighboring images and makes the resulting mosaic look more seamless.

[SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) and [SDO_GEOR_AGGR.getMosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) provide some basic color balancing methods during the mosaicking process. Several color balancing methods are provided. They are identified by the keyword `colorbalance` in the `mosaicParam` parameter:

- `LINEARSTRETCHING`: Perform the min-max stretch on each band of the source images to a reference minimum and maximum range.

- `STATISTICSMATCHING`: Perform the image stretching so that the mean and standard deviation of each band of the source images is stretched and matched to the reference mean and standard deviation values.

- `HISTOGRAMMATCHING`: Perform the image stretching so that the histograms of the resulting images match the reference histograms.

There are several ways to specify the reference values for the color balancing methods. They are identified by the keyword `cbreference` in the `mosaicParam` parameter:

- VALUE: The reference values are provided through `referenceValue1`, `referenceValue2`, or `refHistograms` parameters directly.

- IMAGE: The reference values are derived from the image specified by the `referenceImage` parameter. The reference image must have the same number of bands as the source image.

- OVERLAP: The reference values are determined by the neighboring image through the overlapped area with the neighboring image. This option requires the source images have large enough overlaps so that the reference values can be derived from the overlapped area. Note that because linear stretching method does not provide a good result for this option, overlapped area reference is not supported for the linear stretching method.

Example 6-20 LINEARSTRETCHING Color Balancing

This example shows how to use the `LINEARSTRETCHING` color balancing method on the source images in the [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) procedure. The reference minimum and maximum values are specified in the `referenceValue1` and `referenceValue2` parameters. In the example, each band has different reference value.

    DECLARE
    gr sdo_georaster;
    resolutions  sdo_number_array;
    ref_min    sdo_number_arrray;
    ref_max   sdo_number_array;
    BEGIN
        -- create the new GeoRaster object for mosaic
        insert into georaster_table (georid, georaster)
            values (10, sdo_geor.init('RDT_1',10))
             returning georaster into gr;

        -- set the output resolution
         resolutions := sdo_number_array(30, 30);

        -- Set the reference values, there are 3 values, one for each band
        ref_min := sdo_number_array(10, 10, 10);
        ref_max := sdo_number_array(200, 255, 230);

        -- Mosaic
        sdo_geor_aggr.MosaicSubset('georaster_table_1',
                       'georaster', null, 32610, null, null, null, null,
                        null, null, null, resolutions, null,
                       'colorBalance=linearstretching, cbreference=value',
                       'blocking=optimalpadding, blocksize=(512,512,3)',
                        gr, null, 'parallel=4', referenceValue1=>ref_min,
                        referenceValue2=>ref_max);

         update georaster_table set georaster = gr where georid=10;
         commit;
    END;
    /

Example 6-21 HISTOGRAMMATCHING Color Balancing

This example shows how to use the HISTOGRAMMATCHING color balancing method on the source images in the [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) procedure. The reference histograms are derived from the reference image. The reference image must have the same number of bands as the source images.

    DECLARE
    gr sdo_georaster;
    resolutions  sdo_number_array;
    ref_gr    sdo_georaster;
    BEGIN
        -- create the new GeoRaster object for mosaic
        insert into georaster_table (georid, georaster)
            values (10, sdo_geor.init('RDT_1',10))
             returning georaster into gr;

        -- set the output resolution
        resolutions := sdo_number_array(30, 30);

    -- retrieve the reference image
    Select georaster into ref_gr from georaster_table where georid = 1;

        -- Mosaic
        sdo_geor_aggr.MosaicSubset('georaster_table_1',
                       'georaster', null, 32610, null, null, null, null,
                        null, null, null, resolutions, null,
                       'colorBalance=histogramMatching, cbreference=image',
                       'blocking=optimalpadding, blocksize=(512,512,3)',
                        gr, null, 'parallel=4', refereneImage=>ref_gr);

         update georaster_table set georaster = gr where georid=10;
         commit;
    END;
    /

Example 6-22 STATISTICSMATCHING Color Balancing

This example shows how to use the `STATISTICSMATCHING` color balancing method on the source images in the [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md)procedure. The reference statistics values are calculated from the overlapped area of the neighboring images. This requires that the source images have significant overlaps so that the statistics of the overlapped area can reflect the color difference between neighboring images.

    DECLARE
    gr sdo_georaster;
    resolutions  sdo_number_array;
    BEGIN
        -- create the new GeoRaster object for mosaic
        insert into georaster_table (georid, georaster)
            values (10, sdo_geor.init('RDT_1',10))
             returning georaster into gr;

        -- set the output resolution
        resolutions := sdo_number_array(30, 30);

        -- Mosaic
        sdo_geor_aggr.MosaicSubset('georaster_table_1',
                       'georaster', null, 32610, null, null, null, null,
                        null, null, null, resolutions, null,
                       'colorBalance=statisticsMatching, cbreference=overlap',
                       'blocking=optimalpadding, blocksize=(512,512,3)',
                        gr, null, 'parallel=4');

         update georaster_table set georaster = gr where georid=10;
         commit;
    END;
    /

**Parent topic:** Large-Scale Image Mosaicking

#### 6.17.2 Parallel Compression, Copying, and Subsetting

To parallelize rectification, orthorectification and reprojecting, use [SDO_GEOR.rectify](SDO_GEOR-reference.md). To parallelize warping, call [SDO_GEOR.warp](SDO_GEOR-reference.md). All raster algebra operations are parallelized too.

You can use the [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) procedure to conduct several types of parallel operations, including parallel compression and decompression, parallel copying or change format copying, parallel subsetting, parallel reprojection, and parallel rectification. The copying and subsetting operations are not parallelized directly. For JPEG and DEFLATE, the [SDO_GEOR.changeFormatCopy](SDO_GEOR-reference.md) procedure can be called to do parallel compression and decompression if reformatting is not required. This topic gives some examples for parallelized compressing, copying, and subsetting operations. In all these cases, the [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) procedure works on single GeoRaster objects.

To illustrate the parallelized operations, the examples in this section use a null value for most parameters. In your applications, you can apply all other parameters of the [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) procedure; however, the `mosaicParam` parameter has no effect when the input is a single GeoRaster object.

Example 6-23 Parallel Compression

Example 6-23 shows parallel compression using the [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) procedure. This applies to both DEFLATE and JPEG compression and decompression.

    DECLARE
      gr sdo_georaster;
      cur sys_refcursor;
      crop_area sdo_geometry := null;
    BEGIN
      -- create a new georaster object with georid = 2
      -- to hold the compressed image
      delete from georaster_table where georid = 2;
      insert into georaster_table(georid, georaster) values (2,
         sdo_geor.init('RDT2', 2)) returning georaster into gr;


      -- reblock and compress the image with georid = 1 into JPEG using parallel degree of 8
      open cur for 'select georaster from georaster_table where georid = 1';
      sdo_geor_aggr.mosaicSubset(cur, 0, null, null, null, crop_area,
                                 null, null, null, null, null, null,
                                 'compression=JPEG-F, blocking=optimalpadding, blocksize=(512,512,3)',
                                 gr, null, 'parallel=8');

      update georaster_table set georaster = gr where georid = 2;
      commit;
    END;
    /

In the preceding example, if you adjust the storageParam parameter, it works as a parallelized [SDO_GEOR.changeFormatCopy](SDO_GEOR-reference.md) operation, including compression and decompression.

Example 6-24 Parallel Subsetting and Copying

Example 6-24 shows parallel subsetting and copying using the[SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) procedure.

    DECLARE
      gr sdo_georaster;
      cur sys_refcursor;
      crop_area sdo_geometry := null;
    BEGIN
      -- create a new georaster object with georid = 2 to hold the copy
      delete from georaster_table where georid = 2;
      insert into georaster_table(georid, georaster) values (2,
         sdo_geor.init('RDT2', 2)) returning georaster into gr;


      -- set the crop_area for subsetting.
      crop_area := sdo_geometry(2003, 26986, null, sdo_elem_info_array(1,1003,1),
                    sdo_ordinate_array(237040,   897924,
                                       237013.3, 897831.6,
                                       237129,   897840,
                                       237182.5, 897785.5,
                                       237239.9, 897902.7,
                                       237223,   897954,
                                       237133,   897899,
                                       237040,   897924));

      -- subset from the image with georid = 1 using parallel degree of 8
      -- and do polygon clipping
      -- If the crop_area is set to null, the same call will do a simple parallelized copying without subsetting.
      open cur for 'select georaster from georaster_table where georid = 1';
      sdo_geor_aggr.mosaicSubset(cur, 0, null, null, null, crop_area,
                                 'true', null, null, null, null, null,
                                 'pyramid=true', gr, null, 'parallel=8');
      update georaster_table set georaster = gr where georid = 2;
      commit;
    END;
    /

In Example 6-24, if you adjust the `storageParam` parameter, it works as a parallelized copy or [SDO_GEOR.changeFormatCopy](SDO_GEOR-reference.md) operation, including compression and decompression.

**Parent topic:** Large-Scale Image Mosaicking

### 6.18 Virtual Mosaic

A virtual mosaic treats a set of GeoRaster images as one large virtually mosaicked image.

For some applications, mosaicking a collection of images into a single physical mosaic is not necessary or desirable. For example, you might not have enough disk space for storing the mosaic separately or you simply want to save disk space. Another example is if you do not want to keep two identical copies of the same data set but prefer to have the original data set stored as is, such as a DEM data set, yet you want to query over this data set seamlessly. Yet another example is if you want to apply different processing and mosaicking rules for the same region when mosaicking the source images -- a physical mosaic has no such flexibility.

In such cases, instead of mosaicking a set of GeoRaster images into one large GeoRaster image and storing it in a GeoRaster table, you can create a virtual mosaic. A virtual mosaic treats a set of GeoRaster images as one large virtually mosaicked image, without storing it in a GeoRaster table.

In GeoRaster, a virtual mosaic is defined as any large collection of georeferenced GeoRaster objects, rectified or unrectified, from one or more GeoRaster tables or views that is treated as if it is a single GeoRaster object. Pyramids of virtual mosaic are supported. A virtual mosaic can contain unlimited number of images, and a whole GeoRaster database can be treated as a virtual mosaic. You issue a single call to query the virtual mosaic based on area-of-interest (that is, subsetting or cropping), and you can request the cropped images to be in different coordinate system with different resolutions. On-the-fly transformations with resampling and mosaicking with common point rules, based on user requests, are done internally and automatically during the query processes.

The following are ways to define a virtual mosaic:

- As a GeoRaster table or a list of GeoRaster tables (see Virtual Mosaic as One or a List of GeoRaster Tables)

- As a database view with a GeoRaster column (see Virtual Mosaic as a View with a GeoRaster Column)

- As a SQL query statement (a cursor) that results in a collection of GeoRaster objects (see Virtual Mosaic as a SQL Query Statement or a Cursor)

Regardless of how the virtual mosaic is defined, the GeoRaster objects in the GeoRaster tables must have the `spatialExtent` attribute generated or set; otherwise, the [SDO_GEOR_AGGR.getMosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) and [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) procedures return an empty lob locator or empty GeoRaster object. For general use cases and best query performance, you should always create a spatial index beforehand on the `spatialExtent` attribute.

After a virtual mosaic is defined, you can use these procedures to query or process it:

- [SDO_GEOR_AGGR.getMosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) to perform on-the-fly queries over the virtual mosaic

  In spatial query of any portion of that virtually mosaicked image, the [SDO_GEOR_AGGR.getMosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) procedure performs the mosaic operation dynamically for the queried area and returns the required result in a BLOB on-the-fly, as if it were subsetting a physically stored mosaicked image.

- [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) to store the mosaicked subset in the database as a GeoRaster object

  The [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) procedure performs the mosaic operation for the queried area and stores the required result in another GeoRaster object persistently

For a typical workflow of using virtual mosaic, see Using Virtual Mosaic in Applications, and Special Considerations for Large-Scale Virtual Mosaic and its related topic Improving Query Performance Using MIN_X_RES\$ and MAX_X_RES\$.

- Virtual Mosaic as One or a List of GeoRaster Tables
- Virtual Mosaic as a View with a GeoRaster Column
- Virtual Mosaic as a SQL Query Statement or a Cursor
- Using Virtual Mosaic in Applications
- Special Considerations for Large-Scale Virtual Mosaic

**Parent topic:** Image Processing and Virtual Mosaic

#### 6.18.1 Virtual Mosaic as One or a List of GeoRaster Tables

A virtual mosaic can be defined as one GeoRaster table or a list of GeoRaster tables. Applications specify each table and its GeoRaster column. In this approach, all GeoRaster objects in the specified GeoRaster columns of those GeoRaster tables are part of the virtual mosaic.

Example 6-25 specifies the source images for virtual mosaicking in a list of GeoRaster tables (GRTAB1, GRTAB2, and GRTAB3, which have the same definitions as GRTAB in Large-Scale Image Mosaicking).

Example 6-25 Virtual Mosaic as a List of GeoRaster Tables

    DECLARE
      lb blob;
      cropArea sdo_geometry;
      outArea  sdo_geometry := null;
      outWin   sdo_number_array:=null;
      resolutions sdo_number_array;
    BEGIN
        dbms_lob.createTemporary(lb, TRUE);

         cropArea :=  sdo_geometry(2003, 32610, null,
                        sdo_elem_info_array(1, 1003, 3),
                        sdo_ordinate_array(399180, 4247820,
                                           496140,4353900) );
          resolutions := sdo_number_array(30, 30);
         sdo_geor_aggr.getMosaicSubset('grtab1, grtab2, grtab3',
                     'grobj, grobj, grobj',
                     0, 32610, null, null, cropArea,
                     null, null, null, resolutions, null,
                     'commonPointRule = end, nodata=true',
                     lb, outArea, outWin);
        dbms_lob.freeTemporary(lb);
        if outWin is not null then
            dbms_output.put_line('output window: (' || outWin(1) || ',' || outWin(2) ||', ' || outWin(3) || ', ' || outWin(4) || ')');
        end if;
    END;
    /

**Parent topic:** Virtual Mosaic

#### 6.18.2 Virtual Mosaic as a View with a GeoRaster Column

A virtual mosaic can be defined as one database view with a GeoRaster column. Applications specify the view name and its GeoRaster column. In this approach, all GeoRaster objects in the specified GeoRaster column of the view are part of the virtual mosaic. This approach allows you to select the images for the virtual mosaic in complex ways from any number of GeoRaster tables, taking advantage of the spatial index and any other relevant indexes.

You can also define a virtual mosaic as a list combining GeoRaster views and GeoRaster tables.

When a virtual mosaic is defined as a database view, the view can be specified in the `georasterTableNames` parameter when you query it. Example 6-26 queries the virtual mosaic defined as a view. Note that in this example, the queries sort the images based on their creation time and pick the latest (newest) image for the resulting mosaic in the overlapping areas.

Example 6-26 Using a View on GeoRaster Tables for Virtual Mosaic

    Create or replace view grview as select * from (
           Select grobj, last_update from grtab1 where cloud_cover=0 union all
           Select grobj, last_update from grtab2 where cloud_cover=0 union all
           Select grobj, last_update from grtab3 ) order by last_update;

    DECLARE
      lb blob;
      cropArea sdo_geometry;
      outArea  sdo_geometry := null;
      outWin   sdo_number_array:=null;
      resolutions sdo_number_array;
    BEGIN
        dbms_lob.createTemporary(lb, TRUE);

         cropArea :=  sdo_geometry(2003, 32610, null,
                        sdo_elem_info_array(1, 1003, 3),
                        sdo_ordinate_array(399180, 4247820,
                                           496140,4353900) );
          resolutions := sdo_number_array(30, 30);
         sdo_geor_aggr.getMosaicSubset('grview', 'grobj',
                     0, 32610, null, null, cropArea,
                     null, null, null, resolutions, null,
                     'commonPointRule = end, nodata=true',
                     lb, outArea, outWin);
        dbms_lob.freeTemporary(lb);
        if outWin is not null then
            dbms_output.put_line('output window: (' || outWin(1) || ',' || outWin(2) ||', ' || outWin(3) || ', ' || outWin(4) || ')');
        end if;
    END;
    /

**Parent topic:** Virtual Mosaic

#### 6.18.3 Virtual Mosaic as a SQL Query Statement or a Cursor

Instead of creating a view, you can define a virtual mosaic as a SQL statement or a runtime database cursor, which selects a collection of GeoRaster objects from the database. Applications create the cursor from the SQL statement and use the cursor as the virtual mosaic. In this definition, all GeoRaster objects in the cursor are part of the virtual mosaic. This approach allows you to select the images for the virtual mosaic in complex ways from any number of GeoRaster tables. However, the spatial indexes are not automatically used in queries over this type of virtual mosaic. To take advantage of spatial indexes, dynamically add a spatial query condition directly using the query window to the SQL statement, so that all images in that query window can be more quickly located.

The [SDO_GEOR_AGGR.getMosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) and [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md)procedures accept a cursor of GeoRaster objects as the virtual mosaic, as shown in Example 6-27. Note that in this example, the queries sort the images based on their creation time and pick the latest (newest) image for the resulting mosaic in the overlapping areas. For best performance when there are many GeoRaster objects in the table, the query of the cursor should use the spatial query window to filter out the unrelated GeoRaster objects, as described in the preceding paragraph.

Example 6-27 Using a Cursor for Virtual Mosaic

    DECLARE
      lb blob;
      outArea  sdo_geometry := null;
      outWin   sdo_number_array:=null;
      resolutions sdo_number_array;
      mosaic_stmt  varchar2(1000);
      condition        varchar2(1000);
    BEGIN
        dbms_lob.createTemporary(lb, TRUE);

        resolutions := sdo_number_array(30, 30);

       -- Define the query window (cropArea)
       cropArea := sdo_geometry(2003, 32610, null,
                               sdo_elem_info_array(1, 1003, 3),
                               sdo_ordinate_array(399180, 4247820, 496140,4353900) );

        -- Define the virtual mosaic
        mosaic_stmt := 'select grobj from (select grobj, last_update from grtab1 ' ||
                       'where cloud_cover=0  union all select grobj, last_update from grtab2 ' ||
                       'where cloud_cover=0) t ';

       -- Apply filtering using the query window (cropArea) to speed up query performance
        condition := 'where sdo_anyinteract(t.grobj.spatialExtent,:1) = ''true'' ' ||
                     ' order by last_update';

       -- Open the virtual mosaic for query
        open cur for mosaic_stmt || condition using cropArea;

       -- Query the virtual mosaic (make sure the cropArea used here is the same
       -- as the one used at opening the cursor)
        sdo_geor_aggr.getMosaicSubset(cur,
                     0, 32610, null, null, cropArea,
                     null, null, null, resolutions, null,
                     'commonPointRule=end, nodata=true',
                     lb, outArea, outWin);
        dbms_lob.freeTemporary(lb);
        close cur;
        if outWin is not null then
            dbms_output.put_line('output window: (' || outWin(1) || ',' || outWin(2) ||', ' || outWin(3) || ', ' || outWin(4) || ')');
        end if;
    END;
    /

**Parent topic:** Virtual Mosaic

#### 6.18.4 Using Virtual Mosaic in Applications

Virtual mosaic can be used as an image serving engine and in a variety of other application scenarios. The definitions of virtual mosaics can be stored by applications separately as strings or other forms. Besides the major query procedures [SDO_GEOR_AGGR.getMosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) and [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md), GeoRaster provides other subprograms in the SDO_GEOR_AGGR package to facilitate application development:

- [SDO_GEOR_AGGR.validateForMosaicSubset](SDO_GEOR_AGGR-referencer-ref.md)

- [SDO_GEOR_AGGR.getMosaicExtent](SDO_GEOR_AGGR-referencer-ref.md)

- [SDO_GEOR_AGGR.getMosaicResolutions](SDO_GEOR_AGGR-referencer-ref.md)

[SDO_GEOR_AGGR.validateForMosaicSubset](SDO_GEOR_AGGR-referencer-ref.md), [SDO_GEOR_AGGR.getMosaicExtent](SDO_GEOR_AGGR-referencer-ref.md), and [SDO_GEOR_AGGR.getMosaicResolutions](SDO_GEOR_AGGR-referencer-ref.md) can be called in an application to make sure that the virtual mosaic is valid and that the spatial query falls inside the virtual mosaic. The following steps describe a possible workflow for virtual mosaic in an application:

1.  Define a virtual mosaic. For example:
        Create or replace view grview as select * from (
        Select grobj, last_update from grtab1 where cloud_cover=0 union all
        Select grobj, last_update from grtab2 where cloud_cover=0 union all
        Select grobj, last_update from grtab3 ) order by last_update;

    Note that tables GRTAB1, GRTAB2, and GRTAB3 were created using the same definition as GRTAB in Large-Scale Image Mosaicking, and Oracle Spatial and Graph spatial indexes have been created on the `spatialExtent` attribute of the GeoRaster object in these tables.
2.  Validate the virtual mosaic data set. For example:
        EXECUTE SDO_GEOR_AGGR.validateForMosaicSubset('grview', 'grobj', OUTSRID, OUTResolutions);

    A validation error table can be created and passed to the call if more detailed validation information is needed. See the [SDO_GEOR_AGGR.validateForMosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) reference section for details.
3.  Get the spatial extent of the virtual mosaic. For example:
        SELECT SDO_GEOR_AGGR.getMosaicExtent('grview', 'grobj', OUTSRID) from dual;
4.  Get the resolution range of the existing source images. For example:
        SELECT SDO_GEOR_AGGR.getMosaicResolutions('grview', 'grobj', 'unit=meter') from dual;

    The resolution range reflects the minimum and maximum resolutions of the source images, including all pyramid levels.
5.  Based on the information acquired in the preceding two steps, pass in the spatial query window `cropArea` and `OUTResolutions` according to the application requests to get a subset of the virtual mosaic and optionally to apply different resampling methods, different common point rules, special nodata handling, and color balancing. For example:
        SDO_GEOR_AGGR.getMosaicSubset('grview', 'grobj', null, OUTSRID, null, null,
          cropArea, null, null, null, OUTResolutions, null,
          'commonPointRule=end, nodata=true', lb, outArea, outWin);

    Note that `OUTResolutions` must be within the source image resolution range. If `OUTResolutions` is the same as the resolutions of the source image at a specified pyramid level, the pyramid data is used in the output mosaic; otherwise, the source image is scaled to the target resolution.

    A typical application repeatedly applies this step to query different areas of interest over the same virtual mosaic for image display, image distribution, or other purposes.

**Parent topic:** Virtual Mosaic

#### 6.18.5 Special Considerations for Large-Scale Virtual Mosaic

A virtual mosaic can contain just several images, but it can also contain tens of thousands or millions of images. Both [SDO_GEOR_AGGR.getMosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) and [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) automatically search (using native spatial indexes) the virtual mosaic for all images touching or inside the `cropArea` and check the resolutions of those images and their pyramids. Only those images or their appropriate pyramid levels touching or inside the `cropArea` and with their resolutions close to the requested resolution will be used in the mosaicking process. So, the configuration of the source images and their pyramids is critical for the quality of the results and the overall query performance.

The guideline is to avoid too many small images from either different source images or their pyramids in the requested crop areas at the requested resolution.

For a smaller virtual mosaic with only a limited number of images, simply generate full pyramids for each source image, and the query performance will be good for most applications.

For a large area with a larger number of images (more than a few hundred images), the application can generate only a certain number of pyramid levels for each source image, mosaic their top pyramids into new GeoRaster objects, and then generate pyramids for those mosaics, and so forth. For large-scale web visualization projects, all images at source resolutions and at lower resolution levels might be stored as GeoRaster objects without any pyramids built for them.

In these cases (large number of images and large-scale web visualization), if each source image is small and there are many resolution levels in the virtual mosaic, a query on the lower resolution levels would involve metadata resolution queries on many unnecessary images at the higher resolution levels, which slows the query. To improve performance, applications can define many virtual mosaics, each of which includes only all the images at a specific resolution or a few resolution levels. Then, the application finds the right virtual mosaic or mosaics based on the requested resolution as the first step, and then only spatially queries those selected virtual mosaics. This approach can significantly improve performance.

In addition to the preceding considerations, see Improving Query Performance Using MIN_X_RES\$ and MAX_X_RES\$ for queries where many different resolution levels are involved for the same area.

- Improving Query Performance Using MIN_X_RES\$ and MAX_X_RES\$

**Parent topic:** Virtual Mosaic

##### 6.18.5.1 Improving Query Performance Using MIN_X_RES\$ and MAX_X_RES\$

A more general solution (instead of defining multiple virtual mosaics) for speeding virtual mosaic queries if there are many different resolution levels involved for the same area is to use the resolution range columns (MIN_X_RES\$ and MAX_X_RES\$) in the GeoRaster tables or views. You must define these columns (NUMBER data type) in the GeoRaster tables of a virtual mosaic, where they specify the minimum and maximum spatial resolution values, respectively, of the source GeoRaster object. After these columns are added and populated with correct resolution data, the [SDO_GEOR_AGGR.getMosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) procedure will (if you use the format with the `georasterTableNames` parameter) use the resolution range stored in these columns to filter out the source GeoRaster objects that are not at the requested resolutions as specified in the `outResolutions` parameter. This avoids parsing the metadata of each GeoRaster objects in the `cropArea`, thus significantly improving performance.

To use this approach, follow these steps:

1.  Add the columns MIN_X_RES\$ and MAX_X_RES\$ to the GeoRaster tables. For example:
        ALTER TABLE georaster_table ADD (MIN_X_RES$ number, MAX_X_RES$ number);
2.  Populate the MIN_X_RES\$ column. For example:
        UPDATE georaster_table t
          SET min_x_res$ = (select column_value from the
            (select sdo_geor.generateSpatialResolutions(t.georaster, null,
            t.georaster.spatialextent.sdo_srid) from dual)
          WHERE rownum=1);
3.  Populate the MAX_X_RES\$ column. For example:
        UPDATE georaster_table t
          max_x_res$ = min_x_res$ * power(2, sdo_geor.getPyramidMaxLevel(t.georaster));
4.  Optionally, create index on the resolution range columns if the table contains large number of source images:
        CREATE INDEX georaster_table_res_idx ON georaster_table(MIN_X_RES$, MAX_X_RES$);

If the virtual mosaic is defined as a view, the view should also have both columns. For example, the view definition in Example 6-26 must be changed to the following:

    Create or replace view grview as select * from (
           Select grobj, min_x_res$, max_x_res$, last_update from grtab1 where cloud_cover=0 union all
           Select grobj, min_x_res$, max_x_res$, last_update from grtab2 where cloud_cover=0 union all
           Select grobj, min_x_res$, max_x_res$, last_update from grtab3 )
           order by last_update;

After a virtual mosaic is defined as described in this section, applications can query and use it in the same ways as with all other virtual mosaics, but with better performance for large-scale virtual mosaics that involve many resolution levels. For more information, see the [SDO_GEOR_AGGR.getMosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) and [SDO_GEOR_AGGR.mosaicSubset](SDO_GEOR_AGGR-referencer-ref.md) reference sections.

**Parent topic:** Special Considerations for Large-Scale Virtual Mosaic

### 6.19 Image Serving

Serving of image and raster data to clients or applications is supported through many features of the GeoRaster PL/SQL and Java APIs.

Direct image serving includes searching and then subsetting or cropping the rasters ([SDO_GEOR.getRasterSubset](SDO_GEOR-reference.md)), applying reprojection and rectification on-the-fly while cropping the images ([SDO_GEOR.reproject](SDO_GEOR-reference.md) and [SDO_GEOR.rectify](SDO_GEOR-reference.md)), and directly exporting to files ([SDO_GEOR.exportTo](SDO_GEOR-reference.md)).

Virtual mosaic is used mainly, and effectively, to serve an image database to various applications, particularly when you do not want to create large physical mosaics. Virtual mosaic does not require the source images to be preprocessed or mosaicked beforehand. Instead, all images are stored as is, and the whole image data set can be served based on small areas of interest using single calls ([SDO_GEOR_AGGR.getMosaicSubset](SDO_GEOR_AGGR-referencer-ref.md)) to the server.

Often, one or a series of preprocessing operations are applied to multiple GeoRaster objects to create the resulting GeoRaster object, and then the features described in this section are used on the resulting GeoRaster object to serve the raster data directly to applications. Thus, a rich set of GeoRaster image manipulation and raster algebra capabilities (described in [GeoRaster Data Query and Manipulation](georaster-data-manipulation.md), [Raster Algebra and Analytics](raster-algebra-and-analytics.md), and this chapter) can be incorporated into the workflow to meet complex image serving requirements.

**Parent topic:** Image Processing and Virtual Mosaic
