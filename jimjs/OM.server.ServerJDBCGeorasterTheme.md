------------------------------------------------------------------------

#### new ServerJDBCGeorasterTheme(name)

Constructs a new dynamic GeoRaster theme (JDBC theme). For example:


After a ServerJDBCTheme is instantiated, other attributes can then be added. For example:


Such a theme may be added into a server map request instance.
For example:

- var req = new OM.server.ServerMapRequest(baseURL);
- req.addTheme(jdbcLandsat);

##### Parameters:

| Name   | Type   | Description                                                                                            |
|--------|--------|--------------------------------------------------------------------------------------------------------|
| `name` | String | The name of the JDBC theme; the theme<br>will be built dynamically using the attributes in this class. |

### Extends

- [OM.server.ServerTheme](OM.server.ServerTheme.md)

### Methods

------------------------------------------------------------------------

#### clearPolygonMaskTableParameters()

Erases polygon mask information based on table parameters.

------------------------------------------------------------------------

#### getDataSourceName()

Get the current MapViewer data source name.

Inherited From:
- [OM.server.ServerTheme#getDataSourceName](OM.server.ServerTheme.md)

##### Returns:

returns the name of the data source.

Type
String

------------------------------------------------------------------------

#### setAlphaBand(bands)

Set the raster alpha band.

##### Parameters:

| Name    | Type   | Description           |
|---------|--------|-----------------------|
| `bands` | String | the alpha band index. |

------------------------------------------------------------------------

#### setAsVirtualMosaic(virtualMosiac)

Sets the GeoRaster theme as virtual mosaic theme or not.

##### Parameters:

| Name            | Type    | Description                              |
|-----------------|---------|------------------------------------------|
| `virtualMosiac` | Boolean | A true or false value. Default is false. |

------------------------------------------------------------------------

#### setBaseTable(name)

Sets the GeoRaster base table name.
This is not needed if theme definition is based on a SQL statement.

##### Parameters:

| Name   | Type   | Description                      |
|--------|--------|----------------------------------|
| `name` | String | The name of the GeoRaster table. |

------------------------------------------------------------------------

#### setBindingParameters(bParams)

Sets the binding parameters. It is an array of {value, type} objects, e.g.
\[
{value: '1', type: 'Integer'},
{value: '2', type: 'Integer'}
\]
The order and number of the parameter objects in the array must match those in the predefined theme in MapViewer theme metadata.

##### Parameters:

| Name      | Type  | Description                                              |
|-----------|-------|----------------------------------------------------------|
| `bParams` | Array | An array of bind parameter (i.e. {value, type}) objects. |

##### Returns:

Type
null

------------------------------------------------------------------------

#### setDataSourceName(dsrcName)

Set the name of the MapViewer data source where this theme is
defined.

##### Parameters:

| Name       | Type   | Description                            |
|------------|--------|----------------------------------------|
| `dsrcName` | String | The name of the MapViewer data source. |

Inherited From:
- [OM.server.ServerTheme#setDataSourceName](OM.server.ServerTheme.md)

------------------------------------------------------------------------

#### setExecuteAsis(flag)

Sets whether the query should be executed as-is on the server side. Default is false.
By default (i.e., false), a subsequent spatial filter is applied to only fetch the needed features to optimize the performance.

##### Parameters:

| Name   | Type    | Description                             |
|--------|---------|-----------------------------------------|
| `flag` | Boolean | A true or false value. Default is false |

------------------------------------------------------------------------

#### setGeorasterColumn(name)

Sets the georaster column name in the query result set.

##### Parameters:

| Name   | Type   | Description                                                    |
|--------|--------|----------------------------------------------------------------|
| `name` | String | The name of the georaster column name in the query result set. |

------------------------------------------------------------------------

#### setImageOperations()

Sets the image operation with its parameters.
Some operations like normalize, equalize and linear stretch makes use of statistics.
By default they are based on statistics of the image area being rendered, and therefore as each tile should have their own statisitics,
it will produce a map with not an uniform pattern.
In order to generate an uniform image across tiles, compute statistics for GeoRaster objects using PLSQL functions,
and then set the use of global statistics on this class.

##### Parameters:

| Type | Description |
|------|-------------|
|      |             |
|      |             |

------------------------------------------------------------------------

#### setImageOperationsUseGlobalStats(useGlobalStats)

Sets the use of computed global statistics for the follwoing operations:
normalize, equalize, and linear stretch (automatic, manual or piecewise).

##### Parameters:

| Name             | Type    | Description                                                                                                                                                                       |
|------------------|---------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `useGlobalStats` | Boolean | true to use global statistics (it must have computed and stored in GeoRaster objects)<br>false will use the statistics of each image tile area (non uniform rendering can happen) |

------------------------------------------------------------------------

#### setName(nm)

Set the theme name

##### Parameters:

| Name | Type   | Description           |
|------|--------|-----------------------|
| `nm` | String | The theme name to set |

Inherited From:
- [OM.server.ServerTheme#setName](OM.server.ServerTheme.md)

------------------------------------------------------------------------

#### setPolygonMaskCoordinates(mask)

Sets the polygon mask coordinates

##### Parameters:

| Name   | Type   | Description                                                                                                            |
|--------|--------|------------------------------------------------------------------------------------------------------------------------|
| `mask` | String | contains the X and Y values for each polyogn point.<br>For example: "20.0,80.0,50.0,80.0,50.0,40.,20.0,40.0,20.0,80.0" |

------------------------------------------------------------------------

#### setPolygonMaskSRID(srid)

Sets the Polygon mask coordinates SRID.
Applies to mask defined with string of coordinates.

##### Parameters:

| Name   | Type   | Description                            |
|--------|--------|----------------------------------------|
| `srid` | String | the spatial reference identifier value |

------------------------------------------------------------------------

#### setPolygonMaskTableParameters(maskTable, maskGeomColumn, maskCondition, maskJoinColumn, maskJoinGeorColumn)

Sets the polygon mask parameters based on table information.
At least mask table and mask table geometry column must be defined.
If join columns to connect geometry table with GeoRaster table are not
defined, then the polygon(s) will apply to any GeoRaster.

##### Parameters:

| Name                 | Type   | Description                                         |
|----------------------|--------|-----------------------------------------------------|
| `maskTable`          | String | the geometry table with polygons to be used as mask |
| `maskGeomColumn`     | String | the geometry column name of mask table              |
| `maskCondition`      | String | a query condition to be applied on geometry table   |
| `maskJoinColumn`     | String | the attribute of geometry table to be used as key   |
| `maskJoinGeorColumn` | String | the attribute of GeoRaster table to be used as key. |

------------------------------------------------------------------------

#### setQuery(sql)

Sets the dynamic SQL to be executed for this theme on the server.

##### Parameters:

| Name  | Type   | Description                                                        |
|-------|--------|--------------------------------------------------------------------|
| `sql` | String | The SQL string. Such as:<br>SELECT select georaster from pci_image |

------------------------------------------------------------------------

#### setRasterBands(bands)

Set the raster band to be displayed.

##### Parameters:

| Name    | Type   | Description                                                                                                                                              |
|---------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| `bands` | String | the RGB band index values. For example "0,2,3" means<br>bands 1 will be assigned to red, 3 will be assigned to green,<br>and 4 will be assigned to blue. |

------------------------------------------------------------------------

#### setRasterDataTable(table)

Sets the raster data table name (rdt)
This should be used when raster id and raster data table are defined.

##### Parameters:

| Name    | Type   | Description  |
|---------|--------|--------------|
| `table` | String | the rdt name |

------------------------------------------------------------------------

#### setRasterId(id)

Sets the Georaster identifier.
This should be used when raster id and raster data table are defined.

##### Parameters:

| Name | Type   | Description           |
|------|--------|-----------------------|
| `id` | String | the raster identifier |

------------------------------------------------------------------------

#### setRasterPyramid(pyramid)

Sets te raster pyramid to be used.
It is recommended to not set this value and leave server calculate the best pyramid level
based on data query window and display area.

##### Parameters:

| Name      | Type   | Description       |
|-----------|--------|-------------------|
| `pyramid` | String | the pyramid level |

------------------------------------------------------------------------

#### setSRID(srid)

Sets the jdbc theme srid

##### Parameters:

| Name   | Type   | Description          |
|--------|--------|----------------------|
| `srid` | String | The jdbc theme srid. |

------------------------------------------------------------------------

#### setVMapplyResolutionFilter(aplly)

Sets if resolution filter should be applied or not in virtual mosaic.

##### Parameters:

| Name    | Type    | Description                             |
|---------|---------|-----------------------------------------|
| `aplly` | Boolean | A true or false value. Default is true. |

------------------------------------------------------------------------

#### setVMcolorBalance(colorBalance)

Sets the virtual mosaic color balance.

##### Parameters:

| Name           | Type   | Description                                                               |
|----------------|--------|---------------------------------------------------------------------------|
| `colorBalance` | String | Available values: NONE, LINEARSTRETCHING, NORMALIZATION. Default is NONE. |

------------------------------------------------------------------------

#### setVMcommonPointRule(pointRule)

Sets the virtual mosaic common point rule.

##### Parameters:

| Name        | Type   | Description                                                                                          |
|-------------|--------|------------------------------------------------------------------------------------------------------|
| `pointRule` | String | Available values: START, END, LATEST, OLDEST. CTC, HIGH, LOW, AVERAGE, HIGHRES.<br>Default is START. |

------------------------------------------------------------------------

#### setVMfillGap(fillGap)

Sets if gaps should be filled in virtual mosaic rendering.

##### Parameters:

| Name      | Type    | Description                             |
|-----------|---------|-----------------------------------------|
| `fillGap` | Boolean | A true or false value. Default is true. |

------------------------------------------------------------------------

#### setVMincludeNODATA(useNodata)

Sets if NODATA should be considered in virtual mosaic overlapping areas.

##### Parameters:

| Name        | Type    | Description                             |
|-------------|---------|-----------------------------------------|
| `useNodata` | Boolean | A true or false value. Default is true. |

------------------------------------------------------------------------

#### setVMmaxStretchValue(value)

Sets the virtual mosaic maximum stretch value.
Applies when color balance equals LINEARSTRETCHING.

##### Parameters:

| Name    | Type    | Description                                |
|---------|---------|--------------------------------------------|
| `value` | Integer | A value between 0 and 255. Default is 255. |

------------------------------------------------------------------------

#### setVMmean(value)

Sets the virtual mosaic mean value.
Applies when color balance equals NORMALIZATION.

##### Parameters:

| Name    | Type   | Description   |
|---------|--------|---------------|
| `value` | Double | Default is 1. |

------------------------------------------------------------------------

#### setVMminStretchValue(value)

Sets the virtual mosaic minimum stretch value.
Applies when color balance equals LINEARSTRETCHING.

##### Parameters:

| Name    | Type    | Description                              |
|---------|---------|------------------------------------------|
| `value` | Integer | A value between 0 and 255. Default is 0. |

------------------------------------------------------------------------

#### setVMresamplingMode(mode)

Sets the virtual mosaic resampling mode.

##### Parameters:

| Name   | Type   | Description                                                                                            |
|--------|--------|--------------------------------------------------------------------------------------------------------|
| `mode` | String | Available values: NN, BILINEAR, BIQUADRATIC, CUBIC, AVERAGE4, AVERAGE16.<br>Default value is BILINEAR. |

------------------------------------------------------------------------

#### setVMresamplingTolerance(value)

Sets the virtual mosaic resampling tolerance value.

##### Parameters:

| Name    | Type   | Description     |
|---------|--------|-----------------|
| `value` | Double | Default is 0.5. |

------------------------------------------------------------------------

#### setVMsql(sql)

Sets the virtual mosaic full SQL query.
If defined, it will have preference over table list if both are defined.

##### Parameters:

| Name  | Type   | Description             |
|-------|--------|-------------------------|
| `sql` | String | A valid full SQL query. |

------------------------------------------------------------------------

#### setVMsrid(srid)

Sets the virtual mosaic spatial reference identifier.

##### Parameters:

| Name   | Type    | Description                                  |
|--------|---------|----------------------------------------------|
| `srid` | Integer | A valid Oracle Spatial reference identifier. |

------------------------------------------------------------------------

#### setVMstandardDeviation(value)

Sets the virtual mosaic standard deviation value.
Applies when color balance equals NORMALIZATION.

##### Parameters:

| Name    | Type   | Description   |
|---------|--------|---------------|
| `value` | Double | Default is 1. |

------------------------------------------------------------------------

#### setVMtables(tables)

Sets the virtual mosaic table parameters.
A list of tables can be defined on a virtual mosaic theme.

##### Parameters:

| Name     | Type  | Description                                                                                                                                                                                                                                                                |
|----------|-------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `tables` | Array | Each table entry must have the table name and geoRaster column defined,<br>and an optional query condition. For example:<br>\[ {"name":"table1", "georaster_column":"georaster"},<br>{"name":"table2", "georaster_column":"georaster", "query_condition":"id = 100"}<br>\] |
