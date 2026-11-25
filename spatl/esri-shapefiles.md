## C Loading ESRI Shapefiles into Spatial and Graph

The Java shapefile converter transforms an ESRI shapefile into an Oracle Database table for use with Oracle Spatial and Graph.

The shapefile converter uses the Oracle Spatial and Graph Java-based shapefile `AdapterShapefileJGeom` and `SampleShapefileToJGeomFeature` classes to load a shapefile directly into a database table, with the Oracle-equivalent `.dbf` data types for the attribute columns and the SDO_GEOMETRY data type for the geometry column.

To load a shapefile into the database, use the converter as described in this appendix. (You can also use the `Adapter` class to create your own applications and interfaces that transform shapefiles to SDO_GEOMETRY or JGeometry data types; however, doing this is beyond the scope of this manual. For information about shapefile-related classes, see [Oracle Spatial and Graph Java API Reference](../spajv/index.md)).

To use the shapefile converter, you must have the following:

- The following Oracle utilities and JDBC libraries: `ojdbc14.jar` or `ojdbc5.jar`, `sdoutl.jar`, and `sdoapi.jar`

- One or more ESRI shapefiles (`.shp`, `.shx`, .and `.dbf` files) to be converted

<!-- -->

- Usage of the Shapefile Converter
- Examples of the Shapefile Converter

**Parent topic:** [Supplementary Information](spatial-supplementary-information.md)

### C.1 Usage of the Shapefile Converter

The following is the syntax for the shapefile converter. (Enter the command all on a single line.)

    > java -cp [ORACLE_HOME]/jdbc/lib/ojdbc5.jar:[ORACLE_HOME]/md/jlib/sdoutl.jar:[ORACLE_HOME]/md/jlib/sdoapi.jar oracle.spatial.util.SampleShapefileToJGeomFeature -h db_host -p db_port -s db_sid|-sn db_service_name -u db_username -d db_password -t db_table -f shapefile_name [-r srid] [-i table_id_column_name][-n start_id] [-g db_geometry_column] [-x max_x,min_x] [-y max_y,min_y] [-o tolerance] [-k keyword_table] [-a append][-c commit_int] [-v println_int]

#### Parameters

`-h`: Host machine with an existing Oracle database

`-p`: Port on the host machine (for example, 1521)

`-s`: SID (database name) on the host machine

`-sn`: Service name on the host machine (do not specify `-s` when using `-sn`)

`-u`: Database user

`-d`: Password for the database user

`-t`: Table name for the converted shapefile

`-f`: File name of an input shapefile (with or without extension)

`-r`: Valid Oracle SRID for coordinate system; use 0 if unknown

`-i`: Column name for unique numeric ID, if required

`-n`: Start ID for column specified in -i parameter

`-g`: Preferred SDO_GEOMETRY column name

`-x`: Bounds for the X dimension; use -180,180 if unknown

`-y`: Bounds for the Y dimension; use -90,90 if unknown

`-o`: Load tolerance fields (x and y) in metadata; if not specified, tolerance fields are 0.05

`-k`: Table name that contains Oracle reserved word(s) in a column named KEYWORD

`-a`: Append shapefile data to an existing table

`-c`: Commit interval; by default, commits occur every 1000 conversions and at the end

`-v`: Println interval; by default, a display every 10 conversions

**Parent topic:** Loading ESRI Shapefiles into Spatial and Graph

### C.2 Examples of the Shapefile Converter

The following examples show the use of the shapefile converter to transform a file named `shapes.shp` to a table named `shapes` containing an SDO_GEOMETRY column named `geom`. The SRID for the Longitude/Latitude (WGS 84) coordinate system is used (8307).

#### Linux Example

    > setenv clpath $ORACLE_HOME/jdbc/lib/ojdbc5.jar:$ORACLE_HOME/md/jlib/sdoutl.jar:$ORACLE_HOME/md/jlib/sdoapi.jar
    > java -cp $clpath oracle.spatial.util.SampleShapefileToJGeomFeature -h gis01 -p 1521 -s orcl -u scott -d <password-for-scott> -t shapes -f shapes.shp -r 8307 -g geom

#### Windows Example

    > java -classpath %ORACLE_HOME%\jdbc\lib\ojdbc5.jar;%ORACLE_HOME%\md\jlib\sdoutl.jar;%ORACLE_HOME%\md\jlib\sdoapi.jar oracle.spatial.util.SampleShapefileToJGeomFeature -h gis01 -p 1521 -s orcl -u scott -d <password-for-scott> -t shapes -f shapes.shp -r 8307 -g geom

**Parent topic:** Loading ESRI Shapefiles into Spatial and Graph
