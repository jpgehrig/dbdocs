## 29  SDO_OLS Package (OpenLS)

The MDSYS.SDO_OLS package contains subprograms for Spatial and Graph OpenLS support.

The To use the subprograms in this chapter, you must understand the conceptual and usage information about OpenLS in [OpenLS Support](openls-concepts.md).

**Note:**

SDO_OLS subprograms are not supported in Oracle Autonomous Database both in Serverless and Dedicated deployments.

The rest of this chapter provides reference information on the subprograms, listed in alphabetical order.

- SDO_OLS.MakeOpenLSClobRequest
- SDO_OLS.MakeOpenLSRequest

**Parent topic:** [Reference Information](spatial-reference-information.md)

### 29.1 SDO_OLS.MakeOpenLSClobRequest

#### Format

    SDO_OLS.MakeOpenLSClobRequest(
         request  IN CLOB
         ) RETURN CLOB;

#### Description

Submits an OpenLS request using a CLOB object, and returns the result as a CLOB object.

#### Parameters

request
OpenLS request in the form of a CLOB object.

#### Usage Notes

To specify the input request as an XMLType object to return an XMLType object, use the SDO_OLS.MakeOpenLSRequest function.

For information about OpenLS support, see [OpenLS Support](openls-concepts.md).

#### Examples

The following example requests the nearest business, in a specified category (that is, with specified `SIC_code` value), to a specified location (longitude: -122.4083257, latitude: 37.788208).

    DECLARE
      request CLOB;
      result CLOB;
    BEGIN
    request := TO_CLOB(
    '<?xml version="1.0" encoding="UTF-8"?>
    <XLS xmlns="http://www.opengis.net/xls" xmlns:gml="http://www.opengis.net/gml"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" version="1.1">
     <RequestHeader clientName="someName" clientPassword="password"/>
     <Request requestID="123" maximumResponses="100" version="1.1"
          methodName="DirectoryRequest">
      <DirectoryRequest>
       <POILocation>
        <Nearest nearestCriterion="Proximity">
         <Position>
          <gml:Point xmlns:gml="http://www.opengis.net/gml">
           <gml:pos dimension="2" srsName="4326">-122.4083257 37.788208</gml:pos>
          </gml:Point>
         </Position>
        </Nearest>
       </POILocation>
       <POIProperties>
        <POIProperty name="SIC_code" value="1234567890"/>
       </POIProperties>
      </DirectoryRequest>
     </Request>
    </XLS>');

    result := SDO_OLS.makeOpenLSClobRequest(request);

    END;
    /

**Parent topic:** SDO_OLS Package (OpenLS)

### 29.2 SDO_OLS.MakeOpenLSRequest

#### Format

    SDO_OLS.MakeOpenLSRequest(
         request  IN XMLTYPE
         ) RETURN XMLTYPE;

#### Description

Submits an OpenLS request using an XMLType object, and returns the result as an XMLType object.

#### Parameters

request
OpenLS request in the form of an XMLType object.

#### Usage Notes

To specify the input request as a CLOB and to return a CLOB, use the SDO_OLS.MakeOpenLSClobRequest function.

For information about OpenLS support, see [OpenLS Support](openls-concepts.md).

#### Examples

The following example requests the nearest business, in a specified category (that is, with specified `SIC_code` value), to a specified location (longitude: -122.4083257, latitude: 37.788208).

    SELECT SDO_OLS.makeOpenLSRequest(XMLTYPE(
    '<?xml version="1.0" encoding="UTF-8"?>
    <XLS xmlns="http://www.opengis.net/xls" xmlns:gml="http://www.opengis.net/gml"
        xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" version="1.1">
     <RequestHeader clientName="someName" clientPassword="password"/>
     <Request requestID="123" maximumResponses="100" version="1.1"
          methodName="DirectoryRequest">
      <DirectoryRequest>
       <POILocation>
        <Nearest nearestCriterion="Proximity">
         <Position>
          <gml:Point xmlns:gml="http://www.opengis.net/gml">
           <gml:pos dimension="2" srsName="4326">-122.4083257 37.788208</gml:pos>
          </gml:Point>
         </Position>
        </Nearest>
       </POILocation>
       <POIProperties>
        <POIProperty name="SIC_code" value="1234567890"/>
       </POIProperties>
      </DirectoryRequest>
     </Request>
    </XLS>')) "OpenLS Response" FROM DUAL;

**Parent topic:** SDO_OLS Package (OpenLS)
