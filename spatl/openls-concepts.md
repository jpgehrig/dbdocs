## 15  OpenLS Support

This chapter describes the Oracle Spatial and Graph support for web services based on the Open Location Services Initiative (OpenLS) of the Open GeoSpatial Consortium (OGC), versions 1.0 and 1.1.

**Note:**

Before you use OpenLS, be sure that you understand the concepts described in [Introduction to Spatial Web Services](introduction-spatial-web-services.md), and that you have performed any necessary configuration work as described in that chapter.

For a description of OpenLS, see [`http://www.opengeospatial.org/standards/ols`](http://www.opengeospatial.org/standards/ols), which includes links for downloads and schemas.

- Supported OpenLS Services
  Spatial and Graph supports the following OGC OpenLS services.
- OpenLS Application Programming Interfaces
  Two application programming interfaces (APIs) are provided using Spatial and Graph OpenLS services: a web services API and a PL/SQL API..
- OpenLS Service Support and Examples
  This section describes the support provided for geocoding, mapping, routing, and directory service (YP). It also contains examples of OpenLS web services API requests and responses.

**Parent topic:** [Spatial Web Services](spatial-web-services.md)

### 15.1 Supported OpenLS Services

Spatial and Graph supports the following OGC OpenLS services.

- Location Utility Service (geocoding)

- Presentation Service (mapping)

- Route Service (driving directions)

- Directory Service (YP, or "Yellow Pages")

Spatial and Graph does not currently support the OGC OpenLS Gateway Service (mobile positioning).

For all supported services except Directory Service (YP, or Yellow Pages), you must first perform certain operations, which might included acquiring and loading third-party data, as well as configuring and deploying underlying technology on which the Spatial and Graph OpenLS service is based. Table 15-1 lists the Spatial and Graph OpenLS services, and the chapter or manual that documents the requirements and underlying technologies.

Table 15-1 Spatial and Graph OpenLS Services Dependencies

| Spatial and Graph OpenLS Service         | Depends On                     | Documented In                                                                   |
|:-----------------------------------------|:-------------------------------|:--------------------------------------------------------------------------------|
| Geocoding                                | Geocoding metadata and data    | [Geocoding Address Data](geocoding-address-data-concepts.md)                    |
| Mapping                                  | Oracle MapViewer               | [Oracle Fusion Middleware User's Guide for Oracle MapViewer](../jimpv/index.md) |
| Driving directions                       | Routing engine                 | [Routing Engine](routing-engine-concepts.md)                                    |
| Business directory (YP, or Yellow Pages) | Data from an external provider | [Business Directory (Yellow Pages) Support](buasiness-directory-yp-concepts.md) |

**Parent topic:** OpenLS Support

### 15.2 OpenLS Application Programming Interfaces

Two application programming interfaces (APIs) are provided using Spatial and Graph OpenLS services: a web services API and a PL/SQL API..

The web services API uses the same SOAP envelope as Web feature services (described in [Web Feature Service (WFS) Support](web-feature-service-wfs-concepts.md)). You enable authentication and authorization using WSS and proxy authentication and user management.

The PL/SQL API is a convenient alternative to web services. Authentication and authorization are enabled through the database connection that you use to call a PL/SQL subprogram to submit an OpenLS request and return the result. The PL/SQL API is implemented in the SDO_OLS package, which is documented in [SDO_OLS Package (OpenLS)](SDO_OLS-reference.md) .

**Parent topic:** OpenLS Support

### 15.3 OpenLS Service Support and Examples

This section describes the support provided for geocoding, mapping, routing, and directory service (YP). It also contains examples of OpenLS web services API requests and responses.

- OpenLS Geocoding
- OpenLS Mapping
- OpenLS Routing
- OpenLS Directory Service (YP)

**Parent topic:** OpenLS Support

#### 15.3.1 OpenLS Geocoding

An OpenLS geocoding `<Request>` element includes the `methodName` attribute with a value of either `GeocodeRequest` or `ReverseGeocodeRequest`, and corresponding a top-level element named `<GeocodeRequest>` or `<ReverseGeocodeRequest>`.

If the `methodName` attribute value is `GeocodeRequest`, the `<GeocodeRequest>` element contains an `<Address>` element that can specify a free-form address, a street address, or an intersection address, with zero or more `<Place>` elements and an optional `<PostalCode>` element. The `<Address>` element has the required attribute `countryCode`, and several optional attributes.

If the `methodName` attribute value is `GeocodeRequest`, the `<ReverseGeocodeRequest>` element contains a `<Position>` element for identifying the location to be reverse geocoded, and an optional `<ReverseGeocodePreference>` element for specifying the information to be returned (default = a street address).

Example 15-1 is a request to geocode two addresses in San Francisco, California.

Example 15-1 OpenLS Geocoding Request

    <XLS
      xmlns=http://www.opengis.net/xls
      xmlns:gml=http://www.opengis.net/gml
      xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance
      xsi:schemaLocation="http://www.opengis.net/xls …"
      version="1.0">
      <RequestHeader clientName="someName" clientPassword="password"/>
      <Request
        maximumResponses="10"
        methodName="GeocodeRequest"
        requestID="123"
        version="1.0">
        <GeocodeRequest>
          <Address countryCode="US">
            <StreetAddress>
              <Building number="400"/>
              <Street>Post Street</Street>
            </StreetAddress>
            <Place type="CountrySubdivision">CA</Place>
            <Place type="Municipality">San Francisco</Place>
            <PostalCode>94102</PostalCode>
          </Address>
          <Address countryCode="US">
            <StreetAddress>
              <Building number="233"/>
              <Street>Winston Drive</Street>
            </StreetAddress>
            <Place type="CountrySubdivision">CA</Place>
            <Place type="Municipality">San Francisco</Place>
            <PostalCode>94132</PostalCode>
          </Address>
        </GeocodeRequest>
      </Request>
    </XLS>

Example 15-2 OpenLS Geocoding Response

Example 15-2 is the response to the request in Example 15-1. The longitude and latitude coordinates are returned for the two addresses (`-122.4083257 37.788208` for the first, `-122.4753965 37.7269066` for the second).

    <xls:XLS
      xmlns:xls=http://www.opengis.net/xls
      xmlns:gml=http://www.opengis.net/gml
      xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance
      version="1.0">
      <xls:ResponseHeader/>
      <xls:Response requestID="123" version="1.0">
        <xls:GeocodeResponse xmlns:xls="http://www.opengis.net/xls">
          <xls:GeocodeResponseList
            xmlns:xls=http://www.opengis.net/xls
            numberOfGeocodedAddresses="1">
            <xls:GeocodedAddress>
              <gml:Point xmlns:gml="http://www.opengis.net/gml">
                <gml:pos dimension="2" srsName="4326">-122.4083257 37.788208</gml:pos>
              </gml:Point>
              <xls:Address countryCode="US">
                <xls:StreetAddress>
                  <xls:Building number="400"/>
                  <xls:Street>POST ST</xls:Street>
                </xls:StreetAddress>
                <xls:Place type="CountrySubdivision">CA</xls:Place>
                <xls:Place type="Municipality">SAN FRANCISCO</xls:Place>
                <xls:PostalCode>94102</xls:PostalCode>
              </xls:Address>
            </xls:GeocodedAddress>
          </xls:GeocodeResponseList>
          <xls:GeocodeResponseList
            xmlns:xls=http://www.opengis.net/xls
            numberOfGeocodedAddresses="1">
            <xls:GeocodedAddress>
              <gml:Point xmlns:gml="http://www.opengis.net/gml">
                <gml:pos dimension="2" srsName="4326">-122.4753965 37.7269066</gml:pos>
              </gml:Point>
              <xls:Address countryCode="US">
                <xls:StreetAddress>
                  <xls:Building number="233"/>
                  <xls:Street>WINSTON DR</xls:Street>
                </xls:StreetAddress>
                <xls:Place type="CountrySubdivision">CA</xls:Place>
                <xls:Place type="Municipality">SAN FRANCISCO</xls:Place>
                <xls:PostalCode>94132</xls:PostalCode>
              </xls:Address>
            </xls:GeocodedAddress>
          </xls:GeocodeResponseList>
        </xls:GeocodeResponse>
      </xls:Response>
    </xls:XLS>

**Parent topic:** OpenLS Service Support and Examples

#### 15.3.2 OpenLS Mapping

An OpenLS mapping `<Request>` element includes the `methodName` attribute with a value of `PortrayMapRequest`, and a top-level element named `<PortrayMapRequest>`.

The `<PortrayMapRequest>` element contains an `<Output>` element that specifies the output of the map to be generated, including the center point of the map.

The `<PortrayMapRequest>` element can contain a `<Basemap>` element specifying a MapViewer base map and one or more themes, and zero or more `<Overlay>` elements, each specifying information to be overlaid on the base map.

Example 15-3 is a request to portray a map image. The image is to be centered at a specified longitude/latitude point, to use a base map and two MapViewer themes, and identify three points on the map.

Example 15-3 OpenLS Mapping Request

    <XLS
      xmlns=http://www.opengis.net/xls
      xmlns:gml=http://www.opengis.net/gml
      xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance
      xsi:schemaLocation="http://www.opengis.net/xls …"
      version="1.1">
      <RequestHeader clientName="someName" clientPassword="password"/>
      <Request
        maximumResponses="1"
        methodName="PortrayMapRequest"
        requestID="456"
        version="1.1">
        <PortrayMapRequest>
          <Output
            BGcolor="#a6cae0"
            content="URL"
            format="GIF_URL"
            height="600"
            transparent="false"
            width="800">
            <CenterContext SRS="8307">
              <CenterPoint srsName="8307">
                <gml:pos>-122.2615 37.5266</gml:pos>
              </CenterPoint>
              <Radius unit="M">50000</Radius>
            </CenterContext>
          </Output>
          <Basemap filter="Include">
            <Layer name="mvdemo.demo_map.THEME_DEMO_COUNTIES"/>
            <Layer name="mvdemo.demo_map.THEME_DEMO_HIGHWAYS"/>
          </Basemap>
          <Overlay zorder="1">
            <POI
              ID="123"
              description="description"
              phoneNumber="1234"
              POIName="Books at Post Str (point)">
              <gml:Point srsName="4326">
                <gml:pos>-122.4083257 37.788208</gml:pos>
              </gml:Point>
            </POI>
          </Overlay>
          <Overlay zorder="2">
            <POI
              ID="456"
              description="description"
              phoneNumber="1234"
              POIName="Books at Winston Dr (address)">
              <Address countryCode="US">
                <StreetAddress>
                  <Building number="233"/>
                  <Street>Winston Drive</Street>
                </StreetAddress>
                <Place type="CountrySubdivision">CA</Place>
                <Place type="CountrySecondarySubdivision"/>
                <Place type="Municipality">San Francisco</Place>
                <Place type="MunicipalitySubdivision"/>
                <PostalCode>94132</PostalCode>
              </Address>
            </POI>
          </Overlay>
          <Overlay zorder="3">
            <Position levelOfConf="1">
              <gml:Point gid="a boat (point)" srsName="4326">
                <gml:pos>-122.8053965 37.388208</gml:pos>
              </gml:Point>
            </Position>
          </Overlay>
        </PortrayMapRequest>
      </Request>
    </XLS>

Example 15-4 OpenLS Mapping Response

Example 15-4 is the response to the request in Example 15-3.; however, in an actual response, the line `<xls:URL>Actual URL replaced with constant string for test</xls:URL>` would contain the actual URL of the map image.

    <xls:XLS
      xmlns:xls=http://www.opengis.net/xls
      xmlns:gml=http://www.opengis.net/gml
      xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance
      xsi:schemaLocation="http://www.opengis.net/xls …"
      version="1.1">
      <xls:ResponseHeader/>
      <xls:Response numberOfResponses="1" requestID="456" version="1.1">
        <xls:PortrayMapResponse>
          <xls:Map>
            <xls:Content format="GIF_URL" height="600" width="800">
              <xls:URL>Actual URL replaced with constant string for test</xls:URL>
            </xls:Content>
            <xls:BBoxContext srsName="4326">
              <gml:pos>-122.86037685607968 37.07744235794024</gml:pos>
              <gml:pos>-121.66262314392031 37.97575764205976</gml:pos>
            </xls:BBoxContext>
          </xls:Map>
        </xls:PortrayMapResponse>
      </xls:Response>
    </xls:XLS>

**Parent topic:** OpenLS Service Support and Examples

#### 15.3.3 OpenLS Routing

An OpenLS routing `<Request>` element includes the `methodName` attribute with a value of `DetermineRouteRequest`, and a top-level element named `<DetermineRouteRequest>`.

The `<DetermineRouteRequest>` element contains a `<RoutePlan>` element that specifies the route preference and points to be included (and optionally avoided) in the route, with at least the start and end points.

The `<DetermineRouteRequest>` element can also contain zero or more of the following elements: `<RouteGeometryRequest>` to return the line string geometry representing the route, `<RouteMapRequest>` to request a map image of the route, and `<RouteInstructionsRequest>` to request driving directions for the route.

Example 15-5 is a request for the route geometry and map image for the fastest route between an address in Cambridge, Massachusetts and an address in Nashua, New Hampshire.

Example 15-5 OpenLS Routing Request

    <XLS
      xmlns=http://www.opengis.net/xls
      xmlns:gml=http://www.opengis.net/gml
      xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance
      xsi:schemaLocation="http://www.opengis.net/xls …"
      version="1.1">
      <RequestHeader clientName="someName" clientPassword="password"/>
        <Request
          maximumResponses="10"
          methodName="DetermineRouteRequest"
          requestID="12345"
          version="1.0">
          <DetermineRouteRequest>
            <RoutePlan>
              <RoutePreference>Fastest</RoutePreference>
              <WayPointList>
                <StartPoint>
                  <POI description="Borders" ID="1" phoneNumber="12345" POIName="Borders">
                    <Address countryCode="US">
                      <StreetAddress>
                        <Building number="100"/>
                        <Street>Cambridgeside Pl</Street>
                      </StreetAddress>
                      <Place type="CountrySubdivision">MA</Place>
                      <Place type="Municipality">Cambridge</Place>
                      <PostalCode>02141</PostalCode>
                    </Address>
                  </POI>
                </StartPoint>
                <EndPoint>
                  <Address countryCode="US">
                    <StreetAddress>
                      <Building number="1"/>
                      <Street>Oracle Dr</Street>
                    </StreetAddress>
                    <Place type="CountrySubdivision">New Hampshire</Place>
                    <Place type="Municipality">Nashua</Place>
                    <PostalCode>03062</PostalCode>
                  </Address>
                </EndPoint>
              </WayPointList>
              <AvoidList/>
            </RoutePlan>
          <RouteGeometryRequest maxPoints="100" provideStartingPortion="true" scale="1">
            <BoundingBox>
              <gml:pos/>
              <gml:pos/>
            </BoundingBox>
          </RouteGeometryRequest>
          <RouteMapRequest>
            <Output BGcolor="" format="" height="600" transparent="false" width="800"/>
          </RouteMapRequest>
        </DetermineRouteRequest>
      </Request>
    </XLS>

Example 15-6 OpenLS Routing Response

Example 15-6 is part of the response to the request in Example 15-5. Example 15-6 shows the total estimated driving time, the total distance, the lower-left and upper-right longitude/latitude coordinates of the minimum bounding rectangle that encloses the route, and the longitude/latitude coordinates of the first few points along the line geometry representing the route.

    <xls:XLS
      xmlns:xls=http://www.opengis.net/xls
      xmlns:gml=http://www.opengis.net/gml
      xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance
      xsi:schemaLocation="http://www.opengis.net/xls …"
      version="1.1">
      <xls:ResponseHeader/>
      <xls:Response numberOfResponses="1" requestID="12345" version="1.0">
        <xls:DetermineRouteResponse>
          <xls:RouteSummary>
            <xls:TotalTime>P0DT0H42M26S</xls:TotalTime>
            <xls:TotalDistance uom="M" value="61528.7"/>
            <xls:BoundingBox srsName="4326">
              <gml:pos dimension="2" srsName="4326">-71.45937289088023 42.36694</gml:pos>
              <gml:pos dimension="2" srsName="4326">-71.06754 42.70824</gml:pos>
            </xls:BoundingBox>
          </xls:RouteSummary>
          <xls:RouteGeometry>
            <gml:LineString srsName="4326">
              <gml:pos
                xmlns:gml=http://www.opengis.net/gml
                dimension="2"
                srsName="4326">-71.07444,42.36792</gml:pos>
              <gml:pos
                xmlns:gml=http://www.opengis.net/gml
                dimension="2"
                srsName="4326">-71.07162,42.37082</gml:pos>
              <gml:pos
                xmlns:gml=http://www.opengis.net/gml
                dimension="2"
                srsName="4326">-71.06954,42.37333</gml:pos>
    . . .

**Parent topic:** OpenLS Service Support and Examples

#### 15.3.4 OpenLS Directory Service (YP)

An OpenLS directory service `<Request>` element includes the `methodName` attribute with a value of `DirectoryRequest`, and a top-level element named `<DirectoryRequest>`.

The `<DirectoryRequest>` element contains a `<POILocation>` element that specifies the location of a point of interest, that is, the center point from which to compute distances of returned businesses.

The `<DirectoryRequest>` element also contains a `<POIProperties>` element that specifies one or more `<POIProperty>` elements, each of which contains a `name` attribute identifying a property and a `value` attribute identifying the value for the property. The `name` attribute can specify any of the following strings: `ID`, `POIName`, `PhoneNumber`, `Keyword`, `NAICS_type`, `NAICS_subType`, `NAICS_category`, `SIC_type`, `SIC_subType`, `SIC_category`, `SIC_code`, or `other`.

Example 15-7 is a request for information about business that have either or both of two specified SIC (Standard Industrial Classification) codes. For this example, the two SIC codes (`1234567890` and `1234567891`) are fictitious, and they are being used with a limited test data set in which these codes have been applied to categories (Book stores and Cafes & Cafeterias) that do not have these SIC codes in the real world.

Example 15-7 OpenLS Directory Service (YP) Request

    <XLS
      xmlns=http://www.opengis.net/xls
      xmlns:gml=http://www.opengis.net/gml
      xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance
      xsi:schemaLocation="http://www.opengis.net/xls …"
      version="1.0">
      <RequestHeader clientName="someName" clientPassword="password"/>
      <Request
        requestID="123"
        maximumResponses="100"
        version="1.1"
        methodName="DirectoryRequest">
        <DirectoryRequest>
          <POILocation>
            <Address countryCode="US">
            </Address>
          </POILocation>
          <POIProperties>
            <POIProperty name="SIC_code" value="1234567890"/>
            <POIProperty name="SIC_code" value="1234567891"/>
          </POIProperties>
        </DirectoryRequest>
      </Request>
    </XLS>

Example 15-8 OpenLS Directory Service (YP) Response

Example 15-8 is the response to the request in Example 15-7. The response contains information about two businesses for which either or both of the specific SIC codes apply.

    <xls:XLS
      xmlns:xls=http://www.opengis.net/xls
      xmlns:gml=http://www.opengis.net/gml
      xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance
      version="1.0">
      <xls:ResponseHeader/>
      <xls:Response requestID="123" version="1.1">
        <DirectoryResponse xmlns="http://www.opengis.net/xls">
          <xls:POIContext xmlns:xls="http://www.opengis.net/xls">
            <xls:POI
              ID="1"
              POIName="Borders Books &amp; More"
              phoneNumber="415-731-0665"
              description="Books &amp; more">
              <POIAttributeList xmlns="http://www.opengis.net/xls">
                <xls:SIC
                  xmlns:xls=http://www.opengis.net/xls
                  category="Book stores"
                  code="1234567890"
                  subType=""
                  type=""/>
                <xls:SIC
                  xmlns:xls=http://www.opengis.net/xls
                  category="Cafes &amp; Cafeterias"
                  code="1234567891"
                  subType="" type=""/>
              </POIAttributeList>
              <gml:Point xmlns:gml="http://www.opengis.net/gml">
                <gml:pos dimension="2" srsName="4326">-122.4753965 37.7269066</gml:pos>
              </gml:Point>
              <xls:Address countryCode="US">
                <xls:StreetAddress>
                  <xls:Building number="233"/>
                  <xls:Street>Winston Drive</xls:Street>
                </xls:StreetAddress>
                <xls:Place type="CountrySubdivision">CA</xls:Place>
                <xls:Place type="CountrySecondarySubdivision"/>
                <xls:Place type="Municipality">San Francisco</xls:Place>
                <xls:Place type="MunicipalitySubdivision"/>
                <xls:PostalCode>94132</xls:PostalCode>
              </xls:Address>
            </xls:POI>
          </xls:POIContext>
          <xls:POIContext xmlns:xls="http://www.opengis.net/xls">
            <xls:POI
              ID="2"
              POIName="Borders Books &amp; More"
              phoneNumber="415-399-1633"
              description="Books &amp; more">
              <POIAttributeList xmlns="http://www.opengis.net/xls">
                <xls:SIC
                  xmlns:xls=http://www.opengis.net/xls
                  category="Book stores"
                  code="1234567890"
                  subType=""
                  type=""/>
                <xls:SIC
                  xmlns:xls=http://www.opengis.net/xls
                  category="Cafes &amp; Cafeterias"
                  code="1234567891"
                  subType=""
                  type=""/>
              </POIAttributeList>
              <gml:Point xmlns:gml="http://www.opengis.net/gml">
                <gml:pos dimension="2" srsName="4326">-122.4083257 37.788208</gml:pos>
              </gml:Point>
              <xls:Address countryCode="US">
                <xls:StreetIntersection>
                  <xls:Street>Post St</xls:Street>
                  <xls:IntersectingStreet>Powell St</xls:IntersectingStreet>
                </xls:StreetIntersection>
                <xls:Place type="CountrySubdivision">CA</xls:Place>
                <xls:Place type="CountrySecondarySubdivision"/>
                <xls:Place type="Municipality">San Francisco</xls:Place>
                <xls:Place type="MunicipalitySubdivision"/>
                <xls:PostalCode>94102</xls:PostalCode>
              </xls:Address>
            </xls:POI>
          </xls:POIContext>
        </DirectoryResponse>
      </xls:Response>
    </xls:XLS>

**Parent topic:** OpenLS Service Support and Examples
