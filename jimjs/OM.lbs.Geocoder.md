------------------------------------------------------------------------

#### new Geocoder(metaData)

Geocoder is a helper class for various geocoding functions. Once constructed,
it can be used to geocode a single address, a batch of addresses, or reverse
geocode a longitude/latitude point.

##### Parameters:

| Name       | Type   | Description                                                                                                                                  |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------|
| `metaData` | Object | MetaData is a class that provides capability and data coverage information for the<br>various services hosted on Oracle's eLocation servers. |

### Methods

------------------------------------------------------------------------

#### batchGeoCode(addressList, callBack)

Use this method to efficiently batch geocode multiple addresses.

##### Parameters:

| Name          | Type     | Description                                                                                                                                                                        |
|---------------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `addressList` | array    | an array of addresses to be geocoded.                                                                                                                                              |
| `callBack`    | function | a user specified function that is invoked when<br>the input address is geocoded. It should declare one parameter, which is an<br>address object that contains the geocoded result. |

##### Example

    var addressList = [
          {"id":"100", "address":"1 oracle drv, Nashua, NH, 03062"},
          {"id":"101", "address":"500 oracle pkwy, Redwood City, CA 94065"}
         ];

         gc.bactchGeocode(addressList, function(results, status) {
             if(status===Geocoder.STATUS_OK)
             {
                 for(var i = 0; i < results.length; i++)
                 {
                    var result = results[i];
                    if(result.matches)
                    {
                         var match = result.matches[0];
                         alert("address "+result.id+" : "+match.longitude+", "+match.latitude);
                    }
                 }
             }
         });

------------------------------------------------------------------------

#### geocode(address, callBack)

This method invokes the geocoding service on Oracle's eLocation server to obtain the longitude/latitude
information for a given street address. It then invokes the user defined
callback function and passes in the geocoded result. The call back function can
then look up the result, extract the longitude/latitude information and display
it on a map.

##### Parameters:

| Name       | Type     | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `address`  | Object   | address is a single JSON object containing the input address.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `callBack` | function | is a user specified function that is invoked when<br>the input address is geocoded. It should declare two parameters 'result' and 'status'.<br>The 'status' parameter contains general status regarding the current geocoding request.<br>For instance it will be set to Geocoder.STATUS_FAILED if there is network issue and the<br>geocoding server cannot be reached. A value of Geocoder.STATUS_OK indicates the<br>geocoding call went through, but it does not necessarily mean the input address<br>actually has found a match by the service.<br>The 'result' parameter contains the actual geocoding result, with the following<br>properties that an application can look up:<br><br>• id : the id (if any) specified in the input address.<br>• rawResponse : the raw (XML) response from the geocoding service.<br>• matches : an array containing one or more instances of Match class |

##### Examples

    //a single JSON object address
      var addr = {id:"100", address:"1 oracle drv, Nashua, NH, 03062", matchCode:OM.lbs.Geocoder.MATCH_MODE_RELAX_POSTAL_CODE} ;
      gc.geocode(addr, function(result, status) {
          if(status===Geocoder.STATUS_OK && result.matches)
          {
             var match = result.matches[0];
             alert(long: +match.longitude + , lat: +match.latitude);
          }
      });



    //a formatted address
      //we can use the formatted address if we know the value for each field of the address. Now we support formatted address:
      //OM.lbs.GdfFormAddress, OM.lbs.GenFormAddress, OM.lbs.USForm1Address, OM.lbs.USForm2Address.
      //These could have a good performance.

      var options={street:"1 Oracle Drive", builtupArea:"Nashua", order1Area:"NH", postalCode:"03062", country:"US",  matchCode:OM.lbs.Geocoder.MATCH_MODE_RELAX_POSTAL_CODE};
      var address=new OM.lbs.GdfFormAddress(options);
      gc.geocode(addr, function(result, status) {
          if(status===Geocoder.STATUS_OK && result.matches)
          {
             var match = result.matches[0];
             alert(long: +match.longitude + , lat: +match.latitude);
          }
      });

------------------------------------------------------------------------

#### reverseGeocode(longitude, latitude, callback)

Find the nearest address to the specified location. Upon successful reverse geocoding,
an instance of the OM.lbs.OutputAddress is passed to the callback function.

##### Parameters:

| Name        | Type     | Description                                                                                              |
|-------------|----------|----------------------------------------------------------------------------------------------------------|
| `longitude` | number   | the longitude of the location                                                                            |
| `latitude`  | number   | the latitude of the location                                                                             |
| `callback`  | function | is a user specified function that is invoked when<br>the input address is successfully reverse geocoded. |

------------------------------------------------------------------------

#### reverseGeocodePoint(mapPoint, callback)

Finds the nearest postal address to the specified map location point.
Similar to reverseGeocode but uses a OM.geometry.Point instance which
may be in a projected coordinate system (as opposed to longitude/latitude).
Such a point is typically obtained from the OM.Map's getCursorLocation() method,
and its coordinates are always in the current map universe's SRID.

##### Parameters:

| Name       | Type                                      | Description                                    |
|------------|-------------------------------------------|------------------------------------------------|
| `mapPoint` | [OM.geometry.Point](OM.geometry.Point.md) | a Point geometry                               |
| `callback` | function                                  | callback function on success reverse geocoding |
