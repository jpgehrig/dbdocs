------------------------------------------------------------------------

#### new UnformatedAddress(options)

Address The typical input to the geocoder is a single address.

##### Parameters:

| Name      | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|-----------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `options` | Object | This is an object literal that specifies the Address options. It can have the following properties.<br><br>• id {String} Optional. The id field is used to uniquely<br>distinguish an address in a batch geocoding request. It is optional<br>when geocoding a single address.<br><br>• address {String} Required. the address to be used for geocoding.<br><br>• country {String}. specify the 2-letter country ISO code; the<br>default value for “country” is always “US”<br><br><br>for example an option object:<br>{<br>"id":"1",<br>"address":"1 Oracle drv, Nashua, NH, 03062",<br>"country":"US"<br>} |
