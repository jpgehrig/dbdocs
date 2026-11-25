------------------------------------------------------------------------

#### new ServerJDBCTheme(name)

Constructs a new dynamic sql theme (JDBC theme). For example:


After a ServerJDBCTheme is instantiated, other attributes can then be added. For example:


Such a theme may be added into a server map request instance.
For example:

- var req = new OM.server.ServerMapRequest(baseURL);
- req.addTheme(jdbcTCounties);


Warning: Since ServerJDBCTheme will send a large number of non-reusable SQL queries to the database,
it is recommended to use ServerPredefinedTheme instead.

##### Parameters:

| Name   | Type   | Description                                                                                           |
|--------|--------|-------------------------------------------------------------------------------------------------------|
| `name` | String | The name of the JDBC theme; the theme<br>will be built dynamically using the attrbites in this class. |

### Extends

- [OM.server.ServerTheme](OM.server.ServerTheme.md)

### Methods

------------------------------------------------------------------------

#### addInfoColumn(ic)

Adds an info-column to the theme.

##### Parameters:

| Name | Type   | Description                                                                                                                      |
|------|--------|----------------------------------------------------------------------------------------------------------------------------------|
| `ic` | Object | The JSON object representing a new info column in the<br>format of<br>` {columnName: 'totpop', displayName: 'Population'} `<br>. |

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
When it is set to true, the query string, as an option, may contain the SDO_FILTER with binding parameters in its WHERE clause, similar to the code snippet below:
var sql="SELECT state_abrv, geom FROM states"+
" WHERE MDSYS.SDO_FILTER(geom, MDSYS.SDO_GEOMETRY(2003, 8265, NULL, MDSYS.SDO_ELEM_INFO_ARRAY(1, 1003, 3), MDSYS.SDO_ORDINATE_ARRAY(?, ?, ?, ?)), 'querytype=WINDOW') = 'TRUE'";
myServerJDBCTheme.setQuery(sql);
When the server detects the SDO_FILTER in the WHERE clause, it will replace the four binding parameters with the map's bounding box.

##### Parameters:

| Name   | Type    | Description                             |
|--------|---------|-----------------------------------------|
| `flag` | Boolean | A true or false value. Default is false |

------------------------------------------------------------------------

#### setGeometryColumnName(name)

Sets the geometry column name in the query result set.

##### Parameters:

| Name   | Type   | Description                                                   |
|--------|--------|---------------------------------------------------------------|
| `name` | String | The name of the geometry column name in the query result set. |

------------------------------------------------------------------------

#### setLabelColumnName(name)

Set the label column name

##### Parameters:

| Name   | Type   | Description           |
|--------|--------|-----------------------|
| `name` | String | The lable column name |

##### Returns:

Type
undefined

------------------------------------------------------------------------

#### setLabelStyleName(name)

Set the label style name

##### Parameters:

| Name   | Type   | Description          |
|--------|--------|----------------------|
| `name` | String | The lable style name |

##### Returns:

Type
undefined

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

#### setQuery(sql)

Sets the dynamic SQL to be executed for this theme on the server.

##### Parameters:

| Name  | Type   | Description                                                                                                                                  |
|-------|--------|----------------------------------------------------------------------------------------------------------------------------------------------|
| `sql` | String | The SQL string. Such as:<br>SELECT s.geom.sdo_point.x long_loc,s.geom.sdo_point.y lat_loc,state,fatalities,injuries,loss<br>FROM wind_3857 s |

------------------------------------------------------------------------

#### setRenderingStyleName(name)

Sets the rendering style name.

##### Parameters:

| Name   | Type   | Description               |
|--------|--------|---------------------------|
| `name` | String | The rendering style name. |

------------------------------------------------------------------------

#### setRenderingStyleValueColumns(columns)

Sets the rendering style value columns

##### Parameters:

| Name      | Type   | Description                                                 |
|-----------|--------|-------------------------------------------------------------|
| `columns` | String | The comma separated value columns to be used for rendering. |

------------------------------------------------------------------------

#### setSRID(srid)

Sets the jdbc theme srid

##### Parameters:

| Name   | Type   | Description          |
|--------|--------|----------------------|
| `srid` | String | The jdbc theme srid. |

------------------------------------------------------------------------

#### setXColumnName(name)

Sets the x column name in the query result set.

##### Parameters:

| Name   | Type   | Description                                       |
|--------|--------|---------------------------------------------------|
| `name` | String | The name of the x column in the query result set. |

------------------------------------------------------------------------

#### setYColumnName(name)

Sets the y column name in the query result set.

##### Parameters:

| Name   | Type   | Description                                       |
|--------|--------|---------------------------------------------------|
| `name` | String | The name of the y column in the query result set. |
