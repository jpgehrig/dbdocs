cURL is an open source, command-line tool for transferring data with URL syntax, supporting various protocols including HTTP and HTTPS.

The examples within this document use cURL to demonstrate how to access theDatabase REST APIs.

To use cURL to access the REST API:

- Install cURL, as described in [Quick Start.](QuickStart.md)

- In a command window, set the cURL environment variable, `CURL_CA_BUNDLE`, to the location of your local CA certificate bundle. For information about CA certificate verification using cURL, see: <http://curl.haxx.se/docs/sslcerts.html>.

- Invoke cURL and specify one or more of the command-line options defined in the following table, as required, to direct its execution

  | cURL Option                    | Description                                                                                                                                             |
  |:-------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------|
  | `-d, --data @file.json`        | Identifies the request document, in JSON format, on the local machine.                                                                                  |
  | `-F, --form @file.json`        | Identifies form data, in JSON format, on the local machine.                                                                                             |
  | `-H`                           | Defines one or both of the following:<br>• Content type of the request document<br>• Custom header, `X-ID-TENANT-NAME`, to identify the identity domain |
  | `-i`                           | Displays response header information.                                                                                                                   |
  | `-u, --user username:password` | Specifies the user name and password for the \<ProductName\> account.                                                                                   |
  | `-X`                           | Indicates the type of request (for example, GET, POST, and so on).                                                                                      |

The following is an example syntax for cURL command:

    curl -i -X GET -u <username>:<password> -H <request-header>:<value> https://<subdomain>.<domain>.com/<path>/<resource-path>
