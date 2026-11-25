## 2 GeoRaster Data Types and Related Structures

The object-relational implementation of GeoRaster consists of a set of object data types for storing data and system data.

Each image or gridded raster data is stored in a column of type SDO_GEORASTER, and the blocks in that raster data are stored in a raster data table of type SDO_RASTER, as explained and illustrated in [GeoRaster Physical Storage](georaster-overview-and-concepts.md). This chapter contains the following major sections.

- SDO_GEORASTER Object Type
  In the GeoRaster object-relational model, a raster image or grid object is stored in a single row, in a single column of object type SDO_GEORASTER in a user-defined table. Tables with at least one column of type SDO_GEORASTER are referred to as GeoRaster tables.
- SDO_RASTER Object Type and the Raster Data Table
  In the GeoRaster object-relational model, a raster data table (RDT) is used to store all cell data in a raster image.
- Other GeoRaster Types
  GeoRaster also porvides some other data types.
- GeoRaster System Data Views (xxx_SDO_GEOR_SYSDATA)
  GeoRaster uses a system data table (also called the sysdata table) to maintain the relationship between GeoRaster tables and their related raster data tables.
- GeoRaster XML Schema
  GeoRaster defines an XML schema to store and manage the GeoRaster metadata.

### 2.1 SDO_GEORASTER Object Type

In the GeoRaster object-relational model, a raster image or grid object is stored in a single row, in a single column of object type SDO_GEORASTER in a user-defined table. Tables with at least one column of type SDO_GEORASTER are referred to as GeoRaster tables.

The SDO_GEORASTER object type is defined as:

    CREATE TYPE sdo_georaster AS OBJECT (
     rasterType       NUMBER,
     spatialExtent    SDO_GEOMETRY,
     rasterDataTable  VARCHAR2(128),
     rasterID         NUMBER,
     metadata         XMLType);

The sections that follow describe the semantics of each SDO_GEORASTER attribute.

- rasterType Attribute
- spatialExtent Attribute
- rasterDataTable Attribute
- rasterID Attribute
- metadata Attribute

**Parent topic:** GeoRaster Data Types and Related Structures

#### 2.1.1 rasterType Attribute

The `rasterType` attribute must be a 5-digit number in the format `[d][b][t][gt]`, where:

- `[d]` identifies the number of spatial dimensions. Must be 2 for the current release.

- `[b]` indicates band or layer information: 0 means one band or layer; 1 means one or more than one band or layer. Note that you are not specifying the total number of bands or layers in this field. (For information about bands and layers, see [Bands\_ Layers\_ and Metadata](georaster-overview-and-concepts.md).)

- `[t]` is reserved for future use and should be specified as 0 (zero).

- `[gt]` identifies the 2-digit GeoRaster type, and must be one of the following values:

  | \[gt\] Value | Meaning                                                                                                                                                                                                              |
  |:-------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | 00           | Reserved for Oracle use.                                                                                                                                                                                             |
  | 01           | Any GeoRaster type. This is the only value supported for the current release. This value causes GeoRaster not to apply any restrictions associated with specific types that might be implemented in future releases. |
  | 02-50        | Reserved for Oracle use.                                                                                                                                                                                             |
  | 51-99        | Reserved for customer use in future releases.                                                                                                                                                                        |

For example, a RasterType value of 20001 means:

- Two-dimensional data

- One band (layer)

- Any GeoRaster type

**Parent topic:** SDO_GEORASTER Object Type

#### 2.1.2 spatialExtent Attribute

The `spatialExtent` attribute identifies the spatial extent, or footprint, associated with the raster data. The spatial extent is an Oracle Spatial and Graph geometry of type SDO_GEOMETRY. The spatial extent geometry can be in any coordinate system, not necessarily in the GeoRaster model space, and can be directly updated by a SQL UPDATE statement specifying a geometry. However, the spatial extent geometry is in the model (ground) space of the GeoRaster object if the GeoRaster object is georeferenced and if you generate the spatial extent geometry using any of the following methods: calling the [SDO_GEOR.generateSpatialExtent](SDO_GEOR-reference.md) function, or specifying `spatialExtent=TRUE` as a storage parameter to the [SDO_GEOR.importFrom](SDO_GEOR-reference.md) procedure or the GeoRaster client-side loader (described in [GeoRaster Tools: Viewer\_ Loader\_ Exporter](georaster-overview-and-concepts.md)).

You can call SDO_CS.transform to convert it to any other supported coordinate system. The spatial extent is set to null, rather than cell space, if its SRID value is null or 0 (zero). The SDO_GEOMETRY data type is described in [Oracle Spatial and Graph Developer's Guide](../spatl/spatial-datatypes-metadata.md).

The GeoRaster spatial extent is generally used to build a spatial R-tree index on the GeoRaster column. For example, you can use a geodetic SRID for all the spatial extents when all GeoRaster objects are in different local projections, and then build a whole-Earth based spatial index on the GeoRaster table and spatially search GeoRaster objects globally. Because of the potential performance benefits of spatial indexing for GeoRaster applications, the geometry is associated with the `spatialExtent` attribute, rather than being included in the XML `metadata` attribute described in metadata Attribute. For information about indexing GeoRaster data, see [Indexing GeoRaster Objects](georaster-database-creation-management.md).

**Parent topic:** SDO_GEORASTER Object Type

#### 2.1.3 rasterDataTable Attribute

The `rasterDataTable` attribute identifies the name of the raster data table. The raster data table must be an object table of type SDO_RASTER or a relational table that includes all columns defined by object type SDO_RASTER. It contains a row for each raster block that is stored. You must create and (if necessary) drop the raster data table. You should never modify the rows in this table directly, but you can query this table to access the raster data.

This attribute must be a valid nonquoted identifier without any period separators, and all the alphanumeric characters must be uppercase.

For more information about the raster data table and the SDO_RASTER type, see SDO_RASTER Object Type and the Raster Data Table.

**Parent topic:** SDO_GEORASTER Object Type

#### 2.1.4 rasterID Attribute

The `rasterID` attribute value is stored in the rows of the raster data table to identify which rows belong to the GeoRaster object. The `rasterDataTable` attribute and `rasterID` attribute together uniquely identify the GeoRaster object in the database. That is, each GeoRaster object has a raster data table, although a raster data table can contain data from multiple GeoRaster objects.

You can specify the `rasterID` and `rasterDataTable` attributes for new GeoRaster objects, as long as each pair is unique in the database. If you do not specify these values, they are automatically generated by the [SDO_GEOR.init](SDO_GEOR-reference.md) and [SDO_GEOR.createBlank](SDO_GEOR-reference.md) functions.

**Parent topic:** SDO_GEORASTER Object Type

#### 2.1.5 metadata Attribute

The `metadata` attribute contains the GeoRaster metadata that is defined by Oracle. The metadata is described by the GeoRaster metadata XML schema, which is documented in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md). The metadata of any GeoRaster object must be validated against this XML schema, and it must also be validated using the [SDO_GEOR.validateGeoRaster](SDO_GEOR-reference.md) function, which imposes additional restrictions not defined by this XML schema.

The default storage option for GeoRaster metadata is binary XML.

**Parent topic:** SDO_GEORASTER Object Type

### 2.2 SDO_RASTER Object Type and the Raster Data Table

In the GeoRaster object-relational model, a raster data table (RDT) is used to store all cell data in a raster image.

The cell data of a GeoRaster object is blocked, and each block is stored in the RDT as one row. You specify this table in the `rasterDataTable` attribute of the SDO_GEORASTER object, as explained in rasterDataTable Attribute. You must create the RDT before you store any cell data in it.

The RDT is an object table, defined as a table of SDO_RASTER object type or as a relational table that includes all columns defined by object type SDO_RASTER. The RDT name must be unique in the database, as described in [Raster Data Table](georaster-overview-and-concepts.md).

The SDO_RASTER object type is defined as:

    CREATE TYPE sdo_raster AS OBJECT (
     rasterID           NUMBER,
     pyramidLevel       NUMBER,
     bandBlockNumber    NUMBER,
     rowBlockNumber     NUMBER,
     columnBlockNumber  NUMBER,
     blockMBR           SDO_GEOMETRY,
     rasterBlock        BLOB);

The sections that follow describe the semantics of each SDO_RASTER attribute.

- rasterID Attribute
- pyramidLevel Attribute
- bandBlockNumber Attribute
- rowBlockNumber Attribute
- columnBlockNumber Attribute
- blockMBR Attribute
- rasterBlock Attribute

**Parent topic:** GeoRaster Data Types and Related Structures

#### 2.2.1 rasterID Attribute

The `rasterID` attribute in the SDO_RASTER object must be a number that matches the `rasterID` value in its associated SDO_GEORASTER object. (The `rasterID` attribute of the SDO_GEORASTER object is described in rasterID Attribute.) The matching of these numbers identifies the raster block as belonging to a specific GeoRaster object.

**Parent topic:** SDO_RASTER Object Type and the Raster Data Table

#### 2.2.2 pyramidLevel Attribute

The `pyramidLevel` attribute identifies the pyramid level for this block of cells. The pyramid level is 0 or any positive integer. Pyramid levels are used to create reduced resolution images that require less storage space. A pyramid level of 0 indicates the original raster data; that is, there is no reduction in the image resolution and no change in the storage space required. Values greater than 0 (zero) indicate increasingly reduced levels of image resolution and reduced storage space requirements. For more information about pyramids, see [Pyramids](georaster-overview-and-concepts.md).

This attribute and the `bandBlockNumber` attribute (described in bandBlockNumber Attribute) are also used to indicate bitmap masks and their pyramids. For more information about bitmap masks, bitmap mask pyramids, and how the `pyramidLevel` and `bandBlockNumber` attributes are used, see [Bitmap Masks](georaster-overview-and-concepts.md).

**Parent topic:** SDO_RASTER Object Type and the Raster Data Table

#### 2.2.3 bandBlockNumber Attribute

The `bandBlockNumber` attribute identifies the block number along the band dimension. For information about bands and layers, see [Bands\_ Layers\_ and Metadata](georaster-overview-and-concepts.md). For more information about how the `bandBlockNumber` attribute is used with bitmap masks and their pyramids, see [Bitmap Masks](georaster-overview-and-concepts.md).

**Parent topic:** SDO_RASTER Object Type and the Raster Data Table

#### 2.2.4 rowBlockNumber Attribute

The `rowBlockNumber` attribute identifies the block number along the row dimension.

**Parent topic:** SDO_RASTER Object Type and the Raster Data Table

#### 2.2.5 columnBlockNumber Attribute

The `columnBlockNumber` attribute identifies the block number along the column dimension.

**Parent topic:** SDO_RASTER Object Type and the Raster Data Table

#### 2.2.6 blockMBR Attribute

The `blockMBR` attribute is the geometry (of type SDO_GEOMETRY) for the minimum bounding rectangle (MBR) for this block. The geometry is in cell space (that is, its SRID value is null), and all ordinates are integers. The ordinates represent the minimum row and column and the maximum row and column stored in this block.

**Parent topic:** SDO_RASTER Object Type and the Raster Data Table

#### 2.2.7 rasterBlock Attribute

The `rasterBlock` attribute contains all raster cell data for this block. It is also used to store bitmap masks of the GeoRaster object. The `rasterBlock` attribute is of type BLOB.

**Parent topic:** SDO_RASTER Object Type and the Raster Data Table

### 2.3 Other GeoRaster Types

GeoRaster also porvides some other data types.

In addition to SDO_GEORASTER, SDO_RASTER, and SDO_RANGE_ARRAY and SDO_RANGE, GeoRaster provides several other object and collection types, which are used for specific kinds of operations. Unlike the SDO_GEORASTER and SDO_RASTER types, which are used for storage in the database (for example, to define a column in a table), the types described in this section are used only with the GeoRaster PL/SQL API in the current release.

- SDO_GEOR_HISTOGRAM Object Type
- SDO_GEOR_HISTOGRAM_ARRAY Collection Type
- SDO_GEOR_COLORMAP Object Type
- SDO_GEOR_GRAYSCALE Object Type
- SDO_RASTERSET Collection Type
- SDO_GEOR_SRS Object Type
- SDO_GEOR_GCP Object Type
- SDO_GEOR_GCP\_ COLLECTION Collection Type
- SDO_GEOR_GCPGEOREFTYPE Object Type

**Related Topics**

- SDO_GEORASTER Object Type
- SDO_RASTER Object Type and the Raster Data Table
- [NODATA Values and Value Ranges](georaster-overview-and-concepts.md)

**Parent topic:** GeoRaster Data Types and Related Structures

#### 2.3.1 SDO_GEOR_HISTOGRAM Object Type

In GeoRaster, the histogram is stored in the GeoRaster metadata using the XML schema defined in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md). The SDO_GEOR_HISTOGRAM object type is used in the PL/SQL API to contain the histogram data of a GeoRaster object or a layer. The layers have the same histogram data structure. Each cell has a value, and for each cell value or a value range there may be any number of cells having that value or falling in that range.

The SDO_GEOR_HISTOGRAM object type is defined as:

    CREATE TYPE sdo_geor_histogram AS OBJECT(
      cellValue  SDO_NUMBER_ARRAY,
      count      SDO_NUMBER_ARRAY);

Table 2-1 describes the attributes of the SDO_GEOR_HISTOGRAM object type. The `cellValue` array and the `count` array must have the same length.

Table 2-1 SDO_GEOR_HISTOGRAM Object Type Attributes

| Attribute | Description                                                             |
|:----------|:------------------------------------------------------------------------|
| cellValue | Array of cell values.                                                   |
| count     | Number of cells that correspond to each cell value or cell value range. |

The histogram contains the cell values (and the implied value ranges) and the total number of cells related to each cell value or each cell value range. For example, if (cellValue1, count1) and (cellValue2, count2) are the two adjacent entries in ascending order in the histogram, the implied value range is \[cellValue1, cellValue2) and the total number of cells in this range is count1. The cell value range is always inclusive in its lower boundary and exclusive in the upper boundary. The size of each range does not necessarily have to be the same. Using this example, the range is equal to or greater than cellValue1 and less than cellValue2. For a lower cell depth (for example, 1-bit to 8-bit integers), the cell value ranges are typically the same as the cell values.

**Parent topic:** Other GeoRaster Types

#### 2.3.2 SDO_GEOR_HISTOGRAM_ARRAY Collection Type

The SDO_GEOR_HISTOGRAM_ARRAY collection type is used to store an array (collection) of SDO_GEOR_HISTOGRAM objects.

The SDO_GEOR_HISTOGRAM_ARRAY collection type is defined as:

    CREATE TYPE sdo_geor_histogram_array AS
      VARRAY(10485760) OF SDO_GEOR_HISTOGRAM;

**Parent topic:** Other GeoRaster Types

#### 2.3.3 SDO_GEOR_COLORMAP Object Type

In GeoRaster, the color information is stored in the GeoRaster metadata using the XML schema defined in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md). The SDO_GEOR_COLORMAP object type is used in the PL/SQL API to contain colormap information, that is, pseudocolor information for identifying the red, green, blue, and (optionally) alpha values of the color to be used to display cells that have a specific value or are in a specific value range. The colormap is also called the pseudocolor table or the palette table. The colormap in GeoRaster is in the default sRGB ColorSpace, which is a proposed standard RGB color space, as explained at

[`http://www.w3.org/Graphics/Color/sRGB.html`](http://www.w3.org/Graphics/Color/sRGB.html)

The ranges for red, green, blue, and alpha values are all scaled to be 8-bit unsigned integers from 0 to 255.

Alpha is also called opacity. An alpha value of 255 means that the color is completely opaque, and an alpha value of 0 means that the color is completely transparent. The color component values are never premultiplied by the alpha value.

The SDO_GEOR_COLORMAP object type is defined as:

    CREATE TYPE sdo_geor_colormap AS OBJECT(
      cellValue  SDO_NUMBER_ARRAY,
      red        SDO_NUMBER_ARRAY,
      green      SDO_NUMBER_ARRAY,
      blue       SDO_NUMBER_ARRAY,
      alpha      SDO_NUMBER_ARRAY);

Table 2-2 describes the attributes of the SDO_GEOR_COLORMAP object type. Each attribute is an array of numbers. The arrays must have the same length, and the values of the same index in each array must correspond to each other. Each `cellValue` value must be consistent with the `cellDepth` value of the GeoRaster object.

The colormap contains the cell values (and the implied value ranges) and the red, green, blue, and/or alpha values related to each cell value or each cell value range. For example, if (cellValue1, red1, green1, blue1, alpha1) and (cellValue2, red2, green2, blue2, alpha2) are the two adjacent entries in ascending order in the colormap, the implied value range is \[cellValue1, cellValue2), and the color components associated with all cells in this range are (red1, green1, blue1, alpha1). The cell value range is always inclusive in its lower boundary and exclusive in the upper boundary. The size of each range does not necessarily have to be the same. In this example, the range is equal to or greater than cellValue1 and less than cellValue2. For a lower cell depth (for example, 1-bit to 8-bit integers), the cell value ranges are typically the same as the cell values.

Table 2-2 SDO_GEOR_COLORMAP Object Type Attributes

| Attribute | Description                                                                                                                                                 |
|:----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------|
| cellValue | Array of cell values. The values must be stored in ascending order.                                                                                         |
| red       | Array of red component values for pseudocolor display of cells that have the values or value ranges in `cellValue`. Must be integer values from 0 to 255.   |
| green     | Array of green component values for pseudocolor display of cells that have the values or value ranges in `cellValue`. Must be integer values from 0 to 255. |
| blue      | Array of blue component values for pseudocolor display of cells that have the values or value ranges in `cellValue`. Must be integer values from 0 to 255.  |
| alpha     | Array of alpha component values for pseudocolor display of cells that have the values or value ranges in `cellValue`. Must be integer values from 0 to 255. |

**Parent topic:** Other GeoRaster Types

#### 2.3.4 SDO_GEOR_GRAYSCALE Object Type

In GeoRaster, the grayscale information is stored in the GeoRaster metadata using the XML schema defined in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md). The SDO_GEOR_GRAYSCALE object type is used in the PL/SQL API to contain grayscale information for identifying the grayscale value to be used to display cells that have a specific value or fall into a specific value range. The grayscale table cell values can be "stretched" in linear proportion using this grayscale table, so that the original raster data can be properly displayed. The grayscale table value range is 8-bit unsigned integer values from 0 to 255. The grayscale table is also called the contrast table or the lookup table.

The SDO_GEOR_GRAYSCALE object type is defined as:

    CREATE TYPE sdo_geor_grayscale AS OBJECT(
      cellValue  SDO_NUMBER_ARRAY,
      gray       SDO_NUMBER_ARRAY);

Table 2-3 describes the attributes of the SDO_GEOR_GRAYSCALE object type. The `cellValue` array and the `gray` array must have the same length. Each `cellValue` value must be consistent with the `cellDepth` value of the GeoRaster object.

The grayscale contains the cell values (and the implied value ranges) and the gray values related to each cell value or each cell value range. For example, if (cellValue1, gray1) and (cellValue2, gray2) are the two adjacent entries in ascending order in the grayscale table, the implied value range is \[cellValue1, cellValue2), and the gray color associated with all cells in this range is gray1. The cell value range is always inclusive in its lower boundary and exclusive in the upper boundary. The size of each range does not necessarily have to be the same. Taking the same example, the range is equal to or greater than cellValue1 and less than cellValue2. For a lower cell depth (for example, 1-bit to 8-bit integers), the cell value ranges are typically the same as the cell values.

Table 2-3 SDO_GEOR_GRAYSCALE Object Type Attributes

| Attribute | Description                                                                                                                                              |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| cellValue | Array of cell values. The values must be stored in ascending order.                                                                                      |
| gray      | Array of gray component values for grayscale display of cells that have the values or value ranges in `cellValue`. Must be integer values from 0 to 255. |

**Parent topic:** Other GeoRaster Types

#### 2.3.5 SDO_RASTERSET Collection Type

The SDO_RASTERSET collection type is used as the return type of table functions that query the raster data blocks (one or many blocks, the whole set or a subset).

The SDO_RASTERSET collection type is defined as:

    CREATE TYPE sdo_rasterset AS TABLE of SDO_RASTER;

**Related Topics**

- SDO_RASTER Object Type and the Raster Data Table

**Parent topic:** Other GeoRaster Types

#### 2.3.6 SDO_GEOR_SRS Object Type

In GeoRaster, the spatial reference system (SRS) information is stored in the GeoRaster metadata using the XML schema defined in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md). The SDO_GEOR_SRS object type is used in the PL/SQL API to contain information related to the spatial referencing of a GeoRaster object. The metadata and the object type contain the same information. You can use the object type to retrieve the SRS information from GeoRaster objects or to load and update the SRS information in GeoRaster objects.

The SDO_GEOR_SRS object type is defined as:

    CREATE TYPE sdo_geor_srs AS OBJECT (
       isReferenced       VARCHAR2(5),
       isRectified        VARCHAR2(5),
       isOrthoRectified   VARCHAR2(5),
       srid               NUMBER,
       spatialResolution  SDO_NUMBER_ARRAY,
       spatialTolerance   NUMBER,
       coordLocation      NUMBER,
       rowOff             NUMBER,
       columnOff          NUMBER,
       xOff               NUMBER,
       yOff               NUMBER,
       zOff               NUMBER,
       rowScale           NUMBER,
       columnScale        NUMBER,
       xScale             NUMBER,
       yScale             NUMBER,
       zScale             NUMBER,
       rowRMS             NUMBER,
       columnRMS          NUMBER,
       totalRMS           NUMBER,
       rowNumerator       SDO_NUMBER_ARRAY,
       rowDenominator     SDO_NUMBER_ARRAY,
       columnNumerator    SDO_NUMBER_ARRAY,
       columnDenominator  SDO_NUMBER_ARRAY,
       xRMS               NUMBER,
       yRMS               NUMBER,
       zRMS               NUMBER,
       modelTotalRMS      NUMBER,
       GCPgeoreferenceModel SDO_GEOR_GCPGEOREFTYPE);

Table 2-4 describes the attributes of the SDO_GEOR_SRS object type.

Table 2-4 SDO_GEOR_SRS Object Type Attributes

| Attribute            | Description                                                                                                                                                                                                                                                                                                                                                 |
|:---------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| isReferenced         | `TRUE` if the GeoRaster object is georeferenced; `FALSE` if the GeoRaster object is not georeferenced.                                                                                                                                                                                                                                                      |
| isRectified          | `TRUE` if the GeoRaster object is both georectified and georeferenced; `FALSE` if the GeoRaster object is not georectified.                                                                                                                                                                                                                                 |
| isOrthoRectified     | `TRUE` if the GeoRaster object is orthorectified, georectified, and georeferenced; `FALSE` if the GeoRaster object is not orthorectified.                                                                                                                                                                                                                   |
| srid                 | SRID value of the model (ground) coordinate system.                                                                                                                                                                                                                                                                                                         |
| spatialResolution    | Spatial resolution values: an array of numeric values, one for each spatial dimension. Each value indicates the number of units of measurement associated with the data area represented by that spatial dimension of a cell.                                                                                                                               |
| spatialTolerance     | Tolerance value, for control of the precision.                                                                                                                                                                                                                                                                                                              |
| coordLocation        | The model coordinate location defines the type of the cell space, which represents either upperleft-based (that is, coordLocation=1) or center-based (that is, coordLocation=0). For more information about model space and cell (raster) space, see [GeoRaster Data Model](georaster-overview-and-concepts.md).                                            |
| rowOff               | Row offset value.                                                                                                                                                                                                                                                                                                                                           |
| columnOff            | Column offset value.                                                                                                                                                                                                                                                                                                                                        |
| xOff                 | X offset value.                                                                                                                                                                                                                                                                                                                                             |
| yOff                 | Y offset value.                                                                                                                                                                                                                                                                                                                                             |
| zOff                 | Z offset value.                                                                                                                                                                                                                                                                                                                                             |
| rowScale             | Row scaling factor value.                                                                                                                                                                                                                                                                                                                                   |
| columnScale          | Column scaling factor value.                                                                                                                                                                                                                                                                                                                                |
| xScale               | X scaling factor value.                                                                                                                                                                                                                                                                                                                                     |
| yScale               | Y scaling factor value.                                                                                                                                                                                                                                                                                                                                     |
| zScale               | Z scaling factor value.                                                                                                                                                                                                                                                                                                                                     |
| rowRMS               | The row-dimension accuracy. It is computed using control points if you call [SDO_GEOR.georeference](SDO_GEOR-reference.md) using GCPs.                                                                                                                                                                                                                      |
| columnRMS            | The column-dimension accuracy. It is computed using control points if you call [SDO_GEOR.georeference](SDO_GEOR-reference.md) using GCPs                                                                                                                                                                                                                    |
| totalRMS             | The total row and column accuracy. It is computed using control points if you call [SDO_GEOR.georeference](SDO_GEOR-reference.md) using GCPs                                                                                                                                                                                                                |
| rowNumerator         | `pType`, `nVars`, `order`, `nCoefficients`, and all coefficients of the numerator of the row polynomial, where `pType`=1 or 2; `nVars`=0, 2, or 3; 0\<=`order`\<=5; and `nCoefficients` is derived from `pType`, `nVars`, and `order`. The polynomials are explained in [Functional Fitting Georeferencing Model](georaster-overview-and-concepts.md).      |
| rowDenominator       | `pType`, `nVars`, `order`, `nCoefficients`, and all coefficients of the denominator of the row polynomial, where `pType`=1 or 2; `nVars`=0, 2, or 3; 0\<=`order`\<=5; and `nCoefficients` is derived from `pType`, `nVars`, and `order`. The polynomials are explained in [Functional Fitting Georeferencing Model](georaster-overview-and-concepts.md).    |
| columnNumerator      | `pType`, `nVars`, `order`, `nCoefficients`, and all coefficients of the numerator of the column polynomial, where `pType`=1 or 2; `nVars`=0, 2, or 3; 0\<=`order`\<=5; and `nCoefficients` is derived from `pType`, `nVars`, and `order`. The polynomials are explained in [Functional Fitting Georeferencing Model](georaster-overview-and-concepts.md).   |
| columnDenominator    | `pType`, `nVars`, `order`, `nCoefficients`, and all coefficients of the denominator of the column polynomial, where `pType`=1 or 2; `nVars`=0, 2, or 3; 0\<=`order`\<=5; and `nCoefficients` is derived from `pType`, `nVars`, and `order`. The polynomials are explained in [Functional Fitting Georeferencing Model](georaster-overview-and-concepts.md). |
| xRMS                 | The x-dimension accuracy. It is computed using check points if you call [SDO_GEOR.georeference](SDO_GEOR-reference.md) using GCPs.                                                                                                                                                                                                                          |
| yRMS                 | The y-dimension accuracy. It is computed using check points if you call [SDO_GEOR.georeference](SDO_GEOR-reference.md) using GCPs.                                                                                                                                                                                                                          |
| zRMS                 | The z-dimension accuracy. It is computed using check points if you call [SDO_GEOR.georeference](SDO_GEOR-reference.md) using GCPs.                                                                                                                                                                                                                          |
| modelTotalRMS        | The total model accuracy. It is computed using check points if you call [SDO_GEOR.georeference](SDO_GEOR-reference.md) using GCPs.                                                                                                                                                                                                                          |
| GCPgeoreferenceModel | The stored function model information, that is, all information about the GCP-based georeferencing model. For information about GCP-based georeferencing model information, see SDO_GEOR_GCPGEOREFTYPE Object Type.                                                                                                                                         |

However, when the direct and inverse solutions are derived from the functional fitting model, the accuracy values listed in Table 2-4 are not considered in GeoRaster internal cell coordinate and model coordinate transformation computations for the current release.

The SDO_GEOR_SRS object type has two constructors:

- One constructor takes no parameters and creates an instance of the type with the `isReferenced` attribute set to `FALSE` and the other attributes set to null values. This constructor allows you to set up either the functional fitting model or the stored function (GCP) model, or to set up both of them together.

- The other constructor takes all the attributes of this object type as parameters, except those related to the stored function (GCP) model.

For examples of how to use the SDO_GEOR_SRS constructor, see the reference section for the [SDO_GEOR.setSRS](SDO_GEOR-reference.md) procedure in [SDO_GEOR Package Reference](SDO_GEOR-reference.md).

**Parent topic:** Other GeoRaster Types

#### 2.3.7 SDO_GEOR_GCP Object Type

In GeoRaster, the ground control point (GCP) information is stored in the GeoRaster metadata using the XML schema defined in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md). The SDO_GEOR_GCP object type is used in the PL/SQL API to contain GCP information related to the georeferencing of a GeoRaster object. The metadata and the object type contain the same information. You can use the object type to retrieve the GCP information from GeoRaster objects or to load and update the GCP information in GeoRaster objects.

The SDO_GEOR_GCP object type is defined as:

    CREATE TYPE sdo_geor_gcp AS OBJECT (
         pointID          VARCHAR2(32),
         description      VARCHAR2(256),
         pointType        NUMBER,
         cellDimension    NUMBER,
         cellCoordinates  SDO_NUMBER_ARRAY,
         modelDimension   NUMBER,
         modelCoordinates SDO_NUMBER_ARRAY,
         accuracy         SDO_NUMBER_ARRAY,
         status           NUMBER
    );

Table 2-5 describes the attributes of the SDO_GEOR_GCP object type.

Table 2-5 SDO_GEOR_GCP Object Type Attributes

| Attribute        | Description                                                                                                                                                                                  |
|:-----------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| pointID          | Unique ID of the control point. Must not more 32 characters.                                                                                                                                 |
| description      | Descriptive information about the control point.                                                                                                                                             |
| pointType        | Point type: 1 (control point) or 2 (check point).                                                                                                                                            |
| cellDimension    | Dimensionality (number of dimensions) of the cell coordinates: 2 or 3.                                                                                                                       |
| cellCoordinates  | Array of cell coordinates for the control points; (row, column) or (row, column, vertical) for each point.                                                                                   |
| modelDimension   | Dimensionality (number of dimensions) of the model coordinates: 2 or 3.                                                                                                                      |
| modelCoordinates | Array of model coordinates for the control point, corresponding to the points in cell space; (X,Y) or (X,Y,Z) for each point.                                                                |
| accuracy         | Accuracy of the control point, expressed as the values of (xRMS, yRMS) or (xRMS, yRMS, zRMS).                                                                                                |
| status           | Status of the GCP: `Measured`, `Removed`, `Estimated`, `Validated`, or `Invalid`. The value of this column is informational only, and it has no effect on the usage of the GCP by GeoRaster. |

The SDO_GEOR_GCP constructor can be used to create an empty instance of this object type. You should then fill in the necessary data before you use this instance.

**Parent topic:** Other GeoRaster Types

#### 2.3.8 SDO_GEOR_GCP\_ COLLECTION Collection Type

The SDO_GEOR_GCP\_ COLLECTION collection type is used to store an array (a collection) of ground control points (GCPs).

The SDO_GEOR_GCP\_ COLLECTION collection type is defined as:

    CREATE TYPE sdo_geor_gcp_collection VARRAY(1048576) OF SDO_GEOR_GCP;

**Related Topics**

- SDO_GEOR_GCP Object Type

**Parent topic:** Other GeoRaster Types

#### 2.3.9 SDO_GEOR_GCPGEOREFTYPE Object Type

In GeoRaster, the GCP-based georeferencing model information is stored in the GeoRaster metadata using the XML schema defined in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md). The SDO_GEOR_GCPGEOREFTYPE object includes the georeferencing functional fitting method (that is, the geometric model), control points for solving the model parameters, and solution accuracy. The SDO_GEOR\_ GCPGEOREFTYPE object type is used in the PL/SQL API to contain georeferencing model information related to the GCP-based georeferencing of a GeoRaster object. The metadata and the object type contain the same information. You can use the object type to retrieve the georeferencing model information from GeoRaster objects or to load and update the georeferencing model information in GeoRaster objects.

The SDO_GEOR_GCPGEOREFTYPE object type is defined as:

    CREATE TYPE sdo_geor_gcpgeoreftype AS OBJECT (
         FFMethodType     VARCHAR2(32),
         numberGCP        NUMBER,
         GCPs             SDO_GEOR_GCP_COLLECTION,
         solutionAccuracy SDO_NUMBER_ARRAY
    );

Table 2-6 describes the attributes of the SDO_GEOR_GCPGEOREFTYPE object type.

Table 2-6 SDO_GEOR_GCPGEOREFTYPE Object Type Attributes

| Attribute        | Description                                                                                                                                                                                                                                                                                                                                                                     |
|:-----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| FFMethodType     | Functional fitting method. Must be one of the following: `Affine`, `QuadraticPolynomial`, `CubicPolynomial`, `DLT`, `QuadraticRational`, or `RPC`.                                                                                                                                                                                                                              |
| numberGCP        | Number of ground control points in the GCP collection (`GCPs` parameter).                                                                                                                                                                                                                                                                                                       |
| GCPs             | The GCP collection, of type SDO_GEOR_GCP_COLLECTION (described in SDO_GEOR_GCP\_ COLLECTION Collection Type).                                                                                                                                                                                                                                                                   |
| solutionAccuracy | Array storing the accuracy of the georeferencing solution in the following format: (rowRMS, columnRMS, totalRMS, xRMS, yRMS, zRMS, modelTotalRMS). The first three RMS numbers are computed using control points, and the last four RMS numbers are computed using check points (if any). This information is for output only; do not store or modify values in this attribute. |

The SDO_GEOR_GCPGEOREFTYPE object type has one constructor. The constructor takes no parameters, and it creates an instance of the type with the `FFMethodType` attribute set to `Affine` and the other attributes set to null values.

**Parent topic:** Other GeoRaster Types

### 2.4 GeoRaster System Data Views (xxx_SDO_GEOR_SYSDATA)

GeoRaster uses a system data table (also called the sysdata table) to maintain the relationship between GeoRaster tables and their related raster data tables.

Each GeoRaster object (if it is not null) has a related raster data table, and it might have other information, such as ground control points (GCPs) and value attribute tables (VATs).

For a given user, the raster data table name plus the `rasterID` uniquely identify a GeoRaster object. It is possible for many GeoRaster objects (each with a different `rasterID` value) in one GeoRaster table to share one raster data table.

Whenever a new GeoRaster object (including empty and blank GeoRaster objects) is created, a raster data table is assigned to it and a `rasterID` value is assigned. All SDO_GEORASTER objects (except atomic null objects) are automatically recorded in the system data table when they are created.

The GeoRaster sysdata table is under the MDSYS schema. Most of the information in the GeoRaster system data table is available for retrieval through system data views, and thus it can be used as a dictionary or a catalog of all GeoRaster objects in a GeoRaster database. Each GeoRaster user has the following system data views available in the schema associated with that user:

- USER_SDO_GEOR_SYSDATA contains system data for all GeoRaster objects owned by the current user.

- ALL_SDO_GEOR_SYSDATA contains system data for all GeoRaster objects accessible by the current user.

The GeoRaster sysdata table and the USER_SDO_GEOR_SYSDATA and ALL_SDO_GEOR_SYSDATA views should never be modified directly by users, although they are updated by the DML trigger that is automatically created on each SDO_GEORASTER column in each GeoRaster table.

The USER_SDO_GEOR_SYSDATA view has the following definition:

    (
       TABLE_NAME            VARCHAR2(128),
       COLUMN_NAME           VARCHAR2(1024),
       METADATA_COLUMN_NAME  VARCHAR2(1024),
       RDT_TABLE_NAME        VARCHAR2(128),
       RASTER_ID             NUMBER,
       OTHER_TABLE_NAMES     SDO_STRING_ARRAY
    );

The ALL_SDO_GEOR_SYSDATA view has all columns in the USER_SDO_GEOR_SYSDATA view, but it also has an OWNER column identifying the schema that owns the table specified in the TABLE_NAME column.

This section describes each of the columns common to both views. Note that for VARCHAR2 data in any columns, names are stored in all uppercase characters.

- TABLE_NAME Column
- COLUMN_NAME Column
- METADATA_COLUMN_NAME Column
- RDT_TABLE_NAME Column
- RASTER_ID Column
- OTHER_TABLE_NAMES Column

**Parent topic:** GeoRaster Data Types and Related Structures

#### 2.4.1 TABLE_NAME Column

The TABLE_NAME column contains the name of a GeoRaster table that has at least one column of type SDO_GEORASTER.

**Parent topic:** GeoRaster System Data Views (xxx_SDO_GEOR_SYSDATA)

#### 2.4.2 COLUMN_NAME Column

The COLUMN_NAME column contains the name of a column of type SDO_GEORASTER in the GeoRaster table specified in the TABLE_NAME column.

**Parent topic:** GeoRaster System Data Views (xxx_SDO_GEOR_SYSDATA)

#### 2.4.3 METADATA_COLUMN_NAME Column

The METADATA_COLUMN_NAME column is ignored for the current release.

**Parent topic:** GeoRaster System Data Views (xxx_SDO_GEOR_SYSDATA)

#### 2.4.4 RDT_TABLE_NAME Column

The RDT_TABLE_NAME column contains the name of the raster data table associated with the table and column specified in the TABLE_NAME and COLUMN_NAME columns.)

**Related Topics**

- SDO_RASTER Object Type and the Raster Data Table

**Parent topic:** GeoRaster System Data Views (xxx_SDO_GEOR_SYSDATA)

#### 2.4.5 RASTER_ID Column

The RASTER_ID column contains a number that, together with the RDT_TABLE_NAME column value, uniquely identifies each GeoRaster object.

**Parent topic:** GeoRaster System Data Views (xxx_SDO_GEOR_SYSDATA)

#### 2.4.6 OTHER_TABLE_NAMES Column

The OTHER_TABLE_NAMES column is ignored for the current release.

**Parent topic:** GeoRaster System Data Views (xxx_SDO_GEOR_SYSDATA)

### 2.5 GeoRaster XML Schema

GeoRaster defines an XML schema to store and manage the GeoRaster metadata.

The definition of this XML schema is included in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md). The namespace defined by the GeoRaster XML schema is `http://xmlns.oracle.com/spatial/georaster`, and it is reserved for use by Oracle. You must refer to this namespace if you want to manipulate a GeoRaster metadata document using the SQL XML functions or the XMLType methods.

GeoRaster uses a table named SDO_GEOR_XMLSCHEMA_TABLE to store the GeoRaster metadata XML schema and other information. This table is under the MDSYS schema, and you must include the schema name if you reference this table. For example:

    DESCRIBE mdsys.sdo_geor_xmlschema_table
     Name                                      Null?    Type
     ----------------------------------------- -------- ----------------------------
     ID                                        NOT NULL NUMBER
     GEORASTERFORMAT                                    VARCHAR2(1024)
     XMLSCHEMA                                          CLOB

Table 2-7 describes the columns of the SDO_GEOR_XMLSCHEMA_TABLE table.

Table 2-7 SDO_GEOR_XMLSCHEMA_TABLE Table Columns

| Column Name     | Data Type      | Description                                                                                                                                 |
|:----------------|:---------------|:--------------------------------------------------------------------------------------------------------------------------------------------|
| id              | NUMBER         | ID number, assigned by Oracle. Values `1` through `50` are reserved for use by Oracle.                                                      |
| georasterFormat | VARCHAR2(1024) | GeoRaster format identifier, assigned by Oracle. The value `GEORASTER` is reserved for use by Oracle.                                       |
| xmlSchema       | CLOB           | GeoRaster metadata XML schema definition. This definition is included in [GeoRaster Metadata XML Schema](georaster-metadata-xml-schema.md). |

There are no GeoRaster views defined on this table. It is mainly of interest to advanced users who might want to query the table for GeoRaster XML schema information.

You are encouraged not to modify the contents of this table, unless you want to define your own XML schema for other metadata that is not included in the GeoRaster XML schema, and to store that metadata in a new row in this table. If you add a row for your own metadata, do not use an ID column value of `1` through `50` or a GEORASTERFORMAT column value of `GEORASTER`, because these column values are reserved for use by Oracle. If you specify an XMLSCHEMA column value, you should choose a unique namespace for your own XML schema and register it using a corresponding schema URL that will also be unique in the database. (For more information, see Oracle XML DB Developer's Guide.)

**Parent topic:** GeoRaster Data Types and Related Structures
