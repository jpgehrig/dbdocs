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

- Prev Class
- [Next Class](AdapterShapefileJGeom.md)

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

oracle.spatial.util

## Class Adapters

- java.lang.Object

- - oracle.spatial.util.Adapters

<!-- -->

-

  ------------------------------------------------------------------------



      public class Adapters
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `Adapters``()`              |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type           | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    |-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static java.sql.Struct`    | `affineTransforms``(java.sql.Struct geom, java.lang.String translation, NUMBER tx, NUMBER ty, NUMBER tz, java.lang.String scaling, java.sql.Struct Psc1, NUMBER sx, NUMBER sy, NUMBER sz, java.lang.String rotation, java.sql.Struct P1, java.sql.Struct line1, NUMBER angle, NUMBER dir, java.lang.String shearing, NUMBER SHxy, NUMBER SHyx, NUMBER SHxz, NUMBER SHzx, NUMBER SHyz, NUMBER SHzy, java.lang.String reflection, java.sql.Struct Pref, java.sql.Struct lineR, NUMBER dirR, java.lang.String planeR, SdoNumberArray n, SdoNumberArray bigD)`  |
    | `static java.lang.String`   | `anyInteract``(java.sql.Struct geom1, java.sql.Struct geom2, java.lang.String is_g3d, NUMBER smajax, NUMBER flattening, NUMBER g3d_geog_crs_uom_factor, NUMBER is_unit_radians, NUMBER tolerance)`                                                                                                                                                                                                                                                                                                                                                          |
    | `static NUMBER`             | `area``(java.sql.Struct geom, java.lang.String is_g3d, NUMBER smajax, NUMBER flattening, NUMBER g3d_geog_crs_uom_factor, NUMBER is_unit_radians, NUMBER tolerance)`                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static java.sql.Struct`    | `buffer``(java.sql.Struct geom, NUMBER bufferWidth, NUMBER sma, NUMBER iflat, NUMBER arcT)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static java.sql.Struct`    | `centroid_3d``(java.sql.Struct geom, NUMBER tolerance)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static java.sql.Struct`    | `closestPoints``(java.sql.Struct geom1, java.sql.Struct geom2, java.lang.String is_g3d, NUMBER smajax, NUMBER flattening, NUMBER g3d_geog_crs_uom_factor, NUMBER is_unit_radians, NUMBER tolerance)`                                                                                                                                                                                                                                                                                                                                                        |
    | `static NUMBER`             | `distance``(java.sql.Struct geom1, java.sql.Struct geom2, java.lang.String is_g3d, NUMBER smajax, NUMBER flattening, NUMBER g3d_geog_crs_uom_factor, NUMBER is_unit_radians, NUMBER tolerance)`                                                                                                                                                                                                                                                                                                                                                             |
    | `static java.sql.Struct`    | `expandG3Dgeoms``(java.sql.Struct geom)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static java.sql.Struct`    | `extract3d``(java.sql.Struct geom, java.lang.String label)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static java.sql.Struct`    | `extrusion2``(java.sql.Struct polygon, SdoNumberArray grdHeight, SdoNumberArray height, NUMBER tolerance, NUMBER optional3dSrid)`                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static java.lang.String`   | `getlabelbyelement``(java.sql.Struct source_Geom, java.sql.Struct qry_Element, NUMBER tolerance)`                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static java.sql.Struct`    | `getNurbsApprox``(java.sql.Struct geom)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static java.sql.Struct`    | `gml311ToSTRUCT``(CLOB gml)`<br>Deprecated. <br>Use oracle.jdbc.OracleClob and `gml311ToSTRUCT(OracleClob)` instead.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static java.sql.Struct`    | `gml311ToSTRUCT``(CLOB gml, NUMBER coordOrder)`<br>Deprecated. <br>Use oracle.jdbc.OracleClob and `gml311ToSTRUCT(OracleClob, NUMBER)` instead.                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static java.sql.Struct`    | `gml311ToSTRUCT``(CLOB gml, java.lang.String srsNameSpace)`<br>Deprecated. <br>Use oracle.jdbc.OracleClob and `gml311ToSTRUCT(OracleClob, String)` instead.                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static java.sql.Struct`    | `gml311ToSTRUCT``(CLOB gml, java.lang.String srsNameSpace, NUMBER coordOrder)`<br>Deprecated. <br>Use oracle.jdbc.OracleClob and `gml311ToSTRUCT(OracleClob, String, NUMBER)` instead.                                                                                                                                                                                                                                                                                                                                                                      |
    | `static java.sql.Struct`    | `gml311ToSTRUCT``(OracleClob gml)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static java.sql.Struct`    | `gml311ToSTRUCT``(OracleClob gml, NUMBER coordOrder)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static java.sql.Struct`    | `gml311ToSTRUCT``(OracleClob gml, java.lang.String srsNameSpace)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static java.sql.Struct`    | `gml311ToSTRUCT``(OracleClob gml, java.lang.String srsNameSpace, NUMBER coordOrder)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static java.sql.Struct`    | `gml311ToSTRUCT``(java.lang.String gml)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static java.sql.Struct`    | `gml311ToSTRUCT``(java.lang.String gml, java.sql.Connection conn)`<br>Deprecated. <br>Connection parameter is ignored; static default connection is used instead. Perhaps this is a bug.                                                                                                                                                                                                                                                                                                                                                                    |
    | `static java.sql.Struct`    | `gml311ToSTRUCT``(java.lang.String gml, java.sql.Connection conn, NUMBER coordOrder)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static java.sql.Struct`    | `gml311ToSTRUCT``(java.lang.String gml, NUMBER coordOrder)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static java.sql.Struct`    | `gml311ToSTRUCT``(java.lang.String gml, java.lang.String srsNameSpace)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static java.sql.Struct`    | `gml311ToSTRUCT``(java.lang.String gml, java.lang.String srsNameSpace, NUMBER coordOrder)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static java.sql.Struct`    | `gmlToSTRUCT``(CLOB gml)`<br>Deprecated. <br>Use oracle.jdbc.OracleClob and `gmlToSTRUCT(OracleClob)` instead.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static java.sql.Struct`    | `gmlToSTRUCT``(CLOB gml, NUMBER coordOrder)`<br>Deprecated. <br>Use oracle.jdbc.OracleClob and `gmlToSTRUCT(OracleClob, NUMBER)` instead.                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static java.sql.Struct`    | `gmlToSTRUCT``(CLOB gml, java.lang.String srsNameSpace)`<br>Deprecated. <br>Use oracle.jdbc.OracleClob and `gmlToSTRUCT(OracleClob, String)` instead.                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static java.sql.Struct`    | `gmlToSTRUCT``(CLOB gml, java.lang.String srsNameSpace, NUMBER coordOrder)`<br>Deprecated. <br>Use oracle.jdbc.OracleClob and `gmlToSTRUCT(OracleClob, String, NUMBER)` instead.                                                                                                                                                                                                                                                                                                                                                                            |
    | `static java.sql.Struct`    | `gmlToSTRUCT``(OracleClob gml)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static java.sql.Struct`    | `gmlToSTRUCT``(OracleClob gml, NUMBER coordOrder)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static java.sql.Struct`    | `gmlToSTRUCT``(OracleClob gml, java.lang.String srsNameSpace)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static java.sql.Struct`    | `gmlToSTRUCT``(OracleClob gml, java.lang.String srsNameSpace, NUMBER coordOrder)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static java.sql.Struct`    | `gmlToSTRUCT``(java.lang.String gml)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static java.sql.Struct`    | `gmlToSTRUCT``(java.lang.String gml, java.sql.Connection conn)`<br>Deprecated. <br>Connection parameter is ignored; static default connection is used instead. Perhaps this is a bug.                                                                                                                                                                                                                                                                                                                                                                       |
    | `static java.sql.Struct`    | `gmlToSTRUCT``(java.lang.String gml, java.sql.Connection conn, NUMBER coordOrder)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static java.sql.Struct`    | `gmlToSTRUCT``(java.lang.String gml, NUMBER coordOrder)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static java.sql.Struct`    | `gmlToSTRUCT``(java.lang.String gml, java.lang.String srsNameSpace)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static java.sql.Struct`    | `gmlToSTRUCT``(java.lang.String gml, java.lang.String srsNameSpace, NUMBER coordOrder)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static java.lang.String`   | `inside3d``(java.sql.Struct geom1, java.sql.Struct geom2, java.lang.String is_g3d, NUMBER smajax, NUMBER flattening, NUMBER g3d_geog_crs_uom_factor, NUMBER is_unit_radians, NUMBER tolerance)`                                                                                                                                                                                                                                                                                                                                                             |
    | `static java.sql.Struct`    | `kmlToSTRUCT``(CLOB kml)`<br>Deprecated. <br>Use oracle.jdbc.OracleClob and `kmlToSTRUCT(OracleClob)` instead.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static java.sql.Struct`    | `kmlToSTRUCT``(OracleClob kml)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static java.sql.Struct`    | `kmlToSTRUCT``(java.lang.String kml)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static java.sql.Struct`    | `kmlToSTRUCT``(java.lang.String kml, java.sql.Connection conn)`<br>Deprecated. <br>conn ignored; uses class static default connection. Perhaps this is a bug.                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static NUMBER`             | `length``(java.sql.Struct geom, NUMBER count_shared_edges, java.lang.String is_g3d, NUMBER smajax, NUMBER flattening, NUMBER g3d_geog_crs_uom_factor, NUMBER is_unit_radians, NUMBER tolerance)`                                                                                                                                                                                                                                                                                                                                                            |
    | `static BLOB`               | `pctrclip``(java.sql.Struct qry, java.sql.Struct attr_qry, BLOB pts, NUMBER npts, NUMBER numdim, BLOB trs, NUMBER ntrs, NUMBER tolerance, NUMBER includeCustomDim)`<br>Deprecated. <br>Use oracle.jdbc.OracleBlob and `pctrclipJS(Struct, Struct, OracleBlob, NUMBER, NUMBER, OracleBlob, NUMBER, NUMBER, NUMBER)` instead.                                                                                                                                                                                                                                 |
    | `static OracleBlob`         | `pctrclipJS``(java.sql.Struct qry, java.sql.Struct attr_qry, OracleBlob pts, NUMBER npts, NUMBER numdim, OracleBlob trs, NUMBER ntrs, NUMBER tolerance, NUMBER includeCustomDim)`                                                                                                                                                                                                                                                                                                                                                                           |
    | `static void`               | `readpts``(BLOB ptlob, int numpts, int ndim, oracle.spatial.util.Adapters.Ptclass[] ptarr, NUMBER includeCustomDim)`<br>Deprecated. <br>Use oracle.jdbc.OracleBlob and `readptsJS(OracleBlob, int, int, Ptclass[], NUMBER)` instead.                                                                                                                                                                                                                                                                                                                        |
    | `static void`               | `readptsJS``(OracleBlob ptlob, int numpts, int ndim, oracle.spatial.util.Adapters.Ptclass[] ptarr, NUMBER includeCustomDim)`                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static java.sql.Struct`    | `ringUnionApprox``(java.sql.Struct polygon, NUMBER tolerance)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static java.sql.Struct`    | `simplifyVW``(java.sql.Struct geom, NUMBER vthreshold, NUMBER sma, NUMBER iflat)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static BLOB`               | `structToWkb``(java.sql.Struct geom)`<br>Deprecated. <br>Use `structToWkbJS(Struct)` instead.                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static BLOB`               | `structToWkb``(java.sql.Struct geom, java.sql.Connection conn)`<br>Deprecated. <br>Use `structToWkbJS(Struct, Connection)` instead.                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static OracleBlob`         | `structToWkbJS``(java.sql.Struct geom)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static OracleBlob`         | `structToWkbJS``(java.sql.Struct geom, java.sql.Connection conn)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static CLOB`               | `structToWkt``(java.sql.Struct geom)`<br>Deprecated. <br>Use `structToWktJS(Struct)` instead.                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static CLOB`               | `structToWkt``(java.sql.Struct geom, java.sql.Connection conn)`<br>Deprecated. <br>Use `structToWktJS(Struct, Connection)` instead.                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static OracleClob`         | `structToWktJS``(java.sql.Struct geom)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static OracleClob`         | `structToWktJS``(java.sql.Struct geom, java.sql.Connection conn)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static java.lang.String`   | `structToWktString``(java.sql.Struct geom)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static java.lang.Object[]` | `toGeo3DLRSInfo``(java.sql.Struct LRSgeom)`<br>This method accepts a Struct SDO_GEOMETRY which is 4D/3D LRS (point, line string or multi-line) geometry and disintegrates the Measure information and outputs an Object array with J3D_Geometry object and double array of measures.                                                                                                                                                                                                                                                                        |
    | `static java.sql.Struct`    | `toGeo3DLRSStruct``(java.lang.Object[] LRSobj)`<br>This method accepts an Object array with J3D_Geometry object and double array of measures and integrates them into Struct SDO_GEOMETRY which is 4D/3D LRS (point, line string or multi-line) geometry.                                                                                                                                                                                                                                                                                                   |
    | `static NUMBER`             | `validate_layer_with_context_3D``(java.lang.String geomTableName, java.lang.String geomColumnName, java.lang.String resultTableName, NUMBER commit_interval, java.lang.String conditional, NUMBER chck3dsrid, NUMBER smajax, NUMBER flattening, NUMBER g3d_geog_crs_uom_factor, NUMBER is_unit_radians, NUMBER tolerance)`                                                                                                                                                                                                                                  |
    | `static java.lang.String`   | `validateGeom``(java.sql.Struct geom, java.lang.String conditional, NUMBER chck3dsrid, NUMBER smajax, NUMBER flattening, NUMBER g3d_geog_crs_uom_factor, NUMBER is_unit_radians, NUMBER tolerance)`                                                                                                                                                                                                                                                                                                                                                         |
    | `static java.lang.String`   | `validateWkb``(BLOB wkb)`<br>Deprecated. <br>Use oracle.jdbc.OracleBlob and `validateWkb(OracleBlob)` instead.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static java.lang.String`   | `validateWkb``(BLOB wkb, java.sql.Connection conn)`<br>Deprecated. <br>Use oracle.jdbc.OracleBlob and `validateWkb(OracleBlob, Connection)` instead.                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static java.lang.String`   | `validateWkb``(OracleBlob wkb)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static java.lang.String`   | `validateWkb``(OracleBlob wkb, java.sql.Connection conn)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static java.lang.String`   | `validateWkt``(CLOB wkt)`<br>Deprecated. <br>Use oracle.jdbc.OracleClob and `validateWkt(OracleClob)` instead.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static java.lang.String`   | `validateWkt``(CLOB wkt, java.sql.Connection conn)`<br>Deprecated. <br>Use oracle.jdbc.OracleClob and `validateWkt(OracleClob, Connection)` instead.                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static java.lang.String`   | `validateWkt``(OracleClob wkt)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static java.lang.String`   | `validateWkt``(OracleClob wkt, java.sql.Connection conn)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static java.lang.String`   | `validateXMLRecord``(CLOB xml, java.lang.String schema)`<br>This method validateXSDXML is used to validate (schema XSD and its) XML instance.                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static java.lang.String`   | `validateXMLRecord``(OracleClob xml, java.lang.String schema)`<br>This method validateXSDXML is used to validate (schema XSD and its) XML instance.                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static NUMBER`             | `validateXSDXMLLayer``(java.lang.String tableName, java.lang.String columnName, java.lang.String schema, java.lang.String resultTableName, NUMBER commit_interval)`<br>This method validateXSDXMLLayer is used to validate (schema XSD and its) all XML instances from a table such as CSW 202 User Table.                                                                                                                                                                                                                                                  |
    | `static NUMBER`             | `volume``(java.sql.Struct geom, java.lang.String is_g3d, NUMBER smajax, NUMBER flattening, NUMBER g3d_geog_crs_uom_factor, NUMBER is_unit_radians, NUMBER tolerance)`                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static java.sql.Struct`    | `wkbToSTRUCT``(BLOB wkb)`<br>Deprecated. <br>Use oracle.jdbc.OracleClob and `wkbToSTRUCT(OracleBlob)` instead.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static java.sql.Struct`    | `wkbToSTRUCT``(BLOB wkb, java.sql.Connection conn)`<br>Deprecated. <br>Use oracle.jdbc.OracleClob and `wkbToSTRUCT(OracleBlob, Connection)` instead.                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static java.sql.Struct`    | `wkbToSTRUCT``(OracleBlob wkb)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static java.sql.Struct`    | `wkbToSTRUCT``(OracleBlob wkb, java.sql.Connection conn)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static java.sql.Struct`    | `wktToSTRUCT``(CLOB wkt)`<br>Deprecated. <br>Use oracle.jdbc.OracleClob and `wktToSTRUCT(OracleClob)` instead.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static java.sql.Struct`    | `wktToSTRUCT``(CLOB wkt, java.sql.Connection conn)`<br>Deprecated. <br>Use oracle.jdbc.OracleClob and `wktToSTRUCT(OracleClob, Connection)` instead.                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static java.sql.Struct`    | `wktToSTRUCT``(OracleClob wkt)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static java.sql.Struct`    | `wktToSTRUCT``(OracleClob wkt, java.sql.Connection conn)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static void`               | `writepts``(BLOB ptlob, int numpts, int ndim, oracle.spatial.util.Adapters.Ptclass[] ptarr, NUMBER includeCustomDim)`<br>Deprecated. <br>Use oracle.jdbc.OracleBlob and `writeptsJS(OracleBlob, int, int, Ptclass[], NUMBER)` instead.                                                                                                                                                                                                                                                                                                                      |
    | `static void`               | `writeptsJS``(OracleBlob ptlob, int numpts, int ndim, oracle.spatial.util.Adapters.Ptclass[] ptarr, NUMBER includeCustomDim)`                                                                                                                                                                                                                                                                                                                                                                                                                               |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### Adapters

          public Adapters()

  <!-- -->

  - ### Method Detail

    - #### wkbToSTRUCT

          public static java.sql.Struct wkbToSTRUCT(BLOB wkb)
                                             throws java.sql.SQLException

      Deprecated. Use oracle.jdbc.OracleClob and `wkbToSTRUCT(OracleBlob)` instead.
      Parameters:
      `wkb` - The BLOB WKB Object

      Returns:
      Struct

      Throws:
      `java.sql.SQLException` - The SQL Exception

    <!-- -->

    - #### wkbToSTRUCT

          public static java.sql.Struct wkbToSTRUCT(BLOB wkb,
                                                    java.sql.Connection conn)
                                             throws java.sql.SQLException

      Deprecated. Use oracle.jdbc.OracleClob and `wkbToSTRUCT(OracleBlob, Connection)` instead.
      Parameters:
      `wkb` - The BLOB WKB Object

      `conn` - The Database Connection

      Returns:
      Struct

      Throws:
      `java.sql.SQLException` - The SQL Exception

    <!-- -->

    - #### wktToSTRUCT

          public static java.sql.Struct wktToSTRUCT(CLOB wkt)
                                             throws java.sql.SQLException

      Deprecated. Use oracle.jdbc.OracleClob and `wktToSTRUCT(OracleClob)` instead.
      Parameters:
      `wkt` - The CLOB WKT Object

      Returns:
      Struct

      Throws:
      `java.sql.SQLException` - The SQL Exception

    <!-- -->

    - #### wktToSTRUCT

          public static java.sql.Struct wktToSTRUCT(CLOB wkt,
                                                    java.sql.Connection conn)
                                             throws java.sql.SQLException

      Deprecated. Use oracle.jdbc.OracleClob and `wktToSTRUCT(OracleClob, Connection)` instead.
      Parameters:
      `wkt` - The CLOB WKT Object

      `conn` - The Database Connection

      Returns:
      Struct

      Throws:
      `java.sql.SQLException` - The SQL Exception

    <!-- -->

    - #### gmlToSTRUCT

          public static java.sql.Struct gmlToSTRUCT(java.lang.String gml)
                                             throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### gml311ToSTRUCT

          public static java.sql.Struct gml311ToSTRUCT(java.lang.String gml)
                                                throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### kmlToSTRUCT

          public static java.sql.Struct kmlToSTRUCT(java.lang.String kml)
                                             throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### buffer

          public static java.sql.Struct buffer(java.sql.Struct geom,
                                               NUMBER bufferWidth,
                                               NUMBER sma,
                                               NUMBER iflat,
                                               NUMBER arcT)
                                        throws java.sql.SQLException,
                                               java.lang.Exception

      Throws:
      `java.sql.SQLException`

      `java.lang.Exception`

    <!-- -->

    - #### simplifyVW

          public static java.sql.Struct simplifyVW(java.sql.Struct geom,
                                                   NUMBER vthreshold,
                                                   NUMBER sma,
                                                   NUMBER iflat)
                                            throws java.sql.SQLException,
                                                   java.lang.Exception

      Throws:
      `java.sql.SQLException`

      `java.lang.Exception`

    <!-- -->

    - #### getNurbsApprox

          public static java.sql.Struct getNurbsApprox(java.sql.Struct geom)
                                                throws java.sql.SQLException,
                                                       java.lang.Exception

      Throws:
      `java.sql.SQLException`

      `java.lang.Exception`

    <!-- -->

    - #### anyInteract

          public static java.lang.String anyInteract(java.sql.Struct geom1,
                                                     java.sql.Struct geom2,
                                                     java.lang.String is_g3d,
                                                     NUMBER smajax,
                                                     NUMBER flattening,
                                                     NUMBER g3d_geog_crs_uom_factor,
                                                     NUMBER is_unit_radians,
                                                     NUMBER tolerance)
                                              throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### distance

          public static NUMBER distance(java.sql.Struct geom1,
                                        java.sql.Struct geom2,
                                        java.lang.String is_g3d,
                                        NUMBER smajax,
                                        NUMBER flattening,
                                        NUMBER g3d_geog_crs_uom_factor,
                                        NUMBER is_unit_radians,
                                        NUMBER tolerance)
                                 throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### length

          public static NUMBER length(java.sql.Struct geom,
                                      NUMBER count_shared_edges,
                                      java.lang.String is_g3d,
                                      NUMBER smajax,
                                      NUMBER flattening,
                                      NUMBER g3d_geog_crs_uom_factor,
                                      NUMBER is_unit_radians,
                                      NUMBER tolerance)
                               throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### area

          public static NUMBER area(java.sql.Struct geom,
                                    java.lang.String is_g3d,
                                    NUMBER smajax,
                                    NUMBER flattening,
                                    NUMBER g3d_geog_crs_uom_factor,
                                    NUMBER is_unit_radians,
                                    NUMBER tolerance)
                             throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### volume

          public static NUMBER volume(java.sql.Struct geom,
                                      java.lang.String is_g3d,
                                      NUMBER smajax,
                                      NUMBER flattening,
                                      NUMBER g3d_geog_crs_uom_factor,
                                      NUMBER is_unit_radians,
                                      NUMBER tolerance)
                               throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### validateGeom

          public static java.lang.String validateGeom(java.sql.Struct geom,
                                                      java.lang.String conditional,
                                                      NUMBER chck3dsrid,
                                                      NUMBER smajax,
                                                      NUMBER flattening,
                                                      NUMBER g3d_geog_crs_uom_factor,
                                                      NUMBER is_unit_radians,
                                                      NUMBER tolerance)
                                               throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### closestPoints

          public static java.sql.Struct closestPoints(java.sql.Struct geom1,
                                                      java.sql.Struct geom2,
                                                      java.lang.String is_g3d,
                                                      NUMBER smajax,
                                                      NUMBER flattening,
                                                      NUMBER g3d_geog_crs_uom_factor,
                                                      NUMBER is_unit_radians,
                                                      NUMBER tolerance)
                                               throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### affineTransforms

          public static java.sql.Struct affineTransforms(java.sql.Struct geom,
                                                         java.lang.String translation,
                                                         NUMBER tx,
                                                         NUMBER ty,
                                                         NUMBER tz,
                                                         java.lang.String scaling,
                                                         java.sql.Struct Psc1,
                                                         NUMBER sx,
                                                         NUMBER sy,
                                                         NUMBER sz,
                                                         java.lang.String rotation,
                                                         java.sql.Struct P1,
                                                         java.sql.Struct line1,
                                                         NUMBER angle,
                                                         NUMBER dir,
                                                         java.lang.String shearing,
                                                         NUMBER SHxy,
                                                         NUMBER SHyx,
                                                         NUMBER SHxz,
                                                         NUMBER SHzx,
                                                         NUMBER SHyz,
                                                         NUMBER SHzy,
                                                         java.lang.String reflection,
                                                         java.sql.Struct Pref,
                                                         java.sql.Struct lineR,
                                                         NUMBER dirR,
                                                         java.lang.String planeR,
                                                         SdoNumberArray n,
                                                         SdoNumberArray bigD)
                                                  throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### gmlToSTRUCT

          public static java.sql.Struct gmlToSTRUCT(java.lang.String gml,
                                                    java.lang.String srsNameSpace)
                                             throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### gmlToSTRUCT

          @Deprecated
          public static java.sql.Struct gmlToSTRUCT(java.lang.String gml,
                                                                 java.sql.Connection conn)
                                                          throws java.sql.SQLException

      Deprecated. Connection parameter is ignored; static default connection is used instead. Perhaps this is a bug.
      Parameters:
      `gml` - The String GML Object

      `conn` - The Database Connection

      Returns:
      Throws:
      `java.sql.SQLException` - The SQL Exception

    <!-- -->

    - #### gmlToSTRUCT

          public static java.sql.Struct gmlToSTRUCT(CLOB gml)
                                             throws java.sql.SQLException

      Deprecated. Use oracle.jdbc.OracleClob and `gmlToSTRUCT(OracleClob)` instead.
      Parameters:
      `gml` - The CLOB GML Object

      Returns:
      Struct

      Throws:
      `java.sql.SQLException` - The SQL Exception

    <!-- -->

    - #### gmlToSTRUCT

          public static java.sql.Struct gmlToSTRUCT(CLOB gml,
                                                    java.lang.String srsNameSpace)
                                             throws java.sql.SQLException

      Deprecated. Use oracle.jdbc.OracleClob and `gmlToSTRUCT(OracleClob, String)` instead.
      Parameters:
      `gml` - The CLOB GML Object

      `srsNameSpace` - The SRS Namespace String Object

      Returns:
      Struct

      Throws:
      `java.sql.SQLException` - The SQL Exception

    <!-- -->

    - #### gml311ToSTRUCT

          public static java.sql.Struct gml311ToSTRUCT(java.lang.String gml,
                                                       java.lang.String srsNameSpace)
                                                throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### gml311ToSTRUCT

          @Deprecated
          public static java.sql.Struct gml311ToSTRUCT(java.lang.String gml,
                                                                    java.sql.Connection conn)
                                                             throws java.sql.SQLException

      Deprecated. Connection parameter is ignored; static default connection is used instead. Perhaps this is a bug.
      Parameters:
      `gml` - The String GML Object

      `conn` - The Database Connection

      Returns:
      Throws:
      `java.sql.SQLException` - The SQL Exception

    <!-- -->

    - #### gml311ToSTRUCT

          public static java.sql.Struct gml311ToSTRUCT(CLOB gml)
                                                throws java.sql.SQLException

      Deprecated. Use oracle.jdbc.OracleClob and `gml311ToSTRUCT(OracleClob)` instead.
      Parameters:
      `gml` - The CLOB GML Object

      Returns:
      Struct

      Throws:
      `java.sql.SQLException` - The SQL Exception

    <!-- -->

    - #### gml311ToSTRUCT

          public static java.sql.Struct gml311ToSTRUCT(CLOB gml,
                                                       java.lang.String srsNameSpace)
                                                throws java.sql.SQLException

      Deprecated. Use oracle.jdbc.OracleClob and `gml311ToSTRUCT(OracleClob, String)` instead.
      Parameters:
      `gml` - The CLOB GML Object

      `srsNameSpace` - The SRS Namespace String Object

      Returns:
      Struct

      Throws:
      `java.sql.SQLException` - The SQL Exception

    <!-- -->

    - #### kmlToSTRUCT

          public static java.sql.Struct kmlToSTRUCT(java.lang.String kml,
                                                    java.sql.Connection conn)
                                             throws java.sql.SQLException

      Deprecated. conn ignored; uses class static default connection. Perhaps this is a bug.
      Parameters:
      `kml` - The String KML Object

      `conn` - The Database Connection

      Returns:
      Throws:
      `java.sql.SQLException` - The SQL Exception

    <!-- -->

    - #### kmlToSTRUCT

          public static java.sql.Struct kmlToSTRUCT(CLOB kml)
                                             throws java.sql.SQLException

      Deprecated. Use oracle.jdbc.OracleClob and `kmlToSTRUCT(OracleClob)` instead.
      Parameters:
      `kml` - The CLOB KML Object

      Returns:
      Struct

      Throws:
      `java.sql.SQLException` - The SQL Exception

    <!-- -->

    - #### structToWkb

          public static BLOB structToWkb(java.sql.Struct geom)
                                  throws java.sql.SQLException

      Deprecated. Use `structToWkbJS(Struct)` instead.
      Parameters:
      `geom` - The Struct Geometry Object

      Returns:
      BLOB

      Throws:
      `java.sql.SQLException` - The SQL Exception

    <!-- -->

    - #### structToWkb

          public static BLOB structToWkb(java.sql.Struct geom,
                                         java.sql.Connection conn)
                                  throws java.sql.SQLException

      Deprecated. Use `structToWkbJS(Struct, Connection)` instead.
      Parameters:
      `geom` - The Struct Geometry Object

      `conn` - The Database Connection

      Returns:
      BLOB

      Throws:
      `java.sql.SQLException` - The SQL Exception

    <!-- -->

    - #### structToWkt

          public static CLOB structToWkt(java.sql.Struct geom)
                                  throws java.sql.SQLException

      Deprecated. Use `structToWktJS(Struct)` instead.
      Parameters:
      `geom` - The Struct Geometry Object

      Returns:
      CLOB

      Throws:
      `java.sql.SQLException` - The SQL Exception

    <!-- -->

    - #### structToWktString

          public static java.lang.String structToWktString(java.sql.Struct geom)
                                                    throws java.sql.SQLException

      Parameters:
      `geom` - The Struct Geometry Object

      Returns:
      String

      Throws:
      `java.sql.SQLException` - The SQL Exception

    <!-- -->

    - #### structToWkt

          public static CLOB structToWkt(java.sql.Struct geom,
                                         java.sql.Connection conn)
                                  throws java.sql.SQLException

      Deprecated. Use `structToWktJS(Struct, Connection)` instead.
      Parameters:
      `geom` - The Struct Geometry Object

      `conn` - The Database Connection

      Returns:
      CLOB

      Throws:
      `java.sql.SQLException` - The SQL Exception

    <!-- -->

    - #### validateWkt

          public static java.lang.String validateWkt(CLOB wkt)

      Deprecated. Use oracle.jdbc.OracleClob and `validateWkt(OracleClob)` instead.
      Parameters:
      `wkt` - The WKT BLOB Object

      Returns:
      String

    <!-- -->

    - #### validateWkt

          public static java.lang.String validateWkt(CLOB wkt,
                                                     java.sql.Connection conn)

      Deprecated. Use oracle.jdbc.OracleClob and `validateWkt(OracleClob, Connection)` instead.
      Parameters:
      `wkt` - The WKT CLOB Object

      `conn` - The Database Connection

      Returns:
      String

    <!-- -->

    - #### validateWkb

          public static java.lang.String validateWkb(BLOB wkb)

      Deprecated. Use oracle.jdbc.OracleBlob and `validateWkb(OracleBlob)` instead.
      Parameters:
      `wkb` - The WKB BLOB Object

      Returns:
      String

    <!-- -->

    - #### validateWkb

          public static java.lang.String validateWkb(BLOB wkb,
                                                     java.sql.Connection conn)

      Deprecated. Use oracle.jdbc.OracleBlob and `validateWkb(OracleBlob, Connection)` instead.
      Parameters:
      `wkb` - The WKB BLOB Object

      `conn` - The Database Connection

      Returns:
      String

    <!-- -->

    - #### validate_layer_with_context_3D

          public static NUMBER validate_layer_with_context_3D(java.lang.String geomTableName,
                                                              java.lang.String geomColumnName,
                                                              java.lang.String resultTableName,
                                                              NUMBER commit_interval,
                                                              java.lang.String conditional,
                                                              NUMBER chck3dsrid,
                                                              NUMBER smajax,
                                                              NUMBER flattening,
                                                              NUMBER g3d_geog_crs_uom_factor,
                                                              NUMBER is_unit_radians,
                                                              NUMBER tolerance)
                                                       throws java.sql.SQLSyntaxErrorException,
                                                              java.sql.SQLException,
                                                              java.lang.Exception

      Throws:
      `java.sql.SQLSyntaxErrorException`

      `java.sql.SQLException`

      `java.lang.Exception`

    <!-- -->

    - #### centroid_3d

          public static java.sql.Struct centroid_3d(java.sql.Struct geom,
                                                    NUMBER tolerance)
                                             throws java.lang.Exception,
                                                    java.sql.SQLException

      Throws:
      `java.lang.Exception`

      `java.sql.SQLException`

    <!-- -->

    - #### extrusion2

          public static java.sql.Struct extrusion2(java.sql.Struct polygon,
                                                   SdoNumberArray grdHeight,
                                                   SdoNumberArray height,
                                                   NUMBER tolerance,
                                                   NUMBER optional3dSrid)
                                            throws java.lang.Exception,
                                                   java.sql.SQLException

      Throws:
      `java.lang.Exception`

      `java.sql.SQLException`

    <!-- -->

    - #### ringUnionApprox

          public static java.sql.Struct ringUnionApprox(java.sql.Struct polygon,
                                                        NUMBER tolerance)
                                                 throws java.lang.Exception,
                                                        java.sql.SQLException

      Throws:
      `java.lang.Exception`

      `java.sql.SQLException`

    <!-- -->

    - #### extract3d

          public static java.sql.Struct extract3d(java.sql.Struct geom,
                                                  java.lang.String label)
                                           throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getlabelbyelement

          public static java.lang.String getlabelbyelement(java.sql.Struct source_Geom,
                                                           java.sql.Struct qry_Element,
                                                           NUMBER tolerance)
                                                    throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### inside3d

          public static java.lang.String inside3d(java.sql.Struct geom1,
                                                  java.sql.Struct geom2,
                                                  java.lang.String is_g3d,
                                                  NUMBER smajax,
                                                  NUMBER flattening,
                                                  NUMBER g3d_geog_crs_uom_factor,
                                                  NUMBER is_unit_radians,
                                                  NUMBER tolerance)
                                           throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### readpts

          public static void readpts(BLOB ptlob,
                                     int numpts,
                                     int ndim,
                                     oracle.spatial.util.Adapters.Ptclass[] ptarr,
                                     NUMBER includeCustomDim)
                              throws java.sql.SQLException,
                                     java.io.IOException

      Deprecated. Use oracle.jdbc.OracleBlob and `readptsJS(OracleBlob, int, int, Ptclass[], NUMBER)` instead.
      Parameters:
      `ptlob` - BLOB Object

      `numpts` - Number of Points

      `ndim` - Number of Dimensions

      `ptarr` - Point Array

      `includeCustomDim` - Include custom dimension

      Throws:
      `java.sql.SQLException` - The SQL Exception

      `java.io.IOException` - The IO Exception

    <!-- -->

    - #### writepts

          public static void writepts(BLOB ptlob,
                                      int numpts,
                                      int ndim,
                                      oracle.spatial.util.Adapters.Ptclass[] ptarr,
                                      NUMBER includeCustomDim)
                               throws java.sql.SQLException,
                                      java.io.IOException

      Deprecated. Use oracle.jdbc.OracleBlob and `writeptsJS(OracleBlob, int, int, Ptclass[], NUMBER)` instead.
      Parameters:
      `ptlob` - BLOB Object

      `numpts` - Number of Points

      `ndim` - Number of dimensions

      `ptarr` - Point Array

      `includeCustomDim` - Include custom dimension

      Throws:
      `java.sql.SQLException` - The SQL Exception

      `java.io.IOException` - The IO Exception

    <!-- -->

    - #### pctrclip

          public static BLOB pctrclip(java.sql.Struct qry,
                                      java.sql.Struct attr_qry,
                                      BLOB pts,
                                      NUMBER npts,
                                      NUMBER numdim,
                                      BLOB trs,
                                      NUMBER ntrs,
                                      NUMBER tolerance,
                                      NUMBER includeCustomDim)
                               throws java.sql.SQLException,
                                      java.io.IOException,
                                      java.lang.Exception

      Deprecated. Use oracle.jdbc.OracleBlob and `pctrclipJS(Struct, Struct, OracleBlob, NUMBER, NUMBER, OracleBlob, NUMBER, NUMBER, NUMBER)` instead.
      Parameters:
      `qry` - The Query

      `attr_qry` - The attr Query

      `pts` - Points

      `npts` - Number of Points

      `numdim` - Dimension Number

      `trs` - BLOB Object

      `ntrs` - NUMBER Object

      `tolerance` - The tolerance

      `includeCustomDim` - Including custom dimension

      Returns:
      BLOB The BLOB Object

      Throws:
      `java.sql.SQLException` - The SQL Exception

      `java.io.IOException` - The IO Exception

      `java.lang.Exception` - The Exception

    <!-- -->

    - #### expandG3Dgeoms

          public static java.sql.Struct expandG3Dgeoms(java.sql.Struct geom)
                                                throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### toGeo3DLRSInfo

          public static java.lang.Object[] toGeo3DLRSInfo(java.sql.Struct LRSgeom)
                                                   throws java.lang.Exception

      This method accepts a Struct SDO_GEOMETRY which is 4D/3D LRS (point, line string or multi-line) geometry and disintegrates the Measure information and outputs an Object array with J3D_Geometry object and double array of measures. This is the reverse process of integrateLRS method. If the double array of measures is null, that means the input geometry geomLRS is not LRS geometry.
      Parameters:
      `LRSgeom` - Struct SDO_GEOMETRY which is 4D/3D LRS (point, line string or multi-line) geometry

      Returns:
      Object\[\] array with 2 elements: J3D_Geometry object and double array of measures

      Throws:
      `java.lang.Exception` - The Exception

    <!-- -->

    - #### toGeo3DLRSStruct

          public static java.sql.Struct toGeo3DLRSStruct(java.lang.Object[] LRSobj)
                                                  throws java.lang.Exception

      This method accepts an Object array with J3D_Geometry object and double array of measures and integrates them into Struct SDO_GEOMETRY which is 4D/3D LRS (point, line string or multi-line) geometry. This is the reverse process of disintegrateLRS method.
      Parameters:
      `LRSobj` - Object\[\] array with 2 elements: J3D_Geometry object and double array of measures

      Returns:
      STRUCT SDO_GEOMETRY which is 4D/3D LRS (point, line string, multi-line) geometry

      Throws:
      `java.lang.Exception` - The Exception

    <!-- -->

    - #### gmlToSTRUCT

          public static java.sql.Struct gmlToSTRUCT(java.lang.String gml,
                                                    NUMBER coordOrder)
                                             throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### gmlToSTRUCT

          public static java.sql.Struct gmlToSTRUCT(java.lang.String gml,
                                                    java.lang.String srsNameSpace,
                                                    NUMBER coordOrder)
                                             throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### gmlToSTRUCT

          public static java.sql.Struct gmlToSTRUCT(java.lang.String gml,
                                                    java.sql.Connection conn,
                                                    NUMBER coordOrder)
                                             throws java.sql.SQLException

      Parameters:
      `gml` - The String GML Object

      `conn` - used for setConnection; class static default connection used for conversion to Struct. Perhaps this is a bug.

      `coordOrder` - The coordinate order

      Returns:
      Struct Object

      Throws:
      `java.sql.SQLException` - The SQLException

    <!-- -->

    - #### gmlToSTRUCT

          public static java.sql.Struct gmlToSTRUCT(CLOB gml,
                                                    NUMBER coordOrder)
                                             throws java.sql.SQLException

      Deprecated. Use oracle.jdbc.OracleClob and `gmlToSTRUCT(OracleClob, NUMBER)` instead.
      Parameters:
      `gml` -

      `coordOrder` -

      Returns:
      Struct

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### gmlToSTRUCT

          public static java.sql.Struct gmlToSTRUCT(CLOB gml,
                                                    java.lang.String srsNameSpace,
                                                    NUMBER coordOrder)
                                             throws java.sql.SQLException

      Deprecated. Use oracle.jdbc.OracleClob and `gmlToSTRUCT(OracleClob, String, NUMBER)` instead.
      Parameters:
      `gml` -

      `srsNameSpace` -

      `coordOrder` -

      Returns:
      Struct

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### gml311ToSTRUCT

          public static java.sql.Struct gml311ToSTRUCT(java.lang.String gml,
                                                       NUMBER coordOrder)
                                                throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### gml311ToSTRUCT

          public static java.sql.Struct gml311ToSTRUCT(java.lang.String gml,
                                                       java.lang.String srsNameSpace,
                                                       NUMBER coordOrder)
                                                throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### gml311ToSTRUCT

          public static java.sql.Struct gml311ToSTRUCT(java.lang.String gml,
                                                       java.sql.Connection conn,
                                                       NUMBER coordOrder)
                                                throws java.sql.SQLException

      Parameters:
      `gml` -

      `conn` - uses this connection and also this class's static default connection. This is perhaps a bug.

      `coordOrder` -

      Returns:
      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### gml311ToSTRUCT

          public static java.sql.Struct gml311ToSTRUCT(CLOB gml,
                                                       NUMBER coordOrder)
                                                throws java.sql.SQLException

      Deprecated. Use oracle.jdbc.OracleClob and `gml311ToSTRUCT(OracleClob, NUMBER)` instead.
      Parameters:
      `gml` -

      `coordOrder` -

      Returns:
      Struct

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### gml311ToSTRUCT

          public static java.sql.Struct gml311ToSTRUCT(CLOB gml,
                                                       java.lang.String srsNameSpace,
                                                       NUMBER coordOrder)
                                                throws java.sql.SQLException

      Deprecated. Use oracle.jdbc.OracleClob and `gml311ToSTRUCT(OracleClob, String, NUMBER)` instead.
      Parameters:
      `gml` -

      `srsNameSpace` -

      `coordOrder` -

      Returns:
      Struct

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### wktToSTRUCT

          public static java.sql.Struct wktToSTRUCT(OracleClob wkt)
                                             throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### wktToSTRUCT

          public static java.sql.Struct wktToSTRUCT(OracleClob wkt,
                                                    java.sql.Connection conn)
                                             throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### wkbToSTRUCT

          public static java.sql.Struct wkbToSTRUCT(OracleBlob wkb)
                                             throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### wkbToSTRUCT

          public static java.sql.Struct wkbToSTRUCT(OracleBlob wkb,
                                                    java.sql.Connection conn)
                                             throws java.sql.SQLException

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### structToWkbJS

          public static OracleBlob structToWkbJS(java.sql.Struct geom)
                                          throws java.sql.SQLException

      Parameters:
      `geom` -

      Returns:
      OracleBlob

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### structToWkbJS

          public static OracleBlob structToWkbJS(java.sql.Struct geom,
                                                 java.sql.Connection conn)
                                          throws java.sql.SQLException

      Parameters:
      `geom` -

      `conn` -

      Returns:
      OracleBlob

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### structToWktJS

          public static OracleClob structToWktJS(java.sql.Struct geom)
                                          throws java.sql.SQLException

      Parameters:
      `geom` -

      Returns:
      OracleClob

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### structToWktJS

          public static OracleClob structToWktJS(java.sql.Struct geom,
                                                 java.sql.Connection conn)
                                          throws java.sql.SQLException

      Parameters:
      `geom` -

      `conn` -

      Returns:
      OracleClob

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### validateWkb

          public static java.lang.String validateWkb(OracleBlob wkb)

      Parameters:
      `wkb` -

      Returns:
      String

    <!-- -->

    - #### validateWkb

          public static java.lang.String validateWkb(OracleBlob wkb,
                                                     java.sql.Connection conn)

      Parameters:
      `wkb` -

      `conn` -

      Returns:
      String

    <!-- -->

    - #### validateWkt

          public static java.lang.String validateWkt(OracleClob wkt)

      Parameters:
      `wkt` -

      Returns:
      String

    <!-- -->

    - #### validateWkt

          public static java.lang.String validateWkt(OracleClob wkt,
                                                     java.sql.Connection conn)

      Parameters:
      `wkt` -

      `conn` -

      Returns:
      String

    <!-- -->

    - #### gml311ToSTRUCT

          public static java.sql.Struct gml311ToSTRUCT(OracleClob gml)
                                                throws java.sql.SQLException

      Parameters:
      `gml` -

      Returns:
      Struct

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### gml311ToSTRUCT

          public static java.sql.Struct gml311ToSTRUCT(OracleClob gml,
                                                       NUMBER coordOrder)
                                                throws java.sql.SQLException

      Parameters:
      `gml` -

      `coordOrder` -

      Returns:
      Struct

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### gml311ToSTRUCT

          public static java.sql.Struct gml311ToSTRUCT(OracleClob gml,
                                                       java.lang.String srsNameSpace)
                                                throws java.sql.SQLException

      Parameters:
      `gml` -

      `srsNameSpace` -

      Returns:
      Struct

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### gml311ToSTRUCT

          public static java.sql.Struct gml311ToSTRUCT(OracleClob gml,
                                                       java.lang.String srsNameSpace,
                                                       NUMBER coordOrder)
                                                throws java.sql.SQLException

      Parameters:
      `gml` -

      `srsNameSpace` -

      `coordOrder` -

      Returns:
      Struct

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### gmlToSTRUCT

          public static java.sql.Struct gmlToSTRUCT(OracleClob gml)
                                             throws java.sql.SQLException

      Parameters:
      `gml` -

      Returns:
      Struct

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### gmlToSTRUCT

          public static java.sql.Struct gmlToSTRUCT(OracleClob gml,
                                                    NUMBER coordOrder)
                                             throws java.sql.SQLException

      Parameters:
      `gml` -

      `coordOrder` -

      Returns:
      Struct

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### gmlToSTRUCT

          public static java.sql.Struct gmlToSTRUCT(OracleClob gml,
                                                    java.lang.String srsNameSpace)
                                             throws java.sql.SQLException

      Parameters:
      `gml` -

      `srsNameSpace` -

      Returns:
      Struct

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### gmlToSTRUCT

          public static java.sql.Struct gmlToSTRUCT(OracleClob gml,
                                                    java.lang.String srsNameSpace,
                                                    NUMBER coordOrder)
                                             throws java.sql.SQLException

      Parameters:
      `gml` -

      `srsNameSpace` -

      `coordOrder` -

      Returns:
      Struct

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### kmlToSTRUCT

          public static java.sql.Struct kmlToSTRUCT(OracleClob kml)
                                             throws java.sql.SQLException

      Parameters:
      `kml` -

      Returns:
      Struct

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### pctrclipJS

          public static OracleBlob pctrclipJS(java.sql.Struct qry,
                                              java.sql.Struct attr_qry,
                                              OracleBlob pts,
                                              NUMBER npts,
                                              NUMBER numdim,
                                              OracleBlob trs,
                                              NUMBER ntrs,
                                              NUMBER tolerance,
                                              NUMBER includeCustomDim)
                                       throws java.sql.SQLException,
                                              java.io.IOException,
                                              java.lang.Exception

      Parameters:
      `qry` -

      `attr_qry` -

      `pts` -

      `npts` -

      `numdim` -

      `trs` -

      `ntrs` -

      `tolerance` -

      `includeCustomDim` -

      Returns:
      OracleBlob

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

      `java.lang.Exception`

    <!-- -->

    - #### readptsJS

          public static void readptsJS(OracleBlob ptlob,
                                       int numpts,
                                       int ndim,
                                       oracle.spatial.util.Adapters.Ptclass[] ptarr,
                                       NUMBER includeCustomDim)
                                throws java.sql.SQLException,
                                       java.io.IOException

      Parameters:
      `ptlob` -

      `numpts` -

      `ndim` -

      `ptarr` -

      `includeCustomDim` -

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### writeptsJS

          public static void writeptsJS(OracleBlob ptlob,
                                        int numpts,
                                        int ndim,
                                        oracle.spatial.util.Adapters.Ptclass[] ptarr,
                                        NUMBER includeCustomDim)
                                 throws java.sql.SQLException,
                                        java.io.IOException

      Parameters:
      `ptlob` -

      `numpts` -

      `ndim` -

      `ptarr` -

      `includeCustomDim` -

      Throws:
      `java.sql.SQLException`

      `java.io.IOException`

    <!-- -->

    - #### validateXMLRecord

          public static java.lang.String validateXMLRecord(CLOB xml,
                                                           java.lang.String schema)
                                                    throws java.lang.Exception

      This method validateXSDXML is used to validate (schema XSD and its) XML instance. This method does not benefit from oracle.spatial.util.XMLValidator2 caching.
      Parameters:
      `xml` - The CLOB object for the XML to be validated.

      `schema` - The URL for the XSD to be validated.

      Returns:
      String The status of the XML validated against its XSD: TRUE/NULL/Error Message

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### validateXMLRecord

          public static java.lang.String validateXMLRecord(OracleClob xml,
                                                           java.lang.String schema)
                                                    throws java.lang.Exception

      This method validateXSDXML is used to validate (schema XSD and its) XML instance. This method does not benefit from oracle.spatial.util.XMLValidator2 caching.
      Parameters:
      `xml` - The Clob object for the XML to be validated.

      `schema` - The URL for the XSD to be validated.

      Returns:
      String The status of the XML validated against its XSD: TRUE/NULL/Error Message

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### validateXSDXMLLayer

          public static NUMBER validateXSDXMLLayer(java.lang.String tableName,
                                                   java.lang.String columnName,
                                                   java.lang.String schema,
                                                   java.lang.String resultTableName,
                                                   NUMBER commit_interval)
                                            throws java.sql.SQLSyntaxErrorException,
                                                   java.sql.SQLException,
                                                   java.lang.Exception

      This method validateXSDXMLLayer is used to validate (schema XSD and its) all XML instances from a table such as CSW 202 User Table. This is another API. This method benefits from oracle.spatial.util.XMLValidator2 caching. -- Open a resultset to fetch each rowid, XML instance "columnName" from the "tableName" -- For each XML instance in resultset. do: -- call your XMLValidator2.schemaValidate -- insert rowid, validate_result(Nothing(TRUE)/NULL/Error Message) into resultTableName if (commit_count == commit_interval) then "commit" and reset the commit_count counter. -- End of for loop (dont raise any exceptions in this loop) -- Update resultTableName set columnName= %s the row "Rows Processed " + tot_XMLInstances_processed_count into the resultTableName.
      Parameters:
      `tableName` - owner.table name which has the Clob objects for the XMLs to be validated.

      `columnName` - Name of the column that has the Clob objects for the XMLs to be validated. (XMLType column)

      `schema` - The URL for the XSD to be validated. The XSD is fetched from table MDSYS.SDO_XSD_TABLE in oracle.spatial.util.SchemaEntityResolver class.

      `resultTableName` - Table name where results of XSD/XML validations are stored (Nothing means TRUE/NULL for NULL XML Object/Error Message).

      `commit_interval` -

      Returns:
      NUMBER The total number of XML Instances processed.

      Throws:
      `java.sql.SQLSyntaxErrorException`

      `java.sql.SQLException`

      `java.lang.Exception`

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

- Prev Class
- [Next Class](AdapterShapefileJGeom.md)

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
