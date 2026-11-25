## 25  SDO_GCDR Package (Geocoding)

The MDSYS.SDO_GCDR package contains subprograms for performing geocoding.

To use the subprograms in this chapter, you must understand the conceptual and usage information about geocoding in [Geocoding Address Data](geocoding-address-data-concepts.md).

**Note:**

- SDO_GCDR.ELOC_GEOCODE and SDO_GCDR.ELOC_GEOCODE_AS_GEOM leverage a hosted geocoding service and are available on Oracle Autonomous Database.
- With the exception of SDO_GCDR.ELOC_GEOCODE and SDO_GCDR.ELOC_GEOCODE_AS_GEOM, geocoding functions require the acquisition and loading of supporting reference data. See [Data Structures for Geocoding](geocoding-address-data-concepts.md) for more information.
- The following subprograms support Oracle Spatial routing capabilities and are available on Oracle Autonomous Database:
  - SDO_GCDR.ELOC_DRIVE_TIME_POLYGON
  - SDO_GCDR.ELOC_ISO_POLYGON
  - SDO_GCDR.ELOC_ROUTE
  - SDO_GCDR.ELOC_ROUTE_DISTANCE
  - SDO_GCDR.ELOC_ROUTE_GEOM
  - SDO_GCDR.ELOC_ROUTE_TIME

The rest of this chapter provides reference information on the subprograms, listed in alphabetical order.

- SDO_GCDR.CREATE_PROFILE_TABLES
- SDO_GCDR.ELOC_DRIVE_TIME_POLYGON
- SDO_GCDR.ELOC_GEOCODE
- SDO_GCDR.ELOC_GEOCODE_AS_GEOM
- SDO_GCDR.ELOC_GRANT_ACCESS
- SDO_GCDR.ELOC_ISO_POLYGON
- SDO_GCDR.ELOC_REVOKE_ACCESS
- SDO_GCDR.ELOC_ROUTE
- SDO_GCDR.ELOC_ROUTE_DISTANCE
- SDO_GCDR.ELOC_ROUTE_GEOM
- SDO_GCDR.ELOC_ROUTE_TIME
- SDO_GCDR.GEOCODE
- SDO_GCDR.GEOCODE_ADDR
- SDO_GCDR.GEOCODE_ADDR_ALL
- SDO_GCDR.GEOCODE_ALL
- SDO_GCDR.GEOCODE_AS_GEOMETRY
- SDO_GCDR.REVERSE_GEOCODE

**Parent topic:** [Reference Information](spatial-reference-information.md)

### 25.1 SDO_GCDR.CREATE_PROFILE_TABLES

#### Format

    SDO_GCDR.CREATE_PROFILE_TABLES;

#### Description

Creates the CG_COUNTRY_PROFILE, GC_PARSER_PROFILES, and GC_PARSER_PROFILEAFS tables in the caller's schema.

#### Parameters

None.

#### Usage Notes

Use this procedure only if your geocoding data provider does not supply the GC_PARSER_PROFILES and GC_PARSER_PROFILEAFS tables. See [Installing the Profile Tables](geocoding-address-data-concepts.md) for more information.

#### Examples

The following example creates the GC_PARSER_PROFILES and GC_PARSER_PROFILEAFS tables in the caller's schema.

    EXECUTE SDO_GCDR.CREATE_PROFILE_TABLES;

**Parent topic:** SDO_GCDR Package (Geocoding)

### 25.2 SDO_GCDR.ELOC_DRIVE_TIME_POLYGON

#### Format

    SDO_GCDR.ELOC_DRIVE_TIME_POLYGON(
      route_preference        IN  VARCHAR2,
      start_address           IN  VARCHAR2,
      country                 IN  VARCHAR2,
      cost                    IN  NUMBER,
      cost_unit               IN  VARCHAR2,
      vehicle_type            IN  VARCHAR2,
      print_request_response  IN  VARCHAR2 DEFAULT 'FALSE'
    ) RETURN SDO_GEOMETRY;

or

    SDO_GCDR.ELOC_DRIVE_TIME_POLYGON(
      route_preference        IN  VARCHAR2,
      longitude               IN  NUMBER,
      latitude                IN  NUMBER,
      cost                    IN  NUMBER,
      cost_unit               IN  VARCHAR2,
      vehicle_type            IN  VARCHAR2,
      print_request_response  IN  VARCHAR2 DEFAULT 'FALSE'
    ) RETURN SDO_GEOMETRY;

#### Description

Computes the drive time polygon around an input location for the specified cost, and returns the geometry of the polygon in `SDO_GEOMETRY` format.

The input location can either be a single-line address or be specified as longitude and latitude.

#### Parameters

route_preference
Routing preference.

Supported values are: `shortest`, `fastest`, and `traffic`.

start_address
Complete start address (not formatted into separate fields).

country
ISO 2-character country code. See Country codes in [ISO Online Browsing Platform (OBP)](https://www.iso.org/obp/ui) to view the list of supported codes.

longitude
Longitude value of the starting point.

latitude
Latitude value of the starting point.

cost
Drive time or drive distance to use for the area of reachability from the starting point.

The output polygon is the area reachable from the start point within the specified cost. If the `route_preference` parameter is set to shortest, then the cost is a distance. If the `route_preference` parameter is set to fastest, then the cost is time.

cost_unit
Unit for cost.

Supported values are: `mile`, `kilometer`, `km`, `meter`, `hour`, `minute`, and `second`.

vehicle_type
Type of vehicle considered for computing the distance.

Supported values are: `auto` and `truck`

print_request_response
Determines if the request sent and response received are to be printed.

By default, the parameter value is `'FALSE'`.

#### Usage Notes

**Note:**

The `SDO_GCDR.ELOC_DRIVE_TIME_POLYGON` function is only supported on Oracle Autonomous Database.

In order to use this function on your Autonomous Database instance, ensure that you have been granted the required permission. See SDO_GCDR.ELOC_GRANT_ACCESS for more information.

The `SDO_GCDR.ELOC_DRIVE_TIME_POLYGON` function can accept one of the following sets of input parameters to compute the drive time polygon (as a geometry) around the specified location:

- Using an unformatted address: Provide the `start_address` parameter where the complete address is stored in a single field (that is, unformatted).
- Using geographic coordinates: Provide the `longitude` and `latitude` parameters to determine the location.

Also, note that each parameter input can be a column from a table or view, or an explicit string or number value.

#### Example

The following example computes the fastest drive time polygon around an address for a truck:

    SELECT SDO_GCDR.ELOC_DRIVE_TIME_POLYGON('fastest', '1 Oracle Dr, Nashua, NH', 'US', 1, 'minute', 'truck') polygon FROM DUAL;

    POLYGON(SDO_GTYPE, SDO_SRID, SDO_POINT(X, Y, Z), SDO_ELEM_INFO, SDO_ORDINATES)
    ------------------------------------------------------------------------------------------
    SDO_GEOMETRY(2003, 4326, NULL, SDO_ELEM_INFO_ARRAY(1, 1003, 1), SDO_ORDINATE_ARRAY(-71.46924,
     42.76051, -71.46928, 42.76, -71.46919, 42.75975, -71.46911, 42.75962, -71.46899, 42.7594,
     -71.46974, 42.75638, -71.47012, 42.75626, -71.47038, 42.75617, -71.46688, 42.7552, -71.46602,
     42.75482, -71.46409, 42.75397, -71.46244, 42.75343, -71.4618, 42.75311, -71.46102, 42.7542,
     -71.46054, 42.75496, -71.45947, 42.75647, -71.45924, 42.75761, -71.45815, 42.75858, -71.45741,
     42.75912, -71.45813, 42.75955, -71.45959, 42.76009, -71.46187, 42.76099, -71.46227, 42.76177,
     -71.46266, 42.76243, -71.46354, 42.76268,-71.46447, 42.76344, -71.46639, 42.76425, -71.4668,
     42.76412, -71.46668, 42.76387, -71.46683, 42.7625, -71.46732, 42.76183, -71.46924, 42.76051))

**Parent topic:** SDO_GCDR Package (Geocoding)

### 25.3 SDO_GCDR.ELOC_GEOCODE

#### Format

    SDO_GCDR.ELOC_GEOCODE(
         street      IN VARCHAR2,
         city        IN VARCHAR2,
         region      IN VARCHAR2,
         postal_code IN VARCHAR2,
         cc2         IN VARCHAR2,
         match_mode  IN VARCHAR2 default 'DEFAULT'
    ) RETURN VARCHAR2;

or

    SDO_GCDR.ELOC_GEOCODE(
         address IN VARCHAR2
    ) RETURN VARCHAR2;

or

    SDO_GCDR.ELOC_GEOCODE(
         longitude IN NUMBER,
         latitude  IN NUMBER
    ) RETURN VARCHAR2;

#### Description

Geocodes a formatted (address parts in separate fields) or an unformatted (complete address in a single string field) address and returns the standardized address with geographic coordinates and geocoding metadata in JSON format.

For longitude and latitude input, the function reverse geocodes the location and returns the address in JSON format.

#### Parameters

street
Name of the street.

city
Name of the city.

region
Name of the region.

postal_code
Postal code.

cc2
ISO 2-character country code. See Country codes in [ISO Online Browsing Platform (OBP)](https://www.iso.org/obp/ui) to view the list of supported codes.

match_mode
Match mode for the geocoding operation. Match modes are explained in [Match Modes](geocoding-address-data-concepts.md).

address
Complete address (not formatted into separate fields).

longitude
Longitude value for reverse geocoding operation.

latitude
Latitude value for reverse geocoding operation.

#### Usage Notes

**Note:**

The `SDO_GCDR.ELOC_GEOCODE` function is only supported on Oracle Autonomous Database.

In order to use this function on your Autonomous Database instance, ensure that you have been granted the required permission. See SDO_GCDR.ELOC_GRANT_ACCESS for more information.

This function performs the following operations depending on the input parameters. Note that each parameter input can be a column from a table or view, or an explicit string or number value.

- Geocoding a formatted address: Provide the address fields corresponding to the parameters of the function (such as `street`, `city`, `region`, `postal_code`, and `cc2`).

  Note that the function uses `'DEFAULT'` as the default match mode for the geocoding operation. See [Match Modes](geocoding-address-data-concepts.md) for more details.

  Refer to Example-1.

- Geocoding an unformatted address: If the complete address is stored in a single field (that is, unformatted), then provide the `address` field corresponding to the complete address.

  Refer to Example-2.

- Reverse geocoding a location: You must provide the longitude and latitude coordinates and the function returns the address in JSON format.

  Refer to Example-3.

#### Examples

Example-1

The following example geocodes a formatted address using the default match mode. It returns the longitude and latitude coordinates of this address as -71.07355166666666 and 42.355174166666664, respectively.

    SELECT SDO_GCDR.ELOC_GEOCODE('123 Beacon St', 'Boston', 'MA', '02116' , 'US') FROM DUAL;

    [{"id":"0","matchCount":"1","matches":[{"sequence":"0","x":-71.07355166666666,"y":42.355174166666664,
      "houseNumber":"123","street":"Beacon St","settlement":"Boston","municipality":"Suffolk","region":"MA",
      "postalCode":"02116","country":"US","language":"ENG","name":"","edgeId":946710796,
      "percent":0.08333333333333333,"side":"R","matchCode":1,"matchVector":"???10101010??000?"}]}]

Example-2

The following example geocodes an unformatted address. It returns the longitude and latitude coordinates of this address as -71.07355166666666 and 42.355174166666664, respectively.

    SELECT SDO_GCDR.ELOC_GEOCODE('123 Beacon St, Boston MA, 02116, US') FROM DUAL;

    [{"id":"0","matchCount":"1","matches":[{"sequence":"0","x":-71.07355166666666,"y":42.355174166666664,
      "houseNumber":"123","street":"Beacon St","settlement":"Boston","municipality":"Suffolk","region":"MA",
      "postalCode":"02116","country":"US","language":"ENG","name":"","edgeId":946710796,
      "percent":0.08333333333333333,"side":"R","matchCode":1,"matchVector":"???10101010??000?"}]}]

Example-3

The following example reverse geocodes a geographic location. It returns the address for the longitude (`-71.073551`) and latitude (`42.355174`) coordinates.

    SELECT SDO_GCDR.ELOC_GEOCODE(-71.073551, 42.355174) FROM DUAL;

    [{"id":"0","matchCount":"1","matches":[{"sequence":"0","x":-71.07355109772594,"y":42.35517433341787,
      "houseNumber":"123","street":"Beacon St","settlement":"Boston","municipality":"Suffolk","region":"MA",
      "postalCode":"02116","country":"US","language":"ENG","name":"","edgeId":946710796,
      "percent":0.08431426223078922,"side":"R","matchCode":1,"matchVector":"???14141414??404?"}]}]

**Parent topic:** SDO_GCDR Package (Geocoding)

### 25.4 SDO_GCDR.ELOC_GEOCODE_AS_GEOM

#### Format

    SDO_GCDR.ELOC_GEOCODE_AS_GEOM(
         street      IN VARCHAR2,
         city        IN VARCHAR2,
         region      IN VARCHAR2,
         postal_code IN VARCHAR2,
         cc2         IN VARCHAR2,
         match_mode  IN VARCHAR2 default 'DEFAULT'
    ) RETURN SDO_GEOMETRY;

or

    SDO_GCDR.ELOC_GEOCODE_AS_GEOM(
         address IN VARCHAR2
    ) RETURN SDO_GEOMETRY;

#### Description

Geocodes a formatted (address parts in separate fields) or an unformatted (complete address in a single string field) address and returns the standardized address with geographic coordinates and geocoding metadata as an SDO_GEOMETRY object.

#### Parameters

street
Name of the street.

city
Name of the city.

region
Name of the region.

postal_code
Postal code.

cc2
ISO 2-character country code. See Country codes in [ISO Online Browsing Platform (OBP)](https://www.iso.org/obp/ui) to view the list of supported codes.

match_mode
Match mode for the geocoding operation. Match modes are explained in [Match Modes](geocoding-address-data-concepts.md).

address
Complete address (not formatted into separate fields).

#### Usage Notes

**Note:**

The `SDO_GCDR.ELOC_GEOCODE_AS_GEOM` function is only supported on Oracle Autonomous Database.

In order to use this function on your Autonomous Database instance, ensure that you have been granted the required permission. See SDO_GCDR.ELOC_GRANT_ACCESS for more information.

This function performs the following operations depending on the input parameters. Note that each parameter input can be a column from a table or view, or an explicit string or number value.

- Geocoding a formatted address: Provide the address fields corresponding to the parameters of the function (such as `street`, `city`, `region`, `postal_code`, and `cc2`).

  Note that the function uses `'DEFAULT'` as the default match mode for the geocoding operation. See [Match Modes](geocoding-address-data-concepts.md) for more details.

- Geocoding an unformatted address: If the complete address is stored in a single field (that is, unformatted), then provide the `address` field corresponding to the complete address.

#### Examples

The following example geocodes a formatted address using the default match mode and returns the output as an `SDO_GEOMETRY` object.

    SELECT SDO_GCDR.ELOC_GEOCODE_AS_GEOM('123 Beacon St', 'Boston', 'MA', '02116' , 'US') FROM DUAL;

    MDSYS.SDO_GEOMETRY(2001, 4326,
            MDSYS.SDO_POINT_TYPE(-71.07355166666666, 42.355174166666664, NULL), NULL, NULL)

Note that if you are using the SQL Worksheet in Database Actions on your Autonomous Database instance, any object type (including `SDO_GEOMETRY`) is displayed as `[object Object]`. To display the result in the SQL Worksheet you can convert the result to a GeoJSON string by applying the `Get_GeoJSON( )` method as follows:

    SELECT (SDO_GCDR.ELOC_GEOCODE_AS_GEOM('123 Beacon St', 'Boston', 'MA', '02116' , 'US')).GET_GEOJSON() FROM DUAL;

    { "type": "Point", "coordinates": [-71.07355166666666, 42.355174166666664] }

**Parent topic:** SDO_GCDR Package (Geocoding)

### 25.5 SDO_GCDR.ELOC_GRANT_ACCESS

#### Format

    SDO_GCDR.ELOC_GRANT_ACCESS(
         user_name IN VARCHAR2);

#### Description

Grants privileges for a user to call the Oracle Maps Geocoder on an Autonomous Database instance.

#### Parameters

user_name
Name of the user who requires access to the Oracle Maps cloud service.

#### Usage Notes

**Note:**

The `SDO_GCDR.ELOC_GRANT_ACCESS` function is only supported on Oracle Autonomous Database.

You must invoke the `SDO_GCDR.ELOC_GRANT_ACCESS` function as the ADMIN user in your Autonomous Database instance.

#### Examples

The following example grants the user `SCOTT` access to use the geocoder functionality on an Autonomous Database instance.

    EXEC SDO_GCDR.ELOC_GRANT_ACCESS('SCOTT');

    PL/SQL procedure successfully completed.

**Parent topic:** SDO_GCDR Package (Geocoding)

### 25.6 SDO_GCDR.ELOC_ISO_POLYGON

#### Format

    SDO_GCDR.ELOC_ISO_POLYGON(
      iso                     IN  VARCHAR2,
      start_address           IN  VARCHAR2,
      country                 IN  VARCHAR2,
      cost                    IN  NUMBER,
      cost_unit               IN  VARCHAR2,
      vehicle_type            IN  VARCHAR2,
      print_request_response  IN  VARCHAR2 DEFAULT 'FALSE'
    ) RETURN CLOB;

or

    SDO_GCDR.ELOC_ISO_POLYGON(
      iso                     IN  VARCHAR2,
      longitude               IN  NUMBER,
      latitude                IN  NUMBER,
      cost                    IN  NUMBER,
      cost_unit               IN  VARCHAR2,
      vehicle_type            IN  VARCHAR2,
      print_request_response  IN  VARCHAR2 DEFAULT 'FALSE'
    ) RETURN CLOB;

#### Description

Computes the drive time polygon around an input location for the specified cost, and returns a JSON CLOB object that includes the cost, cost unit, and geometry of the polygon in GeoJSON format.

The input location can either be a single-line address or be specified as longitude and latitude.

#### Parameters

iso
Determines if it is a time-based or distance-based polygon.

Supported values are:

- `distance`: This applies for a distance-based polygon.
- `time`: This applies for a time-based polygon.

start_address
Complete start address (not formatted into separate fields).

country
ISO 2-character country code. See Country codes in [ISO Online Browsing Platform (OBP)](https://www.iso.org/obp/ui) to view the list of supported codes.

longitude
Longitude value of the starting point.

latitude
Latitude value of the starting point.

cost
Distance or time bounds of the polygon.

cost_unit
Unit for cost.

Supported values are: `mile`, `kilometer`, `km`, `meter`, `hour`, `minute`, and `second`.

vehicle_type
Type of vehicle considered for computing the distance.

Supported values are: `auto` and `truck`

print_request_response
Determines if the request sent and response received are to be printed.

By default, the parameter value is `'FALSE'`.

#### Usage Notes

**Note:**

The `SDO_GCDR.ELOC_ISO_POLYGON` function is only supported on Oracle Autonomous Database.

In order to use this function on your Autonomous Database instance, ensure that you have been granted the required permission. See SDO_GCDR.ELOC_GRANT_ACCESS for more information.

The `SDO_GCDR.ELOC_ISO_POLYGON` function can accept one of the following sets of input parameters to compute the drive time polygon (as a JSON object) around a location:

- Using an unformatted address: Provide the `start_address` parameter where the complete address is stored in a single field (that is, unformatted).
- Using geographic coordinates: Provide the `longitude` and `latitude` parameters to determine the location.

Also, note that each parameter input can be a column from a table or view, or an explicit string or number value.

The following describes the schema for the JSON output:

    {
      "type": "object",
      "properties": {
        "routeResponse": {
          "type": "object",
          "properties": {
            "driveTimePolygon": {
              "type": "object",
              "properties": {
                "id": {
                  "type": "string"
                },
                "cost": {
                  "type": "string"
                },
                "unit": {
                  "type": "string"
                },
                "geometry": {
                  "type": "object",
                  "properties": {
                    "type": {
                      "type": "string"
                    },
                    "coordinates": {
                      "type": "array",
                      "items": {
                        "type": "array",
                        "items": {
                          "type": "array",
                          "items": {
                            "type": "number"
                          }
                        }
                      }
                    }
                  },
                  "required": [..]
                }
              },
              "required": [..]
            }
          },
          "required": [..]
        }
      },
      "required": [..]
    }

#### Example

The following example computes the drive time polygon around an address for an auto. Note that the output values for cost, unit, and polygon geometry are extracted from the resulting JSON object using the `JSON_VALUE` and `JSON_QUERY` functions:

    WITH x AS
    (SELECT SDO_GCDR.ELOC_ISO_POLYGON('time', '1 Oracle Drive, Nashua, NH', 'US', 1, 'minute', 'auto') AS t FROM DUAL)
     SELECT json_value(t, '$.routeResponse.driveTimePolygon.cost') AS cost,
            json_value(t, '$.routeResponse.driveTimePolygon.unit') AS unit,
            json_query(t, '$.routeResponse.driveTimePolygon.geometry' RETURNING clob) AS geom
    FROM x;

    1
    minute
    {"type":"Polygon","coordinates":[[[-71.46924,42.76051],[-71.46928,42.76],[-71.46919,42.75975],[-71.46911,42.75962],
                                      [-71.46899,42.7594],[-71.46974,42.75638],[-71.47012,42.75626],[-71.47038,42.75617],
                                      [-71.46688,42.7552],[-71.46602,42.75482],[-71.46409,42.75397],[-71.46244,42.75343],
                                      [-71.4618,42.75311],[-71.46102,42.7542],[-71.46054,42.75496],[-71.45947,42.75647],
                                      [-71.45924,42.75761],[-71.45815,42.75858],[-71.45741,42.75912],[-71.45813,42.75955],
                                      [-71.45959,42.76009],[-71.46187,42.76099],[-71.46227,42.76177],[-71.46266,42.76243],
                                      [-71.46354,42.76268],[-71.46447,42.76344],[-71.46639,42.76425],[-71.4668,42.76412],
                                      [-71.46668,42.76387],[-71.46683,42.7625],[-71.46732,42.76183],[-71.46924,42.76051]]]}

**Parent topic:** SDO_GCDR Package (Geocoding)

### 25.7 SDO_GCDR.ELOC_REVOKE_ACCESS

#### Format

    SDO_GCDR.ELOC_REVOKE_ACCESS(
         user_name IN VARCHAR2);

#### Description

Revokes privileges for a user to call the Oracle Maps Geocoder on an Autonomous Database instance.

#### Parameters

user_name
Name of the user whose access to the Oracle Maps cloud service is to be revoked.

#### Usage Notes

**Note:**

The `SDO_GCDR.ELOC_REVOKE_ACCESS` function is only supported on Oracle Autonomous Database.

You must invoke the `SDO_GCDR.ELOC_REVOKE_ACCESS` function as the ADMIN user in your Autonomous Database instance.

#### Examples

The following example revokes the privileges for the user `SCOTT` to use the geocoder functionality on an Autonomous Database instance.

    EXEC SDO_GCDR.ELOC_REVOKE_ACCESS('SCOTT');

    PL/SQL procedure successfully completed.

**Parent topic:** SDO_GCDR Package (Geocoding)

### 25.8 SDO_GCDR.ELOC_ROUTE

#### Format

    SDO_GCDR.ELOC_ROUTE(
      route_preference        IN  VARCHAR2,
      distance_unit           IN  VARCHAR2,
      time_unit               IN  VARCHAR2,
      start_address           IN  VARCHAR2,
      end_address             IN  VARCHAR2,
      country                 IN  VARCHAR2,
      vehicle_type            IN  VARCHAR2,
      print_request_response  IN  VARCHAR2 DEFAULT 'FALSE'
    ) RETURN CLOB;

or

    SDO_GCDR.ELOC_ROUTE(
      route_preference        IN  VARCHAR2,
      distance_unit           IN  VARCHAR2,
      time_unit               IN  VARCHAR2,
      start_longitude         IN  NUMBER,
      start_latitude          IN  NUMBER,
      end_longitude           IN  NUMBER,
      end_latitude            IN  NUMBER,
      vehicle_type            IN  VARCHAR2,
      print_request_response  IN  VARCHAR2 DEFAULT 'FALSE'
    ) RETURN CLOB;

#### Description

Computes the route between two locations and returns a JSON CLOB object that includes the route distance, route time, and geometry of the route in GeoJSON format.

The input locations can either be single-line addresses or be specified by geographic coordinates.

#### Parameters

route_preference
Routing preference.

Supported values are: `shortest`, `fastest`, and `traffic`.

distance_unit
Unit of distance.

Supported values are: `mile`, `kilometer`, `km`, and `meter`.

time_unit
Unit of time.

Supported values are: `hour`, `minute`, and `second`.

start_address
Complete start address (not formatted into separate fields).

end_address
Complete end address (not formatted into separate fields).

country
ISO 2-character country code. See Country codes in [ISO Online Browsing Platform (OBP)](https://www.iso.org/obp/ui) to view the list of supported codes.

start_longitude
Longitude value of the starting point.

start_latitude
Latitude value of the starting point.

end_longitude
Longitude value of the ending point.

end_latitude
Latitude value of the ending point.

vehicle_type
Type of vehicle considered for computing the distance.

Supported values are: `auto` and `truck`

print_request_response
Determines if the request sent and response received are to be printed.

By default, the parameter value is `'FALSE'`.

#### Usage Notes

**Note:**

The `SDO_GCDR.ELOC_ROUTE` function is only supported on Oracle Autonomous Database.

In order to use this function on your Autonomous Database instance, ensure that you have been granted the required permission. See SDO_GCDR.ELOC_GRANT_ACCESS for more information.

The `SDO_GCDR.ELOC_ROUTE` function can accept one of the following sets of parameters to determine the route between two points:

- Using unformatted addresses: Provide the `start_address` and `end_address` parameters where the complete address is stored in a single field (that is, unformatted).
- Using geographic coordinates: Provide the `start_longitude`, `start_latitude`, `end_longitude`, and `end_latitude` parameters to determine the start and end locations.

Note that each parameter input can be a column from a table or view, or an explicit string or number value.

The following describes the schema for the output JSON object:

    {
     "type": "object",
      "properties": {
        "routeResponse": {
          "type": "object",
          "properties": {
            "route": {
              "type": "object",
              "properties": {
                "id": {
                  "type": "string"
                },
                "distance": {
                  "type": "string"
                },
                "distanceUnit": {
                  "type": "string"
                },
                "time": {
                  "type": "string"
                },
                "timeUnit": {
                  "type": "string"
                },
                "geometry": {
                  "type": "object",
                  "properties": {
                    "type": {
                      "type": "string"
                    },

                    "coordinates": {
                      "type": "array",
                      "items": {
                        "type": "array",
                        "items": {
                          "type": "number"
                        }
                      }
                    }
                  },
                  "required": [. .]
                }
              },
              "required": [..]
            }
          },
          "required": [..]
        }
      },

      "required": [..]
    }

#### Example

The following example calls the `SDO_GCDR.ELOC_ROUTE` function to compute the fastest route taken by an auto between two geographic coordinates. Note that the output values for route distance, travel time, and route geometry are extracted from the resulting JSON object using the `JSON_VALUE` and `JSON_QUERY` functions:

    WITH x AS
    (SELECT SDO_GCDR.ELOC_ROUTE('fastest', 'km', 'minute', -71.46439, 42.75875,-71.46278, 42.7553, 'auto') AS t FROM DUAL)
    SELECT json_value(t, '$.routeResponse.route.time') AS TIME,
           json_value(t, '$.routeResponse.route.distance') AS DIST,
           json_query(t, '$.routeResponse.route.geometry' RETURNING CLOB
                      ) AS GEOM
    FROM x;

    TIME DIST GEOM
    ---- ---- ---------------------------------------------------------------------------------------------------
    0.7  0.41 {"type":"LineString","coordinates":[[-71.4643900005,42.7587499999],[-71.46439,42.75875],
                                                  [-71.46433,42.75862],[-71.46431,42.75858],[-71.46421,42.75837],
                                                  [-71.4641,42.75813],[-71.46397,42.75785],[-71.46375,42.75739],
                                                  [-71.4637,42.75728],[-71.46368,42.75724],[-71.46359,42.75706],
                                                  [-71.46351,42.75689],[-71.46333,42.75656],[-71.46326,42.75639],
                                                  [-71.46312,42.75605],[-71.46296,42.75568],[-71.46278,42.7553]]}

**Parent topic:** SDO_GCDR Package (Geocoding)

### 25.9 SDO_GCDR.ELOC_ROUTE_DISTANCE

#### Format

    SDO_GCDR.ELOC_ROUTE_DISTANCE(
      route_preference        IN  VARCHAR2,
      distance_unit           IN  VARCHAR2,
      start_address           IN  VARCHAR2,
      end_address             IN  VARCHAR2,
      country                 IN  VARCHAR2,
      vehicle_type            IN  VARCHAR2,
      print_request_response  IN  VARCHAR2 DEFAULT 'FALSE'
    ) RETURN NUMBER;

or

    SDO_GCDR.ELOC_ROUTE_DISTANCE(
      route_preference        IN  VARCHAR2,
      distance_unit           IN  VARCHAR2,
      start_longitude         IN  NUMBER,
      start_latitude          IN  NUMBER,
      end_longitude           IN  NUMBER,
      end_latitude            IN  NUMBER,
      vehicle_type            IN  VARCHAR2,
      print_request_response  IN  VARCHAR2 DEFAULT 'FALSE'
    ) RETURN NUMBER;

#### Description

Computes the route distance between two locations.

The input locations can either be single-line addresses or be specified by geographic coordinates.

#### Parameters

route_preference
Routing preference.

Supported values are: `shortest`, `fastest`, and `traffic`.

distance_unit
Unit of distance.

Supported values are: `mile`, `kilometer`, `km`, and `meter`.

start_address
Complete start address (not formatted into separate fields).

end_address
Complete end address (not formatted into separate fields).

country
ISO 2-character country code. See Country codes in [ISO Online Browsing Platform (OBP)](https://www.iso.org/obp/ui) to view the list of supported codes.

start_longitude
Longitude value of the starting point.

start_latitude
Latitude value of the starting point.

end_longitude
Longitude value of the ending point.

end_latitude
Latitude value of the ending point.

vehicle_type
Type of vehicle considered for computing the distance.

Supported values are: `auto` and `truck`

print_request_response
Determines if the request sent and response received are to be printed.

By default, the parameter value is `'FALSE'`.

#### Usage Notes

**Note:**

The `SDO_GCDR.ELOC_ROUTE_DISTANCE` function is only supported on Oracle Autonomous Database.

In order to use this function on your Autonomous Database instance, ensure that you have been granted the required permission. See SDO_GCDR.ELOC_GRANT_ACCESS for more information.

The `SDO_GCDR.ELOC_ROUTE_DISTANCE` function can accept one of the following sets of parameters to compute the distance between two points:

- Using unformatted addresses: Provide the `start_address` and `end_address` parameters where the complete address is stored in a single field (that is, unformatted).
- Using geographic coordinates: Provide the `start_longitude`, `start_latitude`, `end_longitude`, and `end_latitude` parameters to determine the start and end locations.

Note that each parameter input can be a column from a table or view, or an explicit string or number value.

#### Examples

The following example computes the shortest route distance (in miles) for a truck between two address locations.

    SELECT SDO_GCDR.ELOC_ROUTE_DISTANCE('shortest', 'mile', '1 Oracle Dr, Nashua, NH', '77 Massachusetts Ave, Cambridge, MA', 'US', 'truck') route_dist FROM DUAL;

    ROUTE_DIST
    ----------
         33.22

The following example uses longitude and latitude coordinates to compute the fastest route distance (in miles) for an auto between two points.

    SELECT SDO_GCDR.ELOC_ROUTE_DISTANCE('fastest', 'mile', -122.39436, 37.79579, -122.40459, 37.74211,'auto') route_dist FROM DUAL;

    ROUTE_DIST
    ----------
          4.51

**Parent topic:** SDO_GCDR Package (Geocoding)

### 25.10 SDO_GCDR.ELOC_ROUTE_GEOM

#### Format

    SDO_GCDR.ELOC_ROUTE_GEOM(
      route_preference        IN  VARCHAR2,
      start_address           IN  VARCHAR2,
      end_address             IN  VARCHAR2,
      country                 IN  VARCHAR2,
      vehicle_type            IN  VARCHAR2,
      print_request_response  IN  VARCHAR2 DEFAULT 'FALSE'
    ) RETURN SDO_GEOMETRY;

or

    SDO_GCDR.ELOC_ROUTE_GEOM(
      route_preference        IN  VARCHAR2,
      start_longitude         IN  NUMBER,
      start_latitude          IN  NUMBER,
      end_longitude           IN  NUMBER,
      end_latitude            IN  NUMBER,
      vehicle_type            IN  VARCHAR2,
      print_request_response  IN  VARCHAR2 DEFAULT 'FALSE'
    ) RETURN SDO_GEOMETRY;

#### Description

Computes the route between two locations and returns the geometry of the route in `SDO_GEOMETRY` format.

The input locations can either be single-line addresses or be specified by geographic coordinates.

#### Parameters

route_preference
Routing preference.

Supported values are: `shortest`, `fastest`, and `traffic`.

start_address
Complete start address (not formatted into separate fields).

end_address
Complete end address (not formatted into separate fields).

country
ISO 2-character country code. See Country codes in [ISO Online Browsing Platform (OBP)](https://www.iso.org/obp/ui) to view the list of supported codes.

start_longitude
Longitude value of the starting point.

start_latitude
Latitude value of the starting point.

end_longitude
Longitude value of the ending point.

end_latitude
Latitude value of the ending point.

vehicle_type
Type of vehicle considered for computing the distance.

Supported values are: `auto` and `truck`

print_request_response
Determines if the request sent and response received are to be printed.

By default, the parameter value is `'FALSE'`.

#### Usage Notes

**Note:**

The `SDO_GCDR.ELOC_ROUTE_GEOM` function is only supported on Oracle Autonomous Database.

In order to use this function on your Autonomous Database instance, ensure that you have been granted the required permission. See SDO_GCDR.ELOC_GRANT_ACCESS for more information.

The `SDO_GCDR.ELOC_ROUTE_GEOM` function can accept one of the following sets of parameters to determine the route geometry between two points:

- Using unformatted addresses: Provide the `start_address` and `end_address` parameters where the complete address is stored in a single field (that is, unformatted).
- Using geographic coordinates: Provide the `start_longitude`, `start_latitude`, `end_longitude`, and `end_latitude` parameters to determine the start and end locations.

Note that each parameter input can be a column from a table or view, or an explicit string or number value.

#### Example

The following example computes the shortest route geometry taken by a truck between two geographic coordinates.

    SELECT SDO_GCDR.ELOC_ROUTE_GEOM('shortest', -71.46439, 42.75875,-71.46278, 42.7553, 'truck') route_geom FROM DUAL;

    ROUTE_GEOM
    –-------------------------------------------------------------------------------------------------------------------------------
    MDSYS.SDO_GEOMETRY(2002, 4326, NULL, MDSYS.SDO_ELEM_INFO_ARRAY(1, 2, 1), MDSYS.SDO_ORDINATE_ARRAY(-71.4643900005, 42.7587499999,
        -71.46439, 42.75875, -71.46433, 42.75862, -71.46431, 42.75858, -71.46421, 42.75837, -71.4641, 42.75813, -71.46397, 42.75785,
        -71.46375, 42.75739, -71.4637, 42.75728, -71.46368, 42.75724, -71.46359, 42.75706, -71.46351, 42.75689, -71.46333, 42.75656,
        -71.46326, 42.75639, -71.46312, 42.75605, -71.46296, 42.75568, -71.46278, 42.7553, -71.46278, 42.7553))

**Parent topic:** SDO_GCDR Package (Geocoding)

### 25.11 SDO_GCDR.ELOC_ROUTE_TIME

#### Format

    SDO_GCDR.ELOC_ROUTE_TIME(
      route_preference        IN  VARCHAR2,
      time_unit               IN  VARCHAR2,
      start_address           IN  VARCHAR2,
      end_address             IN  VARCHAR2,
      country                 IN  VARCHAR2,
      vehicle_type            IN  VARCHAR2,
      print_request_response  IN  VARCHAR2 DEFAULT 'FALSE'
    ) RETURN NUMBER;

or

    SDO_GCDR.ELOC_ROUTE_TIME(
      route_preference        IN  VARCHAR2,
      time_unit               IN  VARCHAR2,
      start_longitude         IN  NUMBER,
      start_latitude          IN  NUMBER,
      end_longitude           IN  NUMBER,
      end_latitude            IN  NUMBER,
      vehicle_type            IN  VARCHAR2,
      print_request_response  IN  VARCHAR2 DEFAULT 'FALSE'
    ) RETURN NUMBER;

#### Description

Computes the travel time between two locations.

The input locations can either be single-line addresses or be specified by geographic coordinates.

#### Parameters

route_preference
Routing preference.

Supported values are: `shortest`, `fastest`, and `traffic`.

time_unit
Unit of time.

Supported values are: `hour`, `minute`, and `second`.

start_address
Complete start address (not formatted into separate fields).

end_address
Complete end address (not formatted into separate fields).

country
ISO 2-character country code. See Country codes in [ISO Online Browsing Platform (OBP)](https://www.iso.org/obp/ui) to view the list of supported codes.

start_longitude
Longitude value of the starting point.

start_latitude
Latitude value of the starting point.

end_longitude
Longitude value of the ending point.

end_latitude
Latitude value of the ending point.

vehicle_type
Type of vehicle considered for computing the distance.

Supported values are: `auto` and `truck`

print_request_response
Determines if the request sent and response received are to be printed.

By default, the parameter value is `'FALSE'`.

#### Usage Notes

**Note:**

The `SDO_GCDR.ELOC_ROUTE_TIME` function is only supported on Oracle Autonomous Database.

In order to use this function on your Autonomous Database instance, ensure that you have been granted the required permission. See SDO_GCDR.ELOC_GRANT_ACCESS for more information.

The `SDO_GCDR.ELOC_ROUTE_TIME` function can accept one of the following sets of parameters to compute the travel time between two points:

- Using unformatted addresses: Provide the `start_address` and `end_address` parameters where the complete address is stored in a single field (that is, unformatted).
- Using geographic coordinates: Provide the `start_longitude`, `start_latitude`, `end_longitude`, and `end_latitude` parameters to determine the start and end locations.

Note that each parameter input can be a column from a table or view, or an explicit string or number value.

#### Examples

The following example computes the travel time (in minutes) for a fastest route taken by an auto between two locations determined by the geographic coordinates.

    SELECT SDO_GCDR.ELOC_ROUTE_TIME('fastest', 'minute', -122.39436, 37.79579, -122.40459, 37.74211, 'auto') route_time FROM DUAL;

    ROUTE_TIME
    ----------
          8.02

The following example computes the travel time (in minutes) for a fastest route taken by a truck between two address locations. Also, note that the query produces the request and response output as the `print_request_response` parameter is set to `TRUE`.

    SELECT SDO_GCDR.ELOC_ROUTE_TIME('fastest', 'minute', '1 Oracle Dr, Nashua, NH', '45 Middlesex road, Tyngborough, MA', 'US', 'truck', 'TRUE') route_time FROM DUAL;

    ROUTE_TIME
    ----------
         11.24

    1 row selected.

    REQUEST: xml_request=<route_request id="1" route_preference="fastest"
    time_unit="minute" vehicle_type="truck"> <start_location> <input_location
    id="1"> <input_address><unformatted country="US" > <address_line value="1 Oracle
    Dr, Nashua, NH"/> </unformatted></input_address>
    </input_location></start_location> <end_location> <input_location id="2">
    <input_address><unformatted country="US" > <address_line value="45 Middlesex
    road, Tyngborough, MA"/> </unformatted></input_address>
    </input_location></end_location> </route_request>

    RESPONSE: {
      "type" : "Feature",
      "geometry" :
    {"type":"Polygon","coordinates":[]},
      "properties" : {
        "requestType" :
    "route",
        "featureType" : "route",
        "stepCount" : "0",
        "dist" :
    "6.3",
        "distUnit" : "mile",
        "time" : "11.24",
        "timeUnit" : "minute"

    }
    }

**Parent topic:** SDO_GCDR Package (Geocoding)

### 25.12 SDO_GCDR.GEOCODE

#### Format

    SDO_GCDR.GEOCODE(
         username   IN VARCHAR2,
         addr_lines IN SDO_KEYWORDARRAY,
         country    IN VARCHAR2,
         match_mode IN VARCHAR2
         ) RETURN SDO_GEO_ADDR;

#### Description

Geocodes an unformatted address and returns the result as an SDO_GEO_ADDR object.

#### Parameters

username
Name of the user that owns the tables containing the geocoding data.

addr_lines
An array of quoted strings representing the unformatted address to be geocoded. The SDO_KEYWORDARRAY type is described in [SDO_KEYWORDARRAY Type](geocoding-address-data-concepts.md).

country
Country name or ISO country code.

match_mode
Match mode for the geocoding operation. Match modes are explained in [Match Modes](geocoding-address-data-concepts.md).

#### Usage Notes

This function returns an object of type SDO_GEOR_ADDR, which is described in [SDO_GEO_ADDR Type](geocoding-address-data-concepts.md). It performs the same operation as the SDO_GCDR.GEOCODE_AS_GEOMETRY function; however, that function returns an SDO_GEOMETRY object.

#### Examples

The following example geocodes the address of City Hall in San Francisco, California, using the `RELAX_BASE_NAME` match mode. It returns the longitude and latitude coordinates of this address as -122.41815 and 37.7784183, respectively.

    SELECT SDO_GCDR.GEOCODE('SCOTT', SDO_KEYWORDARRAY('1 Carlton B Goodlett Pl',
       'San Francisco, CA  94102'), 'US', 'RELAX_BASE_NAME') FROM DUAL;

    SDO_GCDR.GEOCODE('SCOTT',SDO_KEYWORDARRAY('1CARLTONBGOODLETTPL','SANFRANCISCO
    --------------------------------------------------------------------------------
    SDO_GEO_ADDR(0, SDO_KEYWORDARRAY(), NULL, 'CARLTON B GOODLETT PL', NULL, NULL, '
    SAN FRANCISCO', NULL, 'CA', 'US', '94102', NULL, '94102', NULL, '1', 'CARLTON B
    GOODLETT', 'PL', 'F', 'F', NULL, NULL, 'L', .01, 23614360, '????#ENUT?B281CP?',
    1, 'RELAX_BASE_NAME', -122.41815, 37.7784183, '????0101010??000?')

**Parent topic:** SDO_GCDR Package (Geocoding)

### 25.13 SDO_GCDR.GEOCODE_ADDR

#### Format

    SDO_GCDR.GEOCODE_ADDR(
         gc_username IN VARCHAR2,
         address     IN SDO_GEO_ADDR
         ) RETURN SDO_GEO_ADDR;

#### Description

Geocodes an input address using attributes in an SDO_GEO_ADDR object, and returns the first matched address as an SDO_GEO_ADDR object.

#### Parameters

gc_username
Name of the user that owns the tables containing the geocoding data.

address
An SDO_GEO_ADDR object with one or more attributes set. The SDO_GEO_ADDR type is described in [SDO_GEO_ADDR Type](geocoding-address-data-concepts.md).

#### Usage Notes

This function enables you to specify as many attributes in the input SDO_GEO_ADDR object as you can or want to set. It finds the first matching address, and returns an SDO_GEO_ADDR object with all possible attributes set.

Unlike the SDO_GCDR.GEOCODE function, which geocodes input addresses specified by unformatted address lines, the SDO_GCDR.GEOCODE_ADDR function input addresses specified by individual addressing fields defined in SDO_GEO_ADDR objects. When you use unformatted address lines, you rely on the geocoding software to parse the input address and decompose it into individual address fields. This process usually works well, but it can produce undesirable results if the input addresses are not well formatted. By contrast, when you specify parts of the input address as SDO_GEO_ADDR object attributes, you can reduce the chance of geocoding errors and produce more desirable results.

For examples of the SDO_GCDR.GEOCODE_ADDR function, see [Example 12-2](geocoding-address-data-concepts.md) and [Example 12-3](geocoding-address-data-concepts.md) in [Geocoding from a Place Name](geocoding-address-data-concepts.md).

See also the SDO_GCDR.GEOCODE_ADDR_ALL function, which performs the same operation as this function, but which can return more than one address.

#### Examples

The following example returns the geocoded result for a point of interest named `CALIFORNIA PACIFIC MEDICAL CTR`. The example uses a user-defined function named `create_addr_from_placename` (as defined in [Example 12-2](geocoding-address-data-concepts.md) in [Geocoding from a Place Name](geocoding-address-data-concepts.md)) to construct the input SDO_GEO_ADDR object.

    SELECT sdo_gcdr.geocode_addr('SCOTT',
      create_addr_from_placename('CALIFORNIA PACIFIC MEDICAL CTR', 'US'))
    FROM DUAL;

    SDO_GCDR.GEOCODE_ADDR('SCOTT',CREATE_ADDR_FROM_PLACENAME('CALIFORNIAPACIFICME
    --------------------------------------------------------------------------------
    SDO_GEO_ADDR(0, SDO_KEYWORDARRAY(), 'CALIFORNIA PACIFIC MEDICAL CTR-SF', 'BUCHAN
    AN ST', NULL, NULL, 'SAN FRANCISCO', NULL, 'CA', 'US', '94115', NULL, '94115', N
    ULL, '2333', NULL, NULL, 'F', 'F', NULL, NULL, 'L', 0, 23599031, '??????????B281
    CP?', 4, 'DEFAULT', -122.43097, 37.79138, '????4141114??404?')

**Parent topic:** SDO_GCDR Package (Geocoding)

### 25.14 SDO_GCDR.GEOCODE_ADDR_ALL

#### Format

    SDO_GCDR.GEOCODE_ADDR_ALL(
         gc_username  IN VARCHAR2,
         address      IN SDO_GEO_ADDR,
         max_res_num  IN NUMBER DEFAULT 4000
         ) RETURN SDO_ADDR_ARRAY;

#### Description

Geocodes an input address using attributes in an SDO_GEO_ADDR object, and returns matching addresses as an SDO_ADDR_ARRAY object (described in [SDO_ADDR_ARRAY Type](geocoding-address-data-concepts.md)).

#### Parameters

gc_username
Name of the user that owns the tables containing the geocoding data.

address
An SDO_GEO_ADDR object with one or more attributes set. The SDO_GEO_ADDR type is described in [SDO_GEO_ADDR Type](geocoding-address-data-concepts.md).

max_res_num
Maximum number of results to return in the SDO_ADDR_ARRAY object. The default value is 4000.

#### Usage Notes

This function enables you to specify as many attributes in the input SDO_GEO_ADDR object as you can or want to set. It finds matching addresses (up to 4000 or the limit specified in the `max_res_num` parameter), and returns an SDO_ADDR_ARRAY object in which each geocoded result has all possible attributes set.

This function performs the same operation as the SDO_GCDR.GEOCODE_ADDR function, except that it can return more than one address. See the Usage Notes for the SDO_GCDR.GEOCODE_ADDR function for more information.

#### Examples

The following example returns up to three geocoded results for a point of interest named `CALIFORNIA PACIFIC MEDICAL CTR`. (In this case only one result is returned, because the geocoding data contains only one address matching that point of interest.) The example uses a user-defined function named `create_addr_from_placename` (as defined in [Example 12-2](geocoding-address-data-concepts.md) in [Geocoding from a Place Name](geocoding-address-data-concepts.md)) to construct the input SDO_GEO_ADDR object.

    SELECT sdo_gcdr.geocode_addr_all('SCOTT',
      create_addr_from_placename('CALIFORNIA PACIFIC MEDICAL CTR', 'US'), 3)
    FROM DUAL;

    SDO_GCDR.GEOCODE_ADDR_ALL('SCOTT',CREATE_ADDR_FROM_PLACENAME('CALIFORNIAPACIF
    --------------------------------------------------------------------------------
    SDO_ADDR_ARRAY(SDO_GEO_ADDR(0, SDO_KEYWORDARRAY(), 'CALIFORNIA PACIFIC MEDICAL C
    TR-SF', 'BUCHANAN ST', NULL, NULL, 'SAN FRANCISCO', NULL, 'CA', 'US', '94115', N
    ULL, '94115', NULL, '2333', NULL, NULL, 'F', 'F', NULL, NULL, 'L', 0, 23599031,
    '??????????B281CP?', 4, 'DEFAULT', -122.43097, 37.79138, '????4141114??404?'))

**Parent topic:** SDO_GCDR Package (Geocoding)

### 25.15 SDO_GCDR.GEOCODE_ALL

#### Format

    SDO_GCDR.GEOCODE_ALL(
         gc_username  IN VARCHAR2,
         addr_lines   IN SDO_KEYWORDARRAY,
         country      IN VARCHAR2,
         match_mode   IN VARCHAR2
         ) RETURN SDO_ADDR_ARRAY;

#### Description

Geocodes all addresses associated with an unformatted address and returns the result as an SDO_ADDR_ARRAY object.

#### Parameters

gc_username
Name of the user that owns the tables containing the geocoding data.

addr_lines
An array of quoted strings representing the unformatted address to be geocoded. The SDO_KEYWORDARRAY type is described in [SDO_KEYWORDARRAY Type](geocoding-address-data-concepts.md).

country
Country name or ISO country code.

match_mode
Match mode for the geocoding operation. Match modes are explained in [Match Modes](geocoding-address-data-concepts.md).

#### Usage Notes

This function returns an object of type SDO_ADDR_ARRAY, which is described in [SDO_ADDR_ARRAY Type](geocoding-address-data-concepts.md). It performs the same operation as the SDO_GCDR.GEOCODE function; however, it can return results for multiple addresses, in which case the returned SDO_ADDR_ARRAY object contains multiple SDO_GEO_ADDR objects. If your application needs to select one of the addresses for some further operations, you can use the information about each returned address to help you make that selection.

Each SDO_GEO_ADDR object in the returned SDO_ADDR_ARRAY array represents the center point of each street segment that matches the criteria in the `addr_lines` parameter. For example, if Main Street extends into two postal codes, or if there are two separate streets named Main Street in two separate postal codes, and if you specify Main Street and a city and state for this function, the returned SDO_ADDR_ARRAY array contains two SDO_GEO_ADDR objects, each reflecting the center point of Main Street in a particular postal code. The house or building number in each SDO_GEO_ADDR object is the house or building number located at the center point of the street segment, even if the input address contains no house or building number or a nonexistent number.

#### Examples

The following example returns an array of geocoded results, each result reflecting the center point of Clay Street in all postal codes in San Francisco, California, in which the street extends. The resulting array includes four SDO_GEOR_ADDR objects, each reflecting the house at the center point of the Clay Street segment in each of the four postal codes (94108, 94115, 94118, and 94109) into which Clay Street extends.

    SELECT SDO_GCDR.GEOCODE_ALL('SCOTT',
      SDO_KEYWORDARRAY('Clay St', 'San Francisco, CA'),
      'US', 'DEFAULT') FROM DUAL;

    SDO_GCDR.GEOCODE_ALL('SCOTT',SDO_KEYWORDARRAY('CLAYST','SANFRANCISCO,CA'),'US
    --------------------------------------------------------------------------------
    SDO_ADDR_ARRAY(SDO_GEO_ADDR(1, SDO_KEYWORDARRAY(), NULL, 'CLAY ST', NULL, NULL,
    'SAN FRANCISCO', NULL, 'CA', 'US', '94109', NULL, '94109', NULL, '1698', 'CLAY',
     'ST', 'F', 'F', NULL, NULL, 'L', 0, 23600700, '????#ENUT?B281CP?', 1, 'DEFAULT'
    , -122.42093, 37.79236, '????4101010??004?'), SDO_GEO_ADDR(1, SDO_KEYWORDARRAY()
    , NULL, 'CLAY ST', NULL, NULL, 'SAN FRANCISCO', NULL, 'CA', 'US', '94111', NULL,
     '94111', NULL, '398', 'CLAY', 'ST', 'F', 'F', NULL, NULL, 'L', 0, 23600678, '??
    ??#ENUT?B281CP?', 1, 'DEFAULT', -122.40027, 37.79499, '????4101010??004?'), SDO_
    GEO_ADDR(1, SDO_KEYWORDARRAY(), NULL, 'CLAY ST', NULL, NULL, 'SAN FRANCISCO', NU
    LL, 'CA', 'US', '94108', NULL, '94108', NULL, '978', 'CLAY', 'ST', 'F', 'F', NUL
    L, NULL, 'L', 0, 23600689, '????#ENUT?B281CP?', 1, 'DEFAULT', -122.40904, 37.793
    85, '????4101010??004?'), SDO_GEO_ADDR(1, SDO_KEYWORDARRAY(), NULL, 'CLAY ST', N
    ULL, NULL, 'SAN FRANCISCO', NULL, 'CA', 'US', '94115', NULL, '94115', NULL, '279
    8', 'CLAY', 'ST', 'F', 'F', NULL, NULL, 'L', 0, 23600709, '????#ENUT?B281CP?', 1
    , 'DEFAULT', -122.43909, 37.79007, '????4101010??004?'), SDO_GEO_ADDR(1, SDO_KEY
    WORDARRAY(), NULL, 'CLAY ST', NULL, NULL, 'SAN FRANCISCO', NULL, 'CA', 'US', '94
    118', NULL, '94118', NULL, '3698', 'CLAY', 'ST', 'F', 'F', NULL, NULL, 'L', 0, 2
    3600718, '????#ENUT?B281CP?', 1, 'DEFAULT', -122.45372, 37.78822, '????4101010??
    004?'))

**Parent topic:** SDO_GCDR Package (Geocoding)

### 25.16 SDO_GCDR.GEOCODE_AS_GEOMETRY

#### Format

    SDO_GCDR.GEOCODE_AS_GEOMETRY(
         username    IN VARCHAR2,
         addr_lines  IN SDO_KEYWORDARRAY,
         country     IN VARCHAR2
         ) RETURN SDO_GEOMETRY;

#### Description

Geocodes an unformatted address and returns the result as an SDO_GEOMETRY object.

#### Parameters

username
Name of the user that owns the tables containing the geocoding data.

addr_lines
An array of quoted strings representing the unformatted address to be geocoded. The SDO_KEYWORDARRAY type is described in [SDO_KEYWORDARRAY Type](geocoding-address-data-concepts.md).

country
Country name or ISO country code.

#### Usage Notes

This function returns an object of type SDO_GEOMETRY. It performs the same operation as the SDO_GCDR.GEOCODE function; however, that function returns an SDO_GEOR_ADDR object.

This function uses a match mode of `'DEFAULT'` for the geocoding operation. Match modes are explained in [Match Modes](geocoding-address-data-concepts.md).

#### Examples

The following example geocodes the address of City Hall in San Francisco, California. It returns an SDO_GEOMETRY object in which the longitude and latitude coordinates of this address are -122.41815 and 37.7784183, respectively.

    SELECT SDO_GCDR.GEOCODE_AS_GEOMETRY('SCOTT',
      SDO_KEYWORDARRAY('1 Carlton B Goodlett Pl', 'San Francisco, CA  94102'),
      'US') FROM DUAL;

    SDO_GCDR.GEOCODE_AS_GEOMETRY('SCOTT',SDO_KEYWORDARRAY('1CARLTONBGOODLETTPL','
    --------------------------------------------------------------------------------
    SDO_GEOMETRY(2001, 8307, SDO_POINT_TYPE(-122.41815, 37.7784183, NULL), NULL, NUL
    L)

**Parent topic:** SDO_GCDR Package (Geocoding)

### 25.17 SDO_GCDR.REVERSE_GEOCODE

#### Format

    SDO_GCDR.REVERSE_GEOCODE(
         username IN VARCHAR2,
         location IN SDO_GEOMETRY,
         country  IN VARCHAR2
         ) RETURN SDO_GEO_ADDR;

#### Description

Reverse geocodes a location, specified by its spatial geometry object and country, and returns the result as an SDO_GEO_ADDR object.

#### Parameters

username
Name of the user that owns the tables containing the geocoding data.

location
An SDO_GEOMETRY object that specifies the point location to be reverse geocoded.

country
Country name or ISO country code.

#### Usage Notes

This function returns an object of type SDO_GEOR_ADDR, which is described in [SDO_GEO_ADDR Type](geocoding-address-data-concepts.md).

A spatial index must be created on the table GC_ROAD_SEGMENT\_\<table-suffix\>.

#### Examples

The following example reverse geocodes a point with the longitude and latitude values (-122.41815, 37.7784183). For this example, a spatial index was created on the GEOMETRY column in the GC_ROAD_SEGMENT_US table.

    SELECT SDO_GCDR.REVERSE_GEOCODE('SCOTT',
      SDO_GEOMETRY(2001, 8307,
        SDO_POINT_TYPE(-122.41815, 37.7784183, NULL), NULL, NULL),
      'US') FROM DUAL;

    SDO_GCDR.REVERSE_GEOCODE('SCOTT',SDO_GEOMETRY(2001,8307,SDO_POINT_TYPE(-122.4
    --------------------------------------------------------------------------------
    SDO_GEO_ADDR(0, SDO_KEYWORDARRAY(), NULL, 'POLK ST', NULL, NULL, 'SAN FRANCISCO'
    , NULL, 'CA', 'US', '94102', NULL, '94102', NULL, '200', 'POLK', 'ST', 'F', 'F',
     NULL, NULL, 'R', .00966633, 23614360, '', 1, 'DEFAULT', -122.41815, 37.7784177,
     '????4141414??404?')

**Parent topic:** SDO_GCDR Package (Geocoding)
