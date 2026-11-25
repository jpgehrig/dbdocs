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

- [Prev Class](RasterInfo.md)
- [Next Class](SubLayerInfo.md)

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

## Class SpatialReferenceInfo

- java.lang.Object

- - oracle.spatial.georaster.SpatialReferenceInfo

<!-- -->

-

  ------------------------------------------------------------------------



      public class SpatialReferenceInfo
      extends java.lang.Object

  SpatialReferenceInfo is a Java class mapped to the XML element SpatialReferenceInfo in the Oracle Spatial GeoRaster metadata.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                                               |
    |---------------------------|-----------------------------------------------------------------------------------------------------|
    | `static int`              | `GCPPOINT_STATUS_ESTIMATED`<br>An integer indicating gcpPointStatus Estimated.                      |
    | `static int`              | `GCPPOINT_STATUS_INVALID`<br>An integer indicating gcpPointStatus Invalidated.                      |
    | `static int`              | `GCPPOINT_STATUS_MEASURED`<br>An integer indicating gcpPointStatus Measured.                        |
    | `static int`              | `GCPPOINT_STATUS_REMOVED`<br>An integer indicating gcpPointStatus Removed.                          |
    | `static int`              | `GCPPOINT_STATUS_VALIDATED`<br>An integer indicating gcpPointStatus Validated.                      |
    | `static int`              | `GCPPOINT_TYPE_CHECKPOINT`<br>An integer indicating gcpPoint type CheckPoint.                       |
    | `static int`              | `GCPPOINT_TYPE_CONTROLPOINT`<br>An integer indicating gcpPoint type ControlPoint.                   |
    | `static int`              | `GEOREFERENCE_TYPE_AFFINE`<br>An integer indicating geoReference type affine.                       |
    | `static int`              | `GEOREFERENCE_TYPE_CUBICPOLYNOMIAL`<br>An integer indicating geoReference type CubicPolynomial.     |
    | `static int`              | `GEOREFERENCE_TYPE_DLT`<br>An integer indicating geoReference type DLT.                             |
    | `static int`              | `GEOREFERENCE_TYPE_QUADRATICPOLYNOMIAL`                                                             |
    | `static int`              | `GEOREFERENCE_TYPE_QUADRATICRATIONAL`<br>An integer indicating geoReference type QuadraticRational. |
    | `static int`              | `GEOREFERENCE_TYPE_RPC`<br>An integer indicating geoReference type RPC.                             |
    | `static int`              | `GEOREFERENCE_TYPE_UNKNOWN`<br>An integer indicating geoReference type UNKNOWN.                     |
    | `static int`              | `MDGRX_SRM_FUNCFITTING`<br>An integer indicating modelType FunctionalFitting.                       |
    | `static int`              | `MDGRX_SRM_RIGOROUS`<br>An integer indicating modelType RigorousModel.                              |
    | `static int`              | `MDGRX_SRM_STOREDFUNC`<br>An integer indicating modelType StoredFunction.                           |
    | `static java.lang.String` | `MODEL_DIMENSION_S`<br>A string indicating the S dimension in the GeoRaster model space.            |
    | `static java.lang.String` | `MODEL_DIMENSION_T`<br>A string indicating the T dimension in the GeoRaster model space.            |
    | `static java.lang.String` | `MODEL_DIMENSION_X`<br>A string indicating the X dimension in the GeoRaster model space.            |
    | `static java.lang.String` | `MODEL_DIMENSION_Y`<br>A string indicating the Y dimension in the GeoRaster model space.            |
    | `static java.lang.String` | `MODEL_DIMENSION_Z`<br>A string indicating the Z dimension in the GeoRaster model space.            |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                             | Method and Description                                                                                                                                                                                                                                                              |
    |---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                        | `addGcpPoints``(java.util.Vector points)`<br>Append the GCP points to existing GCP points.                                                                                                                                                                                          |
    | `double[]`                                                    | `computeSpatialResolutions``(int pyramidLevel)`<br>Computes the spatial resolution based on GeoReference information.                                                                                                                                                               |
    | `double[]`                                                    | `getCellCoordinate``(double x, double y, long pyramidLevel)`<br>Calculates cell coordinates based on given model coordinates.                                                                                                                                                       |
    | `double[]`                                                    | `getCellCoordinate``(double x, double y, long pyramidLevel, double height)`<br>Calculates cell coordinates based on given model coordinates.                                                                                                                                        |
    | [`JGeometry`](../geometry/JGeometry.md)                       | `getCellCoordinate``(`[`JGeometry`](../geometry/JGeometry.md)` geometry, int pyramidLevel)`<br>Transforms a geometry in the ground coordinate system to the location of a geometry in the raster space of the GeoRaster object.                                                     |
    | [`JGeometry`](../geometry/JGeometry.md)                       | `getCellCoordinate``(`[`JGeometry`](../geometry/JGeometry.md)` geometry, int pyramidLevel, double height)`<br>Transforms a geometry in the ground coordinate system to the location of a geometry in the raster space of the GeoRaster object.                                      |
    | `java.lang.String`                                            | `getDescription``()`<br>Returns the georeference description.                                                                                                                                                                                                                       |
    | [`GeorFunctionalFittingModel`](GeorFunctionalFittingModel.md) | `getFunctionalFittingModel``()`<br>Returns a GeorFunctionFittingModel object based on XML metadata.                                                                                                                                                                                 |
    | `int`                                                         | `getGcpFFMethod``()`<br>Returns the GCP FFMethod.                                                                                                                                                                                                                                   |
    | `java.util.Vector`                                            | `getGcpPoints``()`<br>Returns the GCP points.                                                                                                                                                                                                                                       |
    | `java.lang.String`                                            | `getGcpTableName``()`<br>Returns the GCP table name.                                                                                                                                                                                                                                |
    | `int`                                                         | `getGeoreferenceType``()`<br>Returns the georeference type.                                                                                                                                                                                                                         |
    | `double[]`                                                    | `getModelCoordinate``(double row, double column, long pyramidLevel)`<br>calculate model coordinates based on given cell coordinates.                                                                                                                                                |
    | `double[]`                                                    | `getModelCoordinate``(double row, double column, long pyramidLevel, double height)`<br>calculate model coordinates based on given cell coordinates.                                                                                                                                 |
    | [`JGeometry`](../geometry/JGeometry.md)                       | `getModelCoordinate``(`[`JGeometry`](../geometry/JGeometry.md)` geometry, int pyramidLevel, int targetSRID)`<br>Transforms a geometry in the raster space of the GeoRaster object to a geometry in the ground coordinate system.                                                    |
    | [`JGeometry`](../geometry/JGeometry.md)                       | `getModelCoordinate``(`[`JGeometry`](../geometry/JGeometry.md)` geometry, int pyramidLevel, int targetSRID, double height)`<br>Transforms a geometry in the raster space of the GeoRaster object to a geometry in the ground coordinate system.                                     |
    | `java.lang.String`                                            | `getModelCoordinateLocation``()`<br>Returns the model coordinate location.                                                                                                                                                                                                          |
    | `java.lang.String`                                            | `getModelDimensionDescription``()`<br>Returns the model dimension description.                                                                                                                                                                                                      |
    | `java.lang.Integer`                                           | `getModelSRID``()`<br>Returns the SRID.                                                                                                                                                                                                                                             |
    | `int`                                                         | `getModelType``()`<br>Returns the model type.                                                                                                                                                                                                                                       |
    | `java.lang.Double`                                            | `getSpatialResolution``(java.lang.String dimension)`<br>Returns the spatial resolution of the specified dimension stored in the XML without verification and computing; this means return value might be different from the value returned by the method computeSpatialResolutions. |
    | `java.lang.Double`                                            | `getSpatialTolerance``()`<br>Returns the spatial tolerance.                                                                                                                                                                                                                         |
    | `java.lang.Integer`                                           | `getVerticalSRID``()`<br>Returns the vertical SRID.                                                                                                                                                                                                                                 |
    | `java.lang.Boolean`                                           | `isOrthoRectified``()`<br>Returns true if the current GeoRaster object is orthorectified.                                                                                                                                                                                           |
    | `java.lang.Boolean`                                           | `isRectified``()`<br>Returns true if the current GeoRaster object is rectified.                                                                                                                                                                                                     |
    | `java.lang.Boolean`                                           | `isReferenced``()`<br>Returns true if the current GeoRaster object is georeferenced.                                                                                                                                                                                                |
    | `void`                                                        | `setDescription``(java.lang.String description)`<br>Sets the georeference description.                                                                                                                                                                                              |
    | `void`                                                        | `setFunctionFittingModel``(`[`GeorFunctionalFittingModel`](GeorFunctionalFittingModel.md)` srs)`<br>Initiates attribute values based on a given GeorFunctionFittingModel object.                                                                                                    |
    | `void`                                                        | `setGcpFFMethod``(int FFMethod)`<br>Sets the GCP FFMethod.                                                                                                                                                                                                                          |
    | `void`                                                        | `setGcpPoints``(java.util.Vector points)`<br>Sets the GCP points.                                                                                                                                                                                                                   |
    | `void`                                                        | `setGcpTableName``(java.lang.String gcpTableName)`<br>Sets the GCP table name.                                                                                                                                                                                                      |
    | `void`                                                        | `setModelCoordinateLocation``(java.lang.String modelCoordinateLocation)`<br>Sets the model coordinate location.                                                                                                                                                                     |
    | `void`                                                        | `setModelDimensionDescription``(java.lang.String modelDimensionDescription)`<br>Sets the model dimension description.                                                                                                                                                               |
    | `void`                                                        | `setModelSRID``(java.lang.Integer SRID)`<br>Sets the SRID.                                                                                                                                                                                                                          |
    | `void`                                                        | `setModelType``(int modelType)`<br>Sets the model type.                                                                                                                                                                                                                             |
    | `void`                                                        | `setOrthoRectified``(java.lang.Boolean isOrthoRectified)`<br>Sets true if the current GeoRaster object is orthorectified.                                                                                                                                                           |
    | `void`                                                        | `setRectified``(java.lang.Boolean isRectified)`<br>Sets true if the current GeoRaster object is rectified.                                                                                                                                                                          |
    | `void`                                                        | `setReferenced``(java.lang.Boolean isReferenced)`<br>Sets true if the current GeoRaster object is georeferenced.                                                                                                                                                                    |
    | `void`                                                        | `setSpatialResolution``(java.lang.String dimension, java.lang.Double resolution)`<br>Sets the spatial resolution of the specified dimension.                                                                                                                                        |
    | `void`                                                        | `setSpatialTolerance``(java.lang.Double spatialTolerance)`<br>Sets the spatial tolerance.                                                                                                                                                                                           |
    | `void`                                                        | `setWorldFile``(double A, double B, double C, double D, double E, double F)`<br>Initiates attribute values based on given parameters in a world file.                                                                                                                               |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### MODEL_DIMENSION_X

          public static final java.lang.String MODEL_DIMENSION_X

      A string indicating the X dimension in the GeoRaster model space.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MODEL_DIMENSION_Y

          public static final java.lang.String MODEL_DIMENSION_Y

      A string indicating the Y dimension in the GeoRaster model space.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MODEL_DIMENSION_Z

          public static final java.lang.String MODEL_DIMENSION_Z

      A string indicating the Z dimension in the GeoRaster model space.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MODEL_DIMENSION_T

          public static final java.lang.String MODEL_DIMENSION_T

      A string indicating the T dimension in the GeoRaster model space.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MODEL_DIMENSION_S

          public static final java.lang.String MODEL_DIMENSION_S

      A string indicating the S dimension in the GeoRaster model space.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GEOREFERENCE_TYPE_UNKNOWN

          public static final int GEOREFERENCE_TYPE_UNKNOWN

      An integer indicating geoReference type UNKNOWN.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GEOREFERENCE_TYPE_AFFINE

          public static final int GEOREFERENCE_TYPE_AFFINE

      An integer indicating geoReference type affine.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GEOREFERENCE_TYPE_DLT

          public static final int GEOREFERENCE_TYPE_DLT

      An integer indicating geoReference type DLT.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GEOREFERENCE_TYPE_RPC

          public static final int GEOREFERENCE_TYPE_RPC

      An integer indicating geoReference type RPC.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GEOREFERENCE_TYPE_QUADRATICPOLYNOMIAL

          public static final int GEOREFERENCE_TYPE_QUADRATICPOLYNOMIAL

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GEOREFERENCE_TYPE_CUBICPOLYNOMIAL

          public static final int GEOREFERENCE_TYPE_CUBICPOLYNOMIAL

      An integer indicating geoReference type CubicPolynomial.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GEOREFERENCE_TYPE_QUADRATICRATIONAL

          public static final int GEOREFERENCE_TYPE_QUADRATICRATIONAL

      An integer indicating geoReference type QuadraticRational.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GCPPOINT_TYPE_CONTROLPOINT

          public static final int GCPPOINT_TYPE_CONTROLPOINT

      An integer indicating gcpPoint type ControlPoint.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GCPPOINT_TYPE_CHECKPOINT

          public static final int GCPPOINT_TYPE_CHECKPOINT

      An integer indicating gcpPoint type CheckPoint.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GCPPOINT_STATUS_MEASURED

          public static final int GCPPOINT_STATUS_MEASURED

      An integer indicating gcpPointStatus Measured.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GCPPOINT_STATUS_REMOVED

          public static final int GCPPOINT_STATUS_REMOVED

      An integer indicating gcpPointStatus Removed.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GCPPOINT_STATUS_ESTIMATED

          public static final int GCPPOINT_STATUS_ESTIMATED

      An integer indicating gcpPointStatus Estimated.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GCPPOINT_STATUS_VALIDATED

          public static final int GCPPOINT_STATUS_VALIDATED

      An integer indicating gcpPointStatus Validated.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GCPPOINT_STATUS_INVALID

          public static final int GCPPOINT_STATUS_INVALID

      An integer indicating gcpPointStatus Invalidated.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MDGRX_SRM_RIGOROUS

          public static final int MDGRX_SRM_RIGOROUS

      An integer indicating modelType RigorousModel.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MDGRX_SRM_STOREDFUNC

          public static final int MDGRX_SRM_STOREDFUNC

      An integer indicating modelType StoredFunction.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MDGRX_SRM_FUNCFITTING

          public static final int MDGRX_SRM_FUNCFITTING

      An integer indicating modelType FunctionalFitting.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### isReferenced

          public java.lang.Boolean isReferenced()

      Returns true if the current GeoRaster object is georeferenced.
      Returns:
      true if the current GeoRaster object is georeferenced.

    <!-- -->

    - #### setReferenced

          public void setReferenced(java.lang.Boolean isReferenced)

      Sets true if the current GeoRaster object is georeferenced.
      Parameters:
      `isReferenced` - true if the current GeoRaster object is georeferenced

    <!-- -->

    - #### isRectified

          public java.lang.Boolean isRectified()

      Returns true if the current GeoRaster object is rectified.
      Returns:
      true if the current GeoRaster object is rectified.

    <!-- -->

    - #### setRectified

          public void setRectified(java.lang.Boolean isRectified)

      Sets true if the current GeoRaster object is rectified.
      Parameters:
      `isRectified` - true if the current GeoRaster object is rectified

    <!-- -->

    - #### isOrthoRectified

          public java.lang.Boolean isOrthoRectified()

      Returns true if the current GeoRaster object is orthorectified.
      Returns:
      true if the current GeoRaster object is orthorectified.

    <!-- -->

    - #### setOrthoRectified

          public void setOrthoRectified(java.lang.Boolean isOrthoRectified)

      Sets true if the current GeoRaster object is orthorectified.
      Parameters:
      `isOrthoRectified` - true if the current GeoRaster object is orthorectified

    <!-- -->

    - #### getDescription

          public java.lang.String getDescription()

      Returns the georeference description.
      Returns:
      georeference description.

    <!-- -->

    - #### setDescription

          public void setDescription(java.lang.String description)

      Sets the georeference description.
      Parameters:
      `description` - georeference description

    <!-- -->

    - #### getModelSRID

          public java.lang.Integer getModelSRID()

      Returns the SRID.
      Returns:
      SRID.

    <!-- -->

    - #### setModelSRID

          public void setModelSRID(java.lang.Integer SRID)

      Sets the SRID.
      Parameters:
      `SRID` - SRID

    <!-- -->

    - #### getVerticalSRID

          public java.lang.Integer getVerticalSRID()

      Returns the vertical SRID.
      Returns:
      vertical SRID.

    <!-- -->

    - #### getModelDimensionDescription

          public java.lang.String getModelDimensionDescription()

      Returns the model dimension description.
      Returns:
      model dimension description.

    <!-- -->

    - #### setModelDimensionDescription

          public void setModelDimensionDescription(java.lang.String modelDimensionDescription)

      Sets the model dimension description.
      Parameters:
      `modelDimensionDescription` - model dimension description

    <!-- -->

    - #### getSpatialResolution

          public java.lang.Double getSpatialResolution(java.lang.String dimension)

      Returns the spatial resolution of the specified dimension stored in the XML without verification and computing; this means return value might be different from the value returned by the method computeSpatialResolutions.
      Parameters:
      `dimension` - specified dimension string

      Returns:
      spatial resolution of specified dimension.

    <!-- -->

    - #### computeSpatialResolutions

          public double[] computeSpatialResolutions(int pyramidLevel)

      Computes the spatial resolution based on GeoReference information.
      Parameters:
      `pyramidLevel` - specified pyramid level

      Returns:
      spatial resolution of X and Y dimension, if pyramidLevel\<0 then return spatial resolution of pyramid level 0.\< dd\>

    <!-- -->

    - #### setSpatialResolution

          public void setSpatialResolution(java.lang.String dimension,
                                           java.lang.Double resolution)

      Sets the spatial resolution of the specified dimension.
      Parameters:
      `dimension` - specified dimension string

      `resolution` - spatial resolution of specified dimension.

    <!-- -->

    - #### getSpatialTolerance

          public java.lang.Double getSpatialTolerance()

      Returns the spatial tolerance.
      Returns:
      spatial tolerance.

    <!-- -->

    - #### setSpatialTolerance

          public void setSpatialTolerance(java.lang.Double spatialTolerance)

      Sets the spatial tolerance.
      Parameters:
      `spatialTolerance` - spatial tolerance

    <!-- -->

    - #### getModelCoordinateLocation

          public java.lang.String getModelCoordinateLocation()

      Returns the model coordinate location.
      Returns:
      model coordinate location.

    <!-- -->

    - #### setModelCoordinateLocation

          public void setModelCoordinateLocation(java.lang.String modelCoordinateLocation)

      Sets the model coordinate location.
      Parameters:
      `modelCoordinateLocation` - model coordinate location

    <!-- -->

    - #### getModelType

          public int getModelType()

      Returns the model type.
      Returns:
      model type.

    <!-- -->

    - #### setModelType

          public void setModelType(int modelType)

      Sets the model type.
      Parameters:
      `modelType` - model type

    <!-- -->

    - #### getGcpFFMethod

          public int getGcpFFMethod()

      Returns the GCP FFMethod.
      Returns:
      GCP FFMethod.

    <!-- -->

    - #### setGcpFFMethod

          public void setGcpFFMethod(int FFMethod)

      Sets the GCP FFMethod.
      Parameters:
      `FFMethod` - GCP FFMethod

    <!-- -->

    - #### getGcpPoints

          public java.util.Vector getGcpPoints()

      Returns the GCP points.
      Returns:
      GCP points.

    <!-- -->

    - #### setGcpPoints

          public void setGcpPoints(java.util.Vector points)

      Sets the GCP points.
      Parameters:
      `points` - a vector of GCP points

    <!-- -->

    - #### addGcpPoints

          public void addGcpPoints(java.util.Vector points)

      Append the GCP points to existing GCP points.
      Parameters:
      `points` - a vector of GCP points

    <!-- -->

    - #### getGcpTableName

          public java.lang.String getGcpTableName()

      Returns the GCP table name.
      Returns:
      GCP table name.

    <!-- -->

    - #### setGcpTableName

          public void setGcpTableName(java.lang.String gcpTableName)

      Sets the GCP table name.
      Parameters:
      `gcpTableName` - GCP table name

    <!-- -->

    - #### getFunctionalFittingModel

          public GeorFunctionalFittingModel getFunctionalFittingModel()

      Returns a GeorFunctionFittingModel object based on XML metadata.
      Returns:
      GeorFunctionFittingModel object.

    <!-- -->

    - #### setWorldFile

          public void setWorldFile(double A,
                                   double B,
                                   double C,
                                   double D,
                                   double E,
                                   double F)
                            throws GeoRasterException

      Initiates attribute values based on given parameters in a world file.
      Parameters:
      `A` - parameter A defined in the worldfile

      `B` - parameter B defined in the worldfile

      `C` - parameter C defined in the worldfile

      `D` - parameter D defined in the worldfile

      `E` - parameter E defined in the worldfile

      `F` - parameter F defined in the worldfile

      Throws:
      [`GeoRasterException`](GeoRasterException.md)

    <!-- -->

    - #### setFunctionFittingModel

          public void setFunctionFittingModel(GeorFunctionalFittingModel srs)

      Initiates attribute values based on a given GeorFunctionFittingModel object.
      Parameters:
      `srs` - GeorFunctionFittingModel object.

    <!-- -->

    - #### getGeoreferenceType

          public int getGeoreferenceType()

      Returns the georeference type.
      Returns:
      georeference type.

    <!-- -->

    - #### getModelCoordinate

          public double[] getModelCoordinate(double row,
                                             double column,
                                             long pyramidLevel)

      calculate model coordinates based on given cell coordinates.
      Parameters:
      `row` - row number in cell space, which already counts in row ULTCoordinate.

      `column` - column number in cell space, which already counts in column ULTCoordinate.

      `pyramidLevel` - pyramid level.

      Returns:
      model coordinates array (x,y)

    <!-- -->

    - #### getModelCoordinate

          public double[] getModelCoordinate(double row,
                                             double column,
                                             long pyramidLevel,
                                             double height)

      calculate model coordinates based on given cell coordinates.
      Parameters:
      `row` - row number in cell space, which already counts in row ULTCoordinate

      `column` - column number in cell space, which already counts in column ULTCoordinate

      `pyramidLevel` - pyramid level

      `height` - height

      Returns:
      model coordinates array (x,y)

    <!-- -->

    - #### getModelCoordinate

          public JGeometry getModelCoordinate(JGeometry geometry,
                                              int pyramidLevel,
                                              int targetSRID)
                                       throws java.lang.Exception

      Transforms a geometry in the raster space of the GeoRaster object to a geometry in the ground coordinate system. The SRID of ground coordinate system is specified by parameter targetSRID.
      Parameters:
      `geometry` - a geometry in the cell space

      `pyramidLevel` - pyramid level

      `targetSRID` - target SRID; must be greater than zero

      Returns:
      a geometry in the ground coordinate system

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getModelCoordinate

          public JGeometry getModelCoordinate(JGeometry geometry,
                                              int pyramidLevel,
                                              int targetSRID,
                                              double height)
                                       throws java.lang.Exception

      Transforms a geometry in the raster space of the GeoRaster object to a geometry in the ground coordinate system. The SRID of ground coordinate system is specified by parameter targetSRID.
      Parameters:
      `geometry` - a geometry in the cell space

      `pyramidLevel` - pyramid level

      `targetSRID` - target SRID; must be greater than zero

      `height` - height

      Returns:
      a geometry in the ground coordinate system

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getCellCoordinate

          public double[] getCellCoordinate(double x,
                                            double y,
                                            long pyramidLevel)

      Calculates cell coordinates based on given model coordinates.
      Parameters:
      `x` - x in model space

      `y` - y in model space

      `pyramidLevel` - pyramid level

      Returns:
      cell coordinates array (row,column).

    <!-- -->

    - #### getCellCoordinate

          public double[] getCellCoordinate(double x,
                                            double y,
                                            long pyramidLevel,
                                            double height)

      Calculates cell coordinates based on given model coordinates.
      Parameters:
      `x` - x in model space

      `y` - y in model space

      `pyramidLevel` - pyramid level

      `height` - height

      Returns:
      cell coordinates array (row,column)

    <!-- -->

    - #### getCellCoordinate

          public JGeometry getCellCoordinate(JGeometry geometry,
                                             int pyramidLevel)

      Transforms a geometry in the ground coordinate system to the location of a geometry in the raster space of the GeoRaster object.
      Parameters:
      `geometry` - a geometry in the ground coordinate system

      `pyramidLevel` - pyramid level

      Returns:
      a geometry in the raster space of the GeoRaster object

    <!-- -->

    - #### getCellCoordinate

          public JGeometry getCellCoordinate(JGeometry geometry,
                                             int pyramidLevel,
                                             double height)

      Transforms a geometry in the ground coordinate system to the location of a geometry in the raster space of the GeoRaster object.
      Parameters:
      `geometry` - a geometry in the ground coordinate system

      `pyramidLevel` - pyramid level

      `height` - number specifying the Z value for three-dimensional (X, Y, Z) georeferencing

      Returns:
      a geometry in the raster space of the GeoRaster object

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

- [Prev Class](RasterInfo.md)
- [Next Class](SubLayerInfo.md)

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
